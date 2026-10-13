
## Session: 2026-10-13 ET
**Environment:** Antigravity IDE
**What was done:**
- Devon has a $15k phone quote (134 Walnut St, Rossford OH: 5+ layer tear-off, full 7/16 OSB decking, Atlas Pinnacle Pristine) with no name/phone/email yet. Checked the OnPoint Office code: the CRM already treats every job as a lead (stage lead, Pipeline New column, source dropdown, stage history, post-estimate follow-up + mark-lost). No new leads feature needed.
- Added ~/Projects/onpoint-office/scripts/add-lead.mjs (uncommitted): customer + lead job + draft one-option estimate from the command line, safe to re-run. Tested on the local stack and screenshot-verified in the app as sample Devon (job page showed New lead, $15,000 option, the three what-you-get bullets, Email estimate button). Local test rows deleted after.
- Could not write to the live database from the IDE (production writes gated), so the live load is on Yeti.
- Board: Today row (run the script) + Backlog row (leads funnel gaps: nameless leads, where-from report, pre-estimate follow-up, phone-call source, next-touch date).

**What's live / deployed:**
- Nothing. Script is uncommitted in onpoint-office.

**Next up:**
- Yeti: run the add-lead command in the Today board row with Devon's sign-in phone, then Devon fixes the name, adds phone/email, emails the estimate from the job page.
- Decide with Devon after a week on the Pipeline which funnel gaps matter; read his lead spreadsheet columns first (Oct 9 row).

**Notes for other environments:**
- Devon can also just tap New job in app.onpointjd.com with a placeholder name; the script only saves him typing.