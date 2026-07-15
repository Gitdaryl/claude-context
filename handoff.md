## Session: 2026-07-14 ET (Receipts, continued)
**Environment:** Antigravity IDE
**What was done:**
- Phase 2 VERIFIED: Yeti tested ~/debate-copilot/prototype/listen.html with his Deepgram key; live tab transcription works
- Phase 3 built: ~/debate-copilot/prototype/live.html = full Receipts pipeline in one page (Deepgram STT -> claude-haiku-4-5 claim detection every 12s -> claude-opus-4-8 + web search verification -> DEBUNKED / VERIFIED / ASK THIS cards)
- Both API keys prompted once in-browser, stored in localStorage only

**What's live / deployed:**
- Phase 1 demo artifact (private): https://claude.ai/code/artifact/075f6059-1929-4fe8-930a-1d484c7c080b

**Next up:**
- Yeti: create an Anthropic API key at console.anthropic.com (needs billing; separate from the Claude subscription), then open live.html and LISTEN TO A TAB against a debate video
- Add "Receipts" as a Project option in the Session Brain Notion database

**Notes for other environments:**
- Spec: ~/debate-copilot/SPEC.md · demo replay: prototype/dashboard.html · transcript-only: listen.html · full pipeline: live.html