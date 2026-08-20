## Session: Aug 19 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Answered "should the AI Holly weekend script be an automation": yes, and most of the plumbing already existed. thursday-roundup.yml already fires Wed 11pm ET and pulls the same Notion events.
- Resolved the HeyGen question. No MCP connector exists; the key stored in YetiClone/.env.production was dead (401 on /v3/avatars and /v3/users/me). Yeti created a fresh Agent-type key named AI HOLLY, verified working: wallet $97.23, auto-reload OFF.
- Found the Holly avatars. Best candidate pair: avatar_id 3ab0d3a19c8c4f69b120c0d3831ff8c5 with cloned voice_id 5d05bed2a62c4bf586edd4d657e2454f. Not confirmed by a test render, the render call was blocked by the sandbox classifier.
- Built the Wednesday-night script generator in Projects/Manitou-Beach: scripts/holly-persona.md, scripts/holly-weekend-script.js, .github/workflows/holly-weekend-script.yml.
- Dry run against the live Aug 20-23 window worked. Its VERIFY section flagged a likely Lighting/Lightning typo and 3 events missing start times.

**What's live / deployed:**
- Nothing deployed. All three new files are untracked in Projects/Manitou-Beach, not committed and not pushed.

**Next up:**
- Yeti: turn on HeyGen auto-recharge so a Wednesday render never dies silently at zero credits.
- Yeti: add ADMIN_SECRET as a GitHub secret on Gitdaryl/Manitou-Beach. ANTHROPIC_API_KEY and BLOB_READ_WRITE_TOKEN are already there.
- Commit and push the three files, otherwise the cron does not exist.
- Test-render the Holly avatar to confirm the right avatar/voice pair.
- Build the approve-and-render step (Yeti chose a draft-Wednesday, approve-Thursday gate over full auto).

**Notes for other environments:**
- The working HeyGen key is an Agent-type key and it authenticates the plain REST API fine. The Developer/Agent choice in that dialog is a labeling field, not a capability field.
- claude-opus-5 and claude-sonnet-5 run adaptive thinking by default and max_tokens caps thinking plus response text together. A tight max_tokens returns an empty response with no error. This will bite any other script in these repos that sets a small budget.