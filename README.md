![Phantom Detect](icon-192.png)

# Phantom Detect

**AI watermark detector & text humanizer**

Detect AI-written text at the sentence level — then rewrite it to sound authentically human.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-8b5cf6?style=flat-square&logo=github)](https://abdullahmuhy-pixel.github.io/Phantom-Detect)
[![Built with HTML/JS](https://img.shields.io/badge/Built%20with-HTML%20%2F%20JS-f97316?style=flat-square)]()
[![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude%20Sonnet-818cf8?style=flat-square)]()

---

## What it does

Phantom Detect analyses text and tells you — with a per-sentence heatmap — exactly how AI-like it reads. It then rewrites the text at your chosen intensity so it bypasses AI detectors.

| Feature | Description |
|---|---|
| **AI Score** | 0–100 probability score with verdict and confidence rating |
| **Sentence Heatmap** | Every sentence colour-coded from green (human) → red (AI) |
| **Detection Signals** | Named signals: hollow phrases, uniform rhythm, hedge language, etc. |
| **Humanize** | Three rewrite strengths: Light, Moderate, Aggressive |
| **Re-scan** | Automatically re-analyses the humanized text and shows score drop |
| **Score Δ** | Before → after comparison card showing exact point reduction |
| **3,000 words** | Chunked parallel API calls handle up to 3,000 words |
| **PWA** | Installable on mobile and desktop, works offline (app shell cached) |

---

## Getting started

### Use it now

→ **[abdullahmuhy-pixel.github.io/Phantom-Detect](https://abdullahmuhy-pixel.github.io/Phantom-Detect)**

You'll need an **Anthropic API key** — paste it into the field at the top of the app. Keys are session-only and never stored or transmitted anywhere except directly to the Anthropic API.

Get a key at [console.anthropic.com](https://console.anthropic.com).

### Run locally

No build step required — it's a single HTML file.

```bash
git clone https://github.com/abdullahmuhy-pixel/Phantom-Detect.git
cd Phantom-Detect
npx serve .
```

Then open `http://localhost:3000` in your browser.

---

## File structure

```
Phantom-Detect/
├── index.html       # Full app — single self-contained file
├── sw.js            # Service worker (PWA / offline support)
├── manifest.json    # PWA manifest
├── icon-32.png      # Favicon
├── icon-180.png     # Apple touch icon
├── icon-192.png     # PWA icon (Android)
├── icon-512.png     # PWA icon (splash / stores)
└── README.md
```

---

## How it works

Every analysis and rewrite is powered by **Claude Sonnet** via the Anthropic Messages API, called directly from the browser using your own API key — no backend, no server, no data stored anywhere.

For texts up to 3,000 words, the app runs a **two-pass chunked strategy**:

1. **Meta pass** — full text sent once for overall score, verdict, signals, and summary
2. **Sentence passes** — text split into ~500-word chunks, scored in parallel with `Promise.all()`

The humanizer splits text into ~600-word chunks, rewrites them in parallel, then stitches the result back together and automatically re-scans it.

---

## Roadmap

- [ ] History tab with localStorage support
- [ ] Export results to PDF
- [ ] Batch upload (scan multiple texts at once)
- [ ] API key proxy (so users don't need their own key)
- [ ] MatricAce integration (academic integrity module)

---

## Tech stack

- Vanilla HTML / CSS / JavaScript — no framework, no build step
- [Anthropic Claude Sonnet](https://anthropic.com) — detection and rewriting
- [DM Serif Display](https://fonts.google.com/specimen/DM+Serif+Display) + [Lora](https://fonts.google.com/specimen/Lora) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) — typography
- GitHub Pages — hosting

---

*Built by [Abdullah Muhydeen](https://github.com/abdullahmuhy-pixel)*
