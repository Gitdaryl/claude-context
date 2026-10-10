## Session: Oct 9 2026 ET (OnPoint Office live database)
**Environment:** Antigravity IDE
**What was done:**
- Live Supabase project "onpoint" (ref ufddiuyxvnbtbuklfjuo, East US Ohio, Free plan) created from the CLI; all 7 migrations pushed; On Point JD org f3a1473c-1850-4cda-9b28-bd656fc1b564; anon refused everywhere; photo/receipt storage private
- Keys: ~/.config/onpoint-office/service.env (secret, chmod 600), db-ohio.env (DB password, chmod 600), .env.production.local (publishable, gitignored)
- `npm run add-member:live -- --phone ... --name ... --role ...` asks for the PIN hidden

**Next up:**
- Yeti: flip off "Allow new users to sign up" on project "onpoint"; delete the empty Montreal project "onpoint-office" (ref jrqgedhewsooutnotkbx)
- Yeti: run add-member:live for himself (5172605907, role office)
- Twilio: confirm the brand is On Point's; put (567) 708-7208 in messaging service MG2d4165...; set TWILIO_* on the onpointjd site; reply forwarding for inbound texts
- Then: Vercel project app.onpointjd.com