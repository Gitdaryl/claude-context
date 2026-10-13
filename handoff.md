## Session: 2026-10-13 ET (part 3)
**Environment:** Antigravity IDE
**What was done:**
- Yeti reported a team payment "not showing" on app.onpointjd.com after switching the Money tab to This year. Reproduced the whole flow locally with Playwright + network tracing: the app follows the period correctly for This month / Last month / This year (a stale-looking list was my own test helper re-clicking This month). Likely cause of the confusion: the Payments list lives inside the collapsed Pay sheet section whose header said "0 people, $0.00" (that number only counted snow visits), and Yeti's screenshots show People & pay open, not Pay sheet.
- Fixed three things (onpoint-office): Pay sheet header also says "N paid out, $X"; an empty period says "No payments dated in this period. The latest payment is dated ... Pick This year or Pick dates"; saving a payment dated outside the shown period says so in the notice. EN + ES.
- Live DB reads (service key, `supabase db dump`) are blocked by IDE auto mode, so the live rows were not inspected directly.

**What's live / deployed:**
- onpoint-office: ad24184 (support role label), bfb9735 (Money tab, business name on CPA printout), and this session's payment-visibility commit, all pushed to GitHub main; Vercel deploys app.onpointjd.com.

**Next up:**
- Yeti: on the live app, Money > This year > open the **Pay sheet** section (not People & pay). The header now shows the payment count; the list is below the pay-sheet table.
- Yard-sign reimbursement: record as a RECEIPT (Money > Receipts > Add receipt), vendor = sign printer, category Other, note "paid by Daryl, reimbursed check #". Not team pay.
- Candidate builds: "Advertising & marketing" expense category (DB check constraint, migration + db push); "reimbursed to" on receipts; protect tests/ in webp-sweep.py.

**Notes for other environments:**
- Local verify path: `npx vite --port 5179 --strictPort` + `node tests-e2e/support-pay.mjs` (needs the sample support login 5550000080 / 80808080 added with scripts/add-member.mjs).