## Session: July 31, 2026 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Built Idea Greenhouse from scratch: shared kanban idea tracker for Yeti + Holly (spec'd, coded, deployed)
- Pipeline: Germinate, Brainstorm, Planning, Filming, Editing, Releasing, plus Harvest log
- Grow feature: /api/grow sends the idea to Claude (claude-opus-5 + web search) with an anti-sycophancy prompt (mandatory "Why this might flop" section, real research, 3 physical next actions auto-added to the card checklist)
- Storage: Vercel Blob, one blob per card, persist-before-notify, /api/health self-check
- Auth: shared access code + Yeti/Holly picker. Current code: growroom-2026 (change via ACCESS_CODE env var)
- Repo: Gitdaryl/idea-greenhouse (private), pushed to main
- Verified live: card create/move/checklist/delete all pass, UI screenshot confirmed on mobile viewport

**What's live / deployed:**
- https://idea-greenhouse-pi.vercel.app (Vercel project idea-greenhouse, Blob store idea-greenhouse-blob connected)

**Next up:**
- Yeti must add ANTHROPIC_API_KEY env var in Vercel (any existing key from console.anthropic.com works), then the Grow button goes live. Untested end-to-end until then.
- Optional: GROW_MODEL=claude-sonnet-5 env var for cheaper brainstorms (default claude-opus-5, roughly 5 to 15 cents per grow)
- Later ideas in SPEC.md: n8n stale-card pings, auto-grow on create, per-platform release checklists

**Notes for other environments:**
- Holly needs the URL + access code + pick "Holly" on the gate. Works on mobile (columns swipe).
- /api/health shows env + blob status; currently all green except ANTHROPIC_API_KEY.