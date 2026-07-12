# Moments

Keep memorable snippets from Spotify podcasts and YouTube videos — without breaking your listening flow, and without typing. Each snippet is a clean card with the quote, the original audio clip, an optional hand drawing, a one-tap jump back to the exact second, and thoughts you add over time (each stamped with date/time and, optionally, a position in the episode).

No accounts, no server, no tracking: everything lives in your phone's browser storage. Use **⋮ → Export backup** occasionally to keep a JSON copy. Note: live transcription uses the browser's built-in speech service (Google's, on Android Chrome).

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

**Spotify (podcast):** at the memorable moment tap **Share → "Share from …" (current timestamp) → Moments**. The moment is **saved instantly** — link, title and timestamp captured, no mic, no typing — so your podcast keeps playing without interruption. You land on the moment's card.

Add the actual line whenever you like, from that card:
- **Speak it** (the card starts listening, or tap the mic button): say the line in your own words, pause, and it stops by itself. The transcript appears as tappable words with the likely line pre-highlighted — tap the first and last word to pick a different part — then **Save the line**.
- Or just **type** it. Or leave it wordless and rely on **▶ Play from …** to jump back.

Notes:
- Speaking opens the mic, and Android pauses the podcast while the mic is on (that's the OS, not the app). Because the moment is already saved, you can add the words *after* you finish listening, so playback is never interrupted mid-flow. Listening is a single short session (no restarts).
- The mic asks permission once. The chip next to the button toggles transcription language (`de-DE` / `en-US`).

**YouTube:** tap **Share**, tick **"Start at [current time]"**, pick **Moments** — same instant-save flow.

**Podcast / channel name:** captured automatically when possible (YouTube gives the channel name for free; Spotify episode links often don't expose the show name, so add it once by hand in **Edit details ⚙** if it's missing). Shows on the card, as the headline of the detail view (episode title underneath, smaller), in search, and in the caption when you share.

**The collection:** the home screen lays your moments out as a masonry wall of cards — two columns on a phone, three on a tablet — sized to their content, with drawings shown large. Short lines read big and punchy; long ones settle down.

**Opening a card:** the quote and drawing are the focus. Actions sit as a discrete row underneath — a quiet **▶ 0:45** to jump back, and small icons to **share (➚)**, **draw (✎)**, **edit details (⚙)**, and **delete (🗑)**.

**Drawing:** tap **✎** on a card to sketch; it saves instantly, no separate step. Drawings appear on the card and in the shared image.

**Sharing:** tap **➚** to render the moment as a clean card image and hand it to Android's share sheet (WhatsApp, Messages, anywhere), with the quote + jump-back link in the caption. On desktop it downloads the image and copies the caption.

**Later:** open a card → **▶ Play from …** reopens Spotify/YouTube at that exact second. Add thoughts anytime by voice (🎤 Speak) or typing, and give a thought a position like `34:12` to get its own jump link.

## Updating the app

Edit the files, re-upload to the repo (or commit), and bump the cache name in `sw.js` (`moments-v1` → `moments-v2`) so installed phones pick up the new version.
