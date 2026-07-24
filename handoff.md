## Session: 2026-07-24 (evening ET, part 2)
**Environment:** Antigravity IDE
**What was done:**
- Follow-up to Gypsy Blue diagnosis: Yeti supplied the correct coordinates (41.9169583, -84.3115321)
- Patched Lat/Lng on the Gypsy Blue Vineyards record in the Notion businesses DB (the auto-geocode had placed it ~7 km too far south at 41.8489)
- Verified live /api/businesses now serves the corrected pin; endpoint is Cache-Control no-store, so effective immediately with no deploy
- Confirmed the fix can't be overwritten: businesses.js only auto-geocodes on brand-new submissions, never on reads
- Note: notion-business MCP integration returns 401 invalid token; used the default notion integration instead

**What's live / deployed:**
- Gypsy Blue map pin now at the correct location on manitoubeachmichigan.com (data fix in Notion, no code change)

**Next up:**
- Decide whether Discover's "All" view should surface paid businesses (list panel is empty and map is village-centered at zoom 12 until a category chip is tapped) — this is why Kristin thought she was invisible
- Reply to Kristin (draft provided in session part 1)
- Fix or remove the notion-business MCP server token (401s)

**Notes for other environments:**
- Nothing is down; all Manitou feeds healthy. Do NOT run the Notion-feed DOWN runbook.