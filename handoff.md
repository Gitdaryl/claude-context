
## Session: 2026-10-07 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD yard sign print review: QR decodes from the press PDF (even 10 dpi, angled/blurred), /ys 302 -> home with yard-sign UTMs, source sticks for the visit; PDF is vector, fonts embedded, 24.25x18.25 with bleed
- Measured reading distances: phone 1.83in letters (~55 ft), top band 1.1in (~34 ft), FREE INSPECTIONS 0.65in (~20 ft)
- Added yard sign variant B "CALL OR TEXT" (print/build.mjs yardSign('calltext')); A is unchanged pixel for pixel; compare at print/out/compare-yard-sign.png
- README: flutes vertical for H-stakes, same PDF both sides, variant B row

**What's live / deployed:**
- Nothing deployed. build.mjs + README + new out/ files are uncommitted in on-point-jd

**Next up:**
- Yeti picks A or B; B only after a test text to 567-708-8001 is seen
- Door hanger tear-off says $500 OFF, site runs $1,000: reconcile OFFER in print/build.mjs before hangers print
- Optional: point /ys at /estimate (board row filed); Twilio not configured on onpointjd (health twilio:false), lead alerts go by email only

**Notes for other environments:**
- Calls from the yard sign are not attributed; only QR scans and web forms are