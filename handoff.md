## Session: 2026-11-21 ET
**Environment:** Antigravity IDE
**What was done:**
- Sam Quisenberry portal (~/Projects/sam-portal), step 1 of the finished-video flow, on Yeti's "go on step 1":
  - `tools/finish.mjs`: captions from the approved words (whisper supplies timing only), loudness to about -16 LUFS, 3 second text end card from `data/end-card.json`, a full-size file plus a 720p portal copy. Free, runs on the Mac, about 12 seconds per reel.
  - Portal: finished video hidden from Sam until Yeti taps Show to Sam. Sam then sees a player with Post it / Needs a fix (four reasons), and can take back a yes. Admin gets Redo captions and end card, Make it again, and a "What HeyGen reads aloud" respelling field.
  - Watcher (`tools/watch.mjs`): finishes each render, uploads to the private Blob store, texts Yeti, tells him what Sam answered, sends one reminder close to the post date.
  - Email to Sam through Resend: built, tested against a mock, OFF until keys are set.
- Earlier in the day: design answers for the schedule menu and the poster upsell, filed on the board as proposals.

**What's live / deployed:**
- https://samquisenberry.vercel.app deployed Nov 21 with the above. Live test with a throwaway row passed 10 checks (played in real Chrome), row and file removed. Board is back to 11 draft rows.
- Nothing committed to git (not asked).

**Next up:**
- Yeti: watch ~/Previews/2026-11-21 Sam finished video sample (captions + end card).mp4.
- Yeti: turn on Sam's email (4 `vercel env add` commands in the board row and the README), get Sam's office phone and State Farm footer line for the end card.
- Yeti still owes from Nov 20: help clip by ear, Show/Skip the five winter looks, read the 11 scripts, send Sam his link, tell him looks are $24.
- Next builds, in order: schedule menu, three poster samples, b-roll. Posting to Meta stays blocked on Sam's access.

**Notes for other environments:**
- The portal tells Sam "It will post Tue..." after his yes. Nothing posts by itself yet; Yeti posts by hand on that date.
- Every finished video waits for Yeti's tap on Show to Sam (switch: yetiChecksFirst in tools/watch.mjs).
- A "face looks off" report from Sam re-makes that video once by itself, about 36 HeyGen credits.