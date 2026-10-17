
## Session: Oct 17 2026, ~7:30pm to 7:55pm ET
**Environment:** Antigravity IDE
**What was done:**
- Kyle (On Point superintendent) asked for a video tutorial on adding crew in the ? on the Team tab. Built `help/tours/add-crew.mjs` (recorded as the tutorial superintendent, iPad, English, 40.5 s): Add a person, name and phone, Crew or Crew lead, language and work, the PIN shown once, the app-link text, then Change on a row for Reset PIN and Turn off.
- `src/help/clips.ts`: `add-crew` for the superintendent on office:team; People and pay now roles owner/office/sales/bookkeeper (everyone who sees Money), so Kyle no longer gets a clip that sends him to a tab he does not have. Test added in tests/help.test.ts.
- Restarted the local API dev server (it predated this morning's superintendent commit and caches modules per process). Reverted the webp sweep's conversion of tests/fixtures/ruler.jpg and its 3 rewritten refs before staging.
- Board: new row Done with evidence; Backlog row filed for the wording in Kyle's Add a person form ("add them as Sales or Superintendent", which he cannot do).

**What's live / deployed:**
- onpoint-office main 61b307e + 87f4876 pushed; Vercel deployed. Verified: app.onpointjd.com/help/manifest.json lists add-crew; the mp4 serves as video/mp4 (2,273,856 bytes) and the poster as image/webp.

**Next up:**
- The Oct 16 re-record Backlog row still stands (18 clips stale at HEAD per `npm run help:stale`, plus another session's untracked public/field-office.json makes stale.mjs flag everything as "uncommitted app changes").
- Low: fix `people.pmLineOffice` for the superintendent (PersonForm.tsx + i18n), then re-record add-crew.
- Kyle is still crew_lead live; the in-person switch to Superintendent + PIN handoff row stays in Today (he only sees the new clip once he signs in as superintendent).

**Notes for other environments:**
- The ElevenLabs key IS on the Mac (~/.claude/.env); the old "not on the Mac" note was wrong. Memory corrected.
- Commit attribution used "Claude Fable 5.1"; the commit-push skill template still says Opus 5 (1M context). Update the skill if the Fable line is wanted everywhere.