# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-page birthday greeting for "Rafy" — a personal, interactive HTML page with Italian/Spanish cultural theming. No build system, no dependencies, no package manager.

## Running Locally

Open `index.html` directly in a browser, or serve via Docker:

```bash
docker build -t rafy-birthday .
docker run -p 8080:80 rafy-birthday
# Then open http://localhost:8080
```

## Architecture

Everything lives in a single file: [index.html](index.html)

- **CSS** (lines 7–369): Inline styles. Sections marked with `/* ===== SECTION NAME ===== */` comments.
- **HTML** (lines 371–436): Static structure — flag banners, off-screen YouTube player div, chest widget, message card overlay.
- **JavaScript** (lines 438–545): Two `<script>` blocks:
  1. YouTube IFrame API integration — loads asynchronously, handles `ytReady`/`pendingPlay` state for deferred playback of video ID `CNHL66K8S2I` ("Vivo per Lei").
  2. DOM generation + interaction — stars (120), floating particles (22), chest open/close toggle, confetti burst (100 pieces), card close.

## Key Interaction Flow

1. User clicks the CSS-drawn treasure chest → `toggleChest()` opens lid, triggers confetti, shows `.message-card` overlay after 700ms delay.
2. Music button → `toggleMusic()` plays/pauses via YouTube IFrame API (requires internet connection).
3. Photos in the card (`WhatsApp Image 2026-03-26 at *.jpeg`) must be present alongside `index.html`.

## Assets

Two JPEG photos are referenced by filename with spaces — paths must stay exactly as-is or both the HTML `src` attributes and filenames must be updated together.
