
## Addendum 3: OG card + hero upgrade (/social)
- Root cause of missing link previews: og:image/og:url on /social and /lakeaccess pointed at social.yetigroove.com, a subdomain that does not resolve. Both pages now use www.yetigroove.com.
- New og-social.png (1200x630): yeti-influencer from the MB library composed over the page's navy/cyan palette with real typography (Playfair + DM Sans), price chips. Confirmed rendering in iMessage.
- /social hero upgraded to match the card: two-column desktop with floating glowing yeti (73KB webp), stacked mobile, reduced-motion respected. Verified live via headless screenshot.
- Note for future checks: the repo's catch-all rewrite makes EVERY path return 200 with index.html, so "is it deployed" checks must test content-type or content, never status code.
- Offered but not done: same hero treatment for /lakeaccess.