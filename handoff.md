## Session: 2026-07-18 (ET, audio/agent scaffold)
**Environment:** Antigravity IDE
**What was done:**
- Built the full narration + voice-agent layer for never-broken-site, shipped dormant (site looks unchanged until audio is generated):
  - LISTEN buttons on all 19 sections (14 treatment: overview, cold open, room, sessions 1-8, final, epilogue, throughline; 5 structure: parts one-five)
  - narrate.js: manifest-driven player; also injects the ElevenLabs convai widget bottom-right when audio/manifest.json has an agentId
  - scripts/generate_audio.py: extracts section text via the stable data-nb ids, ElevenLabs TTS (default voice Adam, override with ELEVEN_VOICE_ID), hash-cached so only changed sections regenerate on future drafts (~29k chars total for everything)
  - agent-prompt.md: "Coach Story" Hollywood script-teacher persona carrying the whole education (12 stages mapped to Joe, McKee/Snyder, courtship rule, trophy-case logic, full v2 treatment summary, football/franchise metaphors, plain 12-year-old language). Same paste-in pattern as the Manitou concierge
- Purpose per Yeti: Joe absorbs by ear (he cried when his website was narrated); this defeats scan-and-judge

**What's live / deployed:**
- Scaffold live at never-broken-site.vercel.app (buttons hidden while manifest is empty)

**BLOCKED ON: the ElevenLabs API key.** Not on the Mac, not accessible on the VPS (permission-blocked). Yeti needs to paste it into ~/never-broken-site/.env.audio (gitignored; example file .env.audio.example exists). Then next session: run scripts/generate_audio.py, create the Coach Story agent via API (or Yeti pastes agent-prompt.md into the ElevenLabs dashboard and provides the agent id), set agentId in audio/manifest.json, commit + push. One command each.

**Next up:**
- Get key → generate 19 MP3s → create agent → flip manifest → deploy
- Then send Joe both pages

**Notes for other environments:**
- ElevenLabs agent id for Manitou concierge is in Manitou-Beach/.env (VITE_ELEVENLABS_AGENT_ID); the API key was never stored locally, it lives in Yeti's ElevenLabs dashboard