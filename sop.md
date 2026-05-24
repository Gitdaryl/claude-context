# Standard Operating Procedures — All Claude Environments

## The GDay Trigger

**When any Claude instance receives the word `GDay` (case-insensitive), it must:**

1. **Fetch** the following files from this GitHub repo before doing anything else:
   - `CLAUDE.md` — who Yeti is, projects, preferences
   - `environments.md` — what tools/MCPs/skills are set up where
   - `sop.md` — this file (confirm you have the latest version)

2. **Confirm** what was loaded with a brief acknowledgement, e.g.:
   > "GDay! Loaded context: [date of last update]. I'm [environment name]. Ready."

3. **Then** proceed with whatever request follows (or ask what's needed if GDay was sent alone).

**Raw GitHub URLs to fetch:**
```
https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME/main/CLAUDE.md
https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME/main/environments.md
https://raw.githubusercontent.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME/main/sop.md
```
> ⚠️ Replace `YOUR_GITHUB_USERNAME` and `YOUR_REPO_NAME` before deploying.

---

## General Rules (All Environments)

### Before Starting Any Multi-Step Task
- If context is stale (more than 1 session old), suggest a GDay refresh
- Check `environments.md` before recommending a tool — confirm it's available in the current environment

### Recording Work Done
- If you install an MCP, skill, or tool: **update `environments.md`** in the repo and commit
- If you establish a new preference or workflow: **update `CLAUDE.md`**
- Don't let knowledge live only in one environment's session history

### Environment Handoffs
- When handing off a task between environments, summarise:
  1. What was done
  2. What the next step is
  3. Which environment is best suited for the next step

### Updating This Repo
- Any Claude instance with GitHub access should commit context updates directly
- Others should output the updated file content so Yeti can paste/commit manually

---

## Environment-Specific Notes

### Cowork (Claude Desktop)
- Best for: file creation, research, documents, scheduling, image gen, web fetch
- Memory lives in: outputs/memory/ folder (see MEMORY.md)
- Trigger GDay by fetching raw GitHub URLs via web_fetch

### Antigravity IDE Extension (Claude Code)
- Best for: coding, debugging, code review, file edits, terminal commands
- GDay rule is in: `~/.claude/CLAUDE.md` (global config)
- Can read/write project files directly

### Mobile Claude
- Best for: quick lookups, on-the-go questions, short tasks
- Most limited environment — no file tools
- GDay: paste the raw CLAUDE.md URL into first message, or use saved shortcut

---
*Last updated: 2026-05-24*
