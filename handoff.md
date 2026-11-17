
## Session: 2026-11-17 ET
**Environment:** Antigravity IDE
**What was done:**
- Pulled live FB view counts for all 16 OnPoint reels: Shields Up 355 (posted after the Live flip), the other 15 at 0 to 20 (Development-mode era). No comments on any; at most 1 like each.
- Built tools/fb-redo.mjs + social/fb-redo.json: reposts those 15 to Facebook only, one a day at noon ET, Nov 18 to Dec 1, and deletes each old reel only after the new one returns a live link. The Nov 12/13 double post gets one repost and both old copies deleted.
- Installed launchd com.yetigroove.onpoint-fb-redo (12 to 5 pm hourly). Daily 6 pm post unchanged.

**What's live / deployed:**
- fb-redo launchd job on the Mac Studio (not committed to git yet)

**Next up:**
- Check social/fb-redo-log.json after Nov 18 noon run: new link + old reel deleted
- Unload com.yetigroove.onpoint-fb-redo after Dec 1

**Notes for other environments:**
- OnPoint FB will show 2 reels/day (noon redo + 6 pm daily) until Dec 1. Instagram and YouTube not touched.