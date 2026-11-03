
## Session: 2026-11-03 ET
**Environment:** Antigravity IDE
**What was done:**
- Reverse-engineered trackre.app (client transaction timeline app, $19/mo, iOS/Android) and rebuilt it inside Holly's site instead of a separate app: commit c2127fd on Gitdaryl/Holly main, live on hollygriewahn.vercel.app.
- Client page /deal/<id>?k=<key>: dated steps from offer to keys, progress bar, "Up next", what each step means and what the client does, add-to-calendar (.ics), "I did this", Ask Holly thread. No login; the texted link is the key.
- Desk Deals tab: list with past-due and unanswered-question badges, New roadmap (upload the purchase agreement PDF and Claude fills address/price/dates/contingencies; or type two dates), step editor, Text the link, Copy link, reply to questions (also goes out as a text).
- Michigan step templates (buyer financed, buyer cash, seller, lake-home extras) in src/data/deal-templates.js; steps re-date when the closing date moves.
- Hourly cron job 4 in api/cron-followup.js: client texts 2 days before each step and morning-of for their own steps; Holly gets one morning summary incl. overdue.
- Runbook: docs/DEALS.md in the repo.

**What's live / deployed:**
- All of the above, verified live: /deal shell is noindex, robots disallows /deal, bad key = 404, desk reads need the session.

**Next up:**
- Holly makes the first real roadmap from a live purchase agreement; watch the extraction output against the contract.
- Document uploads on a step (Dotloop/report PDFs) not built; steps take a link only.
- Lender / title partner access (Trackre's "team collaboration") not built.

**Notes for other environments:**
- Treat trackre.app as covered for Holly; do not sign her up. The desk tab is called Deals; the client page is "Your roadmap".