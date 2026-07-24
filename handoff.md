
## Addendum 2: em-dash slop purge (MB blog + newsletter)
- SOP updated in claude-context repo: new "Writing Style" section, zero tolerance for em dashes in all output, pre-publish slop check. All platforms get it on next GDay.
- Manitou-Beach generators patched + deployed: api/generate-article.js and api/cron-newsletter-draft.js now forbid em dashes in the prompt AND scrub them from every AI output (stripEmDashes). Future blog posts and newsletter drafts cannot contain them.
- Existing content cleaned in Notion: scanned all 14 Dispatch articles, fixed 28 body blocks + 6 property fields across 5 articles (incl. live "July's Sweet Spot" and "Lake's Finally Showing Off"). Re-scan verified zero em dashes remain. Formatting/links preserved.
- Note: newsletter issues already sent through beehiiv can't be un-sent; everything from here forward is clean.