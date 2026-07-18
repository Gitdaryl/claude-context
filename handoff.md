## Session: 2026-07-18 (ET, narration live)
**Environment:** Antigravity IDE
**What was done:**
- Generated all 19 narration clips (~29k chars, 32MB): treatment narrated in the "Dr Joseph Profit" voice (voice id 13fpLkxdyC2oV0VgouJ9, Yeti's ElevenLabs voice-design recreation of Joe's voice); structure page narrated by Bill (premade, the teacher voice)
- Created ElevenLabs conversational agent "Coach Story (Never Broken)" agent_6701kxssqah0ef9vtg44vmhjbm3d, Bill's voice, full craft prompt from agent-prompt.md; widget live bottom-right on both pages
- Verified live: 14 LISTEN buttons on treatment + 5 on structure, cold open plays (60s), widget renders ("Start a call")
- ElevenLabs API key stored in ~/never-broken-site/.env.audio (gitignored, chmod 600). Regeneration workflow: edit treatment → python3 scripts/generate_audio.py (only changed sections regenerate) → commit audio/ → push
- Coach Story is wired to never confirm the narration is really Joe if he asks; deflects to Daryl. Disclosure flag raised with Yeti: before material goes to funders/third parties, the synthetic voice must be disclosed and Joe must sign off

**What's live / deployed:**
- https://never-broken-site.vercel.app/treatment.html: Draft v2, notes, narration in Joe's voice, Coach Story widget
- https://never-broken-site.vercel.app/structure.html: education page, narration by Bill, widget

**Next up:**
- Yeti sends Joe the treatment link (suggest: "tap LISTEN on any section")
- Collect Joe's notes; v3 cycle when ready (regenerate only changed audio via the hash cache)

**Notes for other environments:**
- The API key was pasted in chat this session; if that ever bothers Yeti, rotate it at elevenlabs.io and update .env.audio, nothing else references it