
## Session: 2026-11-13 ET (permit readiness checklist)
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: "Ready to apply here?" checklist on each office card, same list on the job Permit card, "Jobs waiting" filter on the Permits tab. Built and tested locally, not committed.

**What's live / deployed:**
- Nothing new. Permit apply (8032163) is live from earlier today.

**Next up:**
- Yeti: `cd ~/Projects/onpoint-office && npx supabase db push` (one migration, 20261115000000_permit_ready.sql), then say "push".
- Then the live setup row on the board (applicant = Jay, Devon fills Northwood and Wood County).

**Notes for other environments:**
- None.