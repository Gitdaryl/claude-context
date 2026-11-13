
## Session: 2026-11-13 ET (later)
**Environment:** Antigravity IDE
**What was done:**
- On Point JD Office: built apply-for-a-permit, all three phases, per Yeti's go ("build it as if they have everything")
- New: migration 20261114000000_permit_apply.sql, Permit card on the job, office recipient in /api/messages, office replies filed on the job, digest nudge, schedule warning, Business info "Permits go in under"
- Tests: 1,639 unit/server pass, browser flow passes, build passes

**What's live / deployed:**
- Nothing. Uncommitted in ~/Projects/onpoint-office. Migration applied to the local database only.

**Next up:**
- Yeti: from ~/Projects/onpoint-office run `npx supabase db push`, then say "push" (commit + push main)
- After ship: set Business info > Permits go in under = Jay; Devon saves how Northwood and Wood County take applications
- Jay in person: is On Point registered with Northwood zoning and Wood County

**Notes for other environments:**
- Schedule warning was not seen in a browser (test could not reach that screen); the rule behind it is unit tested