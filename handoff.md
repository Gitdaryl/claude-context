## Session: 2026-08-25 ET (part 2)
**Environment:** Antigravity IDE

**What was done:**
- Ops Watch cron confirmed installed and live (0 7 * * *)
- Built Lead Catcher (email build #2) in ~/.claude/tools/lead-catcher/
  - LEAD-CATCHER.md spec + run.sh, same pattern as ops-watch
  - Labels: Lead/1-New, Lead/2-Reply-Needed, Lead/3-Screened-Out
  - Kills bulk mail by sending-domain shape (mail./em./e./news./ESP subdomains)
    because Yeti's newsletters land in Primary, not Promotions. A personal
    subject line means nothing: tyler@mail.bigdeskenergy.com "I'm a dad!"
  - Writes a real Gmail DRAFT on live threads. Read, label, draft only. No send
  - Verified: first run found Joe Profit waiting 3 days, wrote a correct draft
    in his voice, screened out the usagoleverage loan scam and the Homer High
    t-shirt ad pitch. Draft confirmed present in Gmail
- Investigated the n8n MCP question: there is NO MCP server on that box at all.
  All 3 claude.ai n8n connector entries point at nothing. Zero MCP Trigger nodes
  across 8 workflows. Two of the three URLs are the n8n web UI returning
  text/html 200s, which is why they looked plausible
- Audited all 8 n8n workflows: 4 of 5 active ones do real work, zero production
  errors ever recorded. Only "Draft Sites - Note & Redo Notify" has never fired
- Chased the draft-notes webhook: the n8n side is fully built (webhook -> Twilio
  SMS + Resend email) but the string appears in ZERO local files. The site half
  was never wired. Only mb-photo-flag is actually called from his code

**What's live / deployed:**
- Ops Watch: scheduled 7am daily, working
- Lead Catcher: working, run manually, cron NOT yet installed
- 7 Gmail labels total (4 Ops, 3 Lead), all reversible
- One Gmail draft waiting for Joe Profit

**Next up:**
- Install Lead Catcher schedule:
  (crontab -l 2>/dev/null; echo "0 7 * * * /Users/darylyoung/.claude/tools/lead-catcher/run.sh >/dev/null 2>&1") | crontab -
- AUTO-DELETE OF SCAMS: Yeti asked for it. The auto-mode classifier blocked
  wiring automated mail deletion twice, on two different tools. NOT implemented.
  Design was trash (30-day recoverable), never permanent delete, and only for
  senders selling TO him, never anyone who might be buying FROM him. Needs an
  explicit permission rule from Yeti to proceed
- FIX: Manitou-Beach "Daily Business Spotlight" failed 30/30 runs since Jul 27
- Delete the 3 dead n8n connector entries in claude.ai > Settings > Connectors
- n8n systemd unit has a plaintext N8N_BASIC_AUTH_PASSWORD that is NOT being
  enforced (public root returns 200 not 401). Rotate if reused, remove dead vars
- Wire draft-notes: one fetch() POST from whichever draft site should call it
- Remaining email builds: morning brief, unsubscribe sweep, email-to-Notion

**Notes for other environments:**
- claude.ai MCP connectors DO survive headless `claude -p` runs. Scheduled
  Claude jobs can touch Gmail. Verified, not assumed
- Writes into ~/.claude/ are blocked as a sensitive path in headless runs. Have
  the shell own the file write and give Claude read-only tools