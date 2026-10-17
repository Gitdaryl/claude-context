
## Session: Oct 17 2026, 12:10 pm ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: home-screen install already worked (PWA). Built phone alerts (web push) on branch feature/push-alerts in ~/Projects/onpoint-office
- Bell + Alerts sheet: Got it, Open job, Directions, Sent view (who got / saw / tapped Got it / was texted)
- Alerts: new lead, customer reply, issue photo, put on a job, job moved. Backup text if no Got it: 10 min leads/replies, 30 min job news (held to 7am)
- Tests: 15 new, full suite 1342/1343 (1 = PIN hourly cap from repeated runs)

**What's live / deployed:**
- Nothing. Uncommitted on feature/push-alerts. Migration only on LOCAL Supabase.

**Next up:**
- Commit/push, `npx supabase db push`, VAPID keys in Vercel (`npx web-push generate-vapid-keys`), deploy, real iPhone test
- Website (on-point-jd) to skip phones listed in the app's `pushed` answer
- Group texts as push (deferred)

**Notes for other environments:**
- Task board rows filed (Today: take alerts live). Old dev API still running on :8787 from 12:14 am, left alone.