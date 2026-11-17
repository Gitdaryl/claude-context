
## Session: Nov 16 2026, ~10 pm ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office, branch money-split (HEAD dde1ed6, fast-forwards onto live a3a4286): Anderson Roofing / Sunny Skies / Joe as sub companies; Add receipt (AI reads photo, now Sonnet) vs Add a cost; crew add + see own receipts (Sent to OnPoint, duplicate warning); Fill New Job from a work order PDF; change a sent material order (rev 2 CHANGED PO, old kept), returns, add items; money split (Devon price + materials, Kyle materials only, Jay/Linda/Daryl everything; app only records what Holt/Anderson paid).
- Verified: tsc clean, 1750 tests pass (4 pre-existing failures), browser click-through of 8 flows, real AI on the Menards receipt ($109.45) and both real work orders (every field right).
- Jay answered the money questions by text; Sunny Skies is still operating (memory corrected).

**What's live / deployed:**
- Nothing. Ship = `npx supabase db push` (5 migrations 20261116000000..400000), then ff-merge money-split to main and push.

**Next up:**
- Yeti ships; as Jay turn on Kyle "Can see job costs"; live test: Menards receipt on Bob's job + a work order upload from a phone.
- Thursday: Teams A/B/C after Yeti's change. Atlas filing card waits on Devon (PRO+?). Northwood permit to file; who owns 567-694-2888.

**Notes for other environments:**
- Board rows filed under On Point JD (ship row is in Today). Don't rebuild these features; they're on money-split.