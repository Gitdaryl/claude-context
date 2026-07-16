
## Session: July 16, 2026 ET (later)
**Environment:** Antigravity IDE
**What was done:**
- Built out /mens-club from the club's real 2026 documents (yearly sponsor letter + golf brochure)
- Replaced invented sponsor tiers ($2500/$1000/$500/$100) with the REAL program: $130 Yearly Sponsor + $50 Golf Hole Sponsor, May 1 deadline, EIN 46-4087550, checks to The Devils Lake & Round Lake Men's Club, 3171 Round Lake Hwy
- CRITICAL FIX: sponsor form was silently discarding submissions (no endpoint). New /api/mens-club-sponsor persists to Vercel Blob (intake/mens-club-sponsors/) BEFORE emailing via Resend; notifications go to admin@yetigroove.com; GET on the endpoint = health check
- Golf outing buildout: $300/foursome, Sign Up Your Team + Sponsor a Hole ($50, mailto jborton1031@gmail.com) cards, Yeti cooler prize, course address/phone
- 2026-2027 Yearly Sponsors thank-you wall, all 48 names from the brochure
- Added Halloween Hot Dog Roast event (AI-generated candid photo, compressed 183K); programs now include Catherine Cobb DV Center, Kiwanis hams, Lakes Preservation
- Verified live end-to-end: health check green, test submission persisted + both emails sent

**What's live / deployed:**
- Commit fe9a6e5 on main, deployed to manitoubeachmichigan.com (rebased over Cowork's 12f5168)

**Next up:**
- Yeti to supply: NTA + Scotty's Body Shop logos for golf sponsor cards (text-only now); a real Halloween Hot Dog Roast photo to replace AI one when available
- Decide if club officer (jborton1031@gmail.com) should ALSO get sponsor notification emails (one-line change in api/mens-club-sponsor.js)
- Delete the TEST sponsor blob when convenient (intake/mens-club-sponsors/, name starts with TEST)

**Notes for other environments:**
- Men's Club sponsor submissions now land in Vercel Blob intake/mens-club-sponsors/ + email admin@yetigroove.com; anyone handling club admin should watch for those emails and follow up within 2 business days (that is what the site promises)