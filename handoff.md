## Session: 2026-07-14 ET
**Environment:** Antigravity IDE
**What was done:**
- Researched real-time AI fact-checking apps (Factiverse, InTruth, Cluely, LiveFC, Filmot)
- Confirmed a gap: nobody combines live listening + qualifying questions for fuzzy claims + YouTube sound-bite receipts
- Drafted MVP spec for "Receipts", a live debate copilot for YT political/religious debaters: ~/debate-copilot/SPEC.md
- Saved project memory: debate-copilot-receipts.md

**What's live / deployed:**
- Nothing deployed; spec only

**Next up:**
- Phase 1 of the spec: dashboard skeleton rendering fake cards from JSON
- Decide on the demo debate episode (tariffs/economy topic) for the end-to-end test

**Notes for other environments:**
- Full spec at ~/debate-copilot/SPEC.md on the Mac; core loop = STT -> claim detect -> triage into verdict card / qualifying-question card / receipt card
- Stack planned: Next.js/Vercel, Deepgram, Claude + web search, Upstash KV, yt-dlp caption index