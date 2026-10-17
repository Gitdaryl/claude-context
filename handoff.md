
## Session: 2026-10-16 ET
**Environment:** Antigravity IDE
**What was done:**
- On Point JD storm trigger built (runbook ~/Projects/on-point-jd/social/STORM-TRIGGER.md)
- 21 noindex town pages /storm/<town> from one template; ad link swaps headline per hail/wind/leak + storm day
- tools/storm-watch.mjs: NWS storm reports + warnings -> per-town ad drafts, FB post draft, text to Yeti
- tools/storm-post.mjs posts the FB draft; tests in tools/test_storm.mjs (9 pass)
- Meta Housing special ad category applies to roof ads (no zips, 15 mi min, no age); ADS-PILOT.md fixed

**What's live / deployed:**
- Nothing. Uncommitted in on-point-jd (other uncommitted files there, .gitignore + crm/meetings, are not from this session)

**Next up:**
- Yeti: push on-point-jd; load the LaunchAgent (commands in STORM-TRIGGER.md, "Switch it on")
- Later: API ad launch, past-customer storm text, door-knock list

**Notes for other environments:**
- Storm ads need the Meta ad account (Meta access row on the board) before any spend