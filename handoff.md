## Session: 2026-11-23 ET
**Environment:** Antigravity IDE
**What was done:**
- Inbox Watch (ops-watch, lead-catcher, heartbeat) diagnosed. The watchers were NOT down: a brief landed every day since Sep 24. What was broken was the heartbeat, which texted a false "Inbox watchers down, mail is NOT being triaged" every day from Sep 25 to Nov 23 because the backup token line in secrets.env was empty.
- Found the long-standing fix on the board was wrong. Read from the installed Claude CLI (2.1.177): a `claude setup-token` token is inference-only and cannot load claude.ai connectors (Gmail, Notion). Pasting it would have cut the watchers off from mail every day.
- Fixed: heartbeat no longer flags the empty token; ops-watch, lead-catcher and sitdown-watch now drop the token on purpose; their sign-out texts now say "sign in again" instead of "run setup-token"; README and the secrets.env note corrected.
- Verified: heartbeat ran under launchd at 13:03, "healthy: ops-watch 1h, lead-catcher 0h", exit 0, no text. Alarm paths still fire in a sandbox test (signed-out morning, 48h stale).
- Real cause of the three outage mornings (Sep 24, Oct 24, Nov 23): Claude gets signed out on the Mac about every 30 days. Signing in again fixes it; retries at 9, 12, 3 and 6 recover the day. Why it signs out is not established.

**What's live / deployed:**
- Local only, nothing pushed. Edited files in ~/.claude/tools: inbox-watch/heartbeat.sh, inbox-watch/README.md, inbox-watch/secrets.env (comment only), ops-watch/run.sh, lead-catcher/run.sh, sitdown-watch/run.sh. Originals in ~/.claude/tools/inbox-watch/backup-2026-11-23/.

**Next up:**
- Tomorrow's 07:00 and 07:20 runs are the first real runs of the edited watcher scripts. If either fails, the 11:07 heartbeat texts.
- Lead Catcher has 1 person waiting today: Dr. Joe Profit (jail photo for the juveniles piece). Draft reply is in Gmail.
- Expect the next sign-out around Dec 23. The text will say to sign in again.
- Not touched: heather-weekly and social-insights still tell Yeti to run setup-token. That is right only if those jobs use no connector (social-insights uses none; Heather not checked).

**Notes for other environments:**
- Do not recommend `claude setup-token` for any scheduled job that uses a claude.ai connector. Board row "Arm backup Claude login for inbox watchers (setup-token)" is closed as the wrong fix. Board row "Arm Inbox Watch SMS" is closed, texts are proven.