## Session: Oct 15 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Transcribed + frame-checked the YouTube video "How I Rank ANY Service Business #1 on Google Within 7 Days". It is a rank-and-rent operator (fake listings, gift-card reviews). Kept the real parts: keyword in the GBP name (only as the real-world name), competitor check per town, fill every GBP section, keyword-mentioning reviews (asked honestly, never paid).
- Built ~/.claude/tools/map-pack (scan.mjs + report.py): headless Google Maps top-20 per phrase per town, scored with the video's 40/40/10/10 weights.
- OnPoint baseline (on-point-jd/seo/MAP-PACK.md + seo/scans/2026-10-15/): "No reviews" on Google, outside the top 20 in all 33 searches. In 9 of 11 towns a company with 24 or fewer reviews and "Roof" in its name holds a top-3 spot ("Toledo City Roofing Experts", 4 reviews, top 3 in Toledo/Oregon/Northwood/Rossford).
- Thank-you + follow-up review emails now ask customers to mention the job and their town (onpoint-office f259b5b, on-point-jd site/api/lib/thanks.js).
- GBP Products paste kit (9 products with UTM links) in seo/MAP-PACK.md. GBP website link already carries utm_campaign=gbp (checked live).

**What's live / deployed:**
- onpoint-office f259b5b pushed to main.
- on-point-jd: review line + seo/ folder (commit pending at time of writing, see git log).

**Next up:**
- Jay: OK to rename GBP to "On Point JD Roofing & Snow Removal" (trade name + stationery first) and the list of every customer since 2022 for review asks (both on the ASK JAY board page).
- Yeti: paste the Products kit with drone photos.
- Re-scan Nov 15 2026; run the scan for Sunny Skies / Mitch bar / Spotted Owl / Yeti Groove.

**Notes for other environments:**
- Never buy or gift-card reviews (FTC 16 CFR 465, up to $51,744 per violation); ask every customer, not just happy ones.
- webp-sweep on on-point-jd takes 10+ minutes (3 GB in social/).