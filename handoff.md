## Session: 2026-10-24 ET
**Environment:** Antigravity IDE
**What was done:**
- Built "Ask the helper" in OnPoint Office: Claude on the job page reads the job, customers and messages (read only, own company, no money) and answers; can offer a draft text that opens in the normal send panel; "Ask Daryl" texts Yeti the question + answer
- New table helper_asks (migration 20261108000000_helper.sql) logs every question, answer, tokens, and Ask Daryl status
- Fixed: stand-in lead names ("Caller (567) ...") no longer used in greetings ("Hi Caller,") or the "Text or email" button
- Tests: 1422 passing; live browser check with real Claude Opus 5.5 passed (about 4 cents a question)

**What's live / deployed:**
- Nothing. Uncommitted in ~/Projects/onpoint-office

**Next up:**
- Ship: `npx supabase db push` first, then commit + push (GitHub main auto-deploys)
- Add ANTHROPIC_API_KEY to the Vercel onpoint-office project
- Optional: HELPER_ALERT_PHONES if Ask Daryl should go somewhere other than ORDER_ALERT_PHONES
- Show Devon and Linda the panel; read helper_asks after a week

**Notes for other environments:**
- The helper runs on Vercel, not the Mac or VPS