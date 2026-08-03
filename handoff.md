## Session: 2026-08-03 ET (continued, pt 3)
**Environment:** Antigravity IDE
**What was done:**
- Ang & Co card photos: Yeti dropped 2 Chateau Fontaine bottle shots into public/images/wineries/; resized 6000px/11MB originals to 1200px web JPGs (ang_co_fontaine_01/02.jpg, ~170KB), removed originals, wired onto the Ang & Co card photo strip (commit 0193eac)
- Earlier this session: 3 tasting rooms marked open + Now Pouring section (aa5a59e), itinerary layout fix (a9ae9bb), wine program + Meckleys hidden behind flags (b2ac00c)

**What's live / deployed:**
- All commits on main → Vercel auto-deploy to manitoubeachmichigan.com/wineries

**Next up:**
- Tasting hours for the 3 open rooms; confirm Boathouse/Michigan Gypsy name + phone
- Higgsfield scroll-scrub hero (cork pop / wine splash) awaiting greenlight
- Flip WINE_PROGRAM_LIVE in src/data/wineries.js + unhide Meckleys when ready
- Photos for Devils Lake View Living and Boathouse cards would match Ang & Co treatment

**Notes for other environments:**
- Wine program hiding is a one-line flag (WINE_PROGRAM_LIVE) in src/data/wineries.js, nothing deleted