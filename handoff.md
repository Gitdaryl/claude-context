
## Session: 2026-10-31, part 4 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Built the lead pipeline for the ElevenLabs "Joe" widget. Agent now extracts name, contact, organization, request_type, summary, shipping address, follow_up_promised, plus a "Needs human follow-up" evaluation (applied via API, live). New endpoint /api/convai-webhook (commit 23d76a9) verifies the HMAC signature with the ElevenLabs SDK and emails Joe (cc BOOKING_CC_EMAIL) only when a human must act.
- Workspace had zero webhooks, so nothing was ever posted anywhere. The local ElevenLabs key lacks convai_write and the IDE cannot write secrets, so three steps are Yeti's (below).
- Revised agent prompt saved at ~/Documents/Joe-Profit/voice-agent/PROMPT-2026-10-31.md (README beside it). Removes the "memorial website" framing and stops the AI promising shipments and calls.

**What's live / deployed:**
- Endpoint deployed; returns 500 "Webhook not configured" until the secret exists.

**Next up (Yeti, board row "finish wiring the AI Joe widget lead alerts"):**
- ElevenLabs: create workspace webhook "Joe Profit site" -> https://www.joeprofitneverbroken.com/api/convai-webhook (HMAC), copy secret.
- Vercel joe-profit: add ELEVENLABS_WEBHOOK_SECRET (Production), redeploy.
- ElevenLabs agent "Support agent": select that post-call webhook; paste the revised prompt. Test with a fake signed-book request.

**Notes for other environments:**
- Two real leads still unanswered in ElevenLabs history (signed book with address; Krystle Grant keynote/$32M pitch). IDs in the board row.