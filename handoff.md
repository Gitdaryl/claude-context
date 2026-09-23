## Session: 2026-09-23 ET
**Environment:** Antigravity IDE
**What was done:**
- Planned and started a 4-part build on Holly Griewahn's site (~/Documents/Claude Code/Holly/Holly-main, Gitdaryl/Holly). Plan at ~/.claude/plans/velvet-foraging-grove.md
- Shipped /events: the Manitou Beach calendar collected for buyers, 64 events through December, prerendered with a real FAQ. Deliberately NOT schema.org/Event (Holly is not the source of truth; ItemList + CollectionPage + isBasedOn instead)
- Fixed a live bug: api/events.js capped at 40 and was silently dropping all of December
- Fixed: lake-page event rows deep-link now. Only 10 of 64 upstream records carry eventUrl, so 33 of 40 rows used to dump you on a generic index
- Shipped /holly-yeti: her own version of the show page, different copy from Manitou's on purpose. Episode wall from the channel's public RSS feed, which needs NO API key
- robots.txt now names 15 AI crawlers in generated groups, Disallow before Allow. Verified with a parser: GPTBot + /admin is blocked, which the old file did not guarantee
- Daily deploy hook (api/cron-refresh.js, 5:30am ET) so prerendered pages a crawler reads never go more than a day stale. Needs VERCEL_DEPLOY_HOOK_URL
- Newsletter foundation: subscribe/confirm/unsubscribe, double opt-in, RFC 8058 one-click, 400-day unsub tokens, ONE shared email template. No send path exists yet, by design
- FOUND: the previous session's entity/SEO work (src/data/profiles.js, buildSameAs) was never committed. The live site had the old 2-entry sameAs. Now committed and live with 6

**What's live / deployed:**
- hollygriewahn.vercel.app, commits 80f9c17, beb5897, 5d4674f, d804848
- /events, /holly-yeti, /api/events?all=1, /api/youtube, /api/newsletter, robots.txt with AI groups, 90 prerendered pages
- Newsletter signup form is deliberately HIDDEN until the env is set, so nothing is half-live

**Next up:**
- Yeti: NEWSLETTER_SECRET, and start the Resend sending domain news.hollygriewahn.com (SPF/DKIM/_dmarc). This does NOT depend on the domain move and is the longest lead time
- Yeti: Vercel Deploy Hook -> VERCEL_DEPLOY_HOOK_URL
- Then: admin Letter tab (draft + preview + approve) and the resumable send endpoint
- Verify whether Resend /emails/batch supports per-message headers before writing the send path

**Notes for other environments:**
- IDX first, then the domain. Everything is built migration-proof: PUBLIC_SITE_URL drives all canonicals, and PRERENDER_ORIGIN now exists so the first build after the flip cannot ship empty pages if the new host is not serving yet
- HARD GATE: no real newsletter send while the site is on vercel.app. Unsubscribe links are absolute URLs that live in inboxes forever
- holly-engage is a PUBLIC blob store, so access:'private' is rejected outright. Subscriber pathnames are HMAC-keyed instead
- @vercel/blob put() does NOT overwrite without allowOverwrite:true, it throws