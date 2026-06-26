## Session: 2026-06-26 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed the Manitou Beach `community-pois` feed outage (SMS alert "Notion query failed", section blank on site).
- Proved the DB + schema were healthy and readable; isolated the fault to the Notion integration behind `NOTION_TOKEN_POIS` — it had been deleted/revoked (no "Community Pois" bot in the workspace).
- Walked Yeti through the fix: recreate the integration, connect it to the Community POIs DB, paste token into Vercel `NOTION_TOKEN_POIS`, redeploy.
- Verified live: `/api/community-pois` now returns 35 POIs + 3 suppressed. Feed restored.
- Wrote a reusable runbook to the repo: `/root/Manitou-Beach/RUNBOOK-notion-feeds.md` (symptom, diagnose, fix, env-var↔integration↔DB map, duplicate-integration gotcha).

**What's live / deployed:**
- manitoubeachmichigan.com community POIs feed is back up (Vercel redeploy by Yeti).
- New file committed to repo working tree on VPS: `RUNBOOK-notion-feeds.md` (not yet git-committed/pushed).

**Next up:**
- Optional cleanup: one harmless DUPLICATE "Community Pois" integration remains in Notion. Keeper = the one whose Access token matches Vercel `NOTION_TOKEN_POIS`; safe to leave both.
- Consider committing/pushing `RUNBOOK-notion-feeds.md` to the repo.
- Optional: verify the other Notion feeds (events, business, hero, dispatch) tokens aren't at similar risk.

**Notes for other environments:**
- The blank-feed failure pattern (deleted/disconnected Notion integration → token can't auth) is now documented in the repo runbook. Tell: a feed's API endpoint returning its data array WITHOUT the `suppressed`/companion field = it's in the failure branch, not genuinely empty.