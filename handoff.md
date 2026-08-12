## Session: Aug 9 to 12 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Recovered deleted footage and photos from a 256GB microSD (DJI Osmo, exFAT, Devils Lake Aug 5 to 8). Deleted in Finder with Trash emptied. Footage is 3840x2160 at 59.94fps HEVC.
- Cloned the card first (`~/SD-Recovery/osmo.dmg`, 238GB, byte exact) and worked only from the clone.
- **Photos: 436 unique, all verified.** Effectively complete.
- **Video: 126,129 of 128,076 frames = 98.5%. 35.1 minutes across 37 clips.** Only clip 0227 unrecoverable (no surviving directory entry). For scale, the first attempt yielded 12.4 minutes with many clips at 0%.
- Wondershare Recoverit (Yeti already owned it) got the filenames right but produced 300 unplayable files. Root cause: DJI writes `mdat` and `moov` non-adjacently and fragments the video with the LRF proxy interleaved, so any naive carve yields a file with no index at all.
- Custom rebuild: scanned the image for all 200 orphaned `moov` atoms, matched each to its clip by exact size (confirmed via `mvhd` timestamps), then reassembled cluster by cluster using each clip's own index to validate HEVC NAL chains.
- Three things made it work: detect fragment length rather than assume it (lengths vary 18 to 87 clusters; a fixed guess produced a convincing but false "short clips recover, long clips are dead" pattern), require 4 consecutive samples to validate, and roll back to where the failing sample starts rather than by one cluster (that last one was causing one dropped frame at every fragment boundary, ie. the stutter).
- Remaining gaps filled with ffmpeg `minterpolate` at full 4K. Verified: clip 0217 went from 22,728 to 23,016 of 23,017 frames.

**What's live / deployed:**
- Nothing deployed. Local plus NAS at `/Volumes/personal_folder/OSMO-recovery-2026-08/` (323GB): `video-final` (37 native clips), `video-smooth-4k` (37 interpolated), 436 photos, 258 thumbnails, previews, notes, and the verified 255.9GB card image.
- `~/SD-Recovery/README.md` documents the full method including what did not work.

**Next up:**
- `sudo rm -rf ~/SD-Recovery/recovered` reclaims ~251GB (root owned, needs password). Local `osmo.dmg` can also go, 238GB, since the NAS copy is verified. Keep the NAS copy: the card is being reused.
- `video-good/` on the NAS (28GB) is a superseded intermediate set, safe to delete whenever.
- Yeti to check `SMOOTH-4K/` for smearing on fast water spray. Interpolated frames are invented, so if any clip looks wrong the `FINAL/` version is untouched and can be redone gently or retimed in Resolve.

**Notes for other environments:**
- Recoverit needs Full Disk Access to read raw devices, and its "Disk Image" import rejects a raw dd clone. Attach with `hdiutil attach -readonly` so it appears as an ordinary drive.
- Lesson worth keeping: verify recovered video by counting decoded frames against expected, never by "the file exists" or "a player opens it". Also check inside a tool's output before deleting it; Recoverit's junk folder held 167 photos nothing else found.
- `caffeinate -dims` blocks display sleep. Use `-ims` for long unattended jobs on a machine in a bedroom.