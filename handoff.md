
## Session: 2026-11-14 ET
**Environment:** Antigravity IDE
**What was done:**
- Diagnosed MB Life low reel views: small follower base (IG 15, FB 539), flyers fail watch time and sends; Decker reel hit 152 because Decker shared it
- Single event reels now post as FB + IG Stories; 39 upcoming schedule rows converted
- New weekly weekend roundup reel (events.mjs --roundup), flyer-grid thumbnail, venue IG collab invites, venue "share it" email (max every 13 days)
- First roundup r-20261120-weekend built and scheduled Thu Nov 19 12:00

**What's live / deployed:**
- Local Mac pipeline only (mb-social ui-reels + rotation); launchd job picks up the changes

**Next up:**
- Confirm the first Story (Fleetwood, Nov 14 13:17) in rotation/post-log.json
- Build roundups for Nov 27, Dec 4, 11, 18, 25 after Yeti reviews the first
- Insights agent: Yeti regenerates Meta token with read_insights + instagram_manage_insights, then build the collector + weekly analyst

**Notes for other environments:**
- Story posts have no caption or link; add link stickers by hand in the app if wanted