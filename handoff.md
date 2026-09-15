
## Session: 2026-09-15 (ET) addendum
**What was done:**
- Pushed Holly repo (3 commits): engagement/seller-report work, real listings + photos, new monthly seasonal article cron.
- api/cron-seasonal-article.js: 1st of month 8am ET. Season note + Holly's live listings + next 45 days of manitoubeachmichigan.com events + "A note from Holly" + FAQs. No calendar needed, no invented stats. ?dry=1 previews without saving. Idempotent per month.
- Ran it for real: "September on Devils Lake: The Quiet Before the Color" saved to Notion Holly Articles as Draft (AUTO_PUBLISH_MODE=safe) https://notion.so/3dc8c729eb5981e5adcfd9314a9eb381
**Next up:**
- Holly/Yeti review the September draft in Notion, tick Blog Safe + set Published Date to make it appear at /blog.
- To go fully automatic: `vercel env rm AUTO_PUBLISH_MODE production && printf autonomous | vercel env add AUTO_PUBLISH_MODE production` in the Holly repo.
- RESEND_API_KEY still unset on hollygriewahn (see earlier entry).