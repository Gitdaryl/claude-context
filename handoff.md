
## Session: 2026-10-13 (ET), update
**Environment:** Antigravity IDE
**What was done:**
- Finished the OnPoint Office help-video system: all 13 clips recorded with ElevenLabs Chris (Yeti's pick), 11 English iPad/office clips + Spanish and English phone clips for roof-day and snow-visit. All under 60 s, frames and sync verified.
- Recorder hardened: tutorial org rebuilt fresh before every take, lock so two recorders never overlap, posters as WebP (the push-time WebP sweep would otherwise orphan JPG names), `npm run help:stale` lists clips whose screens changed since recording.
- SOP written: README "Shipping updates", src/lib/whatsNew.ts comment, help/README.md: a release that changes a screen re-records its clips before deploy.
- ElevenLabs key "OnPoint help clips" (Text to Speech + Voices read) saved in ~/.claude/.env; help/voice.mjs reads it there.
- Board: tutorial row on Today for Yeti (review + push); new rows: in-app roof measurement idea (parked), punch-list wrap bug, sample job 1005 half-finished.

**What's live / deployed:**
- Nothing yet. Everything is uncommitted in ~/Projects/onpoint-office (18 changed/new paths plus help/ and public/help/).

**Next up:**
- Yeti watches the clips, then says "push" (Vercel auto-deploys the help button + clips).
- Optional after commit: re-record all 13 so the manifest build id matches HEAD (VO cached, ~25 min unattended).
- `npm run help:seed` after any `npm run demo` or `db:reset`.

**Notes for other environments:**
- Spanish narration only for crew clips. Office clips English only.
- The pre-existing untracked tests-e2e/review-ux-*.mjs files are from another session; left alone.