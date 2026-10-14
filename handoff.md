
## Session: Oct 14 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Tami Frampton (On Point roof, 2701 Bleeker St, Oregon OH): fixed the Oct 10 transcription (house number was 3701), confirmed with Yeti (419-494-1538, finished Oct 8, paid in full, 10-yr labor); local import passed; Atlas registration due Dec 7
- scripts/import-paper.mjs gained --only KEY
- Built locally (onpoint-office, uncommitted): "More work at this house" (spotted work -> lead job for the same customer, jobs.from_job_id, Pipeline "Past customer" tag) and true photo dates on the insurance report (EXIF date + GPS for library photos, job_photos.time_from)

**What's live / deployed:**
- Nothing. Two migrations local only (20261101000000, 20261101100000)

**Next up:**
- Yeti runs the live Tami import (command in Session Brain row)
- Ship: npx supabase db push FIRST, then commit + push (leave scripts/add-lead.mjs and tests-e2e/review-ux-* out)
- Devon: upload original tear-off photos, make the report, email Tami; add Inside repair + Gutters leads on her job

**Notes for other environments:**
- Board rows: "ship More work..." and "Tami Frampton..." (Today); Tami questions added to ASK DEVON IN PERSON