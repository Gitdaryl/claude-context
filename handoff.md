
## Session: 2026-09-20 ET
**Environment:** Antigravity IDE
**What was done:**
- Organised the vlog / legacy-website / waitlist idea into one funnel: vlog = proof (camera on the client's moment, never on the calendar), /signature = catalog, waitlist = intake with a stated annual limit.
- Pricing decided from the ~200 unbilled hours on Joe Profit: Legacy Site from $15,000 (80-hour budget, 4/yr), Legacy Commission from $50,000 (Joe-grade, 2/yr). Hour budget is the unit of work, like scene count on films. Joe is "the studio's pilot commission, built at studio cost as the showcase", never "free".
- First hire is a production seat; "directed personally by Daryl" is the one first-person line inside the studio "we".
- Built #legacy section on /signature (two tier cards, slots box, Legacy button in hero) and a waitlist mode on the existing inquiry modal; api/signature-lead.js handles mode=legacy (YGL ids, own subject, SMS prefix, client email stating the limit).
- Verified: headless renders at 1440 and 390, modal mode switches both ways, API dry-run with credentials stripped (200/400 paths). Rate card (private, gitignored) has the Legacy section with the math.
- Task board: mailto row for /signature marked Done (was already wired); two new rows (push the Legacy line: Today; vlog build-log pilot: Backlog).

**What's live / deployed:**
- Nothing pushed. Uncommitted in ~/Projects/Yeti-Groove: signature.html, api/signature-lead.js.

**Next up:**
- Yeti says "push" (commit-push runs the WebP sweep first). Then one live waitlist test on /signature#legacy, confirm the YGL email + SMS, delete the test lead blob.
- Vlog pilot clip: the Never Broken story and Joe's reaction.

**Notes for other environments:**
- Cowork: if drafting any legacy copy, the two floors and the "pilot commission at studio cost" wording are fixed. No comps, no "free".