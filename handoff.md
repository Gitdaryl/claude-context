
## Session: 2026-11-11 ET
**Environment:** Antigravity IDE
**What was done:**
- Joe Profit shop: buyers can now order 1-10 print copies (was hardcoded to 1). Quantity picker, Stripe quantity, qty in Joe/buyer emails and admin orders.
- Verified live: Stripe shows Qty 2, $71.87 total for 2 hardcovers.

**What's live / deployed:**
- joeprofitneverbroken.com commit 082796f

**Next up:**
- Joe asked about location-based shipping + sales tax: not built. Needs decisions (flat vs per-book shipping; nonprofit tax status / Stripe Tax).

**Notes for other environments:**
- Shipping is a single flat $7.97 Stripe rate per order regardless of book count.