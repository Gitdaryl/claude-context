# Session Log

> Running log of all IDE sessions. Appended automatically at session end.
> See `handoff.md` for the latest session only.

---

## 2026-05-24 11:25 AEST

## Session: 2026-05-24 15:30 AEST
**Environment:** Antigravity IDE
**What was done:**
- Built cross-environment session sync system
- Created session-handoff.sh Stop hook
- Added handoff.md + sessions.md to context repo
- Updated sop.md with session-end SOP

**What's live / deployed:**
- Hook active in ~/.claude/settings.json

**Next up:**
- Test the hook fires correctly on next session end

**Notes for other environments:**
- Cowork: on GDay, now also fetch handoff.md to see last IDE session

---

## 2026-05-24 15:42 AEST

## Session: 2026-05-24 16:00 AEST
**Environment:** VPS (DigitalOcean yeti-vps)
**What was done:**
- VPS confirmed as DigitalOcean droplet (143.198.171.9, Ubuntu 24.04)
- Claude Code + gh CLI were already installed and authenticated
- Session-handoff Stop hook installed
- CLAUDE.md + settings.json configured
- VPS is now a full environment in the cross-environment sync system

**What's live / deployed:**
- Hook active, VPS ready for mobile sessions

**Next up:**
- Test a real session from mobile Claude app

**Notes for other environments:**
- IDE + Cowork: VPS is confirmed DO droplet, always-on, hook matches IDE setup exactly

---

## 2026-05-24 22:53 AEST

## Session: 2026-05-24 AEST
**Environment:** Antigravity IDE
**What was done:**
- Fixed Vercel Blob CDN stale-cache bug (critical): switched all three writeDb functions from `allowOverwrite: true` to `addRandomSuffix: true` + `del` old blobs — now every write gets a fresh CDN URL, reads always get current data
- Fixed seed-outreach 500 errors: null safety on `place.types`, `.filter(Boolean)` on blob list, global try/catch
- Added Kanban board full-viewport CSS breakout: `width: 100vw; marginLeft: calc(-50vw + 50%)`
- Replaced broken Google Places seed UI with manual Batch Add modal (textarea, category/area/priority selectors)
- Added admin Clear All button (two-step confirm) to wipe bad seed data
- Built `scripts/scrape-irishhills.js`: scrapes all 14 Irish Hills Chamber categories, parses names/phones/addresses, infers area from address, posts 241 businesses in a single request to avoid Blob race conditions
- Fixed scraper parser (names in `<a href="/list/member/...">` not `<h5>`), HTML entity decode, phone alignment (Chamber phone is NOT a tel: link)
- Built full referral/affiliate attribution system:
  - `RefCapture` component in App.jsx captures `?ref=` param on any route into `sessionStorage.outreach_ref`
  - All 5 checkout flows (Layout.jsx, BetaBusinessPage, HomePage, ActivateBusinessPage, FeaturedPage) pass `referredBy` from sessionStorage
  - `create-checkout.js` stores `referredBy` in Stripe metadata for both subscription and one-time modes
  - `outreach.js` batch + single create both persist `referredBy` field on business records
  - `set_referral` PATCH action (admin) to manually assign/fix referral codes
  - BusinessDetail panel shows referral code with inline edit for admin
  - AdminStats Referral Credits ledger: groups paid listings by ref code, shows $25 x count = credit per code
  - Holly's link: `manitoubeachmichigan.com?ref=holly`
- Ran /fewer-permission-prompts: added 4 patterns to `.claude/settings.json`
- Fixed accidental `.env.vercel-preview` staging (had real API keys) — git reset, added to .gitignore, recommitted

**What's live / deployed:**
- All above pushed to main and deployed on Vercel
- 241 Irish Hills Chamber businesses imported to outreach CRM
- Referral system active in production

**Next up:**
- Phase 2 affiliate portal (explicit user request, deferred): self-serve portal for $49/mo tier customers only — they get their own referral link, can see credit balance + referral history
- Affiliate portal should only be accessible to customers with an active `premium` Stripe subscription

**Notes for other environments:**
- The `addRandomSuffix: true` Blob pattern is now the standard for ALL blob-backed JSON DBs — never use `allowOverwrite: true` on a public blob, CDN will serve stale data
- Outreach CRM PIN auth: lead=Chelsea, connector=Erin, followup=Amy, admin=Daryl (env vars)
- Scraper rerun: `OUTREACH_PIN=xxxx node scripts/scrape-irishhills.js` (add `--dry` to preview)

---

## 2026-05-30 11:47 AEST

## Session: 2026-05-30 AEST
**Environment:** Antigravity IDE
**What was done:**

- COO audit led to focused Sunny Skies dispatcher overhaul
- Identified root cause of rotation bug: old routines sorted by `createdTime ascending` so same clips always fired first
- Built `clip-index.json` in `Sunny-Skies/sunny skies stills/10 sec library/` — 46 clips indexed with mood/subject/category tags, 14 flagged review_needed
- Saved clip library memory file + MEMORY.md pointer
- Created 4 new RemoteTrigger routines (all ENABLED):
  - `trig_014nEu4EaMg2L9M78YhRRgoP` — Quotes 9am ET, sorts by last_posted ASC
  - `trig_01SPThcf6gzLaqZiWvohqaFh` — Midday 12pm ET, sorts by last_posted ASC
  - `trig_01GHbiikKb2FimTsCXPVuEPc` — Evening 6pm ET, sorts by last_posted ASC
  - `trig_011qiFPmvXTmbSoxzDiMUvNN` — Fuel Gauge 9:10am ET, Haiku model, checks all 16 Drive folders, SMS alert when any hits ≤7 days
- Disabled all 3 old/broken routines (trig_01Lrty15t44wKwZDT3DaKthC, trig_011kXD1oFtWQx3CMJ5GMuDnQ, trig_01NnLEi2N4zTE1RJ2nTUmwPG)
- Added `api/fuel-alert.js` and `api/internal-alert.js` to Manitou Beach — SMS endpoints for automation
- Committed, pushed, and deployed MB to Vercel production
- FUEL_ALERT_TOKEN (`fgss2026xpk7`) and ADMIN_PHONE (`+15172605907`) confirmed live in Vercel env

**What's live / deployed:**
- manitoubeachmichigan.com/api/fuel-alert — live, used by fuel gauge routine
- manitoubeachmichigan.com/api/internal-alert — live, general-purpose ops alerts
- All 4 new dispatcher routines active and will fire from tomorrow morning

**Next up:**
- Review 14 flagged clips (Install 1-7, rooftop 1-5, shingles 1) — watch them, update clip-index.json entries
- Fix filename typos: `flu up 1.mov` → `fly up 1.mov`, `timplapse build.mov` → `timelapse build.mov`
- Upload local 10 sec library to Google Drive `dyoung@callsunnyskies.com` under `_dispatcher/video-bg-library/` (currently local only)
- Clean up TEST trigger `trig_01LEkWL8pRFypYuYHnyKQqTU` (disabled but exists)
- MCP redundancy cleanup: 4 Notion MCPs, 2 Vercel MCPs — prune duplicates
- Install missing CLIs: stripe, yt-dlp, pnpm, Playwright

**Notes for other environments:**
- Dispatcher is now on new routines — old ones are OFF. Do not re-enable them.
- Fuel gauge SMS token is `fgss2026xpk7` (stored as FUEL_ALERT_TOKEN in Vercel)
- clip-index.json is local only — needs Google Drive upload before mobile can use it

---

## 2026-06-01 15:12 AEST

## Session: 2026-06-01 (AEST)
**Environment:** Antigravity IDE

**What was done:**
- Audited Sunny Skies repurpose.io dispatcher — found 2 bugs causing total failure since 2026-05-30
- Bug 1: All 3 Claude routines had a 1-char typo in connector UUID (`...29e6b` vs `...39e6b`) — fixed via RemoteTrigger API
- Bug 2: CTA Posted folder ID was `VBlw` (non-existent) instead of `VBlv` — fixed in VPS script
- Rebuilt the dispatcher as a proper VPS Node.js cron job at `/root/SunnySkies/dispatcher.js`
- Set up OAuth2 for `admin@yetigroove.com` (GCP project "My First Project", Desktop app client)
- Isaac added `admin@yetigroove.com` to Sunny Skies Shared Drive as contributor
- Tested successfully: dispatcher ran and copied a Before After video to the Posted folder
- Cron live on Yeti VPS: 9am/12pm/6pm ET, logs to `/root/SunnySkies/cron.log`

**What's live / deployed:**
- VPS cron dispatcher LIVE and tested
- All 7 content types now in rotation including CTA and Dev Education
- Claude routines should be DISABLED by Daryl at claude.ai/code/routines (pending)

**Next up:**
- Confirm Daryl disabled the 3 Claude routines (Quotes/Midday/Evening) to prevent double-posting
- Monitor cron.log over next few days to confirm all content types firing
- Add RESEND_API_KEY to `/root/SunnySkies/.env` for failure email alerts (key is in Vercel)

**Notes for other environments:**
- Dispatcher is now VPS-based, not Claude routines — don't recreate or re-enable Claude routines
- To modify rotation or add content types: edit `/root/SunnySkies/dispatcher.js` on VPS directly
- Shared Drive ID: `0ACHTmBWg_9bqUk9PVA` — admin@yetigroove.com is now a contributor
- MCP Drive connector (UUID ...39e6b) is bound to `dyoung@callsunnyskies.com`, NOT admin@yetigroove.com

---

## 2026-06-02 21:32 AEST

## Session: 2026-06-02 AEST
**Environment:** Antigravity IDE

**What was done:**
- Built `/raffle` page - carnival-themed prize prediction wheel for LLLC Summerfest
- Carnival aesthetic: dark tent background, gold pennant bunting, marquee lights ring around wheel, gold pointer, ticket-style result card
- 11 raffle baskets wired with photos from `public/images/ladies-club/Festival-raffle/`
- Basket photos display in result card (white bg, object-fit contain, 160px)
- Share prediction via Web Share API or clipboard copy
- Added `embed` prop to RafflePage (strips navbar/footer/padding for inline use)
- LadiesClubPage: compact teaser card between festival map and sponsor tiers
- Teaser opens full-screen modal popover rendering RafflePage component directly (not iframe)
- Modal sits below navbar (paddingTop: 72px)
- `/raffle` standalone URL still works for sharing on social/SMS

**What's live / deployed:**
- manitoubeachmichigan.com/raffle - standalone page
- manitoubeachmichigan.com/ladies-club - teaser card + modal at bottom of events section

**Next up:**
- LLLC to share /raffle link on Facebook/socials as Summerfest hype
- Prize wheel sponsor version (vendor deals, QR redemption) - spec at specs/prize-wheel-demo-spec.md - deferred until pitch validation

**Notes for other environments:**
- All 11 basket photos committed to repo under public/images/ladies-club/Festival-raffle/
- RafflePage accepts embed={true} prop OR ?embed=true URL param

---

## 2026-06-05 20:00 AEST

## Session: 2026-06-05 AEST
**Environment:** Antigravity IDE

**What was done:**

- **Stays promo update** — May 10 "founding" expired copy replaced with "Summer Launch - free through July 4" across StaysPage, verify-stay.js, create-checkout.js, verify-food-truck.js, beta-signup.js, ActivateBusinessPage
- **Booking fields for stays** — Added Payment Method, Cancellation Policy, Booking Confirmation to Notion Stays DB + all APIs. Surfaces in ManageStayPage edit form and BookingDrawer before the contact form. Selling copy rewritten: "Your booking. Your rules. Your money."
- **Visitor Wall** (`/visitor-wall`) — Full new page built and live:
  - Notion DB: Visitor Pins (ea2866ffd5cb4742b4ab046de80a6eba, env: NOTION_DB_VISITOR_PINS)
  - api/visitor-pin.js — GET all pins + POST new pin
  - api/instagram-gallery.js — pulls @manitoubeachlife Instagram posts
  - VisitorWallPage.jsx — dark hero, live ticker, Google Maps world view, country→city picker, color picker (12 swatches + custom), native share button
  - Added to Community nav dropdown + routing
  - Padlock arch crossover section + Instagram gallery
  - Bug fix: typo visitor-pins→visitor-pin on GET (pins now persist on refresh)
  - Mobile: zoom 1 for full world view at a glance
  - Copy fixed: "One tap" → "Pick your country and city"
  - Share button: Web Share API (SMS/email/WhatsApp) + clipboard fallback

**What's live / deployed:**
- All above pushed to main → Vercel production
- Argentina pin visible on the map (VPN test from earlier session - it worked)
- Visitor wall organic pins already dropping before any promotion

**What's NOT built yet (planned, not coded):**
- Stays tiered photo upgrade (5 photos Listed, 10 Featured) + photo JSON system
- Availability calendar (owner blocks dates, public calendar strip on listing card)
- Request to Book + Waitlist auto-notify (api/stay-request.js, api/stay-waitlist.js)
- "Mark stay complete + notify guest" button in ManageStayPage (post-stay SMS: pin invite + Google review ask)
- Natural width photo strip on listing cards (user chose this, got sidetracked)
- Terms & Privacy update for marketplace/directory disclaimer

**Next up:**
- Daryl's son (Melbourne) + daughter (Utah) to seed first two legit pins
- Social launch: padlock arch photo + "we built the digital version" post to @manitoubeachlife
- Build the "Mark stay complete" button in ManageStayPage (small, high value)
- Then: stays availability calendar + request to book flow

**Notes for other environments:**
- NOTION_DB_VISITOR_PINS=ea2866ffd5cb4742b4ab046de80a6eba is in .env and Vercel production
- Visitor wall is at /visitor-wall, in Community nav dropdown
- Legal decision made: Yetickets should NOT process vacation rental payments (accommodation tax liability, fair housing exposure). MB stays is discovery + request only - no money flows through platform
- Summer Launch promo deadline is July 4 - all beta/founding copy updated to reflect this