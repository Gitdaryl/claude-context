## Session: 2026-09-23 ET
**Environment:** Antigravity IDE
**What was done:**
- Reviewed the Ford "Director, AI Transformation Architect" posting (Dearborn, Ford Next / Integrated Services, LL4) against the AI leadership positioning doc. Verdict: strong match on the job description, stretch on the job level. Four real gaps, two of them put in writing on purpose.
- Re-fetched the posting verbatim after the first summarised fetch invented a preferred qualification about MCPs and CLIs that Ford never wrote. Corrected the advice that came off it.
- Wrote applications/ford-cover-letter.txt (854 words) and applications/ford-ai-transformation-architect.md (requirement map, strategy, interview prep) in yeti-positioning.
- Added the ford entry to site/role.html and the /ford rewrite, registered the ford slug in Yeti-Groove api/role-view.js. The read tracker already existed from the WongDoody application, so it was extended, not rebuilt.
- Found and fixed a disclosure hole: role.html shipped every ROLES entry to whoever opened any role page, so a Ford reviewer viewing source could have read the WongDoody pitch. Archived that entry, documented one-live-role-at-a-time, and de-identified a served comment in index.html that named a company.

**What's live / deployed:**
- https://work.yetigroove.com/ford, verified live, no other company named in the source.
- api/role-view.js accepts slug `ford`, verified with a preview POST so no SMS fired.
- Both repos pushed. Yeti-Groove committed with a pathspec, the modified .gitignore from another machine was left alone.

**Next up:**
- Yeti decides the Dearborn commute question before submitting. 75 miles, 4 days onsite, ends YetiGroove as a running studio.
- On submit: bare work.yetigroove.com in the form field, /ford in the letter body.

**Notes for other environments:**
- Verified platform numbers as of today: 184 non-underscore API endpoints, 20 cron entries, 18 agents reporting to the live status feed, 12 LLM endpoints, 29 Stripe endpoints, 960 commits. SOURCE-DOC.md still says 173/18 from August and is now stale.