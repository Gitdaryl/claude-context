
## Session: 2026-11-06 ET (event reels on auto, weekly page fix)
**Environment:** Antigravity IDE
**What was done:**
- Fixed weekly event pages: no more 'This event has passed', shows Every Wednesday (c537480, verified live)
- Built 47 event reels through Dec 26 with AI flyers and own FB and IG captions; all scheduled in mini-ads/rotation/schedule.json on the mb-daily-post job
- post.mjs re-reads the calendar before each post and refuses changed or cancelled events; refusal tested

**What's live / deployed:**
- Commit c537480 on main. First auto posts Sat Nov 7: Cat Canyon 9:07, Eagles 10:07, Dine in the Vines 1:17

**Next up:**
- Check rotation/post-log.json after Nov 7 and confirm the first three, including whether the IG @mentions took
- New events still need a scene and a JOBS line by hand
- Stale site copy row still open; Tip-Up number needs Yeti

**Notes for other environments:**
- The Mac must be on for scheduled posts. A missed post texts Yeti.