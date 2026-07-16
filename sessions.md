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

---

## 2026-07-02 10:54 AEST

## Session: 2026-07-02 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed recurring "can't drag-and-drop files between Finder windows" issue on the 48GB Mac (macOS Tahoe 26.5.1).
- Root cause: memory/swap thrash, NOT a Finder bug. Firefox had 61 tabs / 67 processes using ~23 GB; Chrome (2.8 GB) and Safari also running. Swap was maxed (~22 GB of 23.5 GB), WindowServer pegged ~40% CPU → dropped drag events. Reboots only held a few hours because Firefox restored all 61 tabs on launch.
- No third-party input tools (BetterTouchTool/Karabiner/Magnet) involved; three-finger-drag off; no Finder/WindowServer crashes.
- Killed runaway Firefox tab, relaunched Finder + Dock, quit Safari/Chrome/Firefox, cleared Firefox sessionstore files so the 61 tabs don't auto-restore.
- Result: free RAM 39% → 70%, swap draining, load 6.5 → 5.3.

**What's live / deployed:**
- Nothing deployed. Local machine cleanup only.

**Next up:**
- Confirm drag-and-drop works reliably going forward (should no longer need frequent reboots).
- Suggested: install Auto Tab Discard in Firefox, avoid running 3 browsers at once, keep tab count down.

**Notes for other environments:**
- User tends to accumulate 60+ Firefox tabs — this is the recurring cause of the drag-drop / slowness symptom on this Mac. Saved to auto-memory as mac-swap-thrash-dragdrop.

---

## 2026-07-02 12:55 AEST

## Session: July 2, 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Researched current (2026) roofing/home-services ad creative trends (Meta focus).
- Confirmed Isaac's thesis with data: native / UGC-style creative beats polished + heavily-branded on CPL (20-50% lower CPC) and engagement. Before/after is the #1 static format; raw short-form before/after video is the category's top performer (reported ~9x vs polished).
- Key caveat surfaced: engagement != leads. Winning structure = native-looking creative + hard offer (free inspection / financing / storm check) + lead form + fast follow-up (respond <5 min, 40% of leads go to first responder).
- Scored Yeti's 5 existing Sunny Skies statics: real assets are strong, but all are "posters" (headline chrome + logo lockups + feature grids) which triggers ad-blindness. Samples #1/#2 (before/after drone) already contain the best asset in the category, just over-packaged. #3 (AI sunset hero) = cut for lead gen. #4/#5 = rework, strip the poster wrapper.
- Generated 4 native-style REFERENCE images via Higgsfield (nano_banana_pro, 4:5): before/after split, storm-damage close-up hook, candid crew-in-action, selfie UGC reveal. Framed as mood-board / shot targets, NOT final ads (real photos beat AI).

**What's live / deployed:**
- Nothing deployed. 4 reference images saved in Higgsfield private workspace + local scratchpad. ~2765 credits remaining.

**Next up (offered to Yeti):**
- Produce stripped-down native variants of his real #1/#2 before/afters.
- Write free-inspection lead-form copy + form questions.
- One-page crew shot-list he can text to the guys.
- Recommend: capture real before/after + 20s raw video on every job; set up Michigan storm geo-audience (summer storm season is live now).

**Notes for other environments:**
- Client/brand: Sunny Skies = roofing / siding / windows / gutters, Michigan. Phone 734.807.4304, callsunnyskies.com. Isaac runs paid ads and is testing static creative (getting some leads).
- Strategy in one line: strip branding chrome, lead with free-inspection offer, native iPhone look, 2-4 fresh concepts/week (fatigue window shrank to 2-3 weeks).

---

## 2026-07-02 19:07 AEST

## Session: 2026-07-02 ET
**Environment:** Antigravity IDE

**What was done:**
- Built and QA'd the Betsy before/after WIPE video (9:16, 1080x1920, 4.4s, loops as a Reel). Faceless, brand band locked to bottom.
- Consolidated every finished deliverable out of the volatile /tmp scratchpad into a permanent folder: ~/Desktop/sunny-skies/ (was about to be lost on reboot).
- Wrote ad-copy.txt (paste-ready Meta hook/headline/description/button for all 3 statics + the video) and a plain-English README.txt.
- Clarified the Higgsfield confusion: Higgsfield only holds the raw AI ingredients; the finished ads/video/cards are built on the Mac and are NOT in Higgsfield.

**What's live / deployed:**
- Nothing boosted yet. All assets are local, staged for Isaac to upload. No deploys.

**Where things are:**
- ~/Desktop/sunny-skies/01-upload-these/  → 3 statics + betsy wipe mp4 + ad-copy.txt (the only files that go into Ads Manager)
- ~/Desktop/sunny-skies/02-previews/       → mockups, reference only
- ~/Desktop/sunny-skies/03-strategy-cards/ → 5 teaching cards (operating model, crew safety, 4 shots, aspect ratio, stack vs side-by-side)

**Next up:**
- Isaac: upload static-1/2/3 + wipe to Meta, paste copy from ad-copy.txt.
- Next drone shoot: hover the SAME spot + altitude for the before AND after pass so the wipe becomes a true same-frame reveal (current one shifts angle between shots). Drop a pin / note altitude on the before flight.
- Offered, not yet taken: a 4:5 in-feed version of the wipe; 5-10 more ready-to-paste ad-copy sets.

**Notes for other environments:**
- CREW SAFETY is a hard rule now (saved to memory): Sunny Skies crew are undocumented; NEVER put an identifiable crew face in any paid/boosted/geo-targeted ad. Faceless only (hands, from-behind, POV, drone, the roof). It also performs better, so it costs nothing.
- The operating model: crew captures (commodity) / Yeti produces the ads (the skill) / documented template = the moat. Prove on Sunny Skies, document, then replicate for other companies.

---

## 2026-07-04 11:48 AEST

## Session: 2026-07-04 ET
**Environment:** Antigravity IDE

**What was done:**
- Traced the "missing" Lake Access Media order (Dennis Babjack, for The Rivers Edge Event Center / Ryan Kinsey). Found there is NO orders database: the form at yetigroove.com/social (repo Gitdaryl/Yeti-Groove, on Vercel, not the VPS) POSTs to /api/social-submit, which only emails daryl@yetigroove.com (Resend) + texts 517-260-5907 (Twilio). The order lives only in that inbox + phone. Photos come as a Drive LINK pasted into "Media Notes".
- Confirmed both of Dennis's bug reports: (1) shared Drive folder is share-set to Viewer (anyone:reader) so uploads are blocked; (2) the "3 ways to tell your story" cards were decorative and didn't map to the 9 selectable example styles.
- Fixed both bugs in social.html + lakeaccess.html: 3 cards are now clickable filters mapped to the 9 styles (photos/mix/promo), paste-a-link is now the primary media path, and the order SMS now names business + style + price.
- Opened PR #1: https://github.com/Gitdaryl/Yeti-Groove/pull/1

**What's live / deployed:**
- Nothing merged yet. PR #1 is open on branch fix/social-order-form; Vercel should build a preview.

**Next up (needs Yeti, outside code):**
- Merge PR #1 after eyeballing the Vercel preview.
- Set the Drive folder (1wApVLL50JpWHpRT7N-4jX7YEzydFk4Zc) link access to Editor if you want the direct-upload button to work.
- Confirm TWILIO_ACCOUNT_SID / TWILIO_AUTH_TOKEN / TWILIO_PHONE env vars exist in the Vercel project, or SMS stays silently off.
- Reconnect the Gmail connector (it's expired) to pull Dennis's actual order email + Ryan Kinsey's follow-up.
- Review the style->bucket mapping in the PR; swap any styles between the 3 buckets if the taxonomy is off (one-line data-group edits).

**Notes for other environments:**
- Lake Access Media = video production by Yeti Groove Media; two intake pages: /social and /lakeaccess (partner-priced). Same backend, same 9 styles.

---

## 2026-07-04 14:02 AEST


## Session: 2026-07-04 ET
**Environment:** Antigravity IDE
**What was done:**
- Added 59th 2026 Summerfest photo (devils-lake-summerfest-2026-59.jpg) to Manitou Beach Ladies Club gallery
- Bumped GALLERY_2026 count 58 -> 59 in src/pages/LadiesClubPage.jsx (gallery is a hardcoded Array.from count, NOT a folder scan)
- Local Documents/Claude Code copy was stale (Jun 21); rebased onto origin/main (16 commits ahead) cleanly, no conflicts
- Build passed, committed, pushed to main (5f4b7fa)

**What's live / deployed:**
- Pushed to Gitdaryl/Manitou-Beach main -> Vercel auto-deploy to manitoubeachmichigan.com

**Next up:**
- Nothing pending. Photo tile should appear after Vercel build completes.

**Notes for other environments:**
- The 2026 Summerfest gallery is a HARDCODED count: `Array.from({ length: N })` at LadiesClubPage.jsx:768. Dropping a new photo in public/images/ladies-club/summerfest2026/ does NOT auto-display it - you must bump N and push.
- Yeti has 3+ local copies of Manitou-Beach (~/Documents/Claude Code/, ~/Desktop/, ~/Downloads/). Only ~/Documents/Claude Code/Manitou-Beach is a real git repo on main. Desktop/Downloads are not git repos - clutter, safe to delete.

---

## 2026-07-04 14:08 AEST

## Session: 2026-07-04 ET
**Environment:** Antigravity IDE

**What was done:**
- Solved the "missing" Lake Access Media order (Dennis Babjack / The Rivers Edge Event Center / Ryan Kinsey). Root cause: the form at yetigroove.com/social (repo Gitdaryl/Yeti-Groove, Vercel project prj_8AvyU7h1hhitvsP5A17ryzqKfR9N under scope daryls-projects-5d48a4f8) has NO order persistence. /api/social-submit only emails daryl@yetigroove.com (Resend) + texts 517-260-5907 (Twilio). Almost certainly the Vercel env vars (RESEND_API_KEY, TWILIO_*) were never set, so delivery failed silently and the order left no trace.
- Confirmed both Dennis bug reports: shared Drive folder (1wApVLL50Jp...) is Viewer-only so uploads fail; the "3 ways to tell your story" cards were decorative and didn't map to the 9 selectable styles.
- PR #1 (branch fix/social-order-form) — 3 commits:
  1. Wired the 3 story cards to filter the 9 example styles; made paste-a-link the primary media path; SMS now names business+style+price.
  2. (same) applied to both social.html and lakeaccess.html.
  3. Robustness: persist-before-notify order logging ([ORDER] JSON) + new /api/health self-check endpoint (reports resend/twilio/notion booleans, 503 if RESEND unset).
- Endorsed build standard saved to memory: persist-before-notify + /api/health on every intake endpoint.

**What's live / deployed:**
- Nothing merged. PR #1 open: https://github.com/Gitdaryl/Yeti-Groove/pull/1 (Vercel builds a preview per push).

**Access limits hit (need Yeti to clear):**
- Gmail connector token EXPIRED - reconnect to let me search the inbox.
- Vercel connector is authed to an empty "yetigroove" team; the real project sits under personal scope daryls-projects-5d48a4f8. I can read project metadata but NOT runtime logs or env vars (403). Re-auth the connector to that scope to unblock log/env reads.

**Next up (needs Yeti):**
- Merge PR #1 after checking the Vercel preview.
- Set env vars in Vercel yeti-groove project: RESEND_API_KEY, TWILIO_ACCOUNT_SID, TWILIO_AUTH_TOKEN, TWILIO_PHONE.
- After deploy, ping me: I'll fetch yeti-groove.vercel.app/api/health (bypasses the Cloudflare block on the apex) and confirm the pipeline is green.
- Set Drive folder link access to Editor if you want the direct-upload button to work.
- Pick one monitored inbox (daryl@ vs admin@ mismatch).
- Have Dennis resubmit once env vars are set (his Drive link + script are not lost).

**Notes for other environments:**
- Lake Access Media = video production by Yeti Groove; two intake pages /social and /lakeaccess share one backend and the 9 styles.
- New build standard applies to ALL future projects: persist before notify, ship /api/health, one notification identity.

---

## 2026-07-04 14:28 AEST


## Session addendum: 2026-07-04 ET (gallery polish)
**What was done:**
- Converted Ladies Club Summerfest galleries (2026 + 2025) from fixed 4:3 grid to CSS masonry (columnWidth 240) so portrait photos no longer get cropped. LadiesClubPage.jsx ~line 791.
- FadeIn already spreads ...style, so break-inside:avoid hangs on it directly.
- Build passed, pushed to main (8aa60d4).

**What's live:**
- Vercel auto-deploy from main -> manitoubeachmichigan.com Ladies Club page.

**Notes for other environments:**
- Gallery is now masonry (down-then-across order), not a strict L-to-R grid. If exact photo sequence ever matters, that's the tradeoff.

---

## 2026-07-04 14:42 AEST


## Session addendum: 2026-07-04 ET (WebP optimization)
**What was done:**
- Converted Ladies Club Summerfest galleries to WebP (cwebp). Two sizes: ~600px thumbs in /thumbs/ for the masonry grid, full-size WebP for the lightbox. Originals (.jpg) kept on disk as source.
- Grid load dropped ~23MB -> 3.3MB (~7x). Lightbox 23MB -> ~9MB, one image at a time.
- LadiesClubPage.jsx: GALLERY arrays now .webp; added thumbSrc() helper (/dir/name.webp -> /dir/thumbs/name.webp); grid img uses thumbSrc(src), lightbox uses full.
- Build passed, pushed to main (ec6b20d).

**Open idea (not yet built):**
- Yeti asked about adding a SHARE option inside the lightbox when swiping photos. Good growth lever for festival attendees sharing their own photos. Recommended: Web Share API (native share sheet on mobile, share the image file), deep-link URL per photo (?photo=...) so shared links open that image, copy-link fallback on desktop, optional download button. Awaiting go-ahead + scope.

**Notes for other environments:**
- 2025 folder (summerfest/) had ~31 source jpgs but gallery only shows 22; extra WebP generated for 23-31 are unused/dead (harmless).

---

## 2026-07-04 16:12 AEST


## Session addendum: 2026-07-04 ET (gallery share feature)
**What was done:**
- Added Share button to the Summerfest lightbox in LadiesClubPage.jsx (LadiesClubGallerySection).
- Mobile: navigator.share() with the original .jpg image file + deep link + CTA text. Desktop: copy-link fallback ("Link copied!" toast).
- Deep links: ?photo=YYYY-NN. On mount, opens lightbox to that photo; URL stays in sync while swiping (replaceState). Shared links land on the exact image.
- Share-only per Yeti (no download button - webp download not useful, screenshot covers it). Goal is traffic-driving.
- Build passed, pushed to main (18bcc05).

**Test notes:**
- Web Share sheet only appears on real mobile browser over HTTPS (the live site). Desktop shows copy-link fallback - that's expected.

---

## 2026-07-04 16:39 AEST


## Session addendum: 2026-07-04 ET (reusable galleries + share icon row + per-photo OG)
**What was done:**
- Reusable public event gallery system on Manitou-Beach:
  - src/data/galleries.js (config: slug -> title/folder/prefix/count) + galleryPhotos()/thumbSrc() helpers
  - src/components/PhotoGallery.jsx: exports PhotoGallery (masonry+lightbox+deeplink via useSearchParams) and ShareRow (FB/X/WhatsApp/Email/Copy/native-More icon row)
  - src/pages/GalleryPage.jsx + route /gallery/:slug in App.jsx
  - scripts/optimize-gallery.sh: converts a source dir -> full webp + /thumbs/ webp + resized jpg, numbered by prefix
- Seeded first gallery: /gallery/july-4-2026 (3 DLYC sunset photos from ~/Downloads/Photos). Set count:3 in galleries.js.
- Share icon row added under the photo in BOTH new galleries and the Ladies Club lightbox (Ladies Club refactored to use shared ShareRow; removed its old single Share button + shareCurrent()).
- Per-photo OG previews in middleware.js: handleGalleryOG for /gallery/:slug?photo=N and an inline override for /ladies-club?photo=YYYY-NN. Both set og:image + twitter:image to the specific photo's .jpg. middleware has its own GALLERY_OG mirror of galleries.js (KEEP IN SYNC when adding galleries).
- Build + middleware `node --check` pass. Pushed to main (1d0f064).

**To add more July 4 photos (or a new gallery):**
1. ./scripts/optimize-gallery.sh <source-dir> july-4-2026 manitou-july-4-2026  (numbers continue from existing; for a NEW gallery use a new slug/prefix)
2. Update count (or add entry) in src/data/galleries.js AND the GALLERY_OG mirror in middleware.js
3. Build, commit, push.

**Test after deploy:**
- /gallery/july-4-2026 renders masonry + lightbox + share icons.
- Ladies Club lightbox still opens and now shows the icon row.
- Per-photo preview: paste manitoubeachmichigan.com/ladies-club?photo=2026-05 into FB/iMessage debugger -> should show that photo. (Middleware only runs on live Vercel, not local.)

---

## 2026-07-04 17:01 AEST


## Session addendum: 2026-07-04 ET (device-aware share fix)
**Problem found in testing:** iOS native share of {title,text,url,files} sent only the text (no photo, no link) to Messages — classic iOS Web Share mangling when mixing image file + link + text.
**Fix:** ShareRow (src/components/PhotoGallery.jsx) is now device-aware:
- Mobile (coarse pointer + navigator.share): one "Share" button (native sheet) that shares the BARE URL only -> recipient app renders the per-photo OG card (photo preview + tappable link = traffic). Plus a Copy link button. No more file/text mixing.
- Desktop: explicit icon row (FB/X/WhatsApp/Email/Copy) where web-share links behave.
- Dropped image-file sharing (was unreliable; link-with-OG-card is better for traffic anyway). If Yeti later wants to post the actual image to Instagram, that's a separate feature.
- Build passed, pushed to main (9cca4ee).
**Note:** mb-context skill is STALE — claims App.jsx is a monolith, but repo is split into src/pages/* + src/components/*. Worth updating that skill.

---

## 2026-07-04 17:23 AEST


## Session addendum: 2026-07-04 ET (lightbox swipe gestures)
- Confirmed per-photo OG previews WORK live (curl showed correct og:image; a never-before-shared 2025 photo rendered the real photo card in Messenger). Earlier logo cards = Facebook's per-URL cache from prior scrapes; re-scrape via FB Sharing Debugger or share a fresh photo.
- Added useSwipeNav hook (src/components/PhotoGallery.jsx): swipe L/R = prev/next, swipe down = close. Applied to both PhotoGallery lightbox and Ladies Club lightbox. touchAction:none on container. Taps <45px still fire buttons.
- Build passed, pushed to main (34ac52c).

---

## 2026-07-04 17:35 AEST


## Session addendum: 2026-07-04 ET (lightbox slide animation)
- Added slide-in animation on photo navigation (LightboxKeyframes: lbInNext/lbInPrev). New photo slides in from swipe direction + fade instead of hard cut. dir state tracks direction; img key remounts to retrigger CSS animation. Applied to both PhotoGallery + Ladies Club lightboxes. Build passed, pushed (48143bc).
- NOTE: it's a slide-IN on release, not a finger-follow carousel (image doesn't track the thumb mid-drag). If Yeti wants finger-follow, that's a bigger build.

---

## 2026-07-04 18:01 AEST


## Session addendum: 2026-07-04 ET (finger-follow carousel lightbox)
- Slide-in animation wasn't native enough; built a real finger-follow carousel.
- New shared Lightbox component in src/components/PhotoGallery.jsx: 3-slide window (prev/current/next), track follows finger via translateX(calc(-100vw + dxpx)) during touchmove, snaps to neighbour/back on release (threshold 20% width), swipe down (>90px vertical) closes. Arrows/keyboard animate via same commit(). Neighbours preloaded, body scroll locked, tap-photo keeps open / tap-outside closes.
- CONSOLIDATED: both galleries now use <Lightbox>. Removed Ladies Club's duplicate inline lightbox + the old slide-in (useSwipeNav, LightboxKeyframes, LB_ANIM_* all removed). LadiesClubPage imports only { Lightbox } now.
- Note: separate GalleryLightbox (line ~199, the "What to Expect" swipe cards) is unrelated/pre-existing, left alone.
- Build passed, pushed to main (8f7b533). Needs phone test for gesture feel.

---

## 2026-07-04 18:18 AEST


## Session addendum: 2026-07-04 ET (OG hardening)
- Confirmed via curl (normal + cache-busted) that middleware returns the CORRECT per-photo og:image for both galleries. The "default card" Yeti saw = Facebook's per-URL cache from URLs scraped earlier today before per-photo OG shipped (1d0f064). Server is flawless. Fix: FB Sharing Debugger scrape-again, or share never-before-scraped photos.
- Added og:image:secure_url + og:image:type=image/jpeg injection in middleware (both handleGalleryOG and the OG_MAP flow) for faster/more reliable first-time scrapes. Skipped og:image:width/height on purpose (mixed portrait/landscape dims; wrong values crop worse than omitting). Verified live (58d7f61).

---

## 2026-07-06 13:05 AEST

## Session: Jul 6 2026 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Recovered a lost Sunny Skies session via csearch.py (session 1a3d03f3, Shade DAM + AI ad pipeline strategy).
- Evaluated 3 real before/after roofing images against the ad-creative strategy (the 4-dial angle-match framework: GPS, altitude, heading, tilt).
- Settled the angle-matching debate: "close enough" is correct for a STACKED STATIC; pixel-perfect only matters for a WIPE. Capture trick = drone EXIF records the 4 dials automatically + shoot the BEFORE as a slow orbit video to harvest a matching frame later. No assistant needed. AI may remove clutter, never fake an angle.
- Compared the clean native aerial style vs the old branded blue/yellow mascot template. Verdict: native wins cold audiences (20-50% lower CPC). Move selling OFF the image (headline->primary text, offer->caption, logo->profile name, CTA->lead form). Keep branded template for yard signs, truck wrap, retargeting only.
- Generated 4 style-reference samples in Higgsfield (nano_banana_pro, 4:5): 2 aerial-native, 2 ground-level iPhone-native. All faceless/crew-safe.
- Wrote paste-ready ad copy (primary text, headline, CTA, lead form) using the "longer you wait, the more it costs" hook.

**What's live / deployed:**
- Nothing boosted. All assets saved to Desktop/sunny-skies/native-samples-jul6/ (4 PNGs + CARD-native-vs-branded.md).

**Next up:**
- A/B one aerial + one ground with identical copy/lead form; keep the cheaper lead.
- July 20 roof shoot: capture before as orbit video, chest-cam ASMR, same drone pin.
- Optional: 9:16 wipe-style version for Reels/Stories.

**Notes for other environments:**
- Samples are AI style-references, NOT shootable ads. Real drone/phone frames will look more authentic.
- Crew-safety rule still hard: no identifiable crew faces in any paid/public asset.

---

## 2026-07-06 15:50 AEST

## Session: 2026-07-06 ET
**Environment:** Antigravity IDE

**What was done:**
- Built a CrowdReel-style community photo feature for the Manitou Beach site (scan a QR board at an event → upload photos → live public gallery). Bolted onto the EXISTING gallery system rather than a new app.
- New API: api/photos-upload, photos-list, photos-report, photos-admin + api/lib/photos.js (Upstash Redis store) + api/lib/photo-slugs.js (server allowlist).
- New UI: src/components/EventPhotoWall.jsx (drop-in module: upload + live feed + flag), src/pages/GalleryHubPage.jsx (/gallery index), src/pages/GalleryAdminPage.jsx (/gallery-admin mobile takedown + printable QR board).
- Extended src/data/galleries.js (crowd galleries: america-250, ladies-club, july-4-2026), GalleryPage.jsx (merges crowd feed + module), PhotoGallery.jsx (added thumbOf + onReport props), App.jsx routes, middleware.js OG mirror.
- Live feed model per Yeti's call: photos post instantly; community can flag; 3 flags auto-hides; Yeti has one-tap takedown. Images downscaled in-browser (max 1600px) before upload; Claude-Vision SEO filenames; stored in Vercel Blob.

**What's live / deployed:**
- Pushed to main (commit 72ab09c), Vercel auto-deploying manitoubeachmichigan.com.
- Code is live but the photo store is INERT until the one setup step below is done (endpoints no-op gracefully, existing site unaffected).

**Next up (Yeti's one setup step):**
- Vercel dashboard → Storage → Marketplace → add Upstash Redis → connect to the `manitou-beach` project. That injects the REST env vars and the whole feature switches on. Phone-friendly, ~4 taps.
- Set ADMIN_SECRET env var (if not already) — it gates /gallery-admin (reuses existing pattern).
- To attach the photo wall directly onto a specific event page (e.g. USA250Page or LadiesClubPage), tell the IDE: it's a one-liner `<EventPhotoWall slug="..." title="..." />`.

**Notes for other environments:**
- Metadata store is Upstash Redis (NOT legacy Vercel KV — that's deprecated). Helper reads KV_REST_API_* or UPSTASH_REDIS_REST_* env names.
- Crowd galleries live in TWO places that must stay in sync: src/data/galleries.js (crowd:true) and api/lib/photo-slugs.js (server allowlist). Add a slug to both.
- Public gallery URL: /gallery/<slug>. Hub: /gallery. Admin: /gallery-admin.

---

## 2026-07-06 20:33 AEST

## Session: 2026-07-06 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Reviewed Yetickets + Manitou Beach from user / event-organiser / admin points of view; found and fixed a batch of real bugs across both.
- Manitou food trucks (the big one): fixed why the "truck is open today" auto-post never fired — the code read env names META_* but production uses FB_*/IG_*; added the fallback so it now finds the token. Added a peak-season reminder cron (texts active trucks their pin-drop link, weekends 10am ET, May–Sep). Made the auto-post alert by SMS on failure instead of failing silently. Fixed a site-wide security header that was silently blocking the GPS pin-drop. Removed an old instant-publish endpoint that bypassed moderation. Fixed event-date bugs (events vanishing early / on time-of-day). Rewrote README to the real workflow and flagged the dead monolith file.
- Yetickets: hardened the Stripe webhook (idempotent, persists+retries, awaits confirmation emails, maxDuration). Fixed an org data-leak (dashboard filter contains→equals) and added a duplicate-org-name guard. NOTE: another environment had hardened the same webhook in parallel; merged both, keeping their payment_status gate + sponsor idempotency plus my awaited-emails + maxDuration.
- Vercel: marked plaintext secrets as Sensitive; set a fresh CRON_SECRET (the old one was flagged "Needs Attention").
- Removed hardcoded Notion tokens from a one-off migration script (now reads from env).

**What's live / deployed:**
- Manitou-Beach `main` @ 75f6d8c — pushed, Vercel auto-deployed. Home + /api/food-trucks return 200.
- Yetickets `master` @ 639dbc8 (merge commit) — pushed, Vercel auto-deployed. Home returns 200.

**Next up:**
- Notion token rotation: DEFERRED on purpose. The exposed tokens never left the local machine (never committed to git; Documents is not cloud-synced), so exposure is contained and low-risk. Rotating live tokens risks site downtime and is now awkward (tokens are Sensitive-masked in Vercel). Do it later only as a deliberate, one-token-at-a-time mini-deploy if wanted.
- Verify the food-truck auto-post on the next real check-in (should post to FB/IG now; a failure will text the admin).
- Reminder cron first fires this Saturday 10am ET.
- Nice-to-haves discussed: manual map-tap fallback for the pin-drop, /api/health endpoints on both apps, and the coupon/attribution loop (post link already carries ?ref= tags for it).

**Notes for other environments:**
- Yetickets stripe-webhook.js was edited in TWO places at once this session (IDE + another env). Now merged. Pull before touching it again.
- Social-posting code reads BOTH META_* and FB_*/IG_* env names; production is configured with FB_*/IG_*.

---

## 2026-07-07 22:13 AEST

## Session: 2026-07-07 ET
**Environment:** Antigravity IDE
**What was done:**
- Assessed a YT transcript about "training Opus/Sonnet to think like Fable"; verdict: mostly valid, and Yeti's ~/.claude/fable-playbook.md already covers his "fable mode" five gates
- Flagged that the video's "leaked Fable system prompt" quotes don't match the real Claude Code prompt; treat as unverified, though the extracted behaviors are accurate
- Added rule 11 to fable-playbook.md: "Big model plans, cheap models execute" with a model/effort routing table (Haiku/Sonnet for mechanical + bounded work at low/medium effort, best model for judgment/verification/orchestration at high) and two guard rules (default effort beats max; workers return evidence, not conclusions)
- Updated the playbook one-liner and the matching summary in ~/.claude/CLAUDE.md to stay in sync

**What's live / deployed:**
- Nothing deployed; local config files only

**Next up:**
- Optionally test the routing table on a real multi-agent task to see the cost difference in practice

**Notes for other environments:**
- The fable-playbook now covers orchestration/routing, not just solo discipline. If Cowork or Mobile use subagents, the same rule applies: big model plans, cheap models execute, escalate effort only on failure or high stakes

---

## 2026-07-10 11:43 AEST

# Session Handoff

## Session: July 10, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Traced where the yetigroove.com/social form submission lands: email to daryl@yetigroove.com (subject "New Order [Social] - <Business>", from orders@yetigroove.com via Resend) + SMS to 517-260-5907. No database; the order is only in that inbox.
- Verified Vercel prod env vars (RESEND_API_KEY, TWILIO_*) are set, so delivery is working (unlike the May lost-order incident).
- Shipped the persist-before-notify standard to Gitdaryl/Yeti-Groove (commit 2a5b8e6): [ORDER] JSON payload logging before any delivery attempt, new /api/health endpoint, Twilio SMS made best-effort so it can't fail a delivered order.

**What's live / deployed:**
- yeti-groove production on Vercel; /api/health returns ok:true with resend+twilio true.

**Next up:**
- Yeti to check daryl@yetigroove.com inbox (and spam) for the customer's order email.
- Known form bugs from Dennis Babjack still open: view-only Drive upload folder; story cards don't map to the 9 video styles.

**Notes for other environments:**
- If an order ever goes missing again: Vercel runtime logs for yeti-groove, search "[ORDER]".

---

## 2026-07-13 18:37 AEST

## Session: July 13, 2026 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Prepped Yeti's pitch to the Devils & Round Lake Men's Club ($1000/yr, all admin included): demo-first structure, $83/mo math, Facebook objection handling, Ladies Club as live proof
- Diagnosed why the scan-and-submit crowd photo feature "never worked": code was deployed all along, but no KV database was connected in production (API returned live:false)
- Yeti created + connected Upstash Redis (upstash-kv-gray-village, Free plan) to the manitou-beach Vercel project; Blob store (manitou-beach-images) already existed
- Added Men's Club crowd gallery: src/data/galleries.js, api/lib/photo-slugs.js allowlist, middleware.js OG mirror. Commit dcdda2f, pushed, deployed
- Verified end to end on production: upload → Blob → Redis index → public list, plus 3-flag auto-hide. All working
- Generated printable QR → ~/Desktop/mens-club-gallery-QR.png → https://manitoubeachmichigan.com/gallery/mens-club

**What's live / deployed:**
- manitoubeachmichigan.com/gallery/mens-club (crowd uploads ON, live:true)
- Photo uploads now work for ALL crowd galleries (america-250, ladies-club, july-4-2026, mens-club) since the KV connection was the shared blocker

**Next up:**
- Hear how the Men's Club pitch went; follow up with QR + working photo wall if they didn't commit on the spot
- Housekeeping: a hidden navy test rectangle sits flagged in the mens-club gallery admin (/gallery-admin) — hide/ignore or purge
- Consider seeding the Ladies Club crowd gallery + printing QRs for their next event now that uploads work
- Longer term: moderation gate for public QR uploads (currently instant-publish with community flagging only)

**Notes for other environments:**
- The photo store env vars are KV_REST_API_URL/TOKEN via Upstash integration; code also accepts UPSTASH_REDIS_REST_* names
- Vercel Web Analytics is installed on the site; per-path stats (e.g. /ladies-club) available in the dashboard Analytics tab

---

## 2026-07-13 18:48 AEST

## Session: July 13, 2026 (evening ET, part 2)
**Environment:** Antigravity IDE
**What was done:**
- Embedded the crowd photo wall directly on /mens-club, above the curated "Memories" gallery (commit 328b472)
- Same mens-club feed powers both /mens-club and /gallery/mens-club, so the printed QR remains valid
- Verified on production via live JS chunks: MensClubPage chunk imports EventPhotoWall with upload UI and photos-upload endpoint

**What's live / deployed:**
- manitoubeachmichigan.com/mens-club with embedded "Add Your Photos" wall (upload + live feed)
- manitoubeachmichigan.com/gallery/mens-club (same feed)

**Next up:**
- Result of tonight's Devils & Round Lake Men's Club pitch ($1000/yr)
- Purge hidden navy test photo via /gallery-admin
- Consider embedding the photo wall on /ladies-club the same way (one-line component drop)
- Moderation gate for public QR uploads (currently instant-publish, 3 community flags auto-hide)

**Notes for other environments:**
- Full context in the part-1 handoff pushed earlier tonight: KV (Upstash) connection fixed uploads for all crowd galleries; QR PNG at ~/Desktop/mens-club-gallery-QR.png

---

## 2026-07-13 20:44 AEST

## Session: July 13, 2026 (night ET, part 3 — RESULT)
**Environment:** Antigravity IDE
**What was done:**
- Men's Club pitch WON: $990/yr check in hand ($1000 minus $10 Men's Club membership Yeti bought on the spot)
- Live QR demo worked in the room: 4 member photos uploaded 7:01-7:06pm, live on /mens-club before the meeting ended (5 total incl. Yeti's test)
- Win logged to Session Brain

**What's live / deployed:**
- manitoubeachmichigan.com/mens-club with embedded crowd photo wall and 5 live community photos

**Next up:**
- Morning-after email + $990 receipt to the check signer, linking to their page with last night's photos
- Finesse pass on /mens-club: 2026 event calendar, officer contacts, membership info
- Moderation gate for QR uploads (QR is now in the wild; only 3-flag community auto-hide protects it)
- Purge navy test photo via /gallery-admin
- Embed photo wall on /ladies-club (one-line drop, slug already exists)

**Notes for other environments:**
- Yeti is now a paying member of the Devils & Round Lake Men's Club — relationship asset for renewals
- Sales pattern that worked: live page demo + audience-participation QR photo upload + $83/mo math; reuse for other org pitches

---

## 2026-07-13 21:41 AEST

## Session: July 13, 2026 (late night ET, part 4 — moderation + hearts build)
**Environment:** Antigravity IDE
**What was done:**
- Built and shipped the full photo moderation + hearts system (commit fe589b3), all verified live on production:
  - Claude Haiku vision pre-screens every upload for family-site safety, piggybacked on the existing SEO-filename call (zero extra API cost); unsafe photos rejected before storage
  - Flags now require a reason (Not from this event / Inappropriate / Someone asked to remove it / Spam) via a calm grey flag + reason sheet in the lightbox
  - One flag per person (device id + IP-hash fallback); 3 distinct people auto-hides. Closed the hole where one person could hide any photo with 3 taps
  - Hearts: toggle per person, count badge on grid tiles and lightbox, published as schema.org InteractionCounter (LikeAction) JSON-LD for AI-search engagement signals
  - New n8n workflow "MB Photo Flag Notify" (webhook mb-photo-flag): Resend email to daryl@yetigroovemedia.com on every flag, + Twilio SMS on auto-hide or AI block
  - Added Photos API (live:true check) to the daily 8am MB Site Audit workflow with a fix-hint for KV disconnects
- Production test run: upload passed pre-screen, heart toggled on/off, duplicate flag correctly rejected, 3-device flag auto-hid the test photo, SMS + email delivered. Test artifacts: Yeti received 1 SMS + ~4 emails marked as tests; two hidden test photos sit in gallery-admin

**What's live / deployed:**
- manitoubeachmichigan.com — hearts + flag reasons on all crowd galleries (mens-club, ladies-club, america-250, july-4-2026)
- n8n.yetigroove.com: MB Photo Flag Notify (new, active), MB Site Audit (updated, active)

**Next up:**
- Yeti: hard-refresh /mens-club and try hearting a photo from your phone
- Morning-after email + $990 receipt to the Men's Club check signer (photos from the meeting are on their page)
- Finesse pass on /mens-club content (2026 calendar, officers, membership info)
- Optional later: true delete (Blob purge) in admin, surface flag reasons in gallery-admin UI

**Notes for other environments:**
- Flag webhook URL is hardcoded default in api/lib/notify.js, overridable via N8N_FLAG_WEBHOOK env var
- Twilio sender +15174350130, SMS to +15172605907; Resend from hello@manitoubeachmichigan.com

---

## 2026-07-13 21:52 AEST

## Session: 2026-07-13 ET
**Environment:** Antigravity IDE
**What was done:**
- Scanned local repos for Remotion usage; found two: Manitou-Beach and Yeti-Signature-Films/stays-broll
- Upgraded both to Remotion 4.0.489 (latest) via `npx remotion upgrade`
  - Manitou-Beach: was 4.0.441 (remotion, @remotion/cli, @remotion/player; zod also bumped to 4.3.6)
  - stays-broll: was 4.0.261 (remotion, @remotion/cli)
- Verified: Manitou-Beach vite build passes; both Remotion bundles compile and list all compositions (EventPromo, StaysPromo, GetListedPromo; StaysBroll)

**What's live / deployed:**
- Nothing deployed — local package upgrades only, not committed or pushed

**Next up:**
- Commit/push the package.json + lockfile changes in both repos if the upgrades should stick
- Optional: Manitou-Beach vite build warns about >500 kB chunks (pre-existing, not from this upgrade)

**Notes for other environments:**
- Remotion is now pinned exact at 4.0.489 in both repos (remotion upgrade uses --save-exact)

---

## 2026-07-13 21:56 AEST

## Session: 2026-07-13 ET (part 2 — commit/push)
**Environment:** Antigravity IDE
**What was done:**
- Committed and pushed the Remotion 4.0.489 upgrades from earlier this session
- Manitou-Beach: commit 8e32767 (package.json + package-lock.json only), rebased on top of 4 newer remote commits (photo moderation + Men's Club gallery work pushed from another environment), pushed to origin/main
- Yeti-Signature-Films: stays-broll committed for the first time (cef0f28 — src + package files; out/ renders and node_modules excluded), pushed to origin/main

**What's live / deployed:**
- Both pushes on GitHub main; Vercel will pick up Manitou-Beach on its next deploy

**Next up:**
- Manitou-Beach still has uncommitted WIP left intact: agent_configs edits, page edits (MensClub, DevilsLake, RoundLake, USA250, discover.js, seed-community-pois.mjs), shop-with-a-cop -> shop-with-a-hero image rename. Preserved through a stash/rebase cycle.

**Notes for other environments:**
- Remote Manitou-Beach commits (photo moderation, crowd gallery) were fetched and are now the base of local main — whoever made them, local is in sync
- Remotion pinned exact at 4.0.489 in both repos

---

## 2026-07-13 22:18 AEST

## Session: July 13, 2026 (late night ET, part 5 — event sections + heart placement)
**Environment:** Antigravity IDE
**What was done (commit 3edf2ad, verified live):**
- Event sections in crowd galleries: upload card asks "Which event are these from?" (Tip-Up Festival, Firecracker 7K, July 4th Fireworks, Golf Outing, default Club Life). Wall groups photos into titled/dated sections in calendar order; empty sections don't render; untagged photos land in Club Life
- Server validates event tags against an allowlist (api/lib/photo-slugs.js GALLERY_EVENTS); forged tags sanitize to '' — verified on prod with a fake tag
- Hearts moved onto the photos per Yeti's feedback: tappable heart pill bottom-right of every thumbnail (heart without opening the lightbox, Instagram-style), lightbox heart moved to bottom-right
- Rebased over an automated Remotion 4.0.489 bump that landed on origin mid-build
- Cleanup done with the notify workflow temporarily paused, so no test SMS/emails this round; two more hidden test photos in gallery-admin

**What's live / deployed:**
- manitoubeachmichigan.com /mens-club and /gallery/mens-club: event-sectioned photo wall with on-photo hearts

**Next up:**
- Yeti: refresh /mens-club, try the event dropdown and thumbnail hearts on your phone
- Morning-after email + $990 receipt to the Men's Club check signer
- To add a new event later (e.g. a dated 2027 edition): add one line in src/data/galleries.js events[] + mirror key in api/lib/photo-slugs.js GALLERY_EVENTS
- Future nice-to-haves: move photo between events in gallery-admin; Blob purge delete; flag reasons shown in admin UI

**Notes for other environments:**
- Event keys live in two places by design (client config + server allowlist); keep in sync
- Gallery-admin has ~4 hidden test photos (navy squares) that can be ignored or purged

---

## 2026-07-13 22:26 AEST

## Session: 2026-07-13 ET
**Environment:** Antigravity IDE
**What was done:**
- Kicked off the Joe Profit movie project ("Never Broken" feature, Seedance production, Joe fundraising)
- Analyzed the full 52k-word book text (Downloads/Never Broken Audiobook.txt) chapter by chapter via 4 parallel readers
- Web-researched Joe's verified career facts and post-book accomplishments for epilogue cards
- Wrote the foundation doc: Documents/Claude Code/Joe-Profit/movie/STORY-ANALYSIS.md
  - Recommended structure: cold open in the 1965 barn scene, five acts as five "fields" (cotton, football, broken, boardroom, service), ends on the quiet 2015 ordination scene, epilogue title cards
  - Verified vs unverified fact split for the fundraise (key flag: "largest minority contract" claim is only self-sourced; research says "first," not "largest")
  - Seedance production notes: 6-age character consistency kit, use Joe's own audiobook narration as VO

**What's live / deployed:**
- Nothing deployed; analysis doc only

**Next up:**
- Yeti + Joe pick logline direction (Fields vs Vow)
- Interview Joe: 2020-2026 activity, Young Authors published-kids count, documentation for Kuwait "largest" claim
- Then write the treatment (5-8 pages) from STORY-ANALYSIS.md section 4

**Notes for other environments:**
- Cowork is well-suited for the treatment writing and the Joe interview question doc
- No 2023-2026 press on Joe was findable; epilogue "still going" card must come from Joe directly

---

## 2026-07-13 22:50 AEST

## Session: 2026-07-13 ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- Story arc decision for the Never Broken movie: Yeti chose the sports arc over the full-life version
- Film now covers 1949-1971 only: cotton field to draft day, resolving at the Joe Profit Day jersey retirement (the community that jeered him fills the hall)
- Business/ministry years become epilogue title cards, led by the knee-injury gut-punch card, each card another field he won
- Updated Documents/Claude Code/Joe-Profit/movie/STORY-ANALYSIS.md: new section 2.5 with the full three-act beat progression; sections 5, 6, 8, 9 revised to match
- Production win: this cut needs 3 character ages (+optional elder for a 1999 Hall of Fame frame) and 2 period looks instead of 6 and 7, and zero NFL game footage (trademark problem disappears)

**What's live / deployed:**
- Nothing deployed; docs only

**Next up:**
- Joe to confirm the 1949-1971 arc and the optional 1999 HoF frame device
- Interview Joe: epilogue "still going" material, Young Authors count, Kuwait "largest vs first" documentation, and what people actually said in the barn / kitchen / locker room (real fragments beat invented dialogue)
- Then the treatment (5-8 pages) from STORY-ANALYSIS.md section 2.5

**Notes for other environments:**
- Cowork: good place to draft the Joe interview question sheet and the treatment

---

## 2026-07-13 22:59 AEST

## Session: July 13, 2026 (night ET, part 6 — heart fix + Shop with a Hero)
**Environment:** Antigravity IDE
**What was done (commits 861d963, a897d59, verified live):**
- Fixed "no heart in enlarged view": the floating Voice Concierge mic button was covering the lightbox heart in the screen corner. Heart now anchors to the photo's own bottom-right corner (rides the image while swiping), verified with headless screenshots on phone + desktop viewports
- Renamed Shop with a Cop → Shop with a Hero site-wide: 9 text references across MensClubPage (program card, mission text, auction desc, gallery caption), DevilsLakePage, RoundLakePage, discover.js (AI description + map pin). Image file renamed to shop-with-a-hero.jpg. Icon 👮 → 🦸, wording broadened to "law enforcement and first responders" (flag if unwanted)

**What's live / deployed:**
- manitoubeachmichigan.com: photo hearts on thumbnails + on-photo lightbox heart, event sections, flag reasons, AI pre-screen, n8n notifications — the complete crowd photo system

**Next up:**
- Morning-after email + $990 receipt to the Men's Club check signer
- /mens-club content finesse (2026 calendar dates, officer contacts, membership info)
- UX debt spotted in screenshots: the floating mic button overlays the photo lightbox on mobile and owns the corner social apps use — consider hiding it while a photo is open
- Future: retag photo between events in admin, Blob purge delete, hearts on curated Memories photos if wanted

**Notes for other environments:**
- Playwright headless (chromium_headless_shell-1223) works on the Mac for visual verification of the live site; script pattern in this session's scratchpad

---

## 2026-07-13 23:05 AEST

## Session: 2026-07-13 ET (part 3)
**Environment:** Antigravity IDE
**What was done:**
- Wrote the Never Broken treatment first draft: Documents/Claude Code/Joe-Profit/movie/TREATMENT.md (cold open in the barn, three acts 1949-1971, climax draft day, resolution Joe Profit Day jersey retirement, epilogue cards led by the knee-injury gut punch)
- Wrote WHY-THIS-STORY.md in the same folder: Joe-facing notes defending the 1949-1971 cut, plus a table routing archival "extras" (old VHS interviews etc.) into the fundraise campaign instead of the film
- Key line for curving Joe: "Nothing gets left out. It gets put where it wins."

**What's live / deployed:**
- Docs only, nothing deployed

**Next up:**
- Yeti reviews treatment, shares with Joe alongside WHY-THIS-STORY.md
- Joe interview: real dialogue fragments (barn, kitchen, locker room), Young Authors count, Kuwait claim docs, decision on the 1999 HoF frame device
- After sign-off: beat sheet, then screenplay, then Seedance shot bible

**Notes for other environments:**
- Cowork: treatment doc could be formatted into a nice PDF for Joe there

---

## 2026-07-14 20:13 AEST

## Session: 2026-07-14 ET
**Environment:** Antigravity IDE
**What was done:**
- Researched real-time AI fact-checking apps (Factiverse, InTruth, Cluely, LiveFC, Filmot)
- Confirmed a gap: nobody combines live listening + qualifying questions for fuzzy claims + YouTube sound-bite receipts
- Drafted MVP spec for "Receipts", a live debate copilot for YT political/religious debaters: ~/debate-copilot/SPEC.md
- Saved project memory: debate-copilot-receipts.md

**What's live / deployed:**
- Nothing deployed; spec only

**Next up:**
- Phase 1 of the spec: dashboard skeleton rendering fake cards from JSON
- Decide on the demo debate episode (tariffs/economy topic) for the end-to-end test

**Notes for other environments:**
- Full spec at ~/debate-copilot/SPEC.md on the Mac; core loop = STT -> claim detect -> triage into verdict card / qualifying-question card / receipt card
- Stack planned: Next.js/Vercel, Deepgram, Claude + web search, Upstash KV, yt-dlp caption index

---

## 2026-07-14 20:26 AEST

## Session: 2026-07-14 ET
**Environment:** Antigravity IDE
**What was done:**
- Researched real-time AI fact-checking apps (Factiverse, InTruth, Cluely, LiveFC, Filmot); confirmed the gap
- Drafted and expanded MVP spec for "Receipts", live debate copilot for YT debaters: ~/debate-copilot/SPEC.md
- Added Yeti's predictive engine idea to spec (pattern library pre-fetches receipts mid-sentence) + v2 ambient monitor mode for live primary debates
- Built phase 1 prototype: ~/debate-copilot/prototype/dashboard.html, single-file dashboard replaying a fake tariff debate with all 3 card types (DEBUNKED / ASK THIS / RECEIPT) plus ghost "predicting" card that resolves instantly
- Verified rendering with headless chromium screenshots; published as Claude artifact: https://claude.ai/code/artifact/075f6059-1929-4fe8-930a-1d484c7c080b
- Saved/updated project memory: debate-copilot-receipts.md

**What's live / deployed:**
- Artifact (private) at the URL above; nothing on Vercel yet

**Next up:**
- Phase 2: Deepgram streaming STT from a browser tab feeding the transcript rail
- Phase 3: Claude claim detection against a hand-labeled 10-min debate clip
- Add "Receipts" as a Project option in the Session Brain Notion database

**Notes for other environments:**
- Full spec at ~/debate-copilot/SPEC.md; open the artifact link on any device to see the prototype run (hit REPLAY)
- Card rule: every card must be usable out loud while still talking

---

## 2026-07-14 20:54 AEST

## Session: 2026-07-14 ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- Receipts (debate copilot) phase 2 scaffolded: ~/debate-copilot/prototype/listen.html captures browser-tab audio via getDisplayMedia and streams PCM16 to a Deepgram nova-2 websocket; API key prompted once and stored in browser localStorage; JS syntax-checked
- Confirmed Yeti already has a Deepgram account (project 117ca8b6, ~$200 pay-as-you-go credit, standard signup credit)

**What's live / deployed:**
- Phase 1 demo artifact (private): https://claude.ai/code/artifact/075f6059-1929-4fe8-930a-1d484c7c080b

**Next up:**
- Yeti: Create API Key in the Deepgram console, open listen.html in Chrome, click LISTEN TO A TAB against a debate video
- Phase 3: Claude claim detection on the live transcript
- Add "Receipts" as a Project option in the Session Brain Notion database

**Notes for other environments:**
- Spec: ~/debate-copilot/SPEC.md · Phase 1 demo: prototype/dashboard.html · Phase 2 listener: prototype/listen.html

---

## 2026-07-14 21:18 AEST

## Session: 2026-07-14 ET (Receipts, continued)
**Environment:** Antigravity IDE
**What was done:**
- Phase 2 VERIFIED: Yeti tested ~/debate-copilot/prototype/listen.html with his Deepgram key; live tab transcription works
- Phase 3 built: ~/debate-copilot/prototype/live.html = full Receipts pipeline in one page (Deepgram STT -> claude-haiku-4-5 claim detection every 12s -> claude-opus-4-8 + web search verification -> DEBUNKED / VERIFIED / ASK THIS cards)
- Both API keys prompted once in-browser, stored in localStorage only

**What's live / deployed:**
- Phase 1 demo artifact (private): https://claude.ai/code/artifact/075f6059-1929-4fe8-930a-1d484c7c080b

**Next up:**
- Yeti: create an Anthropic API key at console.anthropic.com (needs billing; separate from the Claude subscription), then open live.html and LISTEN TO A TAB against a debate video
- Add "Receipts" as a Project option in the Session Brain Notion database

**Notes for other environments:**
- Spec: ~/debate-copilot/SPEC.md · demo replay: prototype/dashboard.html · transcript-only: listen.html · full pipeline: live.html

---

## 2026-07-14 22:06 AEST

## Session: 2026-07-14 ET (Receipts, working + commercial plan)
**Environment:** Antigravity IDE
**What was done:**
- Receipts full pipeline VERIFIED working by Yeti on a live presser (transcription + claim cards)
- Added speaker diarization (nova-3, colored SPEAKER labels, attributed claims) and multilingual code-switching (10 languages, claims translated to English)
- Cost lesson: first test burned all $4.39 of console credits in minutes; added wallet guard (25 checks/session, 2 concurrent, queued), downgraded verifier to sonnet, max 2 searches/claim
- Drafted commercial architecture: ~/debate-copilot/COMMERCIAL.md (one-tap Expo app, backend relay holds keys, global claim cache = margin, Stripe web credits to hit ~10% markup, mic + YT-link sources first)

**What's live / deployed:**
- Phase 1 demo artifact (private): https://claude.ai/code/artifact/075f6059-1929-4fe8-930a-1d484c7c080b
- Working local prototype: ~/debate-copilot/prototype/live.html

**Next up:**
- Yeti: add credits at platform.claude.com Plans & Billing before next test
- Decide COMMERCIAL.md open questions (name/domain, consumer vs pro-tool first, transcript retention)
- Phase 1 of commercial build: backend relay (moves keys server-side, adds global claim cache)

**Notes for other environments:**
- Docs: SPEC.md (product) + COMMERCIAL.md (business/mobile) in ~/debate-copilot/
- Cowork could research: receipts.app domain availability, competitor pricing, App Store external-purchase-link rules current state

---

## 2026-07-14 22:11 AEST

## Session: 2026-07-14 ET (Receipts: pricing revised)
**Environment:** Antigravity IDE
**What was done:**
- COMMERCIAL.md pricing revised: dropped Yeti's original cost+10% rule (his call, "poverty thinking"). Now value-based pro-tool tiers (sketch: Creator ~$29/mo, Pro ~$79/mo with receipt archives + opus verification) with a structural no-deficit rule: capped allowances, prepaid credit packs for overage, never unlimited, wallet guards at every layer
- Moat framing: not price; a copycat starts with an empty claim cache while ours is instant and near-free on repeat claims

**What's live / deployed:**
- Working prototype: ~/debate-copilot/prototype/live.html; demo artifact: https://claude.ai/code/artifact/075f6059-1929-4fe8-930a-1d484c7c080b

**Next up:**
- Yeti: add console credits before next test; decide COMMERCIAL.md open questions (name/domain, consumer vs pro-first, transcript retention)
- Phase 1 of commercial build: backend relay (keys server-side + global claim cache)

**Notes for other environments:**
- Docs: ~/debate-copilot/SPEC.md + COMMERCIAL.md. Cowork could research receipts.app domain + Otter/Riverside/StreamYard pricing comps.

---

## 2026-07-14 22:18 AEST

## Session: July 14, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Men's Club Golf Outing 2026 build on manitoubeachmichigan.com/mens-club (new yearly page-management contract)
- Hero flips to golf mode until Sept 13: looping Seedance 2.0 video background (4 scenes: tee shot, cart ride, putt, steak/chicken clubhouse lunch, crossfaded into a 22s loop), live countdown to the 8:30 am shotgun start, Call to Sign Up CTA. Auto-reverts to the standard club hero after Sept 13.
- New Golf Outing section: detail cards (check-in 8:00, shotgun 8:30, $75/person, 18 holes + cart, hot dogs at the turn), Ford Bronco Sport hole-in-one callout, tiered sponsors (Gold: NTA, Silver: Scotty's Body Shop, Bronze: Edison Builders), sign-up phone (517) 547-3653, Tip-Up 2027 save-the-date (Feb 5-7)
- Edison Builders logo copied from ladies-club sponsors folder to mens-club/sponsors/
- Golf Outing entry in the annual events list updated with real 2026 details
- Verified locally with Playwright screenshots (hero video + countdown, detail cards, sponsor tiers all render)
- Commit 58bbbd1 pushed to main (also carried forward pending prior-session tweaks: USA250 page edits, shop-with-a-hero rename; resolved one rebase conflict in favor of remote's first-responders wording)

**What's live / deployed:**
- 58bbbd1 pushed to main; Vercel auto-deploy in flight for manitoubeachmichigan.com/mens-club

**Next up:**
- Yeti is collecting the comprehensive Men's Club sponsor list; slot into GOLF_SPONSOR_TIERS in src/pages/MensClubPage.jsx (structure supports multiple sponsors per tier, logo + url fields ready)
- Need clean logo files for NTA and Scotty's Body Shop (currently styled text cards; Edison has its logo)
- Ask the club whether they want an online "register your foursome" form vs call-the-course only (persist-before-notify standard applies if form)
- Raw Seedance clips saved to ~/Desktop/mens-club-golf-clips/ (tee, cart, putt, lunch) for social posts
- Higgsfield credits: 108 spent on the 4 clips, ~430 remaining

**Notes for other environments:**
- Men's Club page now has a dated hero: golf mode is gated by GOLF_OUTING.heroUntil (Sept 14, 2026) and self-reverts, no action needed after the event
- Sponsor tier accents are inline hex in GOLF_SPONSOR_TIERS (gold/silver/bronze), intentional exception to C tokens

---

## 2026-07-14 22:20 AEST

## Session: 2026-07-14 ET (Receipts: modes vision)
**Environment:** Antigravity IDE
**What was done:**
- Vision expansion written into SPEC.md + COMMERCIAL.md: three modes on one pipeline — Debate (current), Reporter/interview (soundbites, timestamped quotables, draft article with fact-check receipts inline; "Opus Clips with receipts"), Conference/meeting (talking points, actionable ideas, market-report inputs)
- Post-session content engine noted as the highest-margin feature (Batches API at 50% price, no latency pressure); added to pricing tiers
- Origin story recorded for pitch/marketing: born from a podcast (ex-OpenAI employee on AI lie detection as a future use); Receipts is the base framework that could host deception detection if it ever becomes real

**What's live / deployed:**
- Working prototype: ~/debate-copilot/prototype/live.html

**Next up:**
- Yeti: add console credits; decide COMMERCIAL.md open questions (name/domain, pro-vs-consumer first, transcript retention)
- Phase 1 of commercial build: backend relay (keys server-side + global claim cache)

**Notes for other environments:**
- All docs in ~/debate-copilot/ (SPEC.md, COMMERCIAL.md). Cowork research ideas: receipts.app domain, Otter/Riverside/Opus Clips pricing comps.

---

## 2026-07-14 22:35 AEST

## Session: July 14, 2026 (ET) - continued
**Environment:** Antigravity IDE
**What was done:**
- Follow-ups to the Men's Club Golf Outing 2026 build on /mens-club:
- Hero club logo enlarged 76px -> 180px in golf mode, readable at hero scale (5cb3318)
- New CTA under the 2026 Golf Outing Sponsors tiers: "Put Your Business on the Course", anchor-jumps to the Become a Sponsor form (new id become-a-sponsor) (78ef4b4)
- Both verified with Playwright screenshots before push

**What's live / deployed:**
- 5cb3318 and 78ef4b4 pushed to main; Vercel auto-deploys manitoubeachmichigan.com/mens-club

**Next up:**
- Sponsor form event dropdown pending Yeti confirming with the club: which event is being sponsored (Men's Club general / Tip-Up / Golf Outing / Firecracker 7K), whether dollars are earmarked per event, whether golf sells event-specific inventory (hole signs, cart sponsor, turn station), and how poster tiers (Gold/Silver/Bronze) map to the form amounts ($1,000/$500/$100). Plan: dropdown on shared CommunityDonationForm, per-event tier sets if needed, golf CTA pre-selects Golf Outing
- Still waiting on: comprehensive sponsor list, clean NTA + Scotty's logos, foursome-registration-form decision

**Notes for other environments:**
- Poster tier names (Gold/Silver/Bronze) and the on-site sponsor form tiers (Presenting/Gold/Silver/Community Partner) don't currently match; flagged to Yeti, resolve after club confirms

---

## 2026-07-15 21:22 AEST

## Session: 2026-07-15 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Picked up HANDOFF-never-broken-site.md from Downloads (built earlier today in claude.ai chat)
- Moved unzipped site from ~/Downloads/never-broken-site to ~/never-broken-site
- Git repo initialized, pushed to private repo github.com/Gitdaryl/never-broken-site
- Deployed to Vercel (project: never-broken-site, scope: yetigroove)
- Verified live: index + treatment return 200, noindex meta present on both pages, robots.txt blocking all crawlers

**What's live / deployed:**
- https://never-broken-site.vercel.app (playbook at /, treatment at /treatment.html) — link-only, not indexed. This is the link to send Joe.

**Next up:**
- Optional: attach playbook.joeprofitneverbroken.com subdomain in Vercel dashboard (Settings → Domains on the never-broken-site project)
- Send Joe the link

**Notes for other environments:**
- claude.ai Vercel connector was failing (empty team list); IDE's Vercel CLI auth worked fine, used that
- Site is NOT connected to GitHub auto-deploy; redeploys are manual via `vercel` in ~/never-broken-site

---

## 2026-07-15 21:24 AEST

## Session: 2026-07-15 (evening ET, follow-up)
**Environment:** Antigravity IDE
**What was done:**
- Verified the never-broken-site Vercel project is connected to GitHub (Vercel auto-linked it at project creation)
- Confirmed auto-deploy works: pushed a test commit to Gitdaryl/never-broken-site main → Vercel auto-built and deployed to production

**What's live / deployed:**
- https://never-broken-site.vercel.app (unchanged, still the link for Joe)

**Next up:**
- Optional: attach playbook.joeprofitneverbroken.com subdomain in Vercel dashboard
- Send Joe the link

**Notes for other environments:**
- Correction to earlier note: GitHub auto-deploy IS wired up. Any session can update the site by pushing to Gitdaryl/never-broken-site main; no Vercel CLI needed.

---

## 2026-07-15 21:38 AEST

## Session: 2026-07-15 (night ET)
**Environment:** Antigravity IDE
**What was done:**
- Added paragraph notes to the Never Broken treatment page so Joe can comment inline: "add note" under every paragraph, notes render as sticky notes matching the binder aesthetic, name remembered per device, anyone with the link can add/delete (no auth by design, link-only site)
- Backend: Vercel Blob store `never-broken-notes` created and linked to the project; api/notes.js (GET/POST/DELETE) with persist-first logging; api/health.js self-check per build standard
- All 29 content paragraphs got stable data-nb ids (rule: never renumber, notes are keyed to them)
- Version workflow set up: "Draft v1" chip + date in header; from v2 on, changed paragraphs get class="revised" data-rev="v2" (gold left border + tag), cleared next version. No word-level track-changes colors. Full workflow in repo README.md
- Tested locally (vercel dev + Playwright UI drive), deployed, verified production: health ok, notes API live, UI screenshot confirmed

**What's live / deployed:**
- https://never-broken-site.vercel.app/treatment.html with working notes
- https://never-broken-site.vercel.app/api/health self-check

**Next up:**
- Send Joe the link, tell him to tap "add note"
- When revising: follow README version workflow (bump chip, mark revised paragraphs, git tag)
- Optional: subdomain playbook.joeprofitneverbroken.com

**Notes for other environments:**
- Notes live in Vercel Blob store never-broken-notes (own store, nothing borrowed from manitou-beach)
- Repo: Gitdaryl/never-broken-site, auto-deploys on push to main

---

## 2026-07-15 22:07 AEST

## Session: July 15, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Queried Manitou Beach - Event Submissions Notion DB for week of July 15-21 events
- Added NEW event (Published): "Wine Tastings at Ang & Co - Chateau Fontaine Tasting Room Now Open", dated 7/17, at 141 N Lakeview Blvd. $2 tastings, $8 glasses, bottles $18-$22, hard cider $6/can. Ang is the first village shop with a wine license; 3 more stores getting licenses soon. Promo Pages: Whats Happening + Wineries
- Wrote Holly & Yeti HeyGen scripts (90-sec main + 35-sec reel) for this week's events, wine-tease angle where AI Holly is jealous real Holly gets to drink. Saved to ~/Downloads/HEYGEN-holly-yeti-wine-weekend-jul17.md

**What's live / deployed:**
- Ang & Co wine event is Published in the events DB, so it should appear on the Manitou Beach site feeds (Whats Happening + Wineries pages)

**Next up:**
- Yeti to record/generate the HeyGen video from the script
- When the other 3 stores get their licenses, add their events too (running gag material: AI Holly's wine jealousy)
- Ang & Co event has no Image URL or hours yet; add the poster image and tasting room hours if available

**Notes for other environments:**
- The Chateau Fontaine poster (wine list + prices) is what the event details came from; poster image itself is not uploaded anywhere yet

---

## 2026-07-16 11:08 AEST

## Session: July 16, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Standardized the Men's Club official name to "Devils Lake & Round Lake Men's Club" across the whole Manitou Beach site (7 files, 14 spots)
- Fixed inconsistent variants: "Devils & Round Lake", "Devils and Round Lake", "Devil's Lake & Round Lake", "Devil's and Round Lake", "Mens Club"
- Updated: /mens-club hero, share bar, donation form, SEO meta description; Devils Lake + Round Lake page callouts; Ladies Club sponsor list; USA250 Firecracker 7K copy; Discover map POI; voice concierge prompt (agent_configs)
- Left short nav labels ("Men's Club") and unrelated names (Fireworks Association, Tip-Up Festival) untouched
- Build passed, committed e0b2f06, pushed to main

**What's live / deployed:**
- Pushed to main → Vercel auto-deploy for manitoubeachmichigan.com

**Next up:**
- Nothing deferred from this task

**Notes for other environments:**
- Official club name is "Devils Lake & Round Lake Men's Club" — use this exact form in all future copy, docs, and marketing across platforms

---

## 2026-07-16 12:31 AEST


## Session: July 16, 2026 ET (later)
**Environment:** Antigravity IDE
**What was done:**
- Built out /mens-club from the club's real 2026 documents (yearly sponsor letter + golf brochure)
- Replaced invented sponsor tiers ($2500/$1000/$500/$100) with the REAL program: $130 Yearly Sponsor + $50 Golf Hole Sponsor, May 1 deadline, EIN 46-4087550, checks to The Devils Lake & Round Lake Men's Club, 3171 Round Lake Hwy
- CRITICAL FIX: sponsor form was silently discarding submissions (no endpoint). New /api/mens-club-sponsor persists to Vercel Blob (intake/mens-club-sponsors/) BEFORE emailing via Resend; notifications go to admin@yetigroove.com; GET on the endpoint = health check
- Golf outing buildout: $300/foursome, Sign Up Your Team + Sponsor a Hole ($50, mailto jborton1031@gmail.com) cards, Yeti cooler prize, course address/phone
- 2026-2027 Yearly Sponsors thank-you wall, all 48 names from the brochure
- Added Halloween Hot Dog Roast event (AI-generated candid photo, compressed 183K); programs now include Catherine Cobb DV Center, Kiwanis hams, Lakes Preservation
- Verified live end-to-end: health check green, test submission persisted + both emails sent

**What's live / deployed:**
- Commit fe9a6e5 on main, deployed to manitoubeachmichigan.com (rebased over Cowork's 12f5168)

**Next up:**
- Yeti to supply: NTA + Scotty's Body Shop logos for golf sponsor cards (text-only now); a real Halloween Hot Dog Roast photo to replace AI one when available
- Decide if club officer (jborton1031@gmail.com) should ALSO get sponsor notification emails (one-line change in api/mens-club-sponsor.js)
- Delete the TEST sponsor blob when convenient (intake/mens-club-sponsors/, name starts with TEST)

**Notes for other environments:**
- Men's Club sponsor submissions now land in Vercel Blob intake/mens-club-sponsors/ + email admin@yetigroove.com; anyone handling club admin should watch for those emails and follow up within 2 business days (that is what the site promises)

---

## 2026-07-16 12:54 AEST


### Addendum (same session): sponsor wall links
- All 48 sponsor names on /mens-club wall reviewed for web presence; 41 now hyperlink (website first, else the business's own FB page), verified for Michigan location + HTTP 200. Names render lake blue with hover underline.
- 7 with no findable web presence stay plain text: Batko Family, Mark Scarlato Family, Edison Builders, Lakeside Construction, Lightning Quick Gas N Go, Rock Hard Concrete (Adrian), The Springs BP
- Pitch angle for Yeti: these 7 (and the FB-only ones) are prime prospects for MB business listings / pages
- Commit 1209cee deployed