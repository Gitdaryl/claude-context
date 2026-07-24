## Session: 2026-07-24 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Investigated Kristin (Gypsy Blue Vineyards) report that their events + business listing weren't showing on manitoubeachmichigan.com
- Verified live /api/events feed: UP, 87 events. All 11 Gypsy Blue events in the Notion Event Submissions DB are Status=Published, none stuck in Pending/Review
- Her newest event (Tyler and Meg duo, Aug 1) was submitted today 4:13 PM ET and IS live on /events (verified with headless Playwright screenshot/text check)
- Gypsy Blue Vineyards IS in /api/businesses (enhanced tier, lat/lng + Place ID present), appears on /discover under the Wineries chip in LOCAL BUSINESSES, and on /wineries trail page (all verified live)
- Root cause of her confusion: /discover default "All" view shows only community POIs in the list (businesses list is empty until a category chip is tapped) and the map opens centered on the village at zoom 12, so her Hudson pin (~15 min south) is off-screen

**What's live / deployed:**
- Nothing deployed; no code changed

**Next up:**
- Decide whether to surface paid businesses on Discover's "All" view (list and/or map bounds) so off-village paying businesses like Gypsy Blue aren't invisible by default — design tradeoff, Yeti to call
- Minor: WINERY_VENUES has Gypsy Blue at lat 41.9170 while the geocoded businesses feed says 41.8489 — one of them is wrong, worth reconciling
- Reply to Kristin (draft provided in session)

**Notes for other environments:**
- Nothing is down. Do NOT run the Notion-feed DOWN runbook; feeds are healthy.