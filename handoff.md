## Session: 2026-08-09 ET
**Environment:** Antigravity IDE

**What was done:**
- Yeti deleted footage from a 256GB microSD (DJI Osmo, label OSMO) and emptied Trash. Wanted the recovery app he'd bought previously
- Identified it as Wondershare Recoverit (installed fresh, v14.0.23.19)
- Unmounted the card immediately, then took a byte-perfect raw clone with `dd` to ~/SD-Recovery/osmo.dmg (255,869,321,216 bytes, matches disk4 exactly)
- Ejected the physical card and attached the clone read-only as a virtual disk, so every scan ran against the image
- Recoverit rejected the raw .dmg import; worked around it by attaching the image as a virtual device
- Recoverit deep scan returned 2658 files / 110.65 GB, but ffprobe showed ALL 300 MP4s unusable (no moov, wrong extents, sizes up to 7.5GB, duplicates)
- Wrote a custom exFAT parser to read deleted directory entries straight from the image
- RECOVERED: 269 stills (135 DNG + 134 JPG), extracted by cluster address, all validated with ffprobe, zero failures
- Recovered 258 DJI .THM/.SCR thumbnails from MISC (outside DCIM, so never deleted) = visual manifest of every lost clip

**Video diagnosis (not solved):**
- exFAT wiped the FAT chains on delete, so block ordering is gone
- Each MP4 is laid out as contiguous mdat + a moov index parked elsewhere on the card
- Scanned the full image and found 200 orphaned moov atoms, all unique sizes = 99 MP4s + 100 LRFs
- Matched every index to its clip by exact size, then CONFIRMED the match independently via mvhd creation timestamps (4h UTC offset vs filename, durations agree)
- Fragmentation is regular: 40 clusters (exactly 5MB) of MP4, then a ~23 cluster gap holding the LRF proxy, repeating
- Built a reassembler using the index as a validation oracle. It did NOT work. All 37 evening clips still fail to decode. Gap search logic is too weak; gap is likely variable, not a constant 23

**Key paths:**
- ~/SD-Recovery/osmo.dmg (238G raw clone, KEEP if pursuing video)
- ~/SD-Recovery/exfat-extract/ (269 verified stills + video attempts)
- ~/SD-Recovery/thumbnails/ (258 THM of every deleted clip)
- ~/SD-Recovery/expected-clips.txt (manifest, 258 clips, Aug 5 13:51 to Aug 8 20:39)
- ~/SD-Recovery/recovered/ (111G Recoverit output, video portion is junk, safe to delete)
- Working scripts in the session scratchpad: exfat parser, moov scanner, reassembler

**Next up:**
- Card is free to reuse. Yeti needs it for the Sunny Skies shoot tomorrow (Aug 10). The clone is byte-perfect so formatting costs nothing
- Video still unrecovered. The clips that mattered were 4:17pm into the night, Aug 8 (37 clips, 30.4GB)
- If resumed: the fix is a smarter gap search (variable gap, validate several consecutive samples per candidate rather than one)
- 499GB free on the Studio. Deleting ~/SD-Recovery/recovered/ reclaims 111GB before the shoot

**Notes for other environments:**
- Only 100 MP4 directory entries survived, all Aug 8. Aug 5 to Aug 7 clips have thumbnails only
- Reusable lesson: for any card recovery, clone with dd first, mount the clone read-only, never scan the physical card