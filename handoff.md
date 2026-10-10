## Session: Oct 9 2026 ET (OnPoint go-live prep)
**Environment:** Antigravity IDE
**What was done:**
- Supabase live project "onpoint" (ref ufddiuyxvnbtbuklfjuo, East US Ohio): 7 migrations, explicit API grants, sign-ups blocked, photo/receipt storage private, On Point JD org, Yeti's office account; mistaken Montreal project deleted
- Twilio A2P approved for On Point JD LLC; (567) 708-7208 in messaging service "OnPoint JD (A2P)"; webhook -> https://onpointjd.com/api/sms-inbound
- onpointjd.com: reply forwarder (/api/sms-inbound, signature-checked, commit 61deabf) live; TWILIO_* + CRON_SECRET set; redeployed; /api/health all green (twilio:true, cronSecret:true)
- OnPoint Office app (~/Projects/onpoint-office, local commits through f96b8f4): storm night, invoices, costs, shifts, update banner; 84 tests + 3 browser flows

**What's live / deployed:**
- onpointjd.com texting (lead alerts, customer confirmation for opted-in leads, reply forwarding); 9 AM follow-up digest email now armed
- Supabase project live but the app itself is NOT deployed yet

**Next up:**
- Tomorrow with Jay + Devon: text (567) 708-7208 (forward test) and a site lead with Text me ticked; Claude checks Vercel logs
- Deploy the app to app.onpointjd.com (needs Yeti's OK); add Jay (owner), Devon (sales), Linda (office), crew via npm run add-member:live
- Ask Jay: bulk salt vs bags, sub pay; Jay opens QuickBooks in On Point's name

**Notes for other environments:**
- Keys for the app are in ~/.config/onpoint-office/ on the Mac only (chmod 600)