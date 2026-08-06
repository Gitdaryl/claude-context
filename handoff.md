## Session: 6 Aug 2026 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Built the Sunny Skies production standard as two locked-together documents, written as the owner/marketer rather than as spec sheets.
- **Editor Brief (13 pages):** defines the six-file kit per roof (hero 28-34s, ASMR 45-60s, 15s ad cutdown, 8s before/after wipe, 4:5 feed reframe, clean no-caption master) plus 3 frame grabs and an .srt, with the reasoning for every length. Locks specs (1080x1920 @30fps timeline, 4K sources, H.264 12-16 Mbps, -14 LUFS, safe zones 250/600/100px), creative direction, banned-technique list, music licensing split, camera-sorted folders, naming, SLA, paid-test scorecard.
- **Videographer Shot List (15 pages):** the capture side, specified as tightly as the edit side. Every shot has an ID (H1-H6 hooks, B1-B12 before, S0-S12 shoot day, A1-A7 after). Red IDs are mandatory. The IDs are the shorthand used in shoot notes and voice memos, so "no B6 on this one" is a complete report.
- Solved the missing-hook problem two ways: a hard rule that two hooks are in the can before the crew leaves site, plus a documented AccuLynx salvage path (pull full-res inspection photos, optionally AI-animate as a 2-3 sec start-frame hook) with hard limits: that job's own photos only, subtle motion only, nothing invented, hook slot only, always flagged. Framed as a repair, not a production method, with the real fix upstream (reps shoot 10 sec of H1/H5 at inspection).
- Added a matched-frame protocol (log drone altitude/heading/GPS, photograph the controller screen, mark ground positions in words) because the 8 sec wipe is entirely dependent on it and it is the highest performing paid asset.
- Carried the faceless crew-safety rule through both docs, plus a new rule: do not film unsafe work at all, rather than capture and cut it later.
- Both rendered to PDF via headless Chrome, verified page by page.

**What's live / deployed:**
- Nothing deployed. Five files in ~/Desktop/sunny-skies/:
  - Sunny-Skies-Editor-Brief-v1.pdf (13 pages, send to Isaac for sign-off)
  - Sunny-Skies-Videographer-Shotlist-v1.pdf (15 pages, page 14 is a printable field card)
  - EDITOR-BRIEF.md (working copy)
  - EDITOR-BRIEF.html and VIDEOGRAPHER-SHOTLIST.html (PDF sources)

**Next up:**
- Isaac approves the editor brief, then Yeti sends it to editor candidates.
- Run the paid test on one real job folder before any ongoing arrangement.
- Set editor rate per kit (not hourly) and the flat fee for the paid test. Both still blank.
- Pull AccuLynx full-res photos for the completed jobs that have no filmed hook and decide which are worth animating.
- Get reps shooting H1 and H5 on their phones at inspection so the gap stops recurring.

**Notes for other environments:**
- Both docs are US-spelled and em-dash-free. The HTML files are the source of truth. Re-render with headless Chrome --print-to-pdf, do not rebuild from the markdown.
- The shot IDs are shared vocabulary across both documents. If a shot is renamed in one, it has to change in the other.