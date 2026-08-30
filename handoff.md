## Session: Aug 30 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Wieners on the Water auto-pin had already fired at 12:30 on a rain day; pulled the pin via the checkout action (Facebook post from 12:30 left standing, needs a manual comment/delete)
- Built home-screen install for food truck vendors: api/truck-manifest.js (per-truck tokenized manifest), install card + manifest injection in FoodTrucksPage vendor mode, new truck-pin icons, and both weekend reminder texts now tell vendors to install it
- Planned "The Lineup Engine" with Yeti: lineup as an attribute of any event, known names auto-pin after a confirm text, unknown names become approved outreach leads, plus a reassignable approver role. Plan artifact: https://claude.ai/code/artifact/1edde638-bc43-46b9-a8f8-c0cd77b9c008
- Built step one of that plan: lineup capture on every event type (api/lib/lineup.js, submit-event.js, event-edit.js, events.js, event-detail.js, LineupPicker.jsx, EventDetailPage "Who's there" block). Added Lineup Trucks / Entertainment / Vendors to the Events DB in Notion.

**What's live / deployed:**
- Both commits pushed to Gitdaryl/Manitou-Beach main and deployed
- Verified live: truck manifest endpoint, icon assets, lineup round-trip through Notion, and the "Who's there" block rendering on a real event page (test data written and then cleared)

**Next up:**
- Confirm-to-pin for known trucks (geocode the venue, morning-of text, reply Y drops the pin)
- Reassignable approver role: Notion table, magic link per request, authority checked at click not at send, escalation to backup then Yeti, decision log
- Unknown lineup names into the outreach queue with drafted pitches held for approval
- Rain-day skipDates + weather gate on the truck auto-pin (still not written)
- Entertainment as its own directory, only after the truck loop is proven

**Notes for other environments:**
- Key finding: a lineup could not be represented before today because Vendor Reg Enabled was only set for eventType 'vendor_market', a switch, so event types were exclusive
- Design rule agreed: an organizer naming a vendor is a claim, not a fact. Publish as expected, hold the pin until the vendor confirms. Nothing auto-sends to a business we found ourselves.