## Session: 2026-09-22 ET
**Environment:** Antigravity IDE

**What was done:**
- Debunked a viral 21-posts-a-week schedule. Real data (Buffer 9.6M posts, Mosseri) is 3-5 feed posts/wk + 1-2 stories daily. Explained reels vs stories vs carousels and FB vs IG.
- Built the **Social Desk** at `~/Projects/social-desk`: Opus briefs and grades, Yeti creates, one client until a 3-clean-week graduation gate. RUBRIC (6 checks as right/wrong pairs), CADENCE, DELIVERY, AUTOMATION, SCORECARD.
- **Audited Sunny Skies live and found it DARK since Sep 10.** READY empty, 67 empty-cron hits, daily SMS ignored 12 days. Dispatcher itself healthy and unpaused.
- Root cause is burn rate, not a bug: 4 posts/day needs 28 finished assets a week. Nobody supplies that.
- Confirmed YouTube fails on every post (known ambient wrong-channel issue, safety net working, not worth chasing).
- Corrected docs against memory: Repurpose.io retired 2026-09-08 so the local RUNBOOK is stale, and Isaac is not the supply line, Yeti is.
- Advised NOT to send Isaac the strategy plan (it creates an approval surface). Drafted a shoot-logistics email instead, with one line owning the 12-day gap.
- Built the commercial flat-roof shoot pack: interview-brick method for a client who will not prep, 15 questions, day-by-day shot list, output map (27 assets = ~3.3 weeks runway), plus a no-visible-leak fallback hook after Yeti flagged there may be no leak to show.
- Made a 6-sheet printable field card, rendered to `~/Desktop/Flat-Roof-Shot-Card.pdf`.
- Caught a real print bug: a `@media print` token block on plain `:root` loses on specificity to the dark-theme `:root:not([data-theme="light"])`, so dark-mode machines print near-white on white. Fixed and verified in both host themes.
- Wrote the reusable **client onboarding SOP + fill-in templates** at `~/Projects/social-desk/_template/` so Holly, Joe, MB and YetiGroove follow the same path.

**What's live / deployed:**
- Nothing deployed. Sunny Skies dispatcher untouched, still live and still empty.
- Artifact: Flat Roof Shot Card, https://claude.ai/code/artifact/e48aa380-e4e6-4704-9a47-3518d4283f86
- PDF on the Desktop, 6 pages, prints pure black.
- 14 rows filed on the Master Task Board, 10 marked Today.
- 7 memories saved (social desk, burn rate, directing non-actors, don't send the plan, fact/inference/evidence, print CSS trap, onboarding SOP).

**Next up:**
- Put assets in READY today. The account has been silent 12 days.
- Drop the dispatcher to 2x/day (config server :3847 or dispatcher-admin).
- Add COMMERCIAL and SPOKESPERSON to `captions.json` before shoot footage lands, or new files post in the wrong voice.
- One attempt at the YouTube active-channel lever, then let it go.
- Commercial flat roof shoot starts ~Sep 24 or Fri 26, 3-4 days. Print the PDF: sheets 0 and 5 in the truck, 1-4 up the ladder.
- Get the membrane system (TPO/EPDM/mod bit/coating, tear-off vs recover) from Isaac in a text before he names anything on camera.
- Metal roof Oct 1: scripts written, parked at Yeti's request.
- Week 1 due Wed Sep 30.

**Notes for other environments:**
- `~/Projects/social-desk` is the source of truth. Not a git repo yet.
- `_template/ONBOARDING.md` is the SOP for adding any new client. Step 1 is audit the live account before planning anything.
- The local `Documents/Claude Code/Sunny-Skies/dispatcher/` mirror is STALE: config says `paused:true` (live is false) and its RUNBOOK describes the retired Repurpose.io hop. The VPS copy is authoritative.