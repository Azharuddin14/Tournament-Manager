# Pitchside — Tournament Manager

A from-scratch cricket tournament/league manager: seasons → groups → knockouts,
with NRR, head-to-head records, and a "Tournament Result" (Winner/Runner-up/
Semi-finalists) summary. Plain static files — no build step, no server.

## Files in this package

- `index.html` — the real app (starts empty, ready for your data)
- `demo-ssn5.html` — the same app, pre-loaded with your Ssn 5 data as a sample
- `manifest.json`, `sw.js` — makes it installable as a PWA
- `icons/icon-192.png`, `icons/icon-512.png` — app icons (placeholder cricket-ball style — swap these for your own anytime)

---

## Step 1 — Upload to GitHub (no coding needed, all in the browser)

1. Go to **github.com**, log in (or create a free account).
2. Click the **+** icon top-right → **New repository**.
3. Name it something like `pitchside` → tick **Public** → **Create repository**.
4. On the new repo's page, click **uploading an existing file** (or drag files
   straight onto the page).
5. Drag in all the files from this package — `index.html`, `manifest.json`,
   `sw.js`, and the whole `icons` folder (drag the folder in as-is; GitHub
   keeps the folder structure).
6. Scroll down, click **Commit changes**.

## Step 2 — Turn on GitHub Pages (this gives you the live link)

1. In the repo, go to **Settings** (top tab) → **Pages** (left sidebar).
2. Under "Build and deployment" → **Source**, choose **Deploy from a branch**.
3. Under **Branch**, choose `main` and folder `/ (root)` → **Save**.
4. Wait 1–2 minutes, then refresh the page — you'll see a green box with your
   live URL, like `https://<your-username>.github.io/pitchside/`.
5. Open that link — that's your app, live, on any device.

To rename a team, add a season, etc. later: just re-upload the changed file
to the same repo (or edit it directly on GitHub using the pencil icon on the
file page) — Pages redeploys automatically in about a minute.

## Step 3 — Package it as an installable app with PWA Builder

Once your GitHub Pages link is live (Step 2), you can turn it into an
installable app (Android, and a Windows package) for free:

1. Go to **pwabuilder.com**.
2. Paste your GitHub Pages URL (e.g. `https://<you>.github.io/pitchside/`)
   into the box → click **Start**.
3. PWA Builder scans the site and shows a score/checklist (manifest, icons,
   service worker — this app already has all three, so it should score well).
4. Click **Package for stores**.
   - **Android**: generates a signed `.aab`/`.apk` you can side-load or
     submit to the Play Store.
   - **Windows**: generates a Microsoft Store-ready package.
   - **iOS**: PWA Builder can generate an Xcode project, but this needs a
     Mac + Apple Developer account to actually build/sign it — for personal
     use, "Add to Home Screen" from Safari on iPhone is the simpler route
     (it installs like a normal app icon, no store needed).
5. Download the package it generates and follow PWA Builder's own
   on-screen instructions for that platform (they walk you through signing
   and installing).

For everyday personal use across your own phone/laptop, you likely don't
need the PWA Builder packaging at all — just open the GitHub Pages link in
Chrome and tap **"Add to Home Screen"** (Android) or **"Add to Home Screen"**
in Safari's share sheet (iPhone). That installs it as an app icon directly,
using the manifest/service worker already in this package.

## How data is stored

Everything (teams, seasons, matches) is saved in the browser's
`localStorage`, per-device, per-browser — there's no server or database, and
no sync between devices. If you install it on two phones, they'll each have
their own separate data unless you re-enter it on both.

## Notation reference

- Runs alone (`143`) = all out at 143.
- `185/4` = 4 wickets down, played the full quota of overs.
- `54/1(6.2)` = finished the chase early, in 6.2 overs.
- `#` marks the winning team in the one-line result.
- Tick "batted first" next to whichever team actually batted first — the
  app works out the winner and formats overs/NRR from the scores itself.

