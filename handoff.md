## Session: September 2, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Built a resume and cover letter for Erin Nicole Young (Yeti's wife) applying for the GSRP Third Person Caregiver position, Onsted MI
- No paid work history, so the resume is skills-based and led by real caregiving: in-home caregiver for a hospice dementia patient, full-time parent, Meals on Wheels, Hudson Museum, school/church volunteering, youth activity leader
- Included her published artwork (international art books and children's books) as a classroom-art differentiator
- Both documents fit on exactly one page each, verified by parsing the rendered PDF page count, not by eye
- Reference letters already in hand from Sherry Vogel and Amanda Taylor

**What's live / deployed:**
- Nothing deployed. Files at ~/Desktop/erin-gsrp/: resume.html, resume.pdf, cover-letter.html, cover-letter.pdf, FILL-IN-FIRST.md, render.sh

**Next up:**
- Erin fills the yellow-highlighted blanks (dates, child count, school name, artwork titles, hospice employer, Amanda's contact), then run render.sh
- Book Pediatric CPR / First Aid class so the resume can say "scheduled for [date]"
- Decide the third reference: hospice supervisor or Meals on Wheels coordinator is strongest

**Notes for other environments:**
- Chromium headless print-to-pdf on this Mac lives at ~/Library/Caches/ms-playwright/chromium-1223/chrome-mac-arm64/, and it ignores nothing important, but the usable page height is ~10.0in. Verify page count by parsing /Count in the PDF; mdls returns stale metadata.