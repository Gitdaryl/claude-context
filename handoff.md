## Session: 2026-11-21 ET
**Environment:** Antigravity IDE
**What was done:**
- Diagnosed home internet ("some devices have it, some don't"). Read-only checks, nothing changed on the Mac.
- Cause: Xfinity gateway stopped handing out addresses after a disturbance in the 5 AM hour. HP printer, a Nest device and one other were on Wi-Fi with self-assigned 169.254 addresses.
- Yeti restarted the gateway about 12:41 PM. Rescan confirms fixed: all three have 10.0.0.x addresses, no self-assigned devices left, 0% packet loss.
- Mac Studio gets internet over Wi-Fi (6 GHz), not cable. Its Ethernet port is the NAS direct link only.

**What's live / deployed:**
- Nothing.

**Next up:**
- Nothing owed. If it recurs, restart the gateway and consider calling Xfinity about the gateway.

**Notes for other environments:**
- "Some devices have internet, some don't" at home = check for 169.254 addresses, then restart the gateway.