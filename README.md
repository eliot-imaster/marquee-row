# Marquee Row

*Read this in: [繁體中文](README.zh-TW.md) · [日本語](README.ja.md)*

A Stream Deck plugin that turns a row (or column) of keys into a single scrolling marquee display. Place the action on every key of a row, and they render one continuous strip of text — like an old-school ticker — spanning the whole row.

## Features

- **Multi-key rendering** — one line of text scrolls seamlessly across as many keys as you assign to a group, using each key's physical column/row position to auto-detect its slice of the strip.
- **Group sync** — every key in the same Group ID shares the same text, speed, colors, and direction. Edit any one key and the rest update automatically; you only type the text once.
- **Four scroll directions** — right-to-left, left-to-right (horizontal), and top-to-bottom, bottom-to-top (vertical, with characters stacked for Japanese/Korean-style vertical text).
- **Live variables** — `{{date}}`, `{{time}}`, `{{HH:MM}}`, `{{weekday}}`, and individual date/time tokens, refreshed every second.
- **Customizable display** — font, font size, text/background color, scroll speed, repeat gap, and a position offset for centering.
- **Localized settings panel** — English, Traditional Chinese, Simplified Chinese, Japanese, and Korean, following your Stream Deck app's language.

## Requirements

- Stream Deck software 6.6 or later
- macOS 10.15+ or Windows 10+
- An internet connection on first load of the settings panel (it loads the [sdpi-components](https://sdpi-components.dev/) UI library from a CDN)

## Installation

Double-click the `.streamDeckPlugin` file to install. If a previous version is already installed, this reinstalls it in place — your existing key settings (text, colors, group assignments) are preserved, since they're stored by the Stream Deck app itself, not inside the plugin package.

## Usage

1. Add the **Marquee Segment** action to every key of a single row (for horizontal scrolling) or a single column (for vertical scrolling).
2. Give them all the same **Group ID** (the default `row1` works fine for a single marquee).
3. Edit the text, direction, speed, or colors on any one key in the group — the rest sync automatically.

Each key figures out its own slice of the strip from its physical column (horizontal directions) or row (vertical directions), so you don't need to configure position manually in most setups.

### Variables

Use these inside the marquee text; they re-evaluate every second.

| Token | Example output |
| --- | --- |
| `{{date}}` | 2026/07/26 |
| `{{time}}` | 09:05:03 |
| `{{HH:MM}}` | 09:05 |
| `{{HH:MM:SS}}` | 09:05:03 |
| `{{YYYY-MM-DD}}` | 2026-07-26 |
| `{{weekday}}` | 星期日 (always rendered in Chinese, regardless of settings-panel language) |

Individual tokens `{{YYYY}}` `{{MM}}` `{{DD}}` `{{HH}}` `{{mm}}` `{{ss}}` can be mixed into free text, e.g. `Now {{HH}}:{{mm}}`.

### Notes

- **Vertical direction (top-to-bottom / bottom-to-top)** requires the keys to be arranged in a single *column*, not a row — the plugin uses each key's row index to tell members apart in vertical mode, so keys spread across a row would all resolve to the same slice.
- **Font** is applied by exact name with no automatic fallback. Picking a font that isn't installed on the machine (commonly Windows-only fonts like Impact, Verdana, or Comic Sans MS) leaves the display showing whatever font it last resolved successfully.

## License

© Eliot. All rights reserved.
