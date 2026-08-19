## Session: 2026-08-18 ET
**Environment:** Antigravity IDE

**What was done:**
- Legwork on Caleb Ulku's YouTube response to Neil Patel's "New Rules of Google". Pulled the full transcript and verified the headline claims against independent sources instead of the video. Note for next time: yt-dlp only gets captions on this video with `--extractor-args "youtube:player_client=android"`; the default, web, ios and mweb clients all fail.
- Claims that hold: 68% zero-click (SparkToro/Similarweb), HubSpot 70-80% organic drop with the CEO naming AI Overviews on the Q1 2025 call, Ask Maps shipped 12 Mar 2026 with no ads so every result is organic. The load-bearing number is informational 74% zero-click vs transactional 31%, which is the actual evidence that local is not in the publishers' boat.
- Claim that is overstated: HubSpot's flat revenue proving brand demand carried it. Likelier the blog traffic was never attached to revenue in the first place.
- Audited our sites with real crawler user agents rather than reading code. Four findings, two fixed and deployed same day.
- Filed the follow-ups to the Master Task Board and logged a Session Brain row. Corrected three existing board rows rather than filing duplicates.

**What's live / deployed:**
- Manitou Beach `main`, commit `7833f69`, cherry-picked so the five unrelated commits on `fix/view-counter-and-cron-observability` stayed on the branch.
- Sitemap: `public/sitemap.xml` was shadowing the `/sitemap.xml` to `/api/sitemap` rewrite, because Vercel resolves static files before rewrites. Google had been reading a 22-URL file containing zero profile pages, so no business, winery or food truck profile had ever been in the sitemap. Now 61 URLs live: 31 business, 10 wineries, 7 food trucks. The generator also now takes its listing set from `/api/businesses` rather than a parallel Notion query, since the two had drifted and it was about to publish `phoenix-rising-wellness`, `devils-lake-inn` and the demo tiers, none of which render.
- Business profile pages: `handleBusinessSchema` was injecting JSON-LD and nothing else, so all 31 profiles served index.html's homepage title with zero body text. Now each has its own title, description, OG/Twitter set and a `noscript` block with name, category, address, phone and description. Town is parsed off the free-text address, so Hammill reads as Addison and Chateau Aeronautique as Onsted.
- yetigroove.com: Yeti turned off Cloudflare's "Block AI training bots". All five AI crawlers went from 403 to 200.

**Next up:**
- Cloudflare's second setting on yetigroove.com, "Manage your robots.txt", still injects a managed file that disallows GPTBot, ClaudeBot and Google-Extended. The door is unlocked but the no-entry sign is still up. Our own robots.txt is already correct, so turning the managed file off is enough.
- Resubmit the MB sitemap in Search Console. Google has been reading the 22-URL file for a long time.
- Backfill Hours and Google Place ID: both sit at 2/31. This is the unfinished half of a board row already marked Done. Place IDs can be pulled in bulk from the Places API.
- Fix `addressLocality` hardcoded to "Manitou Beach" in `src/utils/businessSchema.js`. It tells Google that the Addison, Onsted, Brooklyn and Tipton businesses are all in Manitou Beach. The parser to lift is already shipped as `localityFromAddress()` in `middleware.js`. Left alone because that module is shared with the client render.
- geoFaq is 0/31. FAQPage schema is already wired and waiting on content.

**Notes for other environments:**
- Two domains I assumed were ours are not: `irishhillsrealty.com` is a parked for-sale domain owned by someone else, and `spottedowlevents.com` is an unrelated Wix page. Both sites live on `.vercel.app` URLs. Worth buying the names before either gets promoted.
- Business descriptions measured at median 151 characters, 24 of 31 under 200. Hammill Electric at 494 is the model. This is sellable as a paid rewrite with a visible before and after, not something to absorb.
- Full audit published as an artifact: https://claude.ai/code/artifact/e5e83f36-3ad1-451d-9ec3-35a839d8dae5