
## Session: Nov 5 2026 ET (Watch how + report card link)
**Environment:** Antigravity IDE
**What was done:**
- Watch how button with the Liam tour added to /my-events
- Report card texts now carry 30-day signed owner links

**What's live / deployed:**
- Commit 396ad15 on main, deployed. Video plays in production; live API rejects fake links.

**Next up:**
- Yeti's verdict on the Fix Your Event reel
- Dec 1: check the first report card texts in Vercel logs

**Notes for other environments:**
- A real production-signed link is untested until Dec 1. CRON_SECRET in .env.notion.tmp is stale.