## Session: 2026-08-17 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed "NAS access is super slow" on the 48GB Mac. The NAS was not at fault.
- Measured the NAS clean on every axis: 10GbE link active, 0.46ms latency to 10.10.10.2, 0% packet loss, 0 NIC errors on en0, 336 MB/s sequential read, instant directory listings, link idle at 3.6 MB/s. Spotlight indexing already disabled on all three shares; Time Machine targets the local disk, not the NAS.
- Real cause was memory exhaustion: ~65 MB free RAM, swap 26.5 of 27.6 GB used, 24 GB in the compressor, memory pressure level 2 (warn), Firefox at 80 processes / 15.9 GB.
- Quit Firefox cleanly and moved sessionstore files out of the profile so tabs would not auto-restore and refill swap.
- Result: free RAM 65 MB to ~17 GB, pressure level 2 to 1 (normal), compressor 24 GB to 15 GB, swap file shrank 27.6 GB to 20.5 GB.
- Updated auto-memory note `mac-swap-thrash-dragdrop` to generalize beyond the July drag-and-drop symptom, and refreshed its MEMORY.md index line.

**What's live / deployed:**
- Nothing deployed. Local machine maintenance only.

**Next up:**
- Optional: NAS sequential read tops out at 336 MB/s, about 27% of 10GbE line rate. Likely the array's own ceiling or SMB signing overhead. Worth investigating separately if Resolve scrubbing off Sunny Skies feels sluggish. Not related to today's issue.
- Firefox tab backup sits at `~/.claude/backups/firefox-session-2026-08-17/` (13 MB). Delete once Yeti is confident nothing was lost.

**Notes for other environments:**
- When Yeti reports vague slowness in any subsystem on this Mac, measure the accused subsystem first to rule it out, then check memory. Quick tell: `sysctl kern.memorystatus_vm_pressure_level` (1 normal, 2 warn, 4 critical) plus `sysctl vm.swapusage`.
- `browser.startup.page` is not set in his Firefox prefs, so Firefox does not restore tabs after a clean quit. The July tab restores were crash recovery: Firefox died under the memory pressure it created, and crash recovery restores sessions regardless of the startup pref. A clean quit breaks that loop.