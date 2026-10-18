## Session: Oct 18 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Audited onpointjd.com (home, /estimate, /reasons + 6 personas, 21 storm + 21 snow town pages) against on-point-jd/social/GROWTH-FINDINGS.md checklist
- Fixed in tools/build_pages.py + rebuilt: Ohio 3-day cancel FAQ on home/estimate/storm pages; hail-size (&in=) line removed from storm town pages; persona h1s now name town + persona; reviews newest first; Google review link on every proof block; new price section on reasons pages (total + monthly + decking + warranty + 3-day cancel); reviews added to /storm-damage, /storm/<town>, /estimate; snow pages get review links
- New fact (Yeti): whole roof crew does a thorough final check at the end of every job. In NOTES.md; on site as a reason, an /estimate inclusion and a home reviews line
- Call/text tap beacons now carry utm_campaign (track/tap/<source>/<button>/<campaign>/<uuid>; desk tally unchanged)

**What's live / deployed:**
- Nothing. 82 files changed in ~/Projects/on-point-jd, uncommitted, all 9 test files pass. Push to master = production deploy.

**Next up:**
- Yeti to OK the push (commit with pathspec; social/ADS-PILOT.md + STORM-TRIGGER.md are someone else's uncommitted work, leave them)
- Decide the $1,000 offer + bonus wheel (no end date; OAC 109:4-3-04(H) risk)
- Build personas "roof turned 15 (insurance)" and "property manager" once facts are in
- Ask Jay: who answers the phone after hours; a real "you didn't need a roof" story; OK the storm line "we'll tell you honestly if it's worth a claim"

**Notes for other environments:**
- Desk does not yet group taps or leads by utm_campaign; the data is now being captured for it