## Session: July 22, 2026 ET
**Environment:** Antigravity IDE
**What was done (8580 Marr Hwy listing site, continued):**
- Address corrected to Manitou Beach, MI 49253 across the site (Mitch confirmed; Zillow's record was right, Onsted is the informal area name). Aerial captions re-edited by Yeti and redeployed, verified byte-for-byte live
- Facts row filled from Zillow record: 4 bed, 4 bath, 2,025 sqft, 2.17 acres, built 2003. Price hidden until Mitch sets it
- Kitchen copy de-risked: "breakfast-bar island with stainless appliances" (counters likely laminate, not granite)
- Basement details added: full kitchen, half bath, large entertaining area, kids game nook, loads of storage
- Share button in hero (native share sheet on mobile, copy-link on desktop) + OG tags fixed with absolute image URL; preview verified
- Mobile audit passed; added swipe navigation in lightbox, sticky bar hides under lightbox

**What's live / deployed:**
- https://irish-hills-realty.vercel.app/8580-marr-hwy fully current and verified

**Next up:**
- MLS photo export (waiting on Mitch's MLS photo cap; will cut ordered 2048px JPEGs to Desktop)
- List price from Mitch
- CubiCasa floorplan due 7/23: set floorplanImage in src/data/properties.js
- Vertical video: set videoUrl when cut
- Prime the URL in Facebook Sharing Debugger before Mitch shares (new-domain Messenger quirk)
- Custom domain decision

**Notes for other environments:**
- Photos carry a 1-year immutable cache header; anyone who viewed the old aerials today needs a hard refresh to see the new captions. New visitors are unaffected
- drone-3 has a faint ghost of the old caption behind the new text; cosmetic, Yeti's call whether to polish