## Session: July 20, 2026 (ET), part 8
**Environment:** Antigravity IDE
**What was done:**
- Built the n8n notify pipeline directly on the Yeti VPS (n8n runs there as a systemd service, n8n.yetigroove.com): new workflow "Draft Sites — Note & Redo Notify" (id DraftNotesNtfy01), imported via n8n CLI and published
- Workflow: Webhook (POST /webhook/draft-notes) -> Build Notice code node (formats note.created / redo.proposed / redo.failed events) -> Twilio SMS to Yeti's 517 number + Resend email to daryl@yetigroovemedia.com, reusing the existing Twilio and Resend credentials from the MB Photo Flag Notify workflow
- Set NOTIFY_WEBHOOK_URL=https://n8n.yetigroove.com/webhook/draft-notes on BOTH Vercel projects (long-shutdown-site, never-broken-site) and redeployed+promoted both to production

**Blocked on one 30-second step (permission classifier would not let me restart the n8n service):**
- The workflow is in n8n's database as active, but the RUNNING n8n instance registers webhooks only on restart or UI toggle. Webhook currently 404s.
- Yeti fix, either: (a) open n8n.yetigroove.com, open "Draft Sites — Note & Redo Notify", toggle Active OFF then ON; or (b) SSH: systemctl restart n8n
- Then test: add a margin note on either site -> SMS + email should arrive

**What's live / deployed:**
- Both sites redeployed with webhook env var; the moment the n8n webhook registers, pings are live end-to-end with no further changes

**Next up:**
- Yeti: the toggle above, plus Fal balance top-up (fal.ai/dashboard/billing) for the Redo Loop
- After both: full demo loop = margin note pings phone; redo request -> edited image -> PROPOSED -> Keep/Toss, with pings

**Notes for other environments:**
- n8n VPS details: systemd service, basic auth, workflows exportable via n8n CLI; Twilio cred id Wlns5s20LRGlNhMH, Resend cred id LimIIXrVhmkoqge5, Resend verified sender domain manitoubeachmichigan.com