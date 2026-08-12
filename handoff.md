## Session: 2026-08-11 ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- Made `/my-events` installable to a phone home screen, so an organizer taps an icon instead of hunting for a link.
- `api/my-events-manifest.js` generates the web app manifest per organizer. A static manifest would have been the trap: the launcher uses `start_url`, which would drop the token and open a stranger's sign-in screen. The token rides along in start_url.
- iOS meta tags (`apple-mobile-web-app-title`, capable, touch icon) are injected by the page rather than sitting in index.html, because Safari reads them from the live DOM at Add to Home Screen time and they shouldn't apply to every page on the site.
- Install card detects iOS vs Android and shows the right instructions, using the real `beforeinstallprompt` button where the browser offers one. Dismissible, remembered in localStorage.
- Token TTL raised from 30 days to a year. An icon that dies in a month is worse than no icon.
- Event links inside the list switched to router `<Link>` so the installed app doesn't bounce out to Safari on tap.
- Icons generated at 192 and 512 from the existing 1052px `manitou_beach_icon.png`.
- Turned the voice concierge off on `/my-events`, `/events/edit` and `/submit-event`. Caught it in an iPhone screenshot sitting on top of the "tap Share at the bottom of Safari" line. Nobody editing their own event wants to ask a tourism bot a question.

**What's live / deployed:**
- Commits e5906a4 and 23333e9 on main, deployed and verified by asset content-type.
- Verified headless at an iPhone 13 viewport: manifest link injected carrying the token, apple title "My Events", touch icon set, install card visible with correct iOS wording, manifest fetches 200 with the token in start_url, events list renders. Re-shot after the concierge fix and confirmed the instructions are fully readable.

**Next up:**
- Three events still sitting unseen from when the admin alerts were failing: two duplicate "Widow and Widower Group" (Review, Jun 10, angandco.mi@gmail.com) and "Topless In The Hills" (Pending, May 16, Lgervick@newgenauto.com). Approve or reject.
- Send Gypsy Blue the /my-events link and mention the home screen trick.
- Untested on a real device: only checked in a simulated iPhone viewport. Worth adding it to a real phone once to see the icon land.

**Notes for other environments:**
- `/my-events` is the front door for event organizers now. Send that, not individual edit links.
- If other pages ever need install-to-home-screen, the pattern is in MyEventsPage's `useInstallable` plus a per-user manifest endpoint.