## Session: 2026-08-03 ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- Continued Manitou Beach wineries work (3 open tasting rooms shipped earlier: aa5a59e)
- Fixed itinerary time column overflowing into bullet dots (a9ae9bb), verified live via Playwright screenshot
- Per Yeti: hid the whole wine program until it launches - WINE_PROGRAM_LIVE=false flag in src/data/wineries.js hides passport widget, stamp buttons, ratings, scorecard, season standings, passport how-it-works, awards ceremony (one-line flip to relaunch) (b2ac00c)
- Meckleys Flavor Fruit Farm hidden via `hidden: true` venue flag (not signed up yet); itinerary Meckleys stops kept as code comments; trail copy reworked without them
- /rate page still reachable by direct URL only (no links to it while hidden)

**What's live / deployed:**
- Commits aa5a59e, a9ae9bb, b2ac00c on main → Vercel auto-deploy to manitoubeachmichigan.com/wineries

**Next up:**
- Yeti sent 3 photos of Chateau Fontaine bottles at Ang & Co (pasted in chat, not saved to disk) - need the files (Desktop or repo) to add a photo strip to the Ang & Co card
- Tasting hours for the 3 open rooms; confirm Boathouse/Michigan Gypsy name + phone
- Higgsfield scroll-scrub hero (cork pop / wine splash) awaiting greenlight
- Flip WINE_PROGRAM_LIVE + unhide Meckleys when program/partnership are real

**Notes for other environments:**
- Wine program hiding is a data flag, not deleted code - src/data/wineries.js top of file