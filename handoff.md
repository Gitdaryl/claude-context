## Session: 2026-06-02 AEST
**Environment:** Antigravity IDE

**What was done:**
- Built `/raffle` page - carnival-themed prize prediction wheel for LLLC Summerfest
- Carnival aesthetic: dark tent background, gold pennant bunting, marquee lights ring around wheel, gold pointer, ticket-style result card
- 11 raffle baskets wired with photos from `public/images/ladies-club/Festival-raffle/`
- Basket photos display in result card (white bg, object-fit contain, 160px)
- Share prediction via Web Share API or clipboard copy
- Added `embed` prop to RafflePage (strips navbar/footer/padding for inline use)
- LadiesClubPage: compact teaser card between festival map and sponsor tiers
- Teaser opens full-screen modal popover rendering RafflePage component directly (not iframe)
- Modal sits below navbar (paddingTop: 72px)
- `/raffle` standalone URL still works for sharing on social/SMS

**What's live / deployed:**
- manitoubeachmichigan.com/raffle - standalone page
- manitoubeachmichigan.com/ladies-club - teaser card + modal at bottom of events section

**Next up:**
- LLLC to share /raffle link on Facebook/socials as Summerfest hype
- Prize wheel sponsor version (vendor deals, QR redemption) - spec at specs/prize-wheel-demo-spec.md - deferred until pitch validation

**Notes for other environments:**
- All 11 basket photos committed to repo under public/images/ladies-club/Festival-raffle/
- RafflePage accepts embed={true} prop OR ?embed=true URL param