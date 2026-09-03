## Session: 2026-09-03 ET
**Environment:** Antigravity IDE

**What was done:**
- Yeti asked whether important email could alert him instead of getting buried. Investigated before building and found the system already existed: `ops-watch` and `lead-catcher` in `~/.claude/tools/`, with the full `Ops/*` and `Lead/*` Gmail label taxonomy already created.
- Found it had been dead for 9 days. `ops-watch` ran from cron, cron cannot unlock the login Keychain where Claude Code keeps its OAuth token, so `claude -p` exited in 3 seconds with "Not logged in" every morning since Aug 26 and reported nothing. `lead-catcher` was never scheduled at all, it had run exactly once on Aug 25.
- Moved both jobs off cron onto LaunchAgents: `com.yetigroove.ops-watch` (07:00), `com.yetigroove.lead-catcher` (07:20). LaunchAgents run inside the GUI session (Keychain reachable) and fire a missed job on wake instead of skipping the day. Removed the ops-watch cron line; the three `sync-daryl.sh` entries were left untouched.
- Built `~/.claude/tools/inbox-watch/`: `notify.sh` (desktop plus SMS through the already-deployed `manitoubeachmichigan.com/api/internal-alert` relay, capped at 6 texts a day), `heartbeat.sh` plus `com.yetigroove.inbox-heartbeat` at 11:07, and `README.md`.
- The heartbeat is a dead man's switch. It checks brief files and their age, not whether a process is running, because a watcher that cannot run also cannot tell you it did not run. Both runners now grep specifically for "Not logged in" and alert on it, and both say something on quiet days so silence stays meaningful.
- Verified end to end: ops-watch ran clean under launchd and produced a correct brief.

**What's live / deployed:**
- Three LaunchAgents loaded and registered. Nothing was deployed to any server; all changes are local to the Mac.
- First real brief in 9 days found a genuine P1: `Daily Business Spotlight` on Gitdaryl/Manitou-Beach has failed every scheduled run Aug 29 through Sep 2, dying in ~35s.
- It also correctly declined to alert on two things: AI Holly failures that recovered on their own, and a Stripe message that was a real $9.99 sale rather than an outage.
- Four rows filed on the Master Task Board, one of them Done.

**Next up:**
- Yeti must paste `ALERT_TOKEN` into `~/.claude/tools/inbox-watch/secrets.env`. Until then alerts stop at the desktop and nothing reaches the phone. Pulling the secret was blocked by the safety classifier, correctly, so this step is his.
- Import `~/.claude/tools/unsub-sweep/yetigroove-filters.xml` into Gmail to archive the bulk mail. 67 filters, already written, excludes all banking, ops, and human senders.
- Fix the Daily Business Spotlight workflow. Check the existing Node 20 to 24 Backlog row first, it names that same workflow file.
- `lead-catcher` was still running its first full pass when the session ended. Check `~/.claude/tools/lead-catcher/briefs/2026-09-03.md`.

**Notes for other environments:**
- Inbox triage lives on the Mac, not in the cloud. It only runs when the Mac is awake and logged in. Cowork and Mobile cannot trigger it.
- If "Not logged in" ever returns, the permanent fix is `claude setup-token` into `CLAUDE_CODE_OAUTH_TOKEN` in that same secrets file.
- General rule worth carrying: any unattended watcher needs a separate check on its output, not its process.