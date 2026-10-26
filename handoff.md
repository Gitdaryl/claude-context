
### Addendum 4 (Oct 26 evening, IDE): Yeti voice v2 + voice library
- Yeti recorded the 2-min closet read. Built the new HeyGen clone **Yeti v2 `ddfbbb70a02d4538b1244d208d0279bb`**, with noise removal off. Yeti approved the **orca** engine by ear, so the old 042720d3 is retired (boxy).
- All 10 launch-week lines (L-02, CL-05, CL-10) are voiced with v2 orca: `~/Projects/mb-social/banks/classifieds/audio/lines/`. Nothing left to record except L-01 (real footage).
- HeyGen plan premium credits ran out Oct 26. TTS now runs on the API wallet (`HEYGEN_API_KEY` from ~/.config/heygen-api-key).
- **Voice library:** `~/Clients/yeti-groove/media/voice-library/` (vlib.py find/scan/cut/list). 365 takes are indexed across MB, Holly and OnPoint with whisper text and word timings. Run `find` before generating any VO and `scan` after. A nightly launchd scan was not installed (auto-mode blocked it; it needs Yeti's OK).
- Open: re-voice the Halloween reel's Yeti lines with v2 before Oct 31, if it isn't posted yet.