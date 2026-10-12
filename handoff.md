## Session: 2026-10-12 ET
**Environment:** Antigravity IDE
**What was done:**
- Priced OnPoint Office as a product, "Field Office": Clone $12-18k + $650-900/mo, Adapted $20-35k + $900-1,200/mo, Custom $40-60k+ + $1,200-1,500/mo. The pick is $15k + $750/mo.
- Built the landing page yetigroove.com/field-office in Yeti-Groove: field-office.html, api/field-office-lead.js, a vercel.json rewrite and media/field-office/.
- Built a 72 s teaser video (16:9 + vertical) from the real app on fake data, with OnPoint's prices blurred. Source is in ~/Projects/field-office-media/video.
- Built the health watcher for app.onpointjd.com. Code: onpoint-office monitor/, api/health.ts monitor mode, digest job_runs record, migration 20261028000000_job_runs.sql.
- Tests: 16 new + 143 related pass. A live dry run passed.

**What's live / deployed:**
- Nothing. All changes are uncommitted in onpoint-office and Yeti-Groove.

**Next up:**
- Board row "switch on the health watcher": db push, MONITOR_TOKEN, deploy, VPS .env + cron. Order is in the row and in monitor/README.md.
- Board row "review /field-office page + teaser", then push Yeti-Groove (PUBLIC repo).
- Supabase Pro for OnPoint backups (Free has none).

**Notes for other environments:**
- Never publish stills 01/03/05/09 in ~/Projects/field-office-media/stills. They show OnPoint's price-book figures.
- The watcher never re-sends customer texts or emails. That is by design.