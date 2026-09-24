
## Session: 2026-09-23 ET
**Environment:** Antigravity IDE
**What was done:**
- AI Holly Sep 24-27 reel: 5 of 10 events had no card. Fixed 4 matcher bugs in holly-reel-kit/reel/build.mjs (street-address Location borrows venue from title pipe prefix; full-name-first rule now falls back to short variants when full name appears fewer times than the venue has events, with adjacent hits collapsed; 12s same-venue dedup skipped across a day word; event-name fallback treats & as "and" with 0.80 bar for long names). All 10 anchor.
- Trimmed the opener: reel now starts at "Here's your weekend" (cut at 13.8s of the HeyGen take), 73s.
- Re-rendered locally: ~/Projects/holly-reel-kit/holly-2026-09-24-OVERLAID(-web).mp4. NOT uploaded, NOT sent.

**What's live / deployed:**
- Nothing. build.mjs changes are local and uncommitted (holly-reel-kit still has no remote).

**Next up:**
- Yeti QA the reel, then upload/publish (`node run.mjs --video <trimmed> --thursday=2026-09-24 --keep-transcript --upload --publish`).
- Data: Cherry Creek Location fields are bare street addresses again; Wheels and Wine + Tyler Aukerman have blank Cost; Bike Night time shows 10:00 PM (check).
- Push holly-reel-kit to GitHub.

**Notes for other environments:**
- Opener trim was a one-off for this week, not built into the pipeline.