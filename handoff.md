## Session: 2026-07-18 ET
**Environment:** Antigravity IDE
**What was done:**
- Fixed the manitoubeachmichigan.com homepage events ticker racing. Root cause: the Jul 16 marquee seam fix added `width: max-content` to the shared `.marquee-track` class, so the homepage ticker's fixed 35s animation suddenly spanned the full 4x-repeated content instead of half a viewport, making it fly.
- Restored the original gentle crawl (~20px/s) by scaling the animation duration to content width in the EventTicker component (HomePage.jsx), keeping the seamless-loop fix intact. Men's club ticker pace untouched.
- Built, committed (a6a0e70), pushed to main, Vercel production deploy Ready, and verified the live speed headlessly with Playwright (measured exactly 20px/s).

**What's live / deployed:**
- manitoubeachmichigan.com production: homepage ticker back to original crawl speed.

**Next up:**
- Nothing pending from this session.

**Notes for other environments:**
- The homepage EventTicker now sets its own animation-duration in JS (35s x trackWidth/viewportWidth). If ticker speed ever needs tuning, change the 35 in HomePage.jsx EventTicker, not the .marquee-track CSS.