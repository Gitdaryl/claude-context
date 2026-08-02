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

## Universal Conversation Backup SOP (ALL environments)

Every substantive conversation must be findable from every platform. Two systems, both required:

1. **Session Brain (Notion)** - the queryable cross-platform memory
2. **Context repo handoff** - what GDay loads at session start

### Session Brain: every platform writes it

Database: **Session Brain** under the Yeti Command Center.
- URL: https://app.notion.com/p/9d5702d67e804d6c9abb5ac650edd233
- Data source ID: `cb17cfa2-7849-45d2-93bd-3aaefe5c66d0`

At the end of any substantive session (3+ meaningful actions), append ONE row: Session (short title), Date, Platform (IDE / Cowork / Mobile / VPS), Project, Summary, What's Live, Next Up, Tags. Dense and plain.

This applies to Cowork and Mobile the same as IDE. A conversation that only happened in chat still counts if anything important was said.

### The Log-It-Now rule

Do NOT wait for session end when any of these land mid-conversation:

- Client feedback or testimonials (especially pricing signals)
- A decision Yeti makes about direction, pricing, or strategy
- A new client, referral, or lead
- Anything Yeti says he wants to remember or find later

Log it to Session Brain immediately as its own row (Tags: feedback / decision / lead). Session-end summaries compress; important things get lost or the session never gets logged at all. Real example: Dave's feedback on the Devils Lake Cove video ($2,000 paid, $30,000 California comp) lived only in an unlogged conversation and could not be found later from any platform.

### Finding past discussions

When Yeti asks "did we ever..." or "find the session where...":
1. Query Session Brain (Notion) first - works from every platform
2. On IDE only: `python3 ~/.claude/tools/csearch.py "search terms"` greps all local transcripts
3. Check `sessions.md` in this repo for the handoff history

If a discussion cannot be found, say so plainly and ask Yeti to relay what he remembers, then log THAT to Session Brain so it is captured going forward.

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

## Signature Films Quoting SOP (all platforms)

Yeti sells commissioned films for unbuilt developments (see yetigroove.com/signature). Expected flow: he takes a discovery meeting remotely, then reports to whichever Claude is closest, often Mobile, while it is fresh. Every platform must know this play:

**The source of truth** lives in the Gitdaryl/Yeti-Groove repo under `docs/`:
- `SIGNATURE-RATE-CARD.md` - tiers ($7,500 / $15,000 / $25,000) + PRIVATE a la carte prices
- `DISCOVERY-CALL-SHEET.md` - the questions Yeti answers after a meeting
- `PROPOSAL-TEMPLATE.md` - the branded proposal structure
- `SERVICE-AGREEMENT-TEMPLATE.md` - the contract (attorney review required before first use)

Fetch via GitHub (raw URL or GitHub MCP). Local on the Mac: ~/Documents/Claude Code/Yeti-Groove/docs/.

**The flow:**
1. Inquiry arrives -> respond same day, schedule discovery call. Log the lead to Session Brain (Tags: client).
2. Yeti reports meeting answers (any platform, any order). Whichever Claude receives them logs a Session Brain row IMMEDIATELY (Log-It-Now) with everything he said, tagged client + decision.
3. Scope against the rate card: map to a tier, price extras from the a la carte list. NEVER quote a commissioned film below $7,500. Quotes are proposals, never bare numbers.
4. Best platform finishes: Mobile captures and logs; Cowork or IDE generates the proposal from the template and the agreement + deposit invoice on acceptance.
5. Payment: 50/50 under $15,000; 40/30/30 at $15,000 and above. Two revision rounds included, then $300/round, changes by written change order.

**Rules that never bend:** studio voice (never solo phrasing), renders are always presented as visualizations of approved plans, drafts watermarked until final payment, a la carte prices never published publicly.

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
*Last updated: 2026-08-02*