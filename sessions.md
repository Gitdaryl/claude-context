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

---

## 2026-06-06 13:50 AEST

## Session: 2026-06-06 AEST
**Environment:** Antigravity IDE

**What was done:**
- Stays card UX overhaul: collapsed to 185px default, gradient fade, always-visible bottom bar with Show more + Check Availability buttons
- GuestCalendar moved full-width outside the content column (was nested in left side of flex row — looked terrible)
- Per-card photo lightbox working; "📷 X photos" label under main photo clicks to open lightbox
- Zillow-style map detail panel: clicking a card in map view replaces the right panel with full detail view — photo grid (1 large + 2x2), all property info, inline calendar, "Back to search"
- Mobile audit: fixed map card using wrong image field (logo vs photos[0]), fixed MapDetailPanel scroll (flex:1 + minHeight:0), bottom action bar wraps on narrow screens
- Google Calendar tip added to iCal field in both listing form and ManageStay
- Free tier listings now have Contact Owner → (email or phone) in bottom bar — was a dead end before
- MapDetailPanel falls back to Call Owner → if no email
- iCal failure alerting: sync-ical.js now SMS-alerts PLATFORM_ADMIN_PHONE when any feed fails (add this env var in Vercel)
- Three-POV audit done (owner / guest / admin) — key findings documented in conversation
- Owner listing form: terms checkbox required before submit (YetiGroove LLC liability disclaimer)
- Guest inquiry form: plain-language platform disclaimer shown before send button

**What's live / deployed:**
- All changes pushed to main, Vercel auto-deploys
- manitoubeachmichigan.com/stays reflects all changes

**Next up:**
- Add PLATFORM_ADMIN_PHONE env var in Vercel so iCal failure alerts actually fire
- Post-beta (after July 4): Stripe payment path needed for paid tier listings — currently stays in "New" status after verification, requires manual Notion promotion
- Guest messaging thread (deferred v2) — post-inquiry handoff is SMS-only, no in-app continuity
- Admin dashboard (deferred) — approvals, revenue, active listings view

**Notes for other environments:**
- Stays feature is functionally complete for beta: owner signup, verification, manage, iCal sync, guest calendar, inquiry/waitlist, terms all working
- No money through platform — messaging and legal disclaimers now explicit in both owner and guest flows
- Date range blocking in ManageStay already worked (2-click calendar) — audit initially flagged it as missing but it was built
- iCal is optional; Google Calendar is the free option for owners not on Airbnb/VRBO

---

## 2026-06-06 14:13 AEST

## Session: 2026-06-06 AEST
**Environment:** Antigravity IDE

**What was done:**
- Built lakeaccess.html (`social.yetigroove.com/lakeaccess`) - co-branded Lake Access x Yeti Groove partner page with pre-applied discounted pricing ($100/$130/$200 vs standard $150/$180/$250), strikethrough pricing showing the deal, no coupon code field
- Cleaned up social.html (`social.yetigroove.com/social`) as the public-facing standard-rate page, removed Lake Access branding
- Added SMS order alerts to Daryl's phone (5172605907) via Twilio on every order submission
- Rotated exposed Twilio auth token via secondary token promotion flow, updated both MB and yeti-groove projects
- Added filming disclaimer copy to both pages
- Removed inaccurate "30-second" duration promise from copy on both pages
- Full audit (mobile, comms, customer/Dennis/admin POV) - found and fixed:
  - No customer confirmation email being sent (now fixed - customer gets warm branded receipt)
  - Admin email FROM was hardcoded "Lake Access Orders" for all orders (now "Yeti Groove Orders")
  - Source/page not shown in admin email body or subject (now shows [Lake Access Media] or [Social])
  - Video card labels cramped on 2-col mobile (now stacks vertically)
  - social.html meta description still said "Lake Access Media advertiser exclusive" (fixed)

**What's live / deployed:**
- `social.yetigroove.com/lakeaccess` - Lake Access partner page, partner pricing, no coupon, co-branded
- `social.yetigroove.com/social` - Public page, standard pricing, Yeti Groove branded
- Both pages fire SMS to Daryl + email to Daryl + customer confirmation email on submit
- Twilio token rotated and live in both MB and yeti-groove projects

**Next up:**
- Vercel "Needs Attention" env var audit across MB (17+ flagged) and yeti-groove - deferred from this session
  - MB flagged: RESEND_API_KEY, NOTION_TOKEN_*, STRIPE_*, FB_PAGE_ACCESS_TOKEN, ANTHROPIC_API_KEY, etc.
  - TWILIO_AUTH_TOKEN already fixed
- Google Drive upload folder is shared - consider creating a subfolder per customer to keep media organised as volume grows
- At ~10+ Lake Access orders consider a simple Notion order tracking DB

**Notes for other environments:**
- The lakeaccess page URL is the access control - Dennis gives it to his advertisers, no coupon code needed
- Revision policy: 1 round included, $50/round additional, no exceptions - this is enforced in copy only (no technical gate)
- Invoice is sent manually on delivery - no automated payment flow yet

---

## 2026-06-08 12:28 AEST

## Session: 2026-06-08 AEST
**Environment:** Antigravity IDE

**What was done:**
- Added global pause switch to Sunny Skies VPS dispatcher (tracking.json paused flag, pause.sh + resume.sh scripts)
- Built standalone Dispatcher Admin UI — dispatcher-admin-six.vercel.app (React+Vite+Tailwind+dnd-kit)
- All 3 time slots (9am, 12pm, 6pm) fully drag-and-drop configurable — Quotes is no longer hardcoded to 9am
- Per content type on/off toggles
- VPS config server running on port 3847 via PM2, boot-persistent (pm2 startup + pm2 save done)
- Vercel API proxies to VPS config server — no Vercel KV/storage needed
- VPS dispatcher updated to read remote config, respect disabled types, use schedule-driven slot assignment, fall back to hardcoded defaults if config server unreachable
- PM2 installed on VPS, ss-config process saved for reboot persistence

**What's live / deployed:**
- dispatcher-admin-six.vercel.app — Sunny Skies control panel
- VPS config server: 143.198.171.9:3847 (PM2 managed)
- dispatcher.js on VPS fully updated

**Next up:**
- Adding new content type (e.g. Testimonials): needs Google Drive source folder + Posted subfolder, repurpose.io workflow, add to CONTENT_TYPES array in dispatcher.js, add to TYPE_META in admin UI src/lib/typeMeta.js and defaults.js

**Notes for other environments:**
- Dispatcher admin URL: dispatcher-admin-six.vercel.app
- To pause dispatcher remotely: tell Claude "pause Sunny Skies" (runs /root/SunnySkies/pause.sh via VPS MCP)

---

## 2026-06-09 17:16 AEST

## Session: 2026-06-09 (AEST)
**Environment:** Antigravity IDE

**What was done:**
- Strategic discussion on AGI prep + competitive moat for the MB "fishbowl" expansion. Key reframe: the moat is hyperlocal network density + merchant relationships, NOT software features. A funded competitor can clone the code; they can't clone the local trust/relationships. Defense = speed to density per territory + templatization + hoarding operating data, not "staying ahead on tech."
- Built the **Weekly Tech Radar agent** (Daryl's "capability monitor" idea, scoped down from AGI-prediction to fast frontier adoption).

**What's live / deployed:**
- Pushed to Gitdaryl/Manitou-Beach main (commit e6db693):
  - `scripts/tech-radar.js` — scans AI releases (HN Algolia), dev tooling + MCP/skills (GitHub Search API), video/creative AI, optional competitor/clone alerts (Brave). Haiku ranks each item vs Daryl's stack/projects/moat → do/watch/ignore. Emails ranked digest via Resend + creates Command Center tasks for "do" items only. Every external dep degrades gracefully.
  - `.github/workflows/weekly-tech-radar.yml` — runs Mon 8am ET (13:00 UTC) + manual workflow_dispatch with preview flag.
- Runs out of the box for EMAIL using existing MB secrets (ANTHROPIC_API_KEY, RESEND_API_KEY).
- Caught + fixed a real bug pre-ship: Command Center Status is a select, not Notion status type.

**Next up (Daryl action — added to Command Center, Status=Today):**
- Add GitHub secret `NOTION_COMMAND_CENTER_TOKEN` (Yeti-workspace Notion integration token shared to the Command Center board) to enable auto-task-creation. Without it, radar still emails fine.
- Optional secrets: `BRAVE_API_KEY` (enables clone/competitor alerts), `RADAR_FROM`/`RADAR_TO` overrides.
- Test now: Actions → Weekly Tech Radar → Run workflow → preview=true.

**Notes for other environments:**
- The radar is portfolio-wide tooling that happens to live in the MB repo (MB has the mature GitHub Actions + Haiku + Resend infra). Conceptually it belongs to Yeti Groove Media.
- Tune what it watches by editing PORTFOLIO_CONTEXT + the query arrays in tech-radar.js.

---

## 2026-06-10 14:55 AEST

## Session: 2026-06-10 AEST
**Environment:** Antigravity IDE

**What was done:**
- Built MB event "change of plans" lifecycle system (cancel / postpone / pause + attendee ribbon + organizer self-serve + outdoor change-risk tiering)
- Data layer: api/events.js (reads Lifecycle/Outdoors/Change Note, derives changeRisk, filters Paused from public feed), api/submit-event.js (outdoors checkbox write + resilient retry), api/event-edit.js (organizer sets lifecycle/changeNote via existing magic-link token + retry)
- UI: src/components/LifecycleRibbon.jsx (new shared), ribbon rendered on HappeningPage list rows + weekly recurring cards + EventDetailPage hero; EventEditPage "Change of plans?" control (Running/Postponed/Cancelled + note); SubmitEventPage "held outdoors" checkbox
- All code is backward-compatible: defaults to 'Active' if Notion fields absent, so deploying is safe even before schema fields exist

**What's live / deployed:**
- NOTHING deployed yet. Code built clean (npm run build x2) but NOT committed/pushed.

**Next up (BLOCKING GATE):**
- Add 3 fields to Notion "Manitou Beach - Event Submissions" data source (id 30d8c729-eb59-80bf-9a15-000b72e7ef4d): Lifecycle (select: Active/Paused/Postponed/Cancelled), Outdoors (checkbox), Change Note (rich_text). Auto-mode classifier blocked the automated schema add — needs Daryl's explicit OK or manual add. Feature is inert until these exist.
- Then commit + push + deploy.
- Widow support group recurring event: pause it (set Lifecycle=Paused in Notion, or keep current Status=Review which already hides it). It's a sensitive event — silent pause, NO public ribbon. Check back with organizer in ~3 weeks.

**Phase 2 (deliberately NOT built):**
- Weather-triggered organizer check-in for High change-risk (outdoor) events using existing api/concierge-weather.js. changeRisk is already computed/plumbed for this.
- Did NOT build a recurring "confirm your event?" nag (spammy for weekly events).

**Notes for other environments:**
- changeRisk tiers: outdoors=high; Markets&Vendors/Sports&Outdoors/Boating&Water=high; Live Music/Arts&Culture/Community/Food&Social=low; else medium.

---

## 2026-06-11 13:32 AEST

## Session: 2026-06-11 (AEST)
**Environment:** Antigravity IDE

**What was done:**
- Analyzed HeyGen's new credit-based pricing (replaces old "unlimited"). Key: Avatar V/IV burn 20 credits/min; standard avatars ~1/min. API rule ~$3/min for Avatar V ($0.05/sec).
- REVIVED YetiClone. The project was shelved 2026-04-13 because Avatar V had no API and v2 Avatar IV gave floating-teeth output. Avatar V API shipped May 2026 - re-validated live with Daryl's account: 10/10 generations clean, 0 failures, frame-checked, teeth-gate FIXED. Both original blockers are dead.
- Migrated generate endpoint v2 -> v3 (engine.type avatar_v, orientation->aspect_ratio). Commit 36e4221.
- Built the shared backend + missing product pieces (commit 45f0c33): Vercel Blob JSON DB (replaces localStorage so client + admin share state), "your video is ready" delivery email (was promised, never built), hybrid QA (new clients gated for first N videos then auto-flip to self-serve), regen loop (backs both client "Request changes" and admin "Flag for Edit"), HeyGen completion webhook. Rewired AdminQueue/VideoLibrary/CreateVideo/Dashboard off localStorage. Build passes.
- UX direction set: all 9:16 vertical, client controls = 3 only (change outfit / regenerate / approve), consolidate the two video-creation doors into one wizard, separate client vs admin nav. Positioning = sell ACCOUNTABILITY not "I hand-make each video" (human-in-the-loop QA is real via gating, not theater).
- Billing: insurance client (Sam Quisenberry, State Farm) is 2 months in, NO invoices sent. Drafted catch-up invoices YC-1001 ($320 May) + YC-1002 ($320 June) = $640, ready to paste into Novo. 10 videos delivered, first 2 free (onboarding bonus), June subtitles comped as a trial - both shown as visible $0 gift lines.
- Locked in "First 2 Free" acquisition SOP (memory: feedback_first_two_free_sop) - per client AND per agent, framed as a bonus never "free".

**What's live / deployed:**
- Code pushed to github Gitdaryl/YetiClone main (36e4221, 45f0c33). Build passes.
- NOT deployed-functional yet: portal is INERT until Vercel env is set (esp. a Blob store for BLOB_READ_WRITE_TOKEN). Nothing runs without it.

**Next up (added to Command Center):**
1. GO LIVE - create Vercel Blob store + set env (HEYGEN_API_KEY validated today, voice/avatar defaults, RESEND_API_KEY). Unlocks self-serve AND auto-billing. Claude can do it with go-ahead. [Status: Today]
2. Consolidate client UI into single wizard (Sonnet).
3. Org/account layer before the 3 other agents onboard (month 3 = now-ish) - one consolidated invoice to the owner.
4. Monthly billing assistant (per-video auto-reminder reading the delivery log) - depends on go-live.
5. Subtitle engagement result from marketing agent -> if positive, bump Hyperframes caption automation up the queue.

**Notes for other environments:**
- ACTION FOR DARYL: send Novo invoices YC-1001 + YC-1002 ($640 total) - 2 months of uncollected revenue.
- HeyGen API key was pasted in plaintext in the IDE session - consider rotating after, Daryl's call.
- "First 2 free" is now standard policy across Yeti Groove Media client acquisition, not just YetiClone.
- Daryl flagged ADHD/overload - lots of projects, forgets what needs attention. The Command Center task list is the externalized memory; keep adding tasks proactively so nothing relies on him remembering.

---

## 2026-06-13 17:43 AEST

## Session: 2026-06-13 AEST
**Environment:** Antigravity IDE

**What was done:**

- Built full Spin to Win vendor onboarding system for Manitou Beach
  - New `/wheel-signup` page with color picker (presets + native color wheel), self-selected 4-digit PIN, logo drag-drop upload
  - New `api/prize-wheel/vendor-signup.js` - creates Notion record, emails vendor, emails + SMSes Daryl with Notion deep link for one-tap approval
  - New `api/prize-wheel/sponsors.js` updated - wheel stays paused until 6 active vendors
  - New `api/prize-wheel/launch-wheel.js` - admin button that resets all trial dates to launch day and notifies all vendors
  - New `api/prize-wheel/sponsors-admin.js` - admin vendor list endpoint
  - Yeti Admin "Wheel" tab added - shows live vendor list, trial status, Launch button
  - Notion DB `NOTION_DB_PRIZE_WHEEL_SPONSORS` schema updated with 6 new columns (Contact Name, Email, Phone, Trial Start, Trial End, Plan Type)

- Built "This Week on Manitou Beach" activity feed in Yeti Desk dashboard
  - New `api/activity-summary.js` (admin-only) - queries 7-day window across Events, Businesses, Food Trucks, Truck Loves, Wheel Vendors, Wheel Claims DBs
  - Dashboard tab now shows activity section: events listed, businesses joined, food trucks signed up, pin activity per truck, wheel vendor apps, spin/redemption stats
  - Live refresh button included

- Updated DARYL.md at workspace root with full Spin to Win documentation
- Created memory entry `reference_daryl_md.md` so DARYL.md is never duplicated

**What's live / deployed:**
- All code pushed to Gitdaryl/Manitou-Beach main branch
- Vercel auto-deploy triggered
- Wheel vendor signup: manitoubeachmichigan.com/wheel-signup
- Yeti Admin wheel tab: manitoubeachmichigan.com/yeti-admin -> Wheel tab
- Activity feed visible in Dashboard tab of Yeti Admin

**Next up:**
- Wheel needs 6 active vendors to go live - start recruiting!
- Daryl approves vendors in Notion (Active = true) then hits Launch Wheel button in admin
- Google review prompt on redemption success screen (not built yet)
- Vendor self-edit portal (deferred)
- Trial-ending performance email at day ~57 (deferred)
- Automated trial expiry cron (deferred)

**Notes for other environments:**
- Wheel signup URL to share with potential vendors: manitoubeachmichigan.com/wheel-signup
- Daryl gets instant SMS when a vendor applies with a Notion deep link - tap it to approve
- DARYL.md is at /Users/darylyoung/Documents/Claude Code/DARYL.md - always append, never replace
- Activity summary queries Notion's built-in `past_week` timestamp filter - no date math needed in queries

---

## 2026-06-20 19:19 AEST

## Session: 2026-06-20 (AEST)
**Environment:** Antigravity IDE

**What was done:**
- Fixed Manitou Beach bug: event organizer photos were not showing as the OG/link-preview image when event URLs were shared (Facebook, iMessage, Nextdoor).
- Root cause: MB is a client-rendered SPA; social crawlers don't run JS. The Vercel Edge Middleware (middleware.js) injected OG tags for /business/:slug pages but explicitly SKIPPED /events/:id.
- Added handleEventOG() to middleware.js (mirrors existing handleBusinessSchema): fetches /api/event-detail, injects event-specific og:image (Vercel Blob photo), og:title, og:description, twitter:* tags, and Event JSON-LD schema server-side. User text HTML-escaped; falls back to default OG on 404/unapproved/no-photo.
- Confirmed event photos are stored as permanent Vercel Blob URLs (via api/upload-image.js), NOT expiring Notion file URLs, so OG image renders reliably.

**What's live / deployed:**
- Committed to main (commit 9b44df6) and deployed to Vercel production via CLI.
- Verified live: curl as facebookexternalhit on the example event now returns the organizer's Blob photo in og:image (was returning default /images/og-image.jpg before).

**Next up:**
- None required. Fix applies to all future events automatically.

**Notes for other environments:**
- Facebook/iMessage cache previews aggressively. Already-shared links may show the old image until re-scraped. To force refresh: paste URL into Facebook Sharing Debugger (developers.facebook.com/tools/debug) → "Scrape Again". New shares pick up the photo automatically.
- Only one file changed: Manitou-Beach/middleware.js.

---

## 2026-06-21 23:42 AEST

## Session: June 21 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- MB Ladies Club page updated for post-Summerfest 2026 (festival was June 20, day before)
- Added 58-photo Summerfest 2026 gallery above existing gallery (now labeled 2025)
- Optimized new photos 41MB -> 17MB (sips 1500px q72), SEO-renamed DSC*.jpg -> devils-lake-summerfest-2026-NN.jpg + descriptive alt text
- Hero countdown (expired) swapped for "Thank you for an amazing Summerfest 2026" message, CTA now -> #festival-gallery
- Festival promo section reframed to past-tense recap ("Summerfest 2026 Recap"); removed spent raffle-wheel teaser + festival map
- Kept sponsors wall + sponsor registration form fully intact (as requested)
- Caught + unstaged .env.local.tmp (live Anthropic/Beehiiv keys, never committed) and added .env*.tmp to .gitignore
- Saved new memory SOP: feedback_image_seo_naming (rename+optimize photos to SEO slugs before galleries)

**What's live / deployed:**
- Pushed to Manitou-Beach main (be0bac7) -> Vercel auto-deploy. Verify /ladies-club on manitoubeachmichigan.com

**Next up:**
- Optional: rename 2025 gallery files (summerfest-N.jpg) to SEO slugs for consistency (low priority, already deployed/linked)
- Club may send official Summerfest content/instructions later - revisit recap copy then

**Notes for other environments:**
- LLLC page is now in "recap" mode, not promo mode. When 2027 promo starts, re-add countdown + raffle wheel (RaffleWheelTeaser component still defined in LadiesClubPage.jsx, just unrendered).

---

## 2026-06-21 23:57 AEST

## Session: June 21 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- MB Ladies Club page updated for post-Summerfest 2026 (festival was June 20, day before)
- Added 58-photo Summerfest 2026 gallery above existing gallery (now labeled 2025); shared lightbox shows "Summerfest YYYY · n / total"
- Optimized new photos 41MB -> 17MB (sips 1500px q72); SEO-renamed BOTH galleries: devils-lake-summerfest-2026-NN.jpg (58) and devils-lake-summerfest-2025-NN.jpg (22), with descriptive alt text
- Hero expired countdown -> "Thank you for an amazing Summerfest 2026" + CTA to #festival-gallery
- Festival section reframed to past-tense recap ("Summerfest 2026 Recap"); removed spent raffle-wheel teaser + festival map
- Sponsors wall + sponsor registration form left fully intact (as requested)
- SECURITY: caught .env.local.tmp (live Anthropic/Beehiiv/Stripe/Twilio/etc keys, plaintext, Vercel CLI pull). Never committed; added .env*.tmp to .gitignore
- Saved memory SOP feedback_image_seo_naming (rename+optimize photos to SEO slugs before galleries)

**What's live / deployed:**
- Manitou-Beach main: be0bac7 (galleries + recap) and be007df (2025 rename) -> Vercel auto-deploy. Verify /ladies-club on manitoubeachmichigan.com

**Next up:**
- Daryl to ROTATE KEYS (priority: Stripe secret + webhook, Twilio auth token, Resend, Anthropic), then update each in Vercel and mark the Notion task Done
- Reminders set: Command Center task "Rotate exposed API keys" (Status Today/High) + daily cloud routine "Key Rotation Nudge" (trig_012gBquMtxVFbAnyeY9cZfHD) runs 8am ET, drops a 9am ET Google Calendar popup + Notion comment until task marked Done. Disable at claude.ai/code/routines once done.
- Club may send official Summerfest content/instructions later - revisit recap copy then

**Notes for other environments:**
- LLLC page is now "recap" mode, not promo. For 2027 promo, re-add countdown + raffle wheel (RaffleWheelTeaser still defined in LadiesClubPage.jsx, just unrendered).

---

## 2026-06-24 22:53 AEST

## Session: 2026-06-24 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed "events disappeared off the events page" on Manitou Beach (MB = manitoubeachmichigan.com, /root/Manitou-Beach on Yeti VPS).
- Root cause: during a Notion key rotation, the `NOTION_TOKEN_EVENTS` env var in Vercel got **blanked to empty** (variable existed, value gone). The events API sent an empty `Bearer` token → Notion `401` → api/events.js silently caught it and returned `{events:[],recurring:[]}`, so the page looked empty. Events were never lost — Notion still had 128+ events.
- Confirmed via a temporary gated debug endpoint (`?debug=mbdiag2026`) that returned `tokenPresent:false, notionStatus:401`. Debug endpoint was reverted/removed after.
- Yeti re-pasted the Events integration secret into Vercel (All Environments). Redeployed → events restored (API returns 128 events + 3 recurring, verified live).
- Hardened api/events.js + src/pages/HappeningPage.jsx so this can't fail silently again (commit 17f2391):
  - Pre-flight guard: missing NOTION_TOKEN_EVENTS/DB → fail fast + SMS alert to ADMIN_PHONE.
  - Notion auth/query failures now return HTTP 503 `{error:'events_unavailable'}` with `Cache-Control: no-store` (never cached, monitorable) instead of silent empty 200.
  - 30-min SMS alert cooldown to avoid storms.
  - Frontend shows a clear "can't load events right now / Refresh" state instead of the misleading "quiet week / no events" empty state.
  - Verified with local `vite build` (BUILD OK) before pushing.

**What's live / deployed:**
- Pushed to GitHub Gitdaryl/Manitou-Beach main → Vercel auto-deploy. Commits: redeploy for token (7c19062), diag + revert (d637ce6/a993d2e), hardening (17f2391).
- Events page is functional again.

**Next up / open items:**
- Verify `ADMIN_PHONE` is set in Vercel env — the new SMS alert only fires if it's present (it's NOT in .env.example). If unset, add it so future outages actually page Yeti.
- Optional: the same silent-empty-on-Notion-failure pattern exists in other NOTION_TOKEN_EVENTS endpoints (event-detail, hero, promotions, ~44 total) and the other token feeds (business, dispatch, pois, page-sponsors). Consider extracting a shared Notion helper that alerts/503s consistently.
- If other keys were rotated in the same session: NOTION_TOKEN_BUSINESS and NOTION_TOKEN_HERO confirmed working; double-check NOTION_TOKEN_DISPATCH / NOTION_TOKEN_POIS / NOTION_TOKEN_PAGE_SPONSORS.

**Notes for other environments:**
- Key lesson: a rotated/blanked Notion token in Vercel manifests as "data disappeared from the site" with no error. Check the relevant `NOTION_TOKEN_*` env var value first.

---

## 2026-06-24 23:07 AEST

## Session: 2026-06-24 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Fixed "events disappeared off the events page" on Manitou Beach (MB = manitoubeachmichigan.com, /root/Manitou-Beach on Yeti VPS).
- Root cause: a Notion key rotation **blanked the value** of env vars in Vercel (the vars stayed, the secrets were wiped). `NOTION_TOKEN_EVENTS` → empty → api/events.js sent an empty Bearer → Notion 401 → code silently returned `{events:[],recurring:[]}`, so the page looked empty. Same thing had emptied the **home-page business listings** that morning via a blanked `NOTION_TOKEN_BUSINESS` (Yeti re-pasted that one ~3h earlier, so businesses recovered first). Data was never lost.
- Proved it with a temporary gated debug endpoint (`?debug=mbdiag2026`) → `tokenPresent:false, notionStatus:401`. Removed/reverted after.
- Yeti re-pasted the Events secret into Vercel (All Environments). Redeploy → events restored (API returns 128 events + 3 recurring, verified live).

**What's live / deployed (GitHub Gitdaryl/Manitou-Beach main → Vercel auto-deploy):**
- 7c19062 redeploy to pick up token · d637ce6/a993d2e diag + revert · 17f2391 events hardening · c76a80e site-wide Notion alerting.
- Events page + home business listings functional again.
- Hardening shipped so this never fails silently again:
  - api/events.js: pre-flight config guard, 503 `{error:'events_unavailable'}` + `no-store` on Notion failure, SMS alert, and a friendly "can't load events / Refresh" UI instead of the misleading empty state.
  - api/lib/notionGuard.js (NEW): `alertOutage()` = throttled SMS to ADMIN_PHONE, 30-min per-feed cooldown. Wired into every public Notion-backed read feed: businesses (home + slots), hero, promotions, food-trucks, community-pois, dispatch-articles, village-businesses, winery-ratings, winery-wines, page-sponsors, lllc-sponsors. Failure paths also set `Cache-Control: no-store`. Legitimate "no results"/config-fallback returns left untouched.
  - Verified with local `vite build` (BUILD OK) + `node --check` on all 12 files before each push.

**Next up / open items:**
- **Verify `ADMIN_PHONE` is set in Vercel** — the SMS alerts only fire if it's present (it's NOT in .env.example). Without it you still get the on-page error + 503/no-store, just no text. This is the one thing left to make the new alerting actually page Yeti.
- If other keys were rotated in the same session: NOTION_TOKEN_BUSINESS + NOTION_TOKEN_HERO confirmed working; double-check NOTION_TOKEN_DISPATCH / NOTION_TOKEN_POIS / NOTION_TOKEN_PAGE_SPONSORS values aren't blanked.
- Deferred (same pattern applies if wanted): concierge-events/concierge-businesses, stays, dispatch-ads, admin-articles, categories, and the cron/write paths.

**Notes for other environments:**
- Key lesson: a rotated/blanked Notion token in Vercel shows up as "data disappeared from the site" with NO error. Check the relevant `NOTION_TOKEN_*` env var value FIRST. The site now SMS-alerts on these failures instead of going quiet.

---

## 2026-06-25 18:42 AEST

## Session: 2026-06-25 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed NAS (UGREEN NASync / UGOS, "YETIGROOVENAS") disconnecting + hourly slowdown. Root cause: Time Machine was backing up ~950 GB hourly to the NAS over Wi-Fi, which choked the link and dropped the NAS entirely mid-use.
- Discovered the Mac Studio reaches the NAS two ways: LAN port 10.0.0.130 (only over Wi-Fi, jittery 6-80ms) and a DIRECT 10GbE cable at 10.10.10.2 (0.5ms, rock solid). Everything was using the slow Wi-Fi path because the NAS hostname resolves to 10.0.0.130.
- Confirmed NAS direct-link port already has a correct static IP (10.10.10.2 / 255.255.255.0) in UGOS Control Panel > Network > Network connection. No change needed there.
- Killed Time Machine: removed the NAS destination via System Settings > General > Time Machine (minus button). Verified: "No destinations configured", AutoBackup=0, Running=0.
- Re-mounted NAS shares over the fast direct link: personal_folder, Sunny Skies, Production all now mounted from smb://10.10.10.2 (active connection confirmed on en0 10GbE, not Wi-Fi).

**What's live / deployed:**
- Time Machine fully disabled (destination removed).
- NAS file shares running over 10GbE direct cable (10.10.10.2), ~100x lower latency than before.

**Next up:**
- Stale root-owned Time Machine SMB mount (/Volumes/.timemachine/...) still lingering — cosmetic only, clears on reboot or via `sudo umount`.
- Recommend adding the 10.10.10.2 mounts to Login Items so they auto-reconnect after reboot.
- Optional: when connecting to NAS always use smb://10.10.10.2, never the hostname or 10.0.0.130, to stay on the fast wire.

**Notes for other environments:**
- Mac Studio en0 = 10GbE direct cable to NAS (10.10.10.1 <-> 10.10.10.2). en1 = Wi-Fi on home LAN (10.0.0.x, router 10.0.0.1). Use the 10.10.10.2 path for all NAS file access.

---

## 2026-06-26 14:39 AEST

## Session: 2026-06-26 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed the Manitou Beach `community-pois` feed outage (SMS alert "Notion query failed", section blank on site).
- Proved the DB + schema were healthy and readable; isolated the fault to the Notion integration behind `NOTION_TOKEN_POIS` — it had been deleted/revoked (no "Community Pois" bot in the workspace).
- Walked Yeti through the fix: recreate the integration, connect it to the Community POIs DB, paste token into Vercel `NOTION_TOKEN_POIS`, redeploy.
- Verified live: `/api/community-pois` now returns 35 POIs + 3 suppressed. Feed restored.
- Wrote a reusable runbook to the repo: `/root/Manitou-Beach/RUNBOOK-notion-feeds.md` (symptom, diagnose, fix, env-var↔integration↔DB map, duplicate-integration gotcha).

**What's live / deployed:**
- manitoubeachmichigan.com community POIs feed is back up (Vercel redeploy by Yeti).
- New file committed to repo working tree on VPS: `RUNBOOK-notion-feeds.md` (not yet git-committed/pushed).

**Next up:**
- Optional cleanup: one harmless DUPLICATE "Community Pois" integration remains in Notion. Keeper = the one whose Access token matches Vercel `NOTION_TOKEN_POIS`; safe to leave both.
- Consider committing/pushing `RUNBOOK-notion-feeds.md` to the repo.
- Optional: verify the other Notion feeds (events, business, hero, dispatch) tokens aren't at similar risk.

**Notes for other environments:**
- The blank-feed failure pattern (deleted/disconnected Notion integration → token can't auth) is now documented in the repo runbook. Tell: a feed's API endpoint returning its data array WITHOUT the `suppressed`/companion field = it's in the failure branch, not genuinely empty.

---

## 2026-06-28 22:01 AEST

## Session: 2026-06-28 ET
**Environment:** Antigravity IDE

**What was done:**
- Added "Skydive Tecumseh 4th of July Drop-In" event (DLYC, July 4th, 8:00 PM) to two places on the Manitou Beach site:
  1. America 250 page (`src/pages/USA250Page.jsx` → `ACTIVITIES` array) — appears in the July timeline with a 🪂 icon.
  2. Events DB (Notion "Manitou Beach - Event Submissions") — created a Published, Admin-Added page so it shows on the live events/Happening page immediately.

**What's live / deployed:**
- Notion event = live now (events page reads Notion live): https://app.notion.com/p/Skydive-Tecumseh-4th-of-July-Drop-In-38e8c729eb5981789aecc5f01ed77763
- America 250 page change committed (8745b83) and pushed to `main` → Vercel auto-deploy in progress.

**Next up:**
- Confirm Vercel deploy succeeded and the new activity card renders on /america-250.

**Notes for other environments:**
- Event details from flyer: July 4th 2026, jump time 8:00 PM, landing in front of Devils Lake Yacht Club, watch from boat/shore, jumpers buzz the lake first, weather permitting. Cost set to Free.