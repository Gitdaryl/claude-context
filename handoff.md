## Session: 2026-08-03 ET (continued, pt 4)
**Environment:** Antigravity IDE
**What was done:**
- Hours + photos (8ca846d): Ang & Co and Devils Lake View Living real hours on cards (DLVL goes daily 10-5 after Labor Day - comment in wineries.js), 3 Brengman photos + Ang & Co storefront wired, Faust House pill now "Coming Soon"
- Cork-pop scroll-scrub hero shipped (82fd02d): concept stills generated in Higgsfield (Soul Cinema, 4 options), Yeti supplied his own cork-pop reference; GPT Image 2 made the matching "corked at rest" start frame; Seedance 2.0 6s 21:9 1080p locked-camera video (54 credits); 73 WebP frames at 1280w (2.7MB); new CorkScrubHero = sticky 260vh canvas scrubber, content parallax/fade, reduced-motion fallback to static hero
- Fixed: overflow-x hidden on html/body breaks position:sticky in Chrome - switched to overflow-x: clip globally (Layout.jsx GlobalStyles) + page root. Documented in project CLAUDE.md (40f0f54)
- Verified locally via Playwright: frame scrub at 3 depths + keyboard scroll SOP pass

**What's live / deployed:**
- All on main → Vercel: manitoubeachmichigan.com/wineries now has the scrub hero

**Next up:**
- Boathouse at Michigan Gypsy: hours, offerings, photos still pending from Yeti/Dave
- Source video kept at scratchpad (temp) - cork-pop.mp4 also retrievable from Higgsfield job 43b78484-d366-4942-a461-8fafcb8a2e53
- Watch for old-Safari (<16) overflow-x:clip fallback if anyone reports horizontal scroll

**Notes for other environments:**
- Scrub kill-switch: SCRUB_FRAME_COUNT=0 in WineriesPage.jsx restores static hero instantly