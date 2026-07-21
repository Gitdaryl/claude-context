## Session: July 21, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Meta domain verification for manitoubeachmichigan.com: walked Yeti through Business Suite (Brand Safety → Domains → Add → "Create a domain", not "Request access"), added the facebook-domain-verification meta tag to index.html (commit 22b1d1d), deployed, and confirmed the tag is live on the homepage exactly as Meta's crawler fetches it (including the http redirect path)
- This follows today's share-card work (f49c543, 9ba665c, d1643bb): photo cards proven working in FB feed, WhatsApp, iMessage, and the Sharing Debugger; Messenger alone suppresses previews for the domain (reputation filter). Domain verification is the trust signal to help that clear

**What's live / deployed:**
- 22b1d1d on Gitdaryl/Manitou-Beach main → Vercel, tag verified live

**Next up:**
- Yeti clicks "Verify Domain" in Meta Business Suite (tag is live now; if Meta claims it can't find it, wait a few minutes and click again - Meta allows up to 72h but it's usually instant)
- Still open from July 20: finish uploading/tagging America 250 photos; paste the YouTube URL into USA250_FILM_URL when the film is live

**Notes for other environments:**
- Memory saved earlier: messenger-og-preview-quirk (3-test matrix for "no preview in Messenger" complaints)