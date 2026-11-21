## Session: 2026-11-20 ET (night)
**Environment:** Antigravity IDE
**What was done:**
- Sam Quisenberry portal (https://samquisenberry.vercel.app, code ~/Projects/sam-portal): new looks are a billed item. Yeti set the price: $24 for a set of 5 looks in a style, $24 for one custom look (data/look-pricing.json).
- Sam taps "Order for $24" for either kind; the request stores price and time agreed. Admin page has a "To invoice" line and a Billed tick.
- Clarified with Yeti: a style order is HeyGen's fixed look pack applied to Sam's face, not five looks from a description; nobody sees the five outfits before they are made.
- Built a 39-second help clip, "Watch: how new looks work", inside the Ask dialog. Narrator: ElevenLabs Chris (Yeti's pick, same as the On Point help clips). Made by node tools/help/record.mjs; rerun it when the dialog, price or wording changes.

**What's live / deployed:**
- samquisenberry.vercel.app with $24 pricing and the help clip (/help/new-looks.mp4 returns 200 video/mp4, range requests 206).
- Nothing sent to Sam. Nothing posted to Meta.

**Next up:**
- Yeti: watch the help clip (~/Previews/2026-11-20 Sam portal help clip (how new looks work).mp4); Claude cannot judge the voice by ear.
- Yeti: Show to Sam or Skip on the five winter-sweater looks. The clip shows all five as the example, so skipping one means a new take.
- Yeti: read the 11 scripts, then text Sam his link and tell him new looks are $24.
- Measure what one hand-made look costs in HeyGen credits on the first real custom order.
- Stage 2 not started: subtitles, b-roll, Sam previewing the finished video, Meta posting.

**Notes for other environments:**
- Look orders are invoiced from the admin page's "To invoice" line; they are not in YetiGroove Office yet.
- HeyGen plan credits: 1,765 (resets Dec 10). The help clip used ElevenLabs only (about 600 characters).