## Session: 2026-09-23 ET
**Environment:** Antigravity IDE
**What was done:**
- Reviewed the Ford "Director, AI Transformation Architect" posting (Dearborn, Ford Next / Integrated Services, LL4) against the positioning doc. Strong on the job description, stretch on the job level.
- Re-fetched the posting verbatim after a summarised fetch invented a preferred qualification about MCPs and CLIs that Ford never wrote.
- Wrote applications/ford-cover-letter.txt and applications/ford-ai-transformation-architect.md, added the ford entry to role.html, registered the ford slug in the existing role-view tracker.
- Researched LL4 comp. No range published because Michigan has no pay transparency law. Ford ladder puts a traditional engineering Director at LL2, so an LL4 titled Director is Ford Next using tech-style titles. Estimate $200k-$250k base, $250k-$320k total.
- Built two visuals on the Ford page: a blast-radius figure (16 jobs act alone, 3 gates wait for a human) and an agent field, a canvas of one node per cron pulsing at its real cadence and coloured by its real status, fed by the HUD's existing poll.
- Fixed three live-data defects found while wiring them, plus a disclosure hole.

**What's live / deployed:**
- https://work.yetigroove.com/ford verified by headless screenshot at 1440 and 390 wide. No horizontal overflow, mobile figure legible.
- HUD now reads the feed's real contract. It had been testing a.health === 'failing', a field the feed has never carried, so it reported "all healthy" over a cron 22 days dead. The NEXT row read a.nextRun, also absent, so it could only render an em dash. Replaced with WATCH.
- The [data-agent-count] slots were only written inside the dormant herolive block, so the prose showed a hardcoded 20 above a HUD reading 18. The HUD owns them now.
- role.html no longer ships every ROLES entry to every reader; the WongDoody entry is archived and the rule is one live role at a time.

**Next up:**
- Yeti decides the Dearborn commute. Ford's 4-day onsite is the company-wide default, not role-specific, and their own relocation policy uses a 50-mile threshold while he is ~75 miles out. Ask the recruiter for the LL4 range and this req's work pattern on call one.
- TWO MANITOU CRONS ARE DEAD: cron-beta-trial-expiry (daily, 22 days silent) and cron-outreach-resolve (never recorded a run). Both registered in vercel.json. Board row filed. The Ford page now shows this publicly in amber, which is honest, but fixing them makes it read green.
- vercel.json registers 20 crons; status-agents only reports 18. cron-reindex and cron-health-check are missing from the feed.

**Notes for other environments:**
- Verified today: 184 non-underscore API endpoints, 20 crons registered, 18 reporting, 12 LLM endpoints, 29 Stripe, 960 commits. SOURCE-DOC.md still says 173/18 from August and is stale.