## Session: 2026-10-03 ET
**Environment:** Antigravity IDE
**What was done:**
- DLYC previz: first visuals produced. All internal, nothing sent to Craig.
- Built a plan-projection pipeline: camera fitted to the Sep 15 beach photo (0010) against Wilson L.01 points, plan warped into the photo at lawn and terrace elevations, walls and steps drawn as 3D, then textured with Gemini 3 Pro Image. Geometry verified by overlaying projected wall lines on the render. Real building pixels pasted back.
- Tested converting Wilson's three L.02 SketchUp perspectives to photoreal. C1 (aerial) usable; C2 and C3 drifted badly. Gemini cannot lock drawing geometry.
- C1 finished per Yeti: sundial is a flat paver compass medallion (no gnomon), lake in background replaced with parking lot + trees, playground enlarged in place. Region-masked composites so nothing else changed.

**What's live / deployed:**
- Nothing deployed. Files on Desktop: `DLYC composites/` (BOARD_B_exact_landscape.jpg, BOARD_C1_aerial.jpg, C1_aerial_FINAL.png, scripts in `_scripts/`).

**Next up:**
- Ask Wilson (via Craig/Otis) for the SketchUp .skp behind L.02: exact geometry for any angle. Add to the unsent Craig/Otis email (board row "DLYC: ask Craig/Otis...").
- NAS offline (no reply on 10.0.0.130 or 10.10.10.2); power-cycle it to reach the drone frames for aerial plan overlays.
- Optional: fal.ai key at ~/.config/fal/key to try line-locked (canny/depth) rendering of the drawings.
- All Wilson perspectives show the 2025 placeholder boathouse, not the Victorian concept.

**Notes for other environments:**
- Yeti-Groove repo is public: the projection scripts were deliberately kept out of it.
- Wilson drawings carry a copyright notice; internal use only until permission.