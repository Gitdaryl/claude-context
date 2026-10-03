
## Session: 2026-10-03 ET
**Environment:** Antigravity IDE
**What was done:**
- Checked the roofing "instant estimate" ad Yeti saw: it is a QuinStreet lead-sale funnel, no real price
- Built OnPoint JD /estimate roof price calculator (tools/build_pages.py estimate(), site/assets/estimate.js, CSS, lead.js estimate field), phone price bar, preview-only rate tuner

**What's live / deployed:**
- Vercel PREVIEW only: https://onpointjd-i7nug355i-daryls-projects-5d48a4f8.vercel.app/estimate (SSO). Not on prod, not committed.

**Next up:**
- Get Jay's real rates (per square basic + full Atlas, steep adders, 2nd layer, minimum, decking per sheet), set ESTIMATE_RATES, then link from /roofing + nav, drop noindex, add to sitemap, deploy prod
- Decide Sunny Skies optics of public pricing

**Notes for other environments:**
- $150/sq is a placeholder; do not publish until Jay's numbers are in