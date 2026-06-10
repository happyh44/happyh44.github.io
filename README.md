# BD Log — Setup Guide

## What's in this folder
- index.html    — the entire app (vanilla JS, data stored in localStorage on your device)
- manifest.json — tells Android this is an installable app
- sw.js         — service worker (makes it work offline)
- icon-192.png / icon-512.png — app icons

## Step 1 — Host on GitHub Pages (~5 min, one time)
1. Create a free account at github.com (if you don't have one)
2. Click "+" (top right) -> New repository
   - Name it exactly:  YOURUSERNAME.github.io   (use your actual username)
   - Public. Click Create.
   - Naming it this way puts the app at the domain root, which the APK step needs.
3. On the repo page: "uploading an existing file" link (or Add file -> Upload files)
4. Drag in all 5 files from this folder. Commit.
5. Wait 2-3 minutes, then visit:  https://YOURUSERNAME.github.io
   The app should load.

## Step 2 — Install as a PWA (try this first)
1. Open that URL in Chrome on your Android
2. Chrome should show an "Install app" prompt, or use: three-dot menu -> Add to Home screen -> Install
3. Done. Own icon, full screen, works offline after first load.
   For most purposes this IS the app — see if you even need Step 3.

## Step 3 — Generate a real APK (optional)
1. Go to pwabuilder.com on a computer
2. Paste your URL: https://YOURUSERNAME.github.io -> Start
3. It scores your PWA (should pass) -> Package For Stores -> Android
4. Choose "Test package" / unsigned for personal sideloading, or signed if you
   may publish to Play Store later. Download the zip.
5. The zip contains the .apk PLUS a file called assetlinks.json:
   - In your GitHub repo: Add file -> Create new file
   - Name it:  .well-known/assetlinks.json   (the slash creates the folder)
   - Paste in the contents of the assetlinks.json from the zip. Commit.
   - Without this, the installed app shows a browser address bar at the top.
6. Transfer the .apk to your phone (email it to yourself, or Google Drive)
7. Tap it -> Android asks to allow installs from that source -> allow -> Install

## Your data
- Everything is stored on your phone (localStorage). Nothing is sent anywhere.
- Use Settings -> Export to CSV regularly as a backup — clearing Chrome's
  site data would wipe the log.
- The app works fully offline after the first visit.

## Updating the app later
Replace index.html in the GitHub repo with a new version. Installed
PWA/APK picks up the change next time it's opened with a connection
(may take one extra open due to caching).
