## Session: July 17, 2026 (ET), early AM
**Environment:** Antigravity IDE
**What was done:**
- Spotted Owl logo chosen: parchment seal with party-hat owl (branding/logo-B1-parchment-seal.png)
- Integrated it sitewide: full seal as og:image (1024x1024), inner owl-medallion circular crop as nav mark (48px, brass ring) and PNG favicon, apple-touch-icon from full seal
- Found Vercel GitHub webhook flaky (push did not auto-deploy); deployed via `vercel deploy --prod --yes` instead. Use CLI deploy for this project going forward.
- Verified live nav renders the owl medallion cleanly via headless screenshot
- Saved cross-session memory: spotted-owl-event-co project memory (repo, live URL, logo decision, copy voice rules)

**What's live / deployed:**
- https://spotted-owl-site.vercel.app with seal logo in nav, favicon, and social share image (main at 0a498dc)

**Next up:**
- Yeti: click FormSubmit activation link in admin@yetigroove.com (if not done yet)
- Real photos for hero/gallery; real Instagram/Etsy footer URLs
- Consider print/sticker uses of the seal (wax-seal stickers for mailed invitations fit the Signature tier)
- Later: custom domain, persist-before-notify form upgrade

**Notes for other environments:**
- Logo files live in ~/Projects/spotted-owl-site/branding/ (4 concepts) and images/ (production crops)
- The full seal is unreadable below ~60px; always use the inner medallion crop for small marks