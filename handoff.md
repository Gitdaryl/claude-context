
## Session: 2026-10-17 ET (later)
**Environment:** Antigravity IDE
**What was done:**
- Teaser narrated by ElevenLabs Chris; scenes now sized to the narration (61.6s, 0.65s gaps); trade-neutral script (roofing example, good/better/best + add-ons, off-season side work)
- Site copy made trade-neutral; new tutorials band ("Technology is a lot. So we make the how-to videos."); FAQ "We are not roofers"
- Fixed a sync-tool bug ($1 backreference corrupted "$184.20" in prerendered HTML)

**What's live / deployed:**
- yetigroove.com/field-office LIVE (Yeti-Groove 67fd4a9), API reads app.onpointjd.com/field-office.json live
- onpoint-office 713fe65 on main: field-office.json + guard test + features:stale (pushed from a clean clone; another session is on feature/team-chat with uncommitted team-chat work, untouched)
- Vercel env FIELD_OFFICE_SOURCES on yeti-groove (production)

**Next up:**
- Backlog row: SEO audit of /field-office, own OG image, booking link

**Notes for other environments:**
- New OnPoint feature = add an entry to onpoint-office public/field-office.json in the same commit; the sales page picks it up within ~15 min.