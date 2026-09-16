
## Session: 2026-09-16 (ET), part 4: secret rotation
**Environment:** Antigravity IDE
**What was done:**
- Vercel "Needs Attention" = readable secrets post April-2026 incident. Built ~/.claude/tools/rotate-env.py (Yeti pastes once; writes hidden Secret to every project holding the key, redeploys, updates local .env + VPS /root/SunnySkies/.env over ssh).
- Resend fully rotated to per-site, domain-locked, sending-only keys: holly-site, yetigroove-sites (yeti-groove/yeticlone/hammill/yetickets), manitou-beach-site, joe-profit-site, sunny-skies-vps. Every one verified by a real send (Holly contact, Joe send-test-email, Manitou subscribe, VPS curl). Hammill + YetiClone email had been dead (deleted key); Yetickets had a re_re_ typo; both fixed as a side effect.
- Fixed un-awaited SMS in Holly contact/chat intakes (Vercel was aborting the Twilio call).
**Next up:**
- Yeti: delete old Resend keys (manitou-beach connect, Onboarding, Yetickets Production). Then same pattern for TWILIO_AUTH_TOKEN (also n8n credential), ANTHROPIC_API_KEY (then source ~/.zshrc), NOTION_TOKEN_DISPATCH, and `ADMIN_SECRET --only hollygriewahn` (press Return to auto-generate). Never rotate Manitou's ADMIN_SECRET blindly.
- Cleanup: 6 "Key test (delete me)" rows in Holly Leads + Holly's inbox; test blobs.
**Notes for other environments:**
- Secrets are now hidden in Vercel: nothing can read them back, verify by sending.