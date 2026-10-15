
## Session: Oct 15 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Added 2 events to Manitou Beach Events DB (Published, Admin-Added): All Sports Spectacular (Irish Hills Chamber, Oct 24, 4:30-8:30 PM, Irish Acres, 8800 Gordon Rd, Cement City; $65/$120/$480 table) and Boo(ze) & Bites (Devils Lake tasting rooms incl. Gypsy Blue, Oct 31, 12-4 PM)
- Flyers committed as public/images/og/all-sports-spectacular-og.jpg + booze-and-bites-og.jpg (commit 0d51fca)

**What's live / deployed:**
- Both events in /api/events with flyers and correct times

**Next up:**
- Boo(ze) & Bites has no ticket link or price (QR would not decode); add Event URL + price if Yeti gets them
- Neither is a Hero Takeover: All Sports (Oct 24) would bump the Men's Club roast hero (paid client) until Oct 24; Yeti to decide

**Notes for other environments:**
- Local .env has no NOTION_TOKEN_EVENTS; the claude.ai Notion connector writes to the Events DB fine