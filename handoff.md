
## Session: 2026-11-20 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: confirmed Kyle can already text crew (superintendent role, Calendar > Text a group)
- Built "Who's where" day board: move crew between jobs for the whole day or from a time, both directions; teams and job crews untouched (new crew_day table + place_crew/reset_crew_day RPCs)
- Moved crew see the job on their phone with times, go on its check-in and day-crew texts; job cost splits a shared day half and half (exact fractions)
- Tests: logic 16, database 7, e2e flow all good; full suite 1875 pass (game.rls local seed gap only)

**What's live / deployed:**
- Nothing yet. Commit 747e3b7 on local main in ~/Projects/onpoint-office, 1 ahead of origin. Auto mode blocked the live db push.

**Next up:**
- Yeti: `npx supabase db push` THEN `git push origin main` in ~/Projects/onpoint-office
- Test Who's where with Kyle in person (board row filed)

**Notes for other environments:**
- Kyle texts Elmer; Elmer runs his own guys. Moves go both ways (B crew can come to A's job).