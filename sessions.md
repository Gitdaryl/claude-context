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