
## Session: Oct 11 2026 ~12:30am ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD: Bleeker before/after (Desktop/onpoint assets) added to the home page. The two drone shots differed in size and angle; the before was SIFT-aligned onto the after and both cropped to a shared 4:3 (1200x900 WebP, named tarp-reroof-* so no street name is in a public URL)
- Home "Recent work" is now 3 sliders, newest first (tarp to new roof, Milford, flat roof); the tarp photo moved beside the "Roof open at 3am?" headline in the storm section
- Word-of-mouth copy: "our three most recent jobs" became "three of our recent jobs, including the two-story re-roof" (Bleeker is newer and not on the pin map)
- Fixed: commit 8875f0c hand-edited the generated terms.html, so any build reverted the tablet/phone opt-in wording; ported into build_pages.py terms()

**What's live / deployed:**
- onpointjd.com home: ff9d3f3 + d1d8239 on origin/master, Vercel READY, screenshot-verified desktop + phone

**Next up:**
- ~/Projects/on-point-jd local master is ahead 8 / behind 2: 5 unpushed commits from other Oct 10 sessions (stationery, warranty cert, thank-you email, SMS forward to office app) + the terms port. Shipped photos from a clean clone to avoid deploying them. Yeti decides: git pull --rebase && git push (check OFFICE_OPTOUT_URL + OPTOUT_SECRET in Vercel first)
- Town + month + customer OK for the 3 before/after jobs turns them into /projects pages (engine already in tools/projects)

**Notes for other environments:**
- New before/after pairs: drop the photos in Desktop/onpoint assets and ask the IDE. The two shots rarely line up and must be aligned before going in a slider.