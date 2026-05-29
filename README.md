<div align="center">

<img src="icon-192.png" width="96" alt="Phantom Detect icon" />

# Phantom Detect

**AI watermark detector & text humanizer**

Detect AI-written text at the sentence level — then rewrite it to sound authentically human.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-8b5cf6?style=flat-square&logo=github)](https://abdullahmuhy-pixel.github.io/Phantom-Detect)
[![HTML](https://img.shields.io/badge/Built%20with-HTML%20%2F%20JS-f97316?style=flat-square)]()
[![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude%20Sonnet-818cf8?style=flat-square)]()

</div>

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
| **Teacher Mode** | Academic integrity scanner with student/assignment fields |
| **Integrity Log** | In-session log of all scanned submissions with flag support |
| **PWA** | Installable on mobile and desktop, works offline (app shell cached) |

---

## Getting started

### Use it now

→ [abdullahmuhy-pixel.github.io/Phantom-Detect](https://abdullahmuhy-pixel.github.io/Phantom-Detect)

You'll need an **Anthropic API key** — paste it into the field at the top of the app. Keys are session-only and never stored or transmitted anywhere except directly to the Anthropic API.

Get a key at [console.anthropic.com](https://console.anthropic.com).

### Run locally

No build step required — it's a single HTML file.

```bash
git clone https://github.com/abdullahmuhy-pixel/Phantom-Detect.git
cd Phantom-Detect
# Open index.html in your browser, or serve it:
npx serve .
```

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

Every analysis and rewrite is powered by **Claude Sonnet** via the Anthropic Messages API. The app calls the API directly from the browser using your own API key — there is no backend, no server, and no data is stored anywhere.

```
User text → Anthropic API → JSON (score, verdict, per-sentence scores, signals)
                         → Heatmap rendered in browser
```

For the humanizer, the rewritten text is automatically re-sent for a second analysis pass, producing the Score Δ comparison.

---

## Modes

### Student mode
Paste your own text to check it and optionally humanize it before submission.

### Teacher / Academic Integrity mode
Enter a student name, assignment title, and grade, then scan their submission. Flag suspicious submissions and save results to the in-session integrity log. *(Supabase logging coming soon for persistent storage.)*

---

## Roadmap

- [ ] Supabase backend for persistent teacher logs
- [ ] Export integrity log to CSV / PDF
- [ ] Batch upload (scan multiple submissions at once)
- [ ] MatricAce integration (school-admin portal)
- [ ] History tab with localStorage support
- [ ] API key proxy (so students don't need their own key)

---

## Tech stack

- Vanilla HTML / CSS / JavaScript — no framework, no build step
- [Anthropic Claude Sonnet](https://anthropic.com) — detection and rewriting
- [DM Serif Display](https://fonts.google.com/specimen/DM+Serif+Display) + [Lora](https://fonts.google.com/specimen/Lora) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) — typography
- GitHub Pages — hosting

---

## Part of MatricAce SA

Phantom Detect is a standalone tool that will be integrated into [MatricAce](https://matricace.co.za) — South Africa's matric study and school management platform — as an academic integrity feature for teachers and school admins.

---

<div align="center">
  <sub>Built by <a href="https://github.com/abdullahmuhy-pixel">Abdullah Muhydeen</a></sub>
</div>
