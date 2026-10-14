
## Session: Oct 14 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Located the real paper-contract data (onpoint-office/import/contracts, gitignored; repo is private). Old local `master` branch still holds unscrubbed history with customer names (never pushed).
- Devon okayed loading all 7 contracts: contracts.json rows all set confirmed:true.
- Yeti archived his own test customer in the live app.

**What's live / deployed:**
- Nothing yet: the contract import waits on Yeti running `npm run import:live` (phone + hidden PIN).

**Next up:**
- Yeti: `cd ~/Projects/onpoint-office && npm run import:live` (loads Spetz, Frampton, Reid x2).
- Devon: McEachen roof price; signed dates for McEachen gutters + Braun roof; Kirk Reid deposits paid? (check numbers/dates). Then re-run the import.
- Optional: mark Yeti's test job(s) lost if they still show on the Jobs list; delete local `master` branch once not needed.

**Notes for other environments:**
- Mobile/Cowork: if Devon texts the McEachen price or the Braun/McEachen dates, pass them to the IDE for contracts.json.