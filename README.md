# StudySpot

A responsive, account-free study space finder. Six fictional Northfield University locations are ready to explore immediately. All photos, icons and map artwork are bundled. There are no external fonts, map services, API keys or dependencies to install.

## Run it

1. Extract the project ZIP if needed.
2. In the **StudySpot** folder (the folder containing `server.mjs`), run `node server.mjs` with Node.js 18 or newer.
3. Open **http://127.0.0.1:4173/**. Stop the server with Ctrl+C. You can set the `PORT` environment variable to use another port.

For a quick offline demo you can also open `dist/index.html` directly. Use the local server for reliable browser storage; file-URL storage behavior varies by browser. The local server is for development only.

## Deploy with VS Code, GitHub and Vercel

1. In VS Code, open the **StudySpot** folder containing this README and `vercel.json`. The prepared local repository uses the `main` branch. If you started from the ZIP, first use **Source Control → Initialize Repository**, then stage and commit the files.
2. Press **Ctrl+Shift+P**, run **Publish to GitHub**, and sign in when prompted. Name the repository **studyspot** and choose its visibility. A private repository works when Vercel has access to it.
3. Open [Vercel New Project](https://vercel.com/new), connect your GitHub account, and import **studyspot**. If the repository is missing, use the GitHub integration's repository access settings to grant Vercel access to **studyspot**.
4. Keep the root directory at the repository root. The included `vercel.json` sets the framework to **Other**, skips installation and building, and publishes **dist**. Click **Deploy**.
5. When Vercel shows **Ready**, open **Visit** and copy the production URL for your hackathon submission.

To release an update, edit the site in VS Code, commit on `main`, and push with **Sync Changes**. Vercel deploys updates to the connected production branch automatically.

After deployment, open the site on a phone and a desktop. Check that images and pins load and that a saved spot survives a refresh. Each hosted domain has its own local data; favorites from the local preview will not carry over.

## A one-minute hackathon demo

- Search for **Alden** and open its reading room to check access, amenities, the two-minute walk, and hours.
- Bookmark it; tap a crowd or noise level. Refresh to show the saved state and timestamped report.
- Clear search and use **Find me a spot**. Pick **Whiteboards**, a maximum **3-minute walk**, and **open**. Willow Commons meets those requirements.
- Add the result and Alden Library to **Compare** to see the differences side by side.
- Use **Map view** to select a pin. Zoom in, drag or focus the map and use arrow keys to pan. The target button resets the map.

## What is sample data?

Northfield University, its map, its six spots, their schedules, accessibility descriptions, starting reports, and route estimates are fictional. The architectural images are AI-generated illustrations of those spaces. “Open now” uses a fixed **Tuesday, 2 PM** snapshot, so the demo behaves consistently at any hour. Walking distances start at **Campus Gate** (blue dot), not the visitor's GPS location.

New crowd/noise reports really update the directory, display an actual device timestamp, and affect filters and recommendations. Favorites, comparisons, filters, preferences, reports and feedback are stored in the current browser under `studyspot.v1`. No records are uploaded, and feedback is not sent to a campus office. Clearing this site's browser storage resets the demo.

## Customization and a future backend

- `dist/data.js`: campus metadata, stable spot IDs, map positions, hours, amenities and seeded conditions. Start here to use your own campus.
- `dist/app.js`: navigation, rendering, local persistence, filters, reports and ranking. The finder first enforces required amenities, maximum walk and opening hours. It ranks eligible spots by closeness to preferred noise/crowd levels, then walking time.
- `dist/styles.css`, `dist/icons.js`, `dist/assets/`: responsive design and self-contained artwork.
- `server.mjs`: optional local static file server.

For shared conditions, replace the sample loader with a spots endpoint and route writes through a server. Keep the stable spot IDs; store **spots**, **reports** (spot ID, condition type, value, server timestamp), and **feedback** separately. Select the latest valid report per spot and condition; keep personal bookmarks local unless accounts are added. Validate incoming fields, rate-limit public writes, and moderate feedback before publication. Use actual campus schedules, a campus time zone and verified access information before describing conditions as current. No production database or API is configured.

## Verification

Browser checks covered search and combined filters, no-results recovery, building and open-now filters, details, favorites and reports after refresh, comparison, recommendations with required amenities, map pins and zoom/reset, feedback validation, both feedback modes, mobile navigation and map/list switching. A temporary failed data request verified the retry screen could load all six records on the next attempt. The page fit 320 px and 768 px test viewports without horizontal page overflow.

