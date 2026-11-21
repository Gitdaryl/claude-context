
## Session: 2026-11-21 ET
**Environment:** Antigravity IDE
**What was done:**
- Diagnosed home internet ("some devices have it, some don't"). Read-only checks, nothing changed.
- Internet upstream is healthy (0% loss to router and internet, DNS and IPv6 fine).
- Mac Studio gets internet over Wi-Fi (6 GHz), not cable. Its Ethernet port is the NAS direct link only.
- Three devices (HP Smart Tank printer, a Nest device, one unidentified) are on Wi-Fi with self-assigned 169.254 addresses: the Xfinity gateway never gave them an address.
- Mac log shows a gateway disturbance in the 5 AM hour today (Wi-Fi drop 5:30:15, IPv6 withdrawn until about 5:51).

**What's live / deployed:**
- Nothing.

**Next up:**
- Yeti power-cycles the Xfinity gateway (unplug 60 seconds), then the stuck devices if they do not recover. Re-run the LAN sweep to confirm no 169.254 devices remain.
- Unconfirmed: whether the gateway refuses new address requests right now (probe was inconclusive).

**Notes for other environments:**
- If devices drop again after a gateway restart, suspect the gateway's address service, not the ISP line.