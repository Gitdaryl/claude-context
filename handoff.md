## Session: 2026-10-13 ET
**Environment:** Antigravity IDE
**What was done:**
- Traced how pay is recorded in OnPoint Office (app.onpointjd.com): Snow margin tab -> Pay sheet -> "Record a payment" writes one row to member_payments (person, date, amount, method, check number, optional work period, note). Not an expense, so margins never double count. Rows show in "Payments to the team" and roll into the CPA printout's "Paid to the team" / January 1099 list.
- Ran the exact demo scenario locally with Playwright (tests-e2e/support-pay.mjs): Yeti's support login (Daryl) records a payment to Daryl, Jay sees it, Jay can delete it. All checks pass.
- Found and fixed one bug: the support role had no label, so the CPA printout showed the raw key `cost.role.support` under Daryl's name. Added EN/ES labels. Commit ad24184 pushed to GitHub main (Vercel auto-deploys).
- Reverted the WebP sweep's conversion of a test fixture (ruler.jpg) before committing.

**What's live / deployed:**
- onpoint-office ad24184 pushed; live /api/health still reported c1e350f at push time (deploy in flight).

**Next up:**
- Yeti: on app.onpointjd.com as Daryl, Snow margin -> Pay sheet -> Record a payment -> pick Daryl, enter Jay's check. Then People & pay -> Daryl -> Tax and insurance file -> Type: LLC (Yeti Groove Media LLC) so the CPA printout is right.
- Optional: the reference field expects just the check number (the method label is prepended, so "Check 2087" prints as "Check Check 2087").
- Optional: add tests/ and tests-e2e/ to webp-sweep.py's protected list.

**Notes for other environments:**
- Live DB reads via the service key are blocked by auto mode in the IDE; local Supabase stack + Playwright is the verified path.