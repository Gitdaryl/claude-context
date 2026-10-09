## Session: Oct 9 2026, ~11:45 ET
**Environment:** Antigravity IDE
**What was done:**
- Answered "why are ZappyCards so expensive vs a QR": $15 to $30 for a ~$0.50 NFC chip holding one URL; tap beats QR on effort, QR wins on reach; the real value is the crew asking at the end of the job.
- Built OnPoint JD's own tap-to-review cards: /r/<id>/tap (chip), /r/<id>/qr (back), /r/<id> (link) redirect to the Google review form and count per card; /desk shows a Review cards panel.
- Print files: CR80 portrait card per id (jay, devon, crew1 to crew3) in print/out, ordering + chip-writing steps in print/README.md.
- Tests: tools/test_review_cards.mjs (41/41 suite passes). Board rows filed (Done, Today for Yeti, Backlog productize).

**What's live / deployed:**
- onpointjd.com/r/... live (commit bfeb508, Vercel deploy READY). /review and other short links unchanged.

**Next up:**
- Yeti: order 5 printed NFC badges from GoToTags (~$53, about 1 week), write chips with NFC Tools (do not lock), tap Jay's card and confirm /desk shows 1 tap. That tap is the only unverified piece (prod Blob write).
- Brief Jay + Devon: ask every customer, no 5-star ask, no incentive.

**Notes for other environments:**
- Card ids live in CARDS in site/api/lib/track.js. Lost card: set off: true and push; replacement gets a new id (jay2).