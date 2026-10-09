## Session: Oct 9 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Designed the OnPoint JD CRM ("OnPoint Office") v0: ~/Projects/on-point-jd/crm/CRM-DESIGN.md (build vs buy with real prices, per-person views, job spine, 14 modules, data model, roles/RLS, money boundary with QuickBooks, branded paperwork set, Ohio contract items for the attorney, runtime model per AI task, build-team model routing, stack, 6 phases, 9 questions)
- Board: marked Done the /desk lead pipeline row and the SMS consent checkbox row (both shipped in 77d7c11, consent tests 10/10) and the EIN row (Yeti has it). Moved "lead alerts live" to Today with the exact Twilio A2P steps. Added a software-clause note to the "reconcile the agreement" row. New rows: CRM Phase 0 (Waiting on Devon) and CRM Phase 1 build (Backlog)

**What's live / deployed:**
- Nothing deployed. crm/CRM-DESIGN.md is uncommitted in ~/Projects/on-point-jd

**Next up:**
- Yeti: buy OnPoint's Twilio number and register the A2P brand with the EIN (steps on the lead alerts row)
- Devon's wishlist + answers to the 9 questions in section 14, then map the wishlist onto the module/phase table
- Terms amendment: software ownership, data export, running costs, care fee (attorney)

**Notes for other environments:**
- OnPoint is Ohio-only, so contract templates follow Ohio law (Home Solicitation Sales Act 3-day cancel, ORC 4722); HB 769 roofing bill status unconfirmed
- Don't send Jay/Devon the design doc; show them a working screen