## Session: 2026-08-03 ET
**Environment:** Antigravity IDE
**What was done:**
- Dave (Manitou Beach Village) asked to feature the 3 open wine tasting rooms on manitoubeachmichigan.com/wineries
- Updated winery data: Devils Lake View Living now pouring Brengman Family Wines (9 organic wines, glass/bottle, fixed "Brenman" misspelling), Ang & Co now pouring Chateau Fontaine (8 wines, taste/glass/bottle, removed French Road Cellars), Boathouse renamed "The Boathouse at Michigan Gypsy" pouring Amoritas Vineyards
- Faust House stays "Opening Soon" with Cherry Creek Cellars
- New "Now Pouring" section after the hero: 3D-tilt cards per open room, pour-format chips, winery links, anchor-scroll to detail cards
- Hero: scroll parallax background + pulsing "3 Village Tasting Rooms Now Pouring" badge
- Passport/stamp system now counts only open rooms (7 total stops); Faust House can't be stamped until it opens
- Refreshed all stale "Opening Spring 2026" copy on wineries page + Village page; SMS opt-in reframed to room #4 + trail events
- SEO: new FAQ schema entry + meta description naming the three tasting rooms

**What's live / deployed:**
- Pushed to main (commit aa5a59e) → Vercel auto-deploy to manitoubeachmichigan.com

**Next up:**
- Confirm hours for the 3 tasting rooms (currently "call for tasting hours") and Amoritas offerings at the Boathouse
- Confirm "The Boathouse at Michigan Gypsy" name/phone/link with Yeti or Dave (kept old FB link + phone)
- Yeti's scroll-scrubbed 3D hero idea (Higgsfield cork-pop/wine-splash frame sequence) - slot is ready in the hero, needs greenlight on credit spend
- Interactive wine tour shelved until full program next season

**Notes for other environments:**
- If Dave replies with hours or the 4th room opening date, edits go in src/data/wineries.js (Manitou-Beach repo)