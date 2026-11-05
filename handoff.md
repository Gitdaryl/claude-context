## Session: 2026-11-05 ET
**Environment:** Antigravity IDE
**What was done:**
- Built the MB mini ad system: three formats, rotation planner, ad pool, Heather seasonal looks, ~/MB-Assets, ~/Previews
- Built /ad-photos intake form on branch ad-intake: logo, 10 photos, season answers, socials to tag, setup help lead, optional text alerts, consent boxes
- Responsive audit passed; 199 local tests pass; one real send on the preview passed end to end, test data cleared
- Connected private store mb-ad-intake-private; ad links now use AD_INTAKE_SIGNING_SECRET
- Backed up SD-Recovery to NAS; osmo.dmg confirmed on NAS at Family Stuff 2026/OSMO-recovery-2026-08

**What's live / deployed:**
- Preview only, branch ad-intake at 4447a65. Nothing on production. Daily Spotlight and weekly AI Holly unchanged

**Next up:**
- Attorney review of Terms draft (mini-ads/offer/DRAFTS.md section 5), then merge, VITE_AD_INTAKE_OPEN=1, make links, announce
- Yeti: sudo rm -rf ~/SD-Recovery/recovered (safe, 333 GB)
- After launch: ad is up text and email, latest reel on profile, tagging test
- Yeti: club organizer names; reel pack prices

**Notes for other environments:**
- Do not share /ad-photos until the Terms update is live