
## Session: 2026-11-27 ET (YetiGroove shared nav bar)
**Environment:** Antigravity IDE
**What was done:**
- One shared nav bar on 18 yetigroove.com studio pages: site-nav.css, site-nav.js, tools/site_nav.py (--check finds drift; question pages come from tools/build_questions.py)
- Fixed /#proof links landing low (reel video had no reserved height) and Field Office #demo double offset

**What's live / deployed:**
- Nothing new. Uncommitted in ~/Projects/Yeti-Groove, tested locally

**Next up:**
- Yeti says push: commit (include the 3 new files, not .DS_Store or .impeccable/), field-office sync first, then verify /site-nav.css and /site-nav.js live and rerun checks; pull ~/Yeti-Groove

**Notes for other environments:**
- Edit the menu only in tools/site_nav.py, never in individual pages