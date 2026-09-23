
## Session: 2026-09-22/23 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Diagnosed the failed Holly demo: the login link was never broken. The guided tour auto-started on first sign-in and from step 7 navigated onto the PUBLIC pages, so the texted link looked like it just opened her website. Fixed: tour is offered by a welcome card (never auto-runs), the desk half ends at a "Show me the site" gate, public steps carry a back-to-desk link, ending/skipping returns to /admin, and a "Your desk" chip sits on every public page while signed in.
- Login field now accepts a pasted login link or the whole text message, not just the admin key; expired links say so.
- The desk is installable: manifest + icons + Apple meta injected only on /admin, so Add to Home Screen opens straight into the desk standalone. One-time hint card explains how (iOS wording on Safari).
- Holly named her site assistant **Heather** (widget greeting/header/aria-label, chat persona, tour step). Verified live: "I'm Heather, the virtual assistant here on Holly's website."
- Entity/SEO work, migration-proof: src/data/profiles.js holds every public profile (Google, Facebook, Instagram, LinkedIn, Manitou listing, hollygriewahn.com) + Foundation Realty (foundationlenawee.com) + phone; schema sameAs derives from buildSameAs(SITE) which drops self-referencing entries automatically when PUBLIC_SITE_URL changes. Fixed api/cron-seasonal-article.js reading SITE_URL instead of PUBLIC_SITE_URL (a domain-move landmine).
- Manitou Beach public/llms.txt now has a "Real Estate on the Lakes" section naming Holly (live). Sand/Evans Lake drone hero, poster and card added for the Cambridge & US-12 Corridor region.
**Careful:**
- Manitou-Beach checkout has uncommitted work from another machine (promo-claim deletions, LaunchPage, offers, robots, wine village files) and is 2 commits behind. I restored it exactly as found and pushed the llms.txt change from a clean clone. See memory dirty-repo-commit-safety.
**Next up:**
- Redo the walkthrough with Holly: text a login link, tap it, land on the desk, then Add to Home Screen while she is there.
- Still owed by Holly (crAIg thread 1a0af84010864c12): seller names/emails, Paragon photos for 22 list-side sales, Original List Price report, lake for 18 sold addresses, brokerage compliance wording, domain registrar, Paragon scheduled report (Way 1) and broker name/email for IDX (Way 2). Plus docs/ASSETS-NEEDED.md items.
- Roadmap remaining: inbound email parser (unlocks listing sync + hotsheet/showing feedback in the Monday update), bookings, milestones/mark-sold, welcome kit, monthly owner update.