# Compliment Generator ✨

> Your daily boost of good energy — personalized compliments across 5 moods, with instant social sharing and dark mode.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![No dependencies](https://img.shields.io/badge/dependencies-none-brightgreen?style=flat)

**Live demo:** [gustav-devhub.github.io/compliment-generator](https://gustav-devhub.github.io/compliment-generator/)

---

## Overview

Compliment Generator is a single-file, zero-dependency web app that delivers personalized compliments on demand. Enter your name, pick a mood, and hit generate — the app animates a fresh compliment into a styled card, fires a confetti burst, and lets you copy or share it instantly.

---

## Features

- **150+ hand-written compliments** across 5 distinct moods
- **Name personalization** — every compliment is addressed to you
- **5 mood categories** — Funny, Heartfelt, Motivational, Romantic, Confidence
- **One-click sharing** to X (Twitter), LinkedIn, and WhatsApp
- **Clipboard copy** with animated feedback
- **Compliment history** — last 5 compliments remembered across sessions
- **Dark mode** with toggle, persisted to `localStorage`
- **Self-contained confetti animation** — no external library required
- **Fully responsive** — works on mobile, tablet, and desktop
- **Accessible** — ARIA labels, `aria-live` region, `aria-pressed` states

---

## Tech Stack

| Layer | Choice | Notes |
|---|---|---|
| Markup | HTML5 | Single file, semantic elements |
| Styling | CSS3 | Custom properties, Grid, animations |
| Logic | Vanilla JS (ES6+) | No frameworks or build tools |
| Fonts | Google Fonts | Playfair Display, DM Sans, Lora |
| Storage | `localStorage` | Persists name, history, theme |

Everything ships in **one `.html` file** — no bundler, no npm, no build step.

---

## Project Structure

```
compliment-generator/
├── index.html      # Entire app — HTML, CSS, and JS in one file
├── favicon.png     # Browser tab icon
└── README.md
```

---

## Getting Started

No installation needed. Just open the file in a browser:

```bash
git clone https://github.com/Gustav-DEVhub/compliment-generator.git
cd compliment-generator
open index.html
```

Or deploy instantly to any static host (GitHub Pages, Netlify, Vercel).

---

## How It Works

### Compliment Engine

150+ compliments are stored in a `COMPLIMENTS` object, keyed by category. Each string uses a `{NAME}` placeholder that gets replaced at runtime with whatever the user typed (falling back to `"you"` if the field is blank). A deduplication loop ensures the same compliment isn't shown twice in a row.

### Confetti

The confetti effect is a fully self-contained canvas animation — no external library, no Web Workers, no blob URLs. Particles spawn from the center of the viewport, fan upward, and fade out over ~160 frames under simulated gravity and drag.

### Persistence

Three keys are saved to `localStorage`:

| Key | Value |
|---|---|
| `radiant_dark` | `"true"` or `"false"` |
| `radiant_name` | Last entered name |
| `radiant_history` | JSON array of last 5 compliments |

All storage calls are wrapped in `try/catch` so the app degrades gracefully in private browsing or restricted environments.

---

## Customization

**Add more compliments** — extend any array inside the `COMPLIMENTS` object in the `<script>` block. Use `{NAME}` wherever you want the personalized name to appear.

**Add a new category** — add a new key to `COMPLIMENTS`, a new button in the `.categories` grid, and a matching label in the `categoryLabels` map inside `handleGenerate`.

**Change the color palette** — all colors are defined as CSS custom properties in `:root`. Dark mode overrides live in `body.dark`.

---

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires ES6+ and the Clipboard API (with a `execCommand` fallback for older environments).

---

---

Made with 💛 by [Gustav](https://github.com/Gustav-DEVhub)