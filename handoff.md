## Session: Aug 9 to 11 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Recovered deleted footage and photos from a 256GB microSD (DJI Osmo, exFAT, Devils Lake Aug 5 to 8). Files were deleted in Finder with Trash emptied.
- Took a byte exact 238GB clone (`~/SD-Recovery/osmo.dmg`) before touching anything. Card was mounted read-write at the time, so unmounting first mattered.
- Wondershare Recoverit was the software Yeti had bought previously. Its "Disk Image" import rejects a raw 238GB clone; workaround is `hdiutil attach -readonly` so it shows up as a normal drive.
- **Photos: 436 unique recovered and verified.** 269 read straight from exFAT directory entries, plus 167 only Recoverit found. Checked before deleting Recoverit's output, which is why those 167 were not lost.
- **Video: 12.4 minutes of post 16:00 footage across 38 clips.** 20 clips at 96 to 100%, 6 partial, 12 lost.
- Wrote a custom repair pass after diagnosing the real problem: DJI stores `mdat` and `moov` non-adjacently, video in fixed 5MB chunks with the LRF proxy woven between. Scanned the image for all 200 orphaned `moov` atoms, matched each to its clip by exact size, verified independently via `mvhd` timestamps, then reassembled fragment by fragment using each clip's own index as a validation oracle.
- Repair beat Recoverit on 9 clips, adding 203 seconds of footage. Biggest wins: 0233 15% to 72% (228s clip), 0243 3% to 73%, 0241 12% to 67%.
- Everything mirrored to NAS at `/Volumes/personal_folder/OSMO-recovery-2026-08/`.

**What's live / deployed:**
- Nothing deployed. Local and NAS only.
- `~/SD-Recovery/README.md` documents the whole method and folder layout.

**Next up:**
- `sudo rm -rf ~/SD-Recovery/recovered` to reclaim ~251GB. Root owned so it needs a password.
- Once `osmo.dmg` finishes copying to NAS and size is verified, the local 238GB copy can go too. Keep the NAS copy, the card is being reused for Sunny Skies.
- The 12 lost clips are all long ones. If ever worth revisiting, the image on the NAS is what to work from.

**Notes for other environments:**
- Yeti's Recoverit licence works. Grant it Full Disk Access or it cannot read raw devices.
- General lesson worth keeping: never scan a card directly, clone it first, then attach the clone read only. Also validate recovered video with `ffprobe`/`ffmpeg` rather than trusting that a file exists or that a player seems to open it.