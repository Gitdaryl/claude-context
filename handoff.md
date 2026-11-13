
## Session: 2026-11-13 ET
**Environment:** Antigravity IDE
**What was done:**
- On Point JD Office: reviewed the Permits section and the message server for "apply for a permit in the app"
- Found: Permits only looks up offices and records answers; the app cannot email an office; office replies would go to Jay's .net inbox or become a lead
- Wrote the build spec: ~/Projects/onpoint-office/docs/PERMIT-APPLY.md (3 phases, untracked)
- Filed the board row "OnPoint Office: apply for a permit from the job page"

**What's live / deployed:**
- Nothing. No code changed.

**Next up:**
- Yeti says go on phase 1 (tracking, permit sheet PDF, portal and paper hand-off)
- Devon's call list: add "how do you take the application" and "must we register first"
- Decide whose name is on applications: On Point JD or Mike

**Notes for other environments:**
- Model split for the build: Opus for database and server, Sonnet for screens, Spanish strings and tests