## Session: 2026-08-09 ET
**Environment:** Antigravity IDE

**What was done:**
- Yeti deleted footage from a 256GB microSD (DJI Osmo, card label OSMO) and emptied Trash
- Identified the previously purchased tool: Wondershare Recoverit (installed, v14.0.23.19)
- Unmounted card immediately to prevent overwrite, then took a byte-perfect raw clone via `dd` to ~/SD-Recovery/osmo.dmg (255,869,321,216 bytes, matches disk4 exactly)
- Ejected physical card; attached the image read-only as a virtual disk so all scanning happens against the clone
- Recoverit rejected the raw .dmg import, so worked around it by attaching the image as a virtual device
- Recoverit deep scan: 2658 files / 110.65 GB recovered to ~/SD-Recovery/recovered/
- Verified with ffprobe: ALL 300 recovered MP4s are unusable (no moov atom, wrong extents, sizes up to 7.5GB, duplicates)
- Wrote a custom exFAT parser to read deleted directory entries straight from the image
- Root cause found: FAT chains cleared on delete, AND DJI interleaves the main MP4 with its LRF proxy on disk, so every MP4 is fragmented. Confirmed cluster 359 holds a real ftyp/avc1 (LRF) only 77 clusters into MP4 0003's 1289-cluster range
- Recovered 258 DJI .THM/.SCR thumbnails (survived in MISC, outside DCIM) = visual manifest of every lost clip
- Extracted 269 stills (135 DNG + 134 JPG) directly from the image via contiguous-cluster extraction, all validated with ffprobe, 100% success

**What's live / deployed:**
- Nothing deployed. Local recovery work only.

**Key paths:**
- ~/SD-Recovery/osmo.dmg (raw clone, keep until footage question is settled)
- ~/SD-Recovery/exfat-extract/ (269 recovered stills, 3.1GB, verified good)
- ~/SD-Recovery/thumbnails/ (258 THM thumbnails of every deleted clip)
- ~/SD-Recovery/expected-clips.txt (manifest, 258 clips, Aug 5 13:51 to Aug 8 20:39)
- ~/SD-Recovery/recovered/ (Recoverit output, 111GB, video portion is junk, safe to delete)

**Next up:**
- Video still unrecovered. Fragmented + FAT cleared means content-based reassembly is required
- Options presented: Klennet Carver (Windows, purpose-built for fragmented video), professional recovery lab, or a custom reassembler attempt
- Awaiting Yeti's decision on which path
- Do NOT reuse the microSD card until this is settled

**Notes for other environments:**
- Only 100 MP4 directory entries survived, all dated Aug 8. The Aug 5 to Aug 7 clips have no surviving metadata, only thumbnails
- Reusable lesson: for any future card recovery, clone first with dd, mount the clone read-only, and never scan the physical card