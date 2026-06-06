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