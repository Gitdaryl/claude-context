## Session: 2026-10-17 ET
**Environment:** Antigravity IDE
**What was done:**
- Answered Kyle's PIN question: 568 566 is a 6-digit crew PIN, correct for his live role (crew_lead, added Oct 14, never signed in). 8 digits is for owner/office/sales/bookkeeper/superintendent.
- Found the gap: the Oct 16 meeting said Kyle adds the crew on the Team tab, but only owner and office could. Yeti chose superintendent + add crew over the office role (keeps Kyle on the no-money line).
- Built it in onpoint-office: a superintendent adds, changes, resets the PIN of and turns off crew, crew leads and subs; never anyone else, never a move out of the field. src/lib/people.ts SUPER_MANAGES, api/_lib/members.ts, migration 20261104000000_superintendent_people.sql (app.members_guard), Team tab opens for him, EN + ES refusal text, docs.
- Tests: new logic, server and RLS cases; full suite 76 files / 1328 tests green.

**What's live / deployed:**
- onpoint-office commit e871894 pushed to main; migration applied to the live Supabase project; Vercel production deploy Ready; app.onpointjd.com serves the new bundle (verified by string in index-Def0UBhi.js).
- Master Task Board: new Done row (build) + updated Notes on "In person: switch Kyle to Superintendent and hand him his new PIN" (still Today).

**Next up:**
- In person: Team tab > Kyle > Change > Superintendent > Save, hand him the 8-digit PIN face to face (568 566 stops the moment the role changes), then show him Team > Add a person and the ? beside Move it.
- Nothing else pending from this session.

**Notes for other environments:**
- Kyle is still crew_lead in the live database until Yeti or Jay flips him on the Team tab. The app and database are ready for him as superintendent.
- The webp sweep would convert tests/fixtures/ruler.jpg in onpoint-office; it was skipped on purpose (test fixture, not served).