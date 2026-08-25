## Session: 2026-08-25 ET
**Environment:** Antigravity IDE

**What was done:**
- Researched pro Gmail-with-Claude patterns; confirmed the claude.ai Gmail connector was ALREADY authenticated (Yeti had been logging in manually for access he already had)
- Diagnosed the inbox with real data: 6,032 messages / 5,731 unread / 1 empty user label / 0 stars. Three identities (hotmail forward, daryl@, admin@) land undivided, so the Aug 23 human-vs-machine split is unenforced at delivery
- Built Ops Watch, the scheduled "tell me when something breaks" job, in ~/.claude/tools/ops-watch/
  - OPS-WATCH.md: classification spec (Broken / Deadline / Security / Billing), grounded in 90 days of the actual mailbox, not guesses
  - run.sh: headless `claude -p` runner, lockfile, logging, osascript notification
  - Gmail labels created: Ops/1-Broken, Ops/2-Deadline, Ops/3-Security, Ops/4-Billing
  - Read-and-label tools only. No send, reply, forward, trash, or delete in the allowlist. Shell owns the file write so Claude has zero write access
  - Verify-before-alert: it runs `gh run list` to confirm a failure is still failing, and collapses repeat failures into one streak line
- Verified end to end with two live runs. Second run proved dedupe (no repeat alerts on already-labeled threads)

**What's live / deployed:**
- Ops Watch installed and working at ~/.claude/tools/ops-watch/, run manually so far
- 4 Gmail labels created, 3 GitHub failure threads labeled Ops/1-Broken
- Cron NOT installed: the crontab edit was blocked by the auto-mode classifier. Yeti must paste one line (in Next up)

**Next up:**
- Install the schedule:
  (crontab -l 2>/dev/null; echo "0 7 * * * /Users/darylyoung/.claude/tools/ops-watch/run.sh >/dev/null 2>&1") | crontab -
- FIX: Manitou-Beach "Daily Business Spotlight" has failed 30 for 30 runs since 2026-07-27, all on commit 471e663. The spotlight feed on the live site is stale
- The Gmail -> Hotmail forward is still alive and still bouncing 550 5.7.509 (7 bounces since June). The Aug 23 decision was to reverse that direction; it was never fully done
- Two emails to Becky re Food Truck Locator (sipandsweets@yahoo.com and sipandsweets2024@yahoo.com) both hard-bounced 552 address not found. She never received either. Needs a correct address
- Vercel: 1 misconfigured domain, notified 5 times since June 14, never resolved
- FormSubmit on spotted-owl-site.vercel.app may never have been activated (Jul 17 activation mail unread), so that form may be dead
- Deadlines ahead: Google AI Studio billing migration Sep 14 2026; Google Cloud 2SV required Oct 20 2026
- Remaining builds from the email plan, in order: lead catcher, morning brief, unsubscribe sweep, email-to-Notion
- claude.ai n8n MCP server needs re-auth (shows "Needs authentication"; two stale duplicate entries also fail to connect)

**Notes for other environments:**
- Gmail, Drive, Calendar, Notion, Vercel, Higgsfield MCP connectors all verified connected at CLI level, and they survive headless `claude -p` runs. That means scheduled Claude jobs CAN touch Gmail
- Writes into ~/.claude/ are blocked as a sensitive path in headless runs. Have the shell do the file write and give Claude read-only tools