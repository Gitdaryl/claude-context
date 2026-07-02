## Session: 2026-07-02 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed recurring "can't drag-and-drop files between Finder windows" issue on the 48GB Mac (macOS Tahoe 26.5.1).
- Root cause: memory/swap thrash, NOT a Finder bug. Firefox had 61 tabs / 67 processes using ~23 GB; Chrome (2.8 GB) and Safari also running. Swap was maxed (~22 GB of 23.5 GB), WindowServer pegged ~40% CPU → dropped drag events. Reboots only held a few hours because Firefox restored all 61 tabs on launch.
- No third-party input tools (BetterTouchTool/Karabiner/Magnet) involved; three-finger-drag off; no Finder/WindowServer crashes.
- Killed runaway Firefox tab, relaunched Finder + Dock, quit Safari/Chrome/Firefox, cleared Firefox sessionstore files so the 61 tabs don't auto-restore.
- Result: free RAM 39% → 70%, swap draining, load 6.5 → 5.3.

**What's live / deployed:**
- Nothing deployed. Local machine cleanup only.

**Next up:**
- Confirm drag-and-drop works reliably going forward (should no longer need frequent reboots).
- Suggested: install Auto Tab Discard in Firefox, avoid running 3 browsers at once, keep tab count down.

**Notes for other environments:**
- User tends to accumulate 60+ Firefox tabs — this is the recurring cause of the drag-drop / slowness symptom on this Mac. Saved to auto-memory as mac-swap-thrash-dragdrop.