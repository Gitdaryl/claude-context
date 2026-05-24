# Environments & Installed Tools

> Track what's installed where. Update this file whenever an MCP, skill, plugin, or tool is added to any environment.

---

## Antigravity IDE (Claude Code Extension)

**Status:** Active
**Best for:** coding, debugging, file edits, terminal commands, deploying

### Session-end sync
- Writes `~/.claude/session-handoff.md` as last action
- Stop hook auto-pushes to context repo and cleans up draft
- Hook path: `~/.claude/hooks/session-handoff.sh`
- Config: `~/.claude/settings.json`

### Installed MCPs
- GitHub (via gh CLI)
- Notion
- Vercel

### Notes
- GDay rule defined in `~/.claude/CLAUDE.md`
- Works on any machine with Claude Code + this hook setup
- To replicate on a new machine: install gh CLI, copy hooks/, update settings.json

---

## Cowork (Claude Desktop App)

**Status:** Active
**Best for:** documents, research, scheduling, image gen, web fetch, Notion management

### Session-end sync
- No Stop hook available in Desktop app
- Claude follows SOP: writes handoff summary then uses GitHub MCP to PUT handoff.md + append sessions.md before ending session

### Installed Plugins
- Engineering plugin (architecture, code-review, debug, deploy-checklist, documentation, incident-response, standup, system-design, tech-debt, testing-strategy)

### Installed Skills
- docx, xlsx, pptx, pdf
- schedule
- skill-creator
- setup-cowork
- consolidate-memory

### Connected MCPs
- Google Drive
- Google Calendar
- Notion
- Vercel
- AI image/video generation
- Claude in Chrome (browser automation)
- Filesystem (local file access)
- GitHub
- Scheduled tasks

### Notes
- Memory stored in outputs/memory/MEMORY.md
- On GDay: fetch handoff.md to catch up on last IDE/VPS session

---

## VPS (Claude Code via Terminus)

**Status:** To be confirmed — Terminus was previously used to connect mobile to a VPS for editing when home Mac was asleep
**Best for:** mobile editing, running builds, anything that needs a persistent server when away from home

### Purpose
Yeti is frequently away from home. When the Mac is asleep, mobile Claude loses the ability to do real edits. A VPS running Claude Code solves this — always-on, accessible from any device via Terminus (iOS/Android SSH client).

### Session-end sync
- Same as IDE — install identical Stop hook on VPS
- Hook path: `~/.claude/hooks/session-handoff.sh`
- Requires: gh CLI authenticated on VPS

### Setup checklist (when provisioning)
- [ ] Claude Code CLI installed
- [ ] gh CLI installed and authenticated
- [ ] `~/.claude/hooks/session-handoff.sh` copied from this repo
- [ ] `~/.claude/settings.json` updated with Stop hook
- [ ] `~/.claude/CLAUDE.md` copied from this repo

### Notes
- Terminus is the SSH client used to connect from mobile
- VPS provider TBC — confirm with Yeti

---

## Mobile (Direct Claude App)

**Status:** Active (read-heavy, limited write capability)
**Best for:** quick lookups, reading handoff.md, short Q&A

### Session-end sync
- No file tools or MCP connectors
- Claude outputs the formatted handoff summary as text
- Yeti manually triggers push via another environment, or VPS handles it if connected via Terminus

### Notes
- GDay: paste raw GitHub URLs or use a saved shortcut
- Primary consumer of handoff.md — catches up on what IDE/VPS did last session

---

## Cross-Environment Tasks Log

| Date | Environment | What was done | Done by |
|------|-------------|---------------|---------|
| 2026-05-24 | All | GDay SOP established, context repo created | Cowork |
| 2026-05-24 | IDE | Stop hook built, handoff.md + sessions.md created, universal SOP written | IDE |

---
*Last updated: 2026-05-24*