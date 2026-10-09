## Session: 2026-10-09 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD Twilio A2P prep: found the new number +1 567-708-7208 sits in the Yeti Groove Media LLC main Twilio account (no Messaging Service, no inbound webhook)
- Decided route: Yeti Groove = ISV; OnPoint gets its own Secondary Customer Profile + Low-Volume Standard brand + Low Volume Mixed campaign, created by API (Console cannot create Secondary profiles)
- Site A2P audit: /terms was a 404, opt-in box did not name the brand or link policies. Fixed: "OnPoint JD can text me about this request" + Privacy Policy and Terms links under all 18 boxes, new /terms page with SMS terms, consent version sms-v2-2026-10-09, tests pass
- Paste-ready brand + campaign answers in on-point-jd/A2P-REGISTRATION.md

**What's live / deployed:**
- Nothing new live. Commit aa62d13 on master, not pushed (push = prod deploy)

**Next up:**
- Yeti: say "deploy"; send legal name exactly as on the CP 575 + address on the letter + Jay's title; say "go" on registration
- Claude: create profile/brand/Messaging Service/campaign from the VPS; EIN typed by Yeti into a hidden prompt
- After approval: inbound reply forwarding, TWILIO_* env on onpointjd, phone test

**Notes for other environments:**
- Do not put 567-708-7208 on Manitou's campaign