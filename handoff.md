## Session: Aug 13 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Wrote AI Holly weekend script for Aug 14-16 from the live events feed: Manitou-Beach/marketing/ai-holly-weekend-aug14-16-2026.md (script + social caption + edit notes)
- Added the antique wooden boat parade (Friday after 7pm, Devils Lake) which was not in the events DB
- Added real Holly's open house Sunday Aug 16, 729 Walnut Hill, 11am-12:30pm, with the "she owes me a pinot" callback
- Fixed a systematic Notion data bug: all 20 Two Lakes Tavern shows had Time End set to bare "11:00 PM", so the events API fell back to reading it as the START time. Every show displayed as starting 11pm. Rewrote all as "8:00 PM – 11:00 PM"; live feed verified clean.
- Cleared the bogus time on the Oct 31 Halloween Party (no confirmed start time, did not guess)

**What's live / deployed:**
- Notion event fixes are live on manitoubeachmichigan.com/api/events now (no deploy needed)
- Script file is local only, not committed

**Next up:**
- Get the real start time for the Two Lakes Halloween Party Oct 31 and put it in Notion
- Root cause still open: the Notion "Time" property is a created_time field, not rich_text, so api/events.js line 121 can never read it. Either convert the property to rich_text or drop the dead branch.

**Notes for other environments:**
- Two Lakes Tavern shows are 8-11 PM. Any older post or graphic saying 11 PM was from the bad data.