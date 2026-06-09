## Session: 2026-06-09 (AEST)
**Environment:** Antigravity IDE

**What was done:**
- Strategic discussion on AGI prep + competitive moat for the MB "fishbowl" expansion. Key reframe: the moat is hyperlocal network density + merchant relationships, NOT software features. A funded competitor can clone the code; they can't clone the local trust/relationships. Defense = speed to density per territory + templatization + hoarding operating data, not "staying ahead on tech."
- Built the **Weekly Tech Radar agent** (Daryl's "capability monitor" idea, scoped down from AGI-prediction to fast frontier adoption).

**What's live / deployed:**
- Pushed to Gitdaryl/Manitou-Beach main (commit e6db693):
  - `scripts/tech-radar.js` — scans AI releases (HN Algolia), dev tooling + MCP/skills (GitHub Search API), video/creative AI, optional competitor/clone alerts (Brave). Haiku ranks each item vs Daryl's stack/projects/moat → do/watch/ignore. Emails ranked digest via Resend + creates Command Center tasks for "do" items only. Every external dep degrades gracefully.
  - `.github/workflows/weekly-tech-radar.yml` — runs Mon 8am ET (13:00 UTC) + manual workflow_dispatch with preview flag.
- Runs out of the box for EMAIL using existing MB secrets (ANTHROPIC_API_KEY, RESEND_API_KEY).
- Caught + fixed a real bug pre-ship: Command Center Status is a select, not Notion status type.

**Next up (Daryl action — added to Command Center, Status=Today):**
- Add GitHub secret `NOTION_COMMAND_CENTER_TOKEN` (Yeti-workspace Notion integration token shared to the Command Center board) to enable auto-task-creation. Without it, radar still emails fine.
- Optional secrets: `BRAVE_API_KEY` (enables clone/competitor alerts), `RADAR_FROM`/`RADAR_TO` overrides.
- Test now: Actions → Weekly Tech Radar → Run workflow → preview=true.

**Notes for other environments:**
- The radar is portfolio-wide tooling that happens to live in the MB repo (MB has the mature GitHub Actions + Haiku + Resend infra). Conceptually it belongs to Yeti Groove Media.
- Tune what it watches by editing PORTFOLIO_CONTEXT + the query arrays in tech-radar.js.