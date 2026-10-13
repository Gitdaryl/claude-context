## Session: 2026-10-13 (late evening ET, part 2: ship)
**Environment:** Antigravity IDE
**What was done:**
- Shipped the OnPoint lead intake built earlier tonight: onpoint-office commit 87c4fdd pushed (Vercel production build Ready; /api/health 200, new hooks refuse unsigned posts with 403), live Supabase migrated with 20261029000000_leads.sql, Twilio +15677087208 voice URL set to https://app.onpointjd.com/api/hooks/voice from the VPS.
- on-point-jd commit abc0e97 pushed to master (the site posts every form lead to the office app; the crew forward names new text leads). Note: this repo's branch is master, not main.
- Yeti chose call forwarding for the phone (8001 unanswered -> 7208); carrier codes for Jay are on the board row. VOICE_RING_PHONES stays unset.
- Board: "ship the lead doors" Done with evidence; inbox row (Resend MX + email.received + Google routing) Today; phone row Waiting on Jay; keys row Today (Yeti will create a NEW Deepgram key since the Holly one is sensitive and unreadable).

**What's live / deployed:**
- app.onpointjd.com: website-form, unknown-text and missed-call leads are live now. Email leads wait on the Resend MX + webhook event + Google routing (Yeti, by hand).
- onpointjd.com: deployed from abc0e97.

**Next up:**
- Yeti: Resend > Domains > onpointjd.com > Receiving MX (paste the record line into the IDE and Claude adds it with vercel dns), add email.received to the app's Resend webhook, Google Admin routing rule JDavis@onpointjd.net -> also deliver to inbox@onpointjd.com, make a new Deepgram key + an Anthropic key for onpoint-office, ask Jay to set call forwarding.
- Test after forwarding: call 8001, let it ring out, expect the greeting; a lead + texts within a minute.

**Notes for other environments:**
- Missed-call and text leads are live. Do not republish 7208; the published number stays 8001 with forwarding.