## Session: 2026-08-25 ET
**Environment:** Antigravity IDE

**What was done:**
- Rebuilt the entire sound FX library from a NAS spaghetti ball into a local, categorised, searchable tree at `~/SFX` (34.5GB, 9,350 audio files)
- Diagnosed the real problem: the library was never badly named, it was never INDEXED. Ocular pack (bought, left zipped) was already full UCS-compliant.
- Extracted 47 Ocular packs (26GB of zips) + 18 loose zips to local SSD, stripped __MACOSX/.DS_Store junk
- Converted 99 .wma files to WAV (Resolve cannot reliably read WMA); ffmpeg, 99/99 success
- Split the flat 4,122-file `SFX lots` folder into categories using its own CATEGORY- filename prefix
- Merged ~50 misc personal folders into ONE unified category namespace (Animal Trax 01/02 + AT 04 + 6003 Birds + Nature creatures all became ANIMAL/734)
- Keyword-classified ~690 files from grab-bag folders (soundfx, 100-free-sfx, The Super Single Vol 1+2, Other, Other 2) per-file
- Deduped: only 51 exact duplicates found (0.02GB). Predicted 15-30%, actual 0.5%. Library was clean, just unsearchable.

**What's live / deployed:**
- `~/SFX/01_Libraries/Ocular/` - 47 categories, UCS-named WAV, untouched vendor metadata
- `~/SFX/02_Personal/` - 118 category folders, unified namespace
- `~/SFX/_INBOX/` - landing zone for new downloads, rule is nothing leaves unnamed
- `~/SFX/_DUPES/` - 145MB quarantine (51 dupes, 99 original WMAs, 19 non-audio) + reorg-manifest.tsv with all 5,925 original paths
- NAS `/Volumes/Production/Sound FX` COMPLETELY UNTOUCHED, read-only source. Nothing deleted anywhere in this job.

**Next up:**
- Install Soundly or Resonic Player, point at `~/SFX` (needs GUI, blocked on Yeti). Soundly reads UCS natively and drags straight to Resolve timeline. Verify Soundly's local-library indexing tier/pricing first, unverified.
- Review `~/SFX/02_Personal/_UNSORTED` (158 files, 2.7%) by ear. Names too ambiguous to classify (Zip1.mp3, give up.mp3, Catches 1.mp3)
- Spot check then delete `~/SFX/_DUPES` when satisfied
- Decide whether to mirror the organised `~/SFX` back to the NAS as the new master

**Notes for other environments:**
- Do NOT load SFX into the Resolve Media Pool, that DOES bloat projects. The Fairlight Sound Library is a separate global DB and does not, but is slow to scan. Best path is an external browser dragging into the timeline.
- macOS gotcha hit this session: filesystems are case-insensitive, so `Scrape/` and `SCRAPE/` are the SAME folder. A merge script moving files between them silently fails. Cost 63 files temporarily, caught by an integrity count, restored.
- macOS now ships `openrsync`, which does NOT support `--info=progress2`. Plain `rsync -a` works.
- `unzip` returns exit code 1 for harmless warnings on Windows-made zips (backslash paths). Do not treat exit 1 as failure.
- Scripts kept at the session scratchpad: unpack-sfx.sh, dedupe.sh, unify.sh. The keyword classifier in unify.sh is reusable for the Sunny Skies 10-sec clip library and footage-indexer.