## Session: July 23, 2026 ET (IDE, Mitch Ramsey listing site)
**Environment:** Antigravity IDE
**What was done:**
- Request-a-Showing form live in the agent band on https://irish-hills-realty.vercel.app/8580-marr-hwy
- /api/showing persists every lead to Blob BEFORE attempting notify (build standard); verified live: test lead saved even with email unconfigured
- /api/leads key-protected lead review, verified 401 on wrong key and 200 with the real one (LEADS_KEY on Vercel; copy at Desktop/irish-hills-leads-key.txt)
- Gotcha logged: piping env values to `vercel env add` needs printf "%s" (no trailing newline) or auth comparisons fail
- Email notify via Resend wired but dormant: RESEND_API_KEY not on this project yet (classifier blocked copying it from the Holly project)

**What's live / deployed:**
- Form, lead persistence, and lead review all live and verified end to end

**Next up:**
- Yeti: `cd ~/Projects/irish-hills-realty && npx vercel env add RESEND_API_KEY production` (paste key from Holly project or Resend dashboard), optional LEAD_EMAIL for Mitch's inbox, then `npx vercel deploy --prod --yes`
- One TEST lead ("TEST Lead (Claude verify)") sits in the store; ignore or delete
- Still open: price/status flip, MLS photo cap + export, Good-to-Know rural facts, print flyer + QR, custom domain, vertical video

**Notes for other environments:**
- Lead review URL pattern: https://irish-hills-realty.vercel.app/api/leads?slug=8580-marr-hwy&key=<LEADS_KEY from Desktop file>