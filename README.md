# Saveo — Universal Media Downloader

**[saveo.pages.dev](https://saveo.pages.dev)** · Free · No signup · No ads

Paste a link, pick your quality, download. That's it.

---

## Supported Platforms

| Platform | Video | Audio | Photo |
|----------|-------|-------|-------|
| TikTok | ✅ | ✅ | — |
| Reddit | ✅ | — | ✅ |
| X (Twitter) | ✅ | — | ✅ |
| Pinterest | — | — | ✅ |
| Vimeo | ✅ | — | — |
| SoundCloud | — | ✅ | — |

> YouTube and Instagram are currently unavailable due to platform-level IP restrictions on cloud servers.

---

## How It Works

1. User pastes a link
2. Frontend detects platform, calls backend `/api/formats` to fetch available qualities
3. User picks quality and clicks download
4. Backend resolves the direct CDN URL via yt-dlp and returns it
5. Browser downloads the file directly from the source — no media bytes pass through the server

Cloudflare Turnstile is used for bot protection on every request.

---

## Tech Stack

**Frontend** — Vanilla HTML/CSS/JS, deployed on Cloudflare Pages  
**Backend** — Python Flask + yt-dlp, deployed on Render  
**Bot protection** — Cloudflare Turnstile  
**Fonts** — Syne + JetBrains Mono (Google Fonts)

---

## Project Structure

```
saveo/
├── index.html       # Main app — all UI, state machine, platform config
├── privacy.html     # Privacy policy page
└── favicon.svg      # Logo
```

Backend lives in a separate private repository.

---

## Features

- Zero signup, zero account, zero tracking
- Dark / light theme with localStorage persistence
- Cloudflare Turnstile bot protection
- Rotating URL placeholder showing supported platforms
- Platform auto-detection from pasted URL
- Quality grid showing only real available formats
- Post-download donate prompt (Ko-fi)
- Support sheet + banner with 3-day cooldown
- Mobile responsive

---

## Local Development

No build step. Just open `index.html` in a browser.

To test against a local backend, update `WORKER_URL` in `index.html`:

```js
const WORKER_URL = 'http://localhost:10000';
```

---

## Self Hosting

**Frontend** — Deploy the repo to Cloudflare Pages, Netlify, or any static host.

**Backend** — See the backend repo (private). Requires Python 3.11+, ffmpeg, and yt-dlp.  
Deploy to Render, Railway, or any platform supporting Docker.

Update `WORKER_URL` in `index.html` to point to your backend URL before deploying.

---

## Fair Use

Saveo is a personal-use tool. All downloaded content remains the intellectual property of its original creators and respective platforms. Do not redistribute, monetize, or claim others' content as your own.

---

## Support

If Saveo saved you time → [ko-fi.com/nirvanayt](https://ko-fi.com/nirvanayt)  
Everything else → [linktr.ee/nirvanaa](https://linktr.ee/nirvanaa)