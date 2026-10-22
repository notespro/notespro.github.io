# NotesPro — Private PWA

A simple, fast, offline-first notes app you can install on your phone or desktop.

**Live:** https://notespro.github.io

## Features

- Fully offline (Service Worker)
- Installable as an app (PWA)
- Optional passcode lock with **AES-256-GCM** encryption
- Dark / light / system theme
- Pin notes, search, export / import
- Zero tracking — everything stays on your device

## Deploy to GitHub Pages

1. Create organization **notespro** (or use your account).
2. Create repository **notespro.github.io** (must be public).
3. Upload all files from this folder to the repo root.
4. Go to **Settings → Pages**.
5. Source: **Deploy from a branch** → `main` → `/ (root)`.
6. After a minute the app is live at:

   **https://notespro.github.io**

7. Open the URL → tap **Install** (or browser menu → Add to Home Screen).

### Install requirements

- HTTPS (GitHub Pages provides this)
- Valid manifest + icons (included)
- Service Worker (included)
- Chrome / Edge / Samsung Internet show the Install button
- iOS Safari: Share → **Add to Home Screen**

## Security

| Layer | Details |
|-------|---------|
| Storage | Notes stay in `localStorage` on your device only |
| Encryption | When lock is on: AES-256-GCM, key via PBKDF2 (210k iterations) from your PIN |
| Passcode | Never stored in plain text — only a salted hash |
| Network | No analytics, no external requests, strict CSP |
| XSS | All note content is HTML-escaped before display |

## Local testing

```bash
npx serve .
# or
python -m http.server 8080
```

Open `http://localhost:8080`
