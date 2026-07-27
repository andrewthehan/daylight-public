# daylight-public

This repo is entirely generated output — there is no app source code here.
It exists to be served by GitHub Pages as two things for the Daylight app:

- **The static web build** (`index.html`, `_expo/`, `assets/`, `favicon.ico`,
  `metadata.json`) — produced by `expo export -p web` in the main app repo.
- **Daily puzzle content** (`puzzles/manifest.json` + `puzzles/<year>-<month>.json`)
  — the app fetches these at runtime (see `lib/remoteContent/` in the main
  repo) so new or corrected puzzles can ship without an app-store release.
  `puzzles/manifest.json` lists a content hash per month; the app only
  re-downloads a month whose hash has changed.

**Nothing here should be hand-edited.** Both the web build and the puzzle
JSON are regenerated from the main (private) app repo and pushed here:

```
REVENUECAT_API_KEY=mock npx expo export -p web --output-dir ../daylight-public
npx tsx scripts/build-remote-content.ts ../daylight-public
```

then commit and push from this checkout.
