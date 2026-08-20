## Session: 2026-08-20 ET
**Environment:** Antigravity IDE

**What was done:**
- Built the Decker & Sons options menu after their discovery meeting. One document, six passes: 30 items across 7 sections, compliance flags (Clear / Wants a look / Needs signoff), a printed Plan B on every flagged line, and a 4-rung fallback ladder for AI Kathy down to a text-only FAQ.
- Confirmed the underwriter is Auto-Owners and built that into every flag.
- Packaged the free Front and Center listing ($49/mo, $588/yr, already live on the MB site). It bundles the full Google Business Profile build, so the menu's GBP line dropped to $175 for the second office only, avoiding a double charge.
- Reworked the bundles after finding they were sums rather than discounts. Now $1,450 / $550 per mo / $995 per mo, first-year build included free on both monthlies, savings printed in dollars off the low end of every range.
- Added an internal 19-question objection prep sheet in Kathy's voice, grouped commitment / carrier / work / reputation / money, with three red "Careful" lines.
- Added a client sign-off page: free listing pre-ticked, pick-a-plan, then two columns. "Starting now" carries the signature and a 50% deposit; "We will submit these to Auto-Owners first" is ticks only, nothing billed until approved. All internal flag vocabulary stripped from that page.
- Print density pass after it came in at 14 pages. The three bundle cards needed 748px and Letter minus margins gives 710px, so they wrapped one per row and ate three pages. Pinned to three columns, tightened paddings, held body copy at 9.5pt for an older reader. Now 10 pages.
- Turned seasonal flex into a real policy: the monthly is a budget not a fixed list, re-pointed four times a year, swap sideways any time, step down only at 12 months, one free 30-day pause a year.
- Decided close mechanics: paper in the room, card link emailed the same day, online form as the echo afterward, and no deposit on any carrier-flagged item so there is never a refund conversation.
- Saved the new-homeowner welcome packet idea to auto-memory and filed it on the board.

**What's live / deployed:**
- PRINT-READY on the Mac at ~/Desktop/Decker-Insurance/ : Decker-Menu-client.pdf (10 pages, everything Kathy sees, ends on the sign-off page) and Decker-Menu-internal.pdf (5 pages, meeting notes + objection sheet). Never print the full document as one job.
- Artifact: https://claude.ai/code/artifact/202f0985-2010-4533-a7ac-f98f9401ae72
- Source HTML: ~/Archive/Clients/Decker-Insurance/decker-options-menu.html
- Nothing deployed to any site this session. No code changed.

**Next up:**
- Print and take to the next Decker meeting, no date set. Queue a Sam Quisenberry video first; the "will AI Kathy look fake" question is only answerable by playing one.
- Ask Kathy whether Auto-Owners offers co-op advertising dollars.
- TWO OPEN CODE ITEMS on manitoubeachmichigan.com before a free listing is handed over: no Insurance category in LISTING_CATEGORIES, and SLOT_CAPS is empty so "top of category" is not enforced (the prep sheet's exclusivity answer relies on it). Board row filed as Today.
- Productize the realtor-branded new-homeowner welcome packet.

**Notes for other environments:**
- The August menu supersedes the July idea menu. The July SEO audit is still the evidence behind the Foundation section.
- Sam Quisenberry's videos live in ~/Archive/Clients/Sam-Insurance and are the proof-of-concept for AI Kathy.
- Re-render the PDFs with the playwright chromium headless shell and --print-to-pdf; the split is done by injecting a display:none rule, not by page ranges.