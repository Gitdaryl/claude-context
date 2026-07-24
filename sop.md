# Standard Operating Procedures — All Claude Environments

## The GDay Trigger

**When any Claude instance receives the word `GDay` (case-insensitive), it must:**

1. Fetch these files before doing anything else:
   - `CLAUDE.md` — who Yeti is, projects, preferences
   - `environments.md` — what tools/MCPs/skills are set up where
   - `sop.md` — this file
   - `handoff.md` — latest session summary (catch up on what the last environment did)

2. Confirm with a brief acknowledgement:
   > "GDay! Loaded context: [date]. I'm [environment]. Ready."

3. Proceed with the request (or ask what's needed if GDay was sent alone).

**Raw GitHub URLs:**
```
https://raw.githubusercontent.com/Gitdaryl/claude-context/main/CLAUDE.md
https://raw.githubusercontent.com/Gitdaryl/claude-context/main/environments.md
https://raw.githubusercontent.com/Gitdaryl/claude-context/main/sop.md
https://raw.githubusercontent.com/Gitdaryl/claude-context/main/handoff.md
```

---

## Session End SOP (ALL environments)

At the end of any substantive session (3+ meaningful actions), Claude must write a handoff summary and push it to the context repo.

### The handoff format

```
## Session: [YYYY-MM-DD HH:MM AEST]
**Environment:** [IDE / Cowork / VPS / Mobile]
**What was done:**
- [bullet list]

**What's live / deployed:**
- [anything pushed or deployed]

**Next up:**
- [deferred tasks or next steps]

**Notes for other environments:**
- [anything another Claude instance should know]
```

### How each environment implements this

| Environment | How it works |
|-------------|-------------|
| **IDE (Claude Code, any machine)** | Write draft to `~/.claude/session-handoff.md` — Stop hook auto-pushes to GitHub and cleans up |
| **VPS (Claude Code via Terminus)** | Same as IDE — identical Stop hook installed |
| **Cowork (Claude Desktop)** | Write the summary, then use GitHub MCP to PUT `handoff.md` and append to `sessions.md` |
| **Mobile (direct Claude)** | Output the formatted summary as text — Yeti copies it and triggers push via another env |

### What "push" means

- `handoff.md` — overwrite with latest session (single file, always current)
- `sessions.md` — append the entry (full history, never overwritten)

---

## General Rules (All Environments)

### Before Starting Any Multi-Step Task
- If context is stale (more than 1 session old), suggest a GDay refresh
- Check `environments.md` before recommending a tool — confirm it's available in the current environment

### Recording Work Done
- If you install an MCP, skill, or tool: update `environments.md` in the repo
- If you establish a new preference or workflow: update `CLAUDE.md`
- Don't let knowledge live only in one environment's session history

### Environment Handoffs
When handing off a task between environments, the handoff summary must include:
1. What was done
2. What the next step is
3. Which environment is best suited for the next step

---

## Writing Style (All Environments, All Output)

Applies to EVERYTHING written for Yeti or his brands: blog posts, newsletters, social copy, site copy, client proposals, emails, video scripts, code comments.

### No em dashes. Ever.
Em dashes (—) read as AI slop. Yeti has found them leaking into the Manitou Beach blog and newsletter. Zero tolerance:

- Rewrite the sentence with a comma, a period, or a colon
- If a dash is truly needed, use a short dash with spaces ( - )
- This applies to NEW writing and to EDITS of existing content: if you touch a file that contains em dashes, clean them while you are there

### Before publishing anything
Run a slop check on the final draft before it ships:
1. Search for em dashes (—) and en dashes (–) used as punctuation
2. Kill filler phrases ("in today's fast-paced world", "dive into", "elevate", "unleash", "game-changer")
3. Read it in Yeti's voice: direct, plain, no waffle

A post that fails the check does not publish until it is cleaned.

---
*Last updated: 2026-07-24*