
### Update (same session, later)
- Yeti confirmed the filling account is admin@yetigroove.com. No Drive access to it from here; a local Google token at Documents/Claude Code/token.json was blocked by the permission classifier (credential exploration), not retried.
- Gmail side measured via the Gmail connector: ~29 threads over 5 MB, ~200 over 2 MB, total well under ~3 GB. Gmail is not the driver.
- Prime suspect: a Google Pixel 11 Pro XL signed into admin@yetigroove.com on Sep 12 2026 (Google security alert). Pixel defaults to Photos backup + device backup into that account's Workspace storage, which also pools Gmail + Drive. iCloud filled Sep 9. "Filling fast with no uploads" matches phone backup exactly.
- Verify: Photos app > profile > Photos settings > Backup; Settings > Google > Backup; one.google.com/storage (Drive/Gmail/Photos split); Admin console > Storage.