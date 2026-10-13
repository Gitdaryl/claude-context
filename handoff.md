## Session: 2026-10-13 ET (part 4)
**Environment:** Antigravity IDE
**What was done:**
- Yeti flagged the Money tab header "0 people, $0.00 · 3 paid out, $1,800" as brain-burning and asked for a tech-noob audit of everything (Jay is a roofer; must read any screen in seconds).
- Rebuilt the Money tab: cards are Snow money, Snow pay estimate, Paid to the team (its own card now, open by default when there is no snow work), Receipts, People & pay rates. Every header is one sentence ("3 payments, $1,800.00", "No snow work for these dates", "Lost $167.20"). Snow money shows one left-over number (after other receipts) and a one-line spent breakdown. Hints cut to one sentence. EN + ES. Browser flow tests-e2e/support-pay.mjs passes (now clears leftover test payments first).
- Wording audit of every other screen by a subagent, saved as docs/PLAIN-WORDS-AUDIT.md: 15 worst offenders (PM jargon, bare numbers on the Home strip, "Needs attention", "Finalize", five names for "owed", Net 30, statute cites on screen, "Pipeline"/"Production"), everything by file, five app-wide rules. NOT applied yet; awaiting Yeti's go. Legal/contract strings should keep the attorney's wording.

**What's live / deployed:**
- onpoint-office pushed to GitHub main (Money tab rebuild + audit doc), after a54cb54 earlier today. Vercel deploys app.onpointjd.com.

**Next up:**
- Yeti decides whether to apply the audit's 15 worst offenders (and then the per-file list). Suggested order: 1 to 7 and 10 to 15 are label changes; 8 and 9 touch legal text, shorten hints only.
- Yard-sign reimbursement: Money > Receipts > Add receipt, vendor = sign printer, category Other, note "paid by Daryl, reimbursed check #". Candidate: Advertising & marketing category (migration).
- Yeti's own file: Money > People & pay rates > Daryl > Tax and insurance file > Business name "Yeti Groove Media LLC", Type LLC.

**Notes for other environments:**
- Local verify: `npx vite --port 5179 --strictPort` + `node tests-e2e/support-pay.mjs` (sample support login 5550000080 / 80808080 via scripts/add-member.mjs).