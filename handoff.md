
## Session: 2026-10-13 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Checked the Master Task Board: "OnPoint Office: tutorial video series" already existed (Backlog since Oct 10). Moved it to Today with the review steps.
- Built the in-app help system in ~/Projects/onpoint-office (UNCOMMITTED): ? button in the top bar opens a sheet of short clips for the current screen; hidden when none; never auto-opens; one-time hint; Spanish falls back to English with a tag; videos excluded from the PWA precache.
- Built the recorder (help/): seeds an isolated tutorial org (local DB holds real customers; reset was blocked), Playwright drives the app with injected cursor, spotlight ring and caption bar, narration placed per step, ffmpeg mux, sync checked.
- Three clips in public/help: add-a-lead.en (43 s), roof-day.es (48 s), roof-day.en (41 s). Narrated with the Mac "say" voice because no ElevenLabs key is on the Mac.
- Office clips English only; Spanish only for crew clips (Yeti's call).

**What's live / deployed:**
- Nothing. All local and uncommitted.

**Next up:**
- Yeti reviews the 3 clips and narration (help/tours/*.mjs).
- Put ELEVENLABS_API_KEY in the shell, `node help/voice.mjs --list`, pick a voice, rerun `npm run help:record -- add-a-lead` and `-- roof-day`.
- Then produce the remaining clips (book-the-inspection, present-and-sign, schedule-and-order, final-walk, invoice-and-payment, send-today, snow-visit) from the same tour pattern.
- Commit + deploy. `npm run help:seed` again after any `npm run demo` or `db:reset`.

**Notes for other environments:**
- The ElevenLabs key is not in any .env on the Mac; it is probably only in Vercel (Joe Profit / Yeti-Groove). Cowork may know where.