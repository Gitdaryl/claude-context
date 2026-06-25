## Session: 2026-06-25 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed NAS (UGREEN NASync / UGOS, "YETIGROOVENAS") disconnecting + hourly slowdown. Root cause: Time Machine was backing up ~950 GB hourly to the NAS over Wi-Fi, which choked the link and dropped the NAS entirely mid-use.
- Discovered the Mac Studio reaches the NAS two ways: LAN port 10.0.0.130 (only over Wi-Fi, jittery 6-80ms) and a DIRECT 10GbE cable at 10.10.10.2 (0.5ms, rock solid). Everything was using the slow Wi-Fi path because the NAS hostname resolves to 10.0.0.130.
- Confirmed NAS direct-link port already has a correct static IP (10.10.10.2 / 255.255.255.0) in UGOS Control Panel > Network > Network connection. No change needed there.
- Killed Time Machine: removed the NAS destination via System Settings > General > Time Machine (minus button). Verified: "No destinations configured", AutoBackup=0, Running=0.
- Re-mounted NAS shares over the fast direct link: personal_folder, Sunny Skies, Production all now mounted from smb://10.10.10.2 (active connection confirmed on en0 10GbE, not Wi-Fi).

**What's live / deployed:**
- Time Machine fully disabled (destination removed).
- NAS file shares running over 10GbE direct cable (10.10.10.2), ~100x lower latency than before.

**Next up:**
- Stale root-owned Time Machine SMB mount (/Volumes/.timemachine/...) still lingering — cosmetic only, clears on reboot or via `sudo umount`.
- Recommend adding the 10.10.10.2 mounts to Login Items so they auto-reconnect after reboot.
- Optional: when connecting to NAS always use smb://10.10.10.2, never the hostname or 10.0.0.130, to stay on the fast wire.

**Notes for other environments:**
- Mac Studio en0 = 10GbE direct cable to NAS (10.10.10.1 <-> 10.10.10.2). en1 = Wi-Fi on home LAN (10.0.0.x, router 10.0.0.1). Use the 10.10.10.2 path for all NAS file access.