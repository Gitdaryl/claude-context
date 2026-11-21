## Session: 2026-11-21 ET (afternoon)
**Environment:** Antigravity IDE
**What was done:**
- Sam Quisenberry portal: email turned on. Yeti made a Resend key named `sam-portal` and added yeti@ as a Workspace alias; Claude added the other four settings and deployed.
  - From `YetiGroove <yeti@yetigroove.com>`, replies and notices to daryl@, Sam's address is his statefarm.com one (taken from his own emails in Gmail).
  - New admin-only action `mailtest` sends the exact email Sam would get to Yeti's address instead. One test sent; it arrived in the inbox, not spam.
- Earlier today: finished-video flow built and live (captions, end card, Yeti's check, Sam's Post it / Needs a fix).

**What's live / deployed:**
- https://samquisenberry.vercel.app, redeployed Nov 21 afternoon. `/api/health` shows `email: true`, `samEmail: true`.
- Nothing has been sent to Sam. Board is 11 draft rows. Not committed to git.

**Next up:**
- Yeti: look at the test email ("[TEST] Your video is ready to check: Meet Sam") and the sample video in ~/Previews.
- Yeti: get Sam's office phone and State Farm footer line for the end card (`data/end-card.json`).
- Yeti still owes from Nov 20: help clip by ear, Show/Skip the five winter looks, read the 11 scripts, send Sam his link, tell him looks are $24.
- Next builds: schedule menu, three poster samples, b-roll. Posting to Meta stays blocked on Sam's access.

**Notes for other environments:**
- Sam's emails go to a State Farm mailbox and the link carries his portal key. Switch to a keyless link with `SAM_EMAIL_LINK=plain` on the Vercel project if that becomes a concern.
- `vercel env add` hangs after saving unless run with `--non-interactive` and stdin closed.