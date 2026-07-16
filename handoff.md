
### Addendum 3 (same session): Photo Mod panel + ticker speed
- New "Photo Mod" tab in /yeti-admin: pick any crowd gallery (Men's Club, Ladies Club, America 250, July 4), flagged photos float first with the flag reason, one-tap Hide/Restore, two-tap permanent Delete (removes KV index + Blob file). Phone-friendly for in-person takedown requests.
- photos-admin API gained the 'delete' action (was hide/restore only).
- Mens-club sponsor ticker sped up 160s -> 75s per loop.
- Commit e3f90ca deployed. Yeti should test the panel once with his real admin login (local verify used mocked API data).