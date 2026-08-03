## Session: 2026-08-03 ET (continued, pt 5)
**Environment:** Antigravity IDE
**What was done:**
- DLVL wine count 9 → 11 everywhere (chip, description, itinerary, SEO FAQ) (122a213)
- Color/energy pass on /wineries (9592bce): new brand tokens C.wine/#6B1F2E, C.wineDeep/#3A0F1A, C.rose/#C97B9A; merlot radial glows on dark sections + rosé blush on cream sections ("page deepens like a glass of red"); scrolling now-pouring marquee of real bottle names on a bordeaux band (reuses .scoreboard-ticker animation, pauses on hover); two fixed-background parallax quote breaks - Chateau Fontaine 5-bottle lineup ("Walk the boulevard. Follow the pour.") and Brengman rack ("Ask Darlene where to start.")
- All verified live on production via Playwright text checks + screenshots

**What's live / deployed:**
- Everything through 9592bce on manitoubeachmichigan.com/wineries: scrub hero, 11 wines, marquee, parallax breaks, wine gradients

**Next up:**
- Boathouse at Michigan Gypsy: hours, offerings, photos still pending
- Marquee wine list is hardcoded in WineriesPage.jsx (NOW_POURING_WINES) - update when lineups rotate
- iOS shows parallax breaks as static photo bands (fixed-bg unsupported) - same as DL-boat pattern

**Notes for other environments:**
- Wine tokens now in src/data/config.js for reuse on other pages