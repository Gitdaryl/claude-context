## Session: July 21, 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Validated the ULM40 newsletter promo flow end to end for Joe Profit's Never Broken store (joe-profit.vercel.app / joeprofitneverbroken.com)
- Found and fixed two blockers: (1) promo code field was digital-only, now enabled on all five editions; (2) physical checkout (paperback/hardcover) had been 500ing since May 18 due to an unsupported Stripe Link parameter in api/checkout.js, removed it
- Verified live: all five editions create checkout sessions; headless screenshot confirms "Add promotion code" on hardcover checkout ($31.95 + $7.97 shipping)
- Updated site copy in src/App.jsx (4 spots) to Joe's own wording: "first Black athlete to play football at a predominantly white college in Louisiana" (per his July 20 note), Gulf States Conference kept as secondary detail
- Wrote newsletter blurb (full + short versions) for SJ at ULM (tuohy@ulm.edu)

**What's live / deployed:**
- Joe-Profit repo, 3 commits pushed to main and auto-deployed via Vercel: promo codes on physical checkouts (40bb348), physical checkout 500 fix (ed486b1), "first" claim wording (085baae)

**Next up:**
- BLOCKER for the newsletter: the ULM40 coupon exists in Stripe (10% off, expires Feb 14, 2027) but has NO promotion code attached, so customers cannot type it at checkout. Yeti must add it: Stripe Dashboard > Coupons > ULM40 > Add promotion code > code ULM40. One-minute task.
- Optional: disable Stripe Link wallet in Dashboard > Settings > Payment methods if the shipping-bypass concern still stands (per-session disable is not supported by the API)
- Naming optics: code is ULM40 but the discount is 10%; consider whether 40 (Joe's jersey number) needs a word of explanation in the newsletter or rename to ULM10
- Repo has unrelated uncommitted changes (api/generate-comp.js, api/webhook.js, deleted public/images/Joe_Joe.png) left unstaged, from a previous session

**Notes for other environments:**
- Joe's canonical "first" wording is now in auto-memory (joe-profit-first-claim-wording); use it in all Joe Profit copy on every platform
- Newsletter blurb delivered in this session's chat; ULM sends the alumni newsletter around end of July