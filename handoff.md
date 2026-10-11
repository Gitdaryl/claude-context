
## Session: Oct 11 2026 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Compared OnPoint Office (built app) with JobNimbus: ~/Projects/on-point-jd/crm/JOBNIMBUS-COMPARE.md. Verdict: JobNimbus ahead only on reports + QuickBooks; ours ahead on taps, crew Spanish, snow, Ohio rules, human-tapped messaging. Board row filed: owner screen (six tappable numbers) + nightly CSV export + QBO sync before Jan 1 2027.
- DEPLOYED OnPoint Office to production: app.onpointjd.com (Vercel project onpoint-office, Node 24). All 29 migrations pushed to live Supabase (project onpoint, ufddiuyxvnbtbuklfjuo), 5 private buckets. Yeti pasted 13 env vars by hand (auto mode blocks secret writes). Resend webhook created by Yeti. Website project got OPTOUT_SECRET + OFFICE_OPTOUT_URL and was redeployed (same build).
- Verified live: /api/health ok:true, tsc/lint/build clean, 795 tests pass locally, webhooks refuse unsigned (403), dev hook off (404).
- Twilio A2P: brand APPROVED, campaign VERIFIED (checked on the VPS, /root/onpoint-a2p).

**What's live / deployed:**
- https://app.onpointjd.com (first production deploy, Yeti's office account is the only user)
- onpointjd.com redeployed (env only, no content change)

**Next up:**
- Yeti: sign in on phone, send one test email + one test text to himself, confirm "delivered". Delete ~/.config/onpoint-office/vercel-prod.env (holds Twilio token).
- GitHub: repo push + history squash were BLOCKED by auto mode (remote repoint / destructive). Local branch untouched (master, 34 commits). Push when Yeti allows; "version: local" on the sign-in screen fixes itself then.
- Terms software clause before real On Point data goes in. Real crew/customers/sites. Supabase Pro ($25/mo) once photos flow (Free pauses after 7 idle days).
- Twilio decisions: campaign says no embedded links but the progress text carries one; texts say "call or text 8001" but send from 7208.
- Owner screen + CSV export + QBO sync row (Backlog).

**Notes for other environments:**
- Both `notion` and `notion-business` MCP connectors return 401 invalid token; the claude.ai Notion connector works. Fix the tokens or drop those two.