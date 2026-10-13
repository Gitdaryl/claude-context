
## Session: 2026-10-13 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Built OnPoint lead intake from every door in ~/Projects/onpoint-office (uncommitted): website form (/api/hooks/lead), unknown-number texts (inbound hook now makes a lead), missed calls + voicemail on the Twilio number (/api/hooks/voice, /api/voicemail, Deepgram or Twilio transcript), and inbox email (Resend email.received on /api/hooks/resend, rules + optional Claude Haiku). Each becomes customer + job at "lead" + a message in Needs attention; calls and emails text the alert phones; a missed call gets one text back. Migration 20261029000000_leads.sql (channel call/web, provider website, unique site_lead_id).
- Website (on-point-jd/site, uncommitted): lead.js posts every form lead to the office app (lib/office.js); the crew forward names a new text lead.
- Tests: 2 new files (15 logic + 14 server), 2 older tests updated; full suite 995 passing; tsc, lint, build clean.
- Docs: office docs/SERVER.md (endpoints, env, "The company inbox" steps); CRM-DESIGN.md decision log.
- Vercel onpoint-office: LEAD_ALERT_PHONES set (from the site's CREW_SMS_PHONES). DEEPGRAM_API_KEY could NOT be copied (sensitive on Holly's project, pull gives a placeholder); removed the bad value.

**What's live / deployed:**
- Nothing deployed. Both repos have uncommitted work. Local Supabase has the migration; live does not.

**Next up:**
- Yeti says "push": commit-push both repos, `npx supabase db push` on the office repo, set the Twilio voice URL on +15677087208 to https://app.onpointjd.com/api/hooks/voice (curl from the VPS with /root/SunnySkies/.env creds).
- Yeti by hand: Resend MX on onpointjd.com root + add email.received to the app's webhook; Google Admin routing rule JDavis@onpointjd.net -> also deliver to inbox@onpointjd.com; DEEPGRAM_API_KEY and ANTHROPIC_API_KEY on onpoint-office; decide the phone (publish 7208, or forward 8001 unanswered calls to it and leave VOICE_RING_PHONES unset).

**Notes for other environments:**
- The lead intake is built but not live until the push + the four manual steps above. Details in onpoint-office/docs/SERVER.md.