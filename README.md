# Moments

Keep memorable snippets from Spotify podcasts and YouTube videos — without breaking your listening flow, and without typing. Each snippet is a clean card with the quote, the original audio clip, an optional hand drawing, a one-tap jump back to the exact second, and thoughts you add over time (each stamped with date/time and, optionally, a position in the episode).

No accounts, no server, no tracking: snippets live in your phone's browser storage and audio clips in its IndexedDB. Use **⋮ → Export backup** occasionally to keep a JSON copy (it includes the audio). Note: live transcription uses the browser's built-in speech service (Google's, on Android Chrome) — the saved audio itself never leaves your phone.

## Files

- `index.html` — the entire app (UI + logic)
- `manifest.webmanifest` — makes it installable and registers it in the Android share sheet
- `sw.js` — service worker, makes it work offline
- `icon-192.png`, `icon-512.png` — app icons
- `serve.ps1` — local dev server only, do **not** upload

## Publish (one-time, ~3 minutes, free)

The share-sheet integration requires the app to be served over HTTPS. Easiest path — GitHub Pages:

1. Go to https://github.com/new → repository name `moments` → **Public** → Create.
2. On the empty repo page, click **uploading an existing file** and drag in: `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`. Commit.
3. Repo **Settings → Pages** → under "Branch" choose `main` and `/ (root)` → Save.
4. After ~1 minute your app is live at `https://<your-username>.github.io/moments/`.

(Any static host works the same: Netlify, Cloudflare Pages, …)

## Install on your Android phone (one-time)

1. Open the URL in **Chrome** on the phone.
2. Menu (⋮) → **Add to Home screen** → **Install**.
3. Open the installed app once. Done — "Moments" now appears in the Android share sheet.

## Daily use

**Spotify (podcast):** at the memorable moment tap **Share → "Share from …" (current timestamp) → Moments**. The link, episode title and timestamp are pre-filled. Then **press and hold the record pad**: it records through the microphone and transcribes live into the quote field (release to stop). Save, switch back.

- Spotify keeps playing in the background while Moments is open. On **loudspeaker**, the pad captures and transcribes the podcast's own words — rewind a few seconds first if you want the exact line. With **headphones**, just say the line in your own words.
- The first hold asks for microphone permission once. The chip next to the pad toggles transcription language (`de-DE` / `en-US`).
- The audio clip itself is kept on the card, playable anytime — even if the transcription missed a word.

**YouTube:** tap **Share**, tick **"Start at [current time]"**, pick **Moments** — same hold-to-record flow.

**Later:** open a card → **▶ Play from …** reopens Spotify/YouTube at that exact second. Add thoughts anytime — also by holding a record pad, no typing — and give a thought a position like `34:12` to get its own jump link.

## Updating the app

Edit the files, re-upload to the repo (or commit), and bump the cache name in `sw.js` (`moments-v1` → `moments-v2`) so installed phones pick up the new version.
