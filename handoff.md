## Session: 2026-08-25 ET (part 3)
**Environment:** Antigravity IDE

**What was done:**
- MAJOR FIND: manitoubeachmichigan.com was never added to Google Workspace, yet
  its MX pointed at smtp.google.com. Every inbound message to that domain had
  been bouncing for the life of the domain, while 20+ site endpoints send AS
  hello@/events@/tickets@ via Resend and api/businesses.js sets reply_to on it.
  Business owners, food truck applicants, LLLC members and sponsors who replied
  all bounced. Outbound was always fine; only inbound was dead.
- Fixed end to end and verified by real delivery:
  - Added MB as a verified secondary domain in Workspace
  - Created 4 Google Groups (hello@ events@ tickets@ trucks@), Custom access,
    "Who can post" ticked for External, external members OFF
  - Confirmed delivery of all four from an outside (Hotmail) sender
- DNS work (all verified live on 8.8.8.8, keys validated as real 2048-bit RSA):
  - manitoubeachmichigan.com: added SPF, added google._domainkey DKIM,
    added google-site-verification. Kept the modern single MX (smtp.google.com)
  - yetigroove.com: added _dmarc TXT and google._domainkey DKIM (Cloudflare, by
    Yeti). Status now reads "Authenticating email with DKIM"
- Published a visual DMARC explainer artifact for Yeti (he is a visual learner):
  https://claude.ai/code/artifact/6cd20e8d-20d0-49c5-bc59-3deffafdf627
- CORRECTION recorded: an earlier claim that neither domain had DKIM was wrong.
  Both had resend._domainkey all along. The real gap was Gmail-sent mail.

**What's live / deployed:**
- Ops Watch, cron 7am daily
- Lead Catcher, working, cron NOT installed
- 7 Gmail labels (4 Ops, 3 Lead) + one draft waiting for Joe Profit
- 67-filter Gmail import file at ~/.claude/tools/unsub-sweep/yetigroove-filters.xml
  NOT yet imported
- Both domains fully authenticated (SPF + DKIM + DMARC)

**Next up:**
- Yeti: import the filter file. Gmail > Settings > Filters > Import filters, and
  TICK "Apply new filters to existing email". This is what collapses the 5,731 unread
- Yeti: install lead catcher cron:
  (crontab -l 2>/dev/null; echo "0 7 * * * /Users/darylyoung/.claude/tools/lead-catcher/run.sh >/dev/null 2>&1") | crontab -
- Confirm START AUTHENTICATION was pressed for manitoubeachmichigan.com DKIM
- Reach out to LLLC / food truck applicants: their replies bounced, they may
  think they were ignored
- FIX: Manitou-Beach "Daily Business Spotlight" failed 30/30 runs since Jul 27
- Wire the draft-notes webhook (n8n side built, site side never was)
- Auto-delete of scams: blocked by the auto-mode classifier, not implemented
- MB Site Audit n8n workflow emails daryl@yetigroovemedia.com, a domain that may
  not exist. Alerts may be going nowhere
- Remaining email builds: morning brief, email-to-Notion
- n8n has NO MCP server; delete the 3 dead connector entries in claude.ai
- n8n systemd unit has a plaintext basic-auth password that is not enforced

**Notes for other environments:**
- claude.ai MCP connectors survive headless `claude -p` runs. Scheduled Claude
  jobs CAN touch Gmail. Verified
- Writes into ~/.claude/ are blocked as a sensitive path in headless runs. Let
  the shell own file writes and give Claude read-only tools
- Google Groups "Public" access type means public WITHIN the org. To accept
  outside senders you must tick External on the "Who can post" row specifically