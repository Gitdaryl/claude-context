## Session: 2026-10-09 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD measured-estimate handoff worked through. Google Cloud project "OnPoint JD" (onpoint-jd) created under yetigroove.com; Solar API + Geocoding API enabled; key restricted to those two, saved in ~/Projects/on-point-jd/.env.solar (gitignored, verified working).
- Built tools/solar_validate.mjs (measured squares vs actual vs live /estimate formula, CSV + summary, cached) and tools/solar_view.py (aerial picture with numbered roof faces, pitch colors, downhill arrows). Data lives in solar-test/ (gitignored).
- Yeti's house: Google measured 28.9 sq (31.8 whole building), porch = face 5, separate garage 11.8 sq via a second lookup. Trees hide one corner. Per-face pitch noise about 1/12.
- Confirmed from Google docs: Solar area is sloped surface (no pitch multiplier). Maps Platform Terms 3.2.3(c) forbid tracing outlines or building 3D models from Google imagery.
- Reviewed FirstMate (1m8.ai): $7 human-traced roof reports (Manila/Nepal technicians, AI-assisted, 4 hr). Decision direction: buy reports, don't build; drone for inspection photos, not measuring.
- Agreed funnel: keep /estimate as is; inspection booking promises drone photos + measured roof report; Google measurement goes to Devon only; Devon orders the $7 report after the appointment is confirmed. No free reports for contact info.

**What's live / deployed:**
- Nothing deployed. Google Cloud project + key are live. tools/solar_validate.mjs, tools/solar_view.py and the .gitignore change are UNCOMMITTED in ~/Projects/on-point-jd (crm/ is untracked from another session, leave it).

**Next up:**
- Yeti: order one $7 FirstMeasure report on his house at app.1m8.ai/portal and send the PDF to compare.
- Devon: ~20 past jobs with address + actual squares; what measuring tool they use and what it costs.
- Then: build the inspection-booking step (board row, Backlog). Check the Solar API caching window before storing measurements with leads.

**Notes for other environments:**
- Board rows filed: key (Done), Solar validation (Waiting on Devon), build vs buy measurement (Backlog, leaning buy), $7 test report (Today, Daryl), inspection booking build (Backlog).
- A public GitHub repo (jackholt647/firstmeasure) appears to be FirstMate's own code; only service connections were looked at, nothing copied.