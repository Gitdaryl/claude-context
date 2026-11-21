## Session: 2026-11-20 ET (late evening)
**Environment:** Antigravity IDE
**What was done:**
- Sam Quisenberry portal (https://samquisenberry.vercel.app, code ~/Projects/sam-portal): new looks are now a billed item. Yeti's decision: a style pack costs 50 HeyGen credits, more than a reel, so it must be billable so it is not abused.
- Prices in data/look-pricing.json: style pack (5 looks) $40, hand-made look $25 as the usual figure. These are Claude's recommended numbers, built in as the default; Yeti asked what a real price should be and has not confirmed them yet.
- Style pack: Sam sees "5 new looks in this style: $40" and the button "Order for $40". The server refuses an order that does not carry the current price and stores price + time agreed.
- Made-to-order look: Yeti sets a price under Admin on the request, Sam taps "OK, make it for $X" (or Yeti taps "Sam said OK"). Re-pricing cancels an earlier OK.
- Admin page: "To invoice: $X for N look orders" line and a Billed tick per request.
- Watcher texts now say whether it is a paid style order or a look that needs a price, and text again when Sam agrees to a quote. It will not auto-start a pack without a price agreement.

**What's live / deployed:**
- samquisenberry.vercel.app redeployed with pricing (verified: both keys return the prices, an unpriced style order is refused, Sam still sees 10 looks, 11 draft rows, 0 requests).
- Nothing sent to Sam. Nothing posted to Meta.

**Next up:**
- Yeti: confirm or change $40 / $25 before texting Sam his link.
- Yeti: Show to Sam or Skip on the five winter-sweater looks (trial, not billed), read the 11 scripts, then text Sam his link.
- Tell Sam new looks are a paid add-on (not in the Nov 13 terms email).
- Stage 2 not started: subtitles, b-roll, Sam previewing the finished video, Meta posting.

**Notes for other environments:**
- Look orders are invoiced from the admin page's "To invoice" line; they are not in YetiGroove Office yet.
- HeyGen plan credits: 1,765 (resets Dec 10).