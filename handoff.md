
**Update, Oct 12 ~7:46 pm ET:**
- Watcher is LIVE on the VPS: cron every 5 min, all 5 keys set, first "all good" text sent.
- On its first run it caught a real production crash: /api/digest (the 7:30 email) and /api/documents (PDFs) failed with ERR_MODULE_NOT_FOUND, from 12 imports missing ".ts". The fix c1e350f is LIVE and verified (digest 401, documents 405 = modules load). tests/server-imports.test.ts now guards it.
- Next: confirm tomorrow's 7:30 email + the 8:30 text has no digest warning.