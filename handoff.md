## Session: 2026-08-03 ET (continued, pt 6)
**Environment:** Antigravity IDE
**What was done:**
- Parallax quote changed to "Walk the village. Follow the pour." per Yeti (0c18d9b)
- Full boulevard → Village copy sweep across wineries + village pages; street addresses keep "Blvd" (7c771c2, 0c890dd)
- Boathouse at Michigan Gypsy hours added: Sun-Mon 11-3, Tue closed, Wed 11-4, Thu 11-5, Fri-Sat 9-5 (7c771c2)
- Scrub hero navbar overlap fixed earlier (73f4b8b)
- All verified live: zero "boulevard" in the deployed wineries bundle, hours live

**What's live / deployed:**
- Everything through 0c890dd on manitoubeachmichigan.com - all 3 open tasting rooms now have real hours

**Next up:**
- Boathouse: Amoritas offerings + photos still pending (only remaining gap on the wineries page)
- Marquee wine list hardcoded in WineriesPage.jsx (NOW_POURING_WINES) - update when lineups rotate

**Notes for other environments:**
- Full day of wineries work: 3 rooms featured, hours, photos, program hidden behind WINE_PROGRAM_LIVE flag, cork-pop scrub hero, wine-red color pass, marquee, 2 parallax breaks