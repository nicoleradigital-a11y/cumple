# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-page gratitude page for Iñi — a personal, interactive HTML page with Spanish and republican flag theming. No build system, no dependencies, no package manager.

## Running Locally

Open `index.html` directly in a browser, or serve via Docker:

```bash
docker build -t gracias-ini .
docker run -p 8080:80 gracias-ini
# Then open http://localhost:8080
```

## Architecture

Everything lives in a single file: [index.html](index.html)

- **CSS**: Inline styles for the full-screen scene, chest, card overlay, flags, and music control.
- **HTML**: Static structure — flag banners, chest widget, message card overlay, and local audio element.
- **JavaScript**: DOM generation + interaction — stars, chest open/close toggle, confetti burst, card close, and local audio play/pause state.

## Key Interaction Flow

1. User clicks the CSS-drawn treasure chest → `toggleChest()` opens lid, triggers confetti, shows `.message-card` overlay after 700ms delay.
2. Music button → `toggleMusic()` plays/pauses the local `marcha-real.ogg` audio file.
3. Photos in the card reuse `foto-ini-amigos.jpg`, which must stay alongside `index.html`.

## Assets

The project depends on two local assets next to `index.html`: `foto-ini-amigos.jpg` and `marcha-real.ogg`.
