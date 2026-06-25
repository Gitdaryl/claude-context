## Session: 2026-06-24 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Fixed "events disappeared off the events page" on Manitou Beach (MB = manitoubeachmichigan.com, /root/Manitou-Beach on Yeti VPS).
- Root cause: a Notion key rotation **blanked the value** of env vars in Vercel (the vars stayed, the secrets were wiped). `NOTION_TOKEN_EVENTS` → empty → api/events.js sent an empty Bearer → Notion 401 → code silently returned `{events:[],recurring:[]}`, so the page looked empty. Same thing had emptied the **home-page business listings** that morning via a blanked `NOTION_TOKEN_BUSINESS` (Yeti re-pasted that one ~3h earlier, so businesses recovered first). Data was never lost.
- Proved it with a temporary gated debug endpoint (`?debug=mbdiag2026`) → `tokenPresent:false, notionStatus:401`. Removed/reverted after.
- Yeti re-pasted the Events secret into Vercel (All Environments). Redeploy → events restored (API returns 128 events + 3 recurring, verified live).

**What's live / deployed (GitHub Gitdaryl/Manitou-Beach main → Vercel auto-deploy):**
- 7c19062 redeploy to pick up token · d637ce6/a993d2e diag + revert · 17f2391 events hardening · c76a80e site-wide Notion alerting.
- Events page + home business listings functional again.
- Hardening shipped so this never fails silently again:
  - api/events.js: pre-flight config guard, 503 `{error:'events_unavailable'}` + `no-store` on Notion failure, SMS alert, and a friendly "can't load events / Refresh" UI instead of the misleading empty state.
  - api/lib/notionGuard.js (NEW): `alertOutage()` = throttled SMS to ADMIN_PHONE, 30-min per-feed cooldown. Wired into every public Notion-backed read feed: businesses (home + slots), hero, promotions, food-trucks, community-pois, dispatch-articles, village-businesses, winery-ratings, winery-wines, page-sponsors, lllc-sponsors. Failure paths also set `Cache-Control: no-store`. Legitimate "no results"/config-fallback returns left untouched.
  - Verified with local `vite build` (BUILD OK) + `node --check` on all 12 files before each push.

**Next up / open items:**
- **Verify `ADMIN_PHONE` is set in Vercel** — the SMS alerts only fire if it's present (it's NOT in .env.example). Without it you still get the on-page error + 503/no-store, just no text. This is the one thing left to make the new alerting actually page Yeti.
- If other keys were rotated in the same session: NOTION_TOKEN_BUSINESS + NOTION_TOKEN_HERO confirmed working; double-check NOTION_TOKEN_DISPATCH / NOTION_TOKEN_POIS / NOTION_TOKEN_PAGE_SPONSORS values aren't blanked.
- Deferred (same pattern applies if wanted): concierge-events/concierge-businesses, stays, dispatch-ads, admin-articles, categories, and the cron/write paths.

**Notes for other environments:**
- Key lesson: a rotated/blanked Notion token in Vercel shows up as "data disappeared from the site" with NO error. Check the relevant `NOTION_TOKEN_*` env var value FIRST. The site now SMS-alerts on these failures instead of going quiet.