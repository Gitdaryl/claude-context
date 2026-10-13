## Session: 2026-10-13 ET (part 2)
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: Costs tab renamed "Snow margin" -> "Money" (EN/ES); "Snow margin" stays the first section with its snow-only note inside it; Jobs/Team/roof-home hints now say "Money, People & pay"; CPA printout back button says "Back to Money".
- CPA printout: a person with a business name on their W-9 file prints that under their name (on screen and in the payments CSV) instead of the app role. Yeti shows as "Daryl / Yeti Groove Media LLC" once the Tax and insurance file has the business name.
- Browser flow tests-e2e/support-pay.mjs extended (business name on the printout). All checks pass locally.
- Reverted the WebP sweep's test-fixture conversion again before committing (memory saved: webp-sweep-converts-test-fixtures).

**What's live / deployed:**
- onpoint-office bfb9735 pushed to GitHub main (after ad24184 earlier today). Vercel deploys app.onpointjd.com.

**Next up:**
- Yeti on the live app: Money > People & pay > Daryl > Tax and insurance file > Business name "Yeti Groove Media LLC", Type LLC. Then Money > Pay sheet > Record a payment > Daryl, Jay's check (number only in the reference field).
- Yard-sign reimbursement: record as a RECEIPT (Money > Receipts), vendor = the sign printer, category Other (no Advertising category exists), note "paid by Daryl, reimbursed check #". Not team pay (it would inflate the 1099 total).
- Candidate build: an "Advertising & marketing" expense category (DB check constraint on expenses, needs a migration + `npx supabase db push`), plus a "reimbursed to" field on receipts.
- Optional: protect tests/ and tests-e2e/ in ~/.claude/tools/webp-sweep.py.

**Notes for other environments:**
- Live DB reads with the service key are blocked by IDE auto mode; verify through the local stack + Playwright.