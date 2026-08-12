## Session: 2026-08-11 ET
**Environment:** Antigravity IDE
**What was done:**
- Started from Gypsy Blue Vineyards reporting she couldn't edit her events. Ended up finding and fixing five separate problems on manitoubeachmichigan.com.
- Bug 1: `api/submit-event.js` session path (events 2+ after the first SMS verify) created an Edit Token and emailed it but never texted it. Fixed.
- Bug 2: the edit page couldn't change the event NAME at all. `EventEditPage.jsx` showed it as a static heading and `api/event-edit.js` ignored the field, so a misspelled performer name in a title was unfixable. Fixed, blanks ignored so a title can't be wiped.
- Bug 3 (found by testing bug 1's fix): `sendSMS()` blindly prefixed "+1". DARYL_PHONE is stored E.164, so every admin alert went to "+1+1XXXXXXXXXX" and failed silently, including the held-for-review notices. Normalization moved into `sendSMS` so all call sites are fixed at once.
- Bug 4: the new edit-link SMS was fire-and-forget, and Vercel freezes the function on return, so the first live test never sent. SMS and welcome email are awaited now.
- Bug 5: the Twilio number's SMS webhook still pointed at `demo.twilio.com`. Inbound texts got Twilio's stock "configure your SMS URL" reply and reached nobody. Gypsy Blue texted on Aug 9 asking about this exact spelling fix and got that back. Built `api/sms-inbound.js` (forwards to Daryl by SMS + email, replies in the site's voice) and repointed the number at it.
- New `/my-events`: enter your phone, get one texted magic link listing every event you've submitted with an edit link on each. HMAC signed, 30 day TTL.
- New date sanity check: `src/utils/dateSanity.js` + `src/components/DateHint.jsx`, wired into the submit and edit forms with min/max picker bounds. Warm amber nudge, never blocks submit.
- Data fix: Gypsy Blue's Sept 5 "Holloway" event had start date `0026-09-05`. The feed filters on start date so it was invisible. Corrected, confirmed live.

**What's live / deployed:**
- Commits c801520, db88e8c, 32c7517 on main, all auto-deployed and verified by asset content-type.
- Verified on production: my-events sends (Twilio shows delivered), magic link returns the right events, forged token rejected, inbound handler returns TwiML and the forward text was delivered. The Twilio log shows the before/after side by side: `+1+15172605907 failed` on Aug 11, `+15172605907 delivered` after the fix.
- Twilio number PNba20430778bb125257249509ff2633d3 SmsUrl changed from `https://demo.twilio.com/welcome/sms/reply` to `https://manitoubeachmichigan.com/api/sms-inbound`. One API call to revert.
- Smoke-test event created during testing was archived in Notion.

**Next up:**
- Three events are sitting unseen because the admin alerts were failing: two "Widow and Widower Group" (Review, Jun 10, angandco.mi@gmail.com, duplicate submissions) and "Topless In The Hills" (Pending, May 16, Lgervick@newgenauto.com, never verified). Decide approve or reject.
- Send Gypsy Blue the /my-events link.

**Notes for other environments:**
- Manitou event edit tokens are per-event. `/my-events` is now the front door for organizers; send that rather than hunting individual edit links.
- `sendSMS` in `api/lib/twilio.js` now normalizes any US phone format. Don't pre-format at call sites.