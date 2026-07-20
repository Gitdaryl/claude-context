## Session: July 20, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Validated the ULM40 promo flow for Joe Profit book purchases end to end
- Found ULM40 exists in Stripe only as a coupon (10% off, redeem by Feb 14, 2027 11:59pm ET) with NO promotion code attached, so customers had nothing to type at checkout. Creating the promotion code was blocked by permissions; Yeti must add it in the Stripe Dashboard (attach code ULM40 to coupon vnPQwIrY)
- Found and fixed a two-month-old bug: physical (paperback/hardcover) checkouts have 500'd since May 18 because of an unsupported Stripe param (payment_method_options.link.display_preference). Removed it
- Enabled allow_promotion_codes on all editions (was digital only)
- Verified live after deploy: all 5 editions create checkout sessions; headless screenshot confirms the Add promotion code button on hardcover checkout
- Wrote ULM alumni newsletter blurb for the offer

**What's live / deployed:**
- Joe-Profit repo: commits 40bb348 + ed486b1 pushed to main, auto-deployed on Vercel (joe-profit.vercel.app / joeprofitneverbroken.com)

**Next up:**
- Yeti: create promotion code ULM40 in Stripe Dashboard (Products > Coupons > ULM40 > Add promotion code), then test by applying ULM40 on any checkout
- Optional: rename to ULM10 (ULM40 reads like 40% off but it is 10%); if 40 is Joe's jersey number, keep and say so in the blurb
- Optional: disable Link wallet in Stripe Dashboard payment method settings if the shipping-bypass concern is still real

**Notes for other environments:**
- Physical book sales were dead May 18 to July 20; if anyone reports "couldn't buy the book," this was why