## Session: 2026-06-24 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed "events disappeared off the events page" on Manitou Beach (MB = manitoubeachmichigan.com, /root/Manitou-Beach on Yeti VPS).
- Root cause: during a Notion key rotation, the `NOTION_TOKEN_EVENTS` env var in Vercel got **blanked to empty** (variable existed, value gone). The events API sent an empty `Bearer` token → Notion `401` → api/events.js silently caught it and returned `{events:[],recurring:[]}`, so the page looked empty. Events were never lost — Notion still had 128+ events.
- Confirmed via a temporary gated debug endpoint (`?debug=mbdiag2026`) that returned `tokenPresent:false, notionStatus:401`. Debug endpoint was reverted/removed after.
- Yeti re-pasted the Events integration secret into Vercel (All Environments). Redeployed → events restored (API returns 128 events + 3 recurring, verified live).
- Hardened api/events.js + src/pages/HappeningPage.jsx so this can't fail silently again (commit 17f2391):
  - Pre-flight guard: missing NOTION_TOKEN_EVENTS/DB → fail fast + SMS alert to ADMIN_PHONE.
  - Notion auth/query failures now return HTTP 503 `{error:'events_unavailable'}` with `Cache-Control: no-store` (never cached, monitorable) instead of silent empty 200.
  - 30-min SMS alert cooldown to avoid storms.
  - Frontend shows a clear "can't load events right now / Refresh" state instead of the misleading "quiet week / no events" empty state.
  - Verified with local `vite build` (BUILD OK) before pushing.

**What's live / deployed:**
- Pushed to GitHub Gitdaryl/Manitou-Beach main → Vercel auto-deploy. Commits: redeploy for token (7c19062), diag + revert (d637ce6/a993d2e), hardening (17f2391).
- Events page is functional again.

**Next up / open items:**
- Verify `ADMIN_PHONE` is set in Vercel env — the new SMS alert only fires if it's present (it's NOT in .env.example). If unset, add it so future outages actually page Yeti.
- Optional: the same silent-empty-on-Notion-failure pattern exists in other NOTION_TOKEN_EVENTS endpoints (event-detail, hero, promotions, ~44 total) and the other token feeds (business, dispatch, pois, page-sponsors). Consider extracting a shared Notion helper that alerts/503s consistently.
- If other keys were rotated in the same session: NOTION_TOKEN_BUSINESS and NOTION_TOKEN_HERO confirmed working; double-check NOTION_TOKEN_DISPATCH / NOTION_TOKEN_POIS / NOTION_TOKEN_PAGE_SPONSORS.

**Notes for other environments:**
- Key lesson: a rotated/blanked Notion token in Vercel manifests as "data disappeared from the site" with no error. Check the relevant `NOTION_TOKEN_*` env var value first.