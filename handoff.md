## Session: Oct 10 2026, late night ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office ops wave (commit 2495ba1, ~/Projects/onpoint-office, local only): "To send today" queue on Today (every customer and crew message due, reviewed and tapped, nothing automatic), 18 new templates, 7:30 am digest email (Vercel cron)
- Customer texts now saved on the customer's job (/api/hooks/inbound); a cancel-like text inside the 3-day window is flagged "possible cancellation" and blocks scheduling until the owner or office decides
- Calendar tab (double-booking, reschedule with reason, dumpster orders with drop-off and pickup), crew daily check-in, problem and decking photos with sheet counts, punch work after signing, PM hand-off, per-job cost card, private job folder
- Integration fixed 2 company-leak bugs (digest and incoming texts now belong to one company: APP_ORG, or the only one) and 7 smaller gaps
- Verified: 681 unit and DB tests, tsc, oxlint 0 errors, 8 browser flows on Chromium and WebKit; demo rebuilt with `npm run demo`
- Website commit 459c548 in ~/Projects/on-point-jd (local): sms-inbound posts every customer text to the app and names the customer and job in the staff forward

**What's live / deployed:**
- Nothing. onpoint-office has no remote. on-point-jd is 5 commits ahead and NOT pushed (a push to master is a live website deploy)

**Next up:**
- Jay answers 7 questions (Master Task Board row "Jay answers 7 questions from the ops wave")
- Yeti: deploy the app, set CRON_SECRET and DIGEST_TO, decide REPLY_TO; THEN push on-point-jd
- Still open: Glen Form 8300 (due Oct 12), Devon's REVIEW.md answers, Twilio campaign update, attorney questions, Devon's drone (Part 107)

**Notes for other environments:**
- Every customer message in the CRM is a draft a person taps to send. Do not describe it to Jay or Devon as automatic texting