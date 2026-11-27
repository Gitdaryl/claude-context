## Session: Nov 27 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- YetiGroove homepage: menu for stray pages, Google review carousel with live score, Lost Customer Check teaser
- One shared nav bar on 18 studio pages (site-nav.css, site-nav.js; menu is edited in tools/site_nav.py, then run it and tools/build_questions.py)
- Live testing found jump links from other pages stopping short (scroll sections grow after the first image loads); fixed in site-nav.js

**What's live / deployed:**
- yetigroove.com: 155a707, 8b0020c, ab9b7de (all verified live; 48/48 jump link loads, 18 pages pass)

**Next up:**
- Board W-09 stays open for canonical/OG tags
- Homepage contact form instead of mailto
- Yeti to check the spiro.media link and "Closes 5 AM" hours on the Google profile
- Yeti to paste full text of 4 cut-off Google reviews for more cards

**Notes for other environments:**
- Local web tests that serve images instantly hide load-timing bugs. Delay images when testing jump links.