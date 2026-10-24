## Session: 2026-10-24 ET
**Environment:** Antigravity IDE
**What was done:**
- Built and shipped "Ask the helper" in OnPoint Office: Claude (Opus 5.5) on the job page reads the job, customers and messages (read only, own company, no money) and answers; offers a draft text that opens in the normal send panel; "Ask Daryl" texts Yeti the question + answer
- New table helper_asks logs every question, answer, tokens and Ask Daryl status
- Fixed: stand-in lead names ("Caller (567) ...") no longer used in greetings ("Hi Caller,") or on the "Text or email" button
- 1422 tests passing; live local test with real Claude about 4 cents a question

**What's live / deployed:**
- app.onpointjd.com commit 41a747a (health confirmed); migration 20261108000000_helper.sql on the live database

**Next up:**
- Show Devon and Linda the "Ask the helper" button; try it on a real lead
- Read helper_asks after a week to see what the team asks

**Notes for other environments:**
- The helper runs on Vercel, not the Mac or VPS; uses the existing ANTHROPIC_API_KEY and ORDER_ALERT_PHONES