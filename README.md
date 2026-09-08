[README.md](https://github.com/user-attachments/files/31960274/README.md)
# TTS Review Tool

A single-page, keyboard-driven review tool for A/B evaluating text-to-speech output. Built for my own RLHF/TTS evaluation work — reviewing paired audio clips against a CMOS scale, flagging what's wrong, and exporting results in a format that drops straight into a spreadsheet.

**[Live demo](https://sezersagir.github.io/tts-review-tool/)** · no backend, runs entirely client-side

> This is a sanitized version with placeholder text and no audio files. The real tool wires the same UI up to signed client audio URLs and a specific team's evaluation rubric — that part stays under NDA.

## What it does

- **Paired or single playback** — play A→B back to back, or jump to just one side, at adjustable speed (1×–2×)
- **CMOS scoring** — a −2 to +2 scale for "A vs. B", set by click or number key (1–5)
- **Reason tagging** — a multi-select of common quality dimensions (articulation, pacing, naturalness, noise, etc.), each bound to a keyboard shortcut
- **Quick-insert comment snippets** — one-click phrases for common problems, so free-text comments stay consistent across a review session instead of everyone phrasing the same issue differently
- **Autosave** — progress is saved as you go and restored if you close the tab and come back
- **Export** — copy as TSV (paste straight into a spreadsheet) or download as CSV

## Keyboard shortcuts

| Key | Action |
|---|---|
| `Space` | Play A → B |
| `A` / `B` | Play just A / just B |
| `1`–`5` | Set CMOS score (A much worse → A much better) |
| `Q W E R T Y U I O P [ ]` | Toggle a reason tag |
| `S` | Cycle playback speed |
| `K` | Pause / resume |
| `←` / `→` | Previous / next item |
| `Enter` | Confirm comment and advance |

## Tech

Vanilla HTML/CSS/JS, no build step, no dependencies. Progress is persisted via a small key-value storage layer (swap in `localStorage`, a backend, or whatever you're already using).

## Running it

Open `index.html` in a browser, or serve the folder with any static file server:

```bash
python3 -m http.server 8000
```

## Data format

Rows live in a `DATA` array at the top of the script:

```js
{ "speaker": "Nora", "text": "…", "audioA": "", "audioB": "", "cmos": "", "reason": "", "comment": "" }
```

Point `audioA` / `audioB` at your own audio URLs to use it for real.

---

Built by [Sezer Mikail Sagir](https://sezersagir.com) — AI Evaluation & RLHF Specialist.
