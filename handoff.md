
## Session: Oct 9 2026 ET (Supabase live)
**What was done:**
- Supabase project onpoint-office (ref jrqgedhewsooutnotkbx, region ca-central-1 Montreal, Free plan) created by Yeti, linked; all 7 migrations pushed; explicit API grants; On Point JD org created (id 7ee4c2a9-ad92-4012-9ff0-48707d8efabf)
- Keys stored at ~/.config/onpoint-office/service.env (chmod 600) and .env.production.local (gitignored); new sb_publishable/sb_secret keys (CLI needs --reveal for the secret)
- Twilio A2P campaign approved (CM3db559ab..., messaging service MG2d4165...)

**Next up:**
- Yeti: turn off "Allow new users to sign up" (Auth > Sign In / Providers); decide keep Montreal or recreate in Ohio
- Yeti: confirm A2P brand is On Point's; add the number to the messaging service; set TWILIO_* on the onpointjd site, then Claude redeploys + test lead
- Yeti's phone + PIN for the first live owner account; then Vercel project app.onpointjd.com