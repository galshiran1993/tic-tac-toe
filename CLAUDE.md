# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file browser game — all HTML, CSS, and JS live in `tictactoe.html`. No build step, no dependencies, no package manager.

## Running the game

```bash
open tictactoe.html
```

## Architecture

Everything is in one file with three logical sections:

1. **CSS** (inside `<style>`) — dark navy theme (`#1a1a2e` background). Player X is red (`#e94560`), player O is teal (`#4ecca3`). State is expressed entirely through CSS classes on `.cell` elements: `taken`, `x`, `o`, `win`.

2. **HTML** — static board of 9 `.cell` divs addressed by `data-i` (0–8, row-major). Score display, turn status line, and a reset button.

3. **JS** (inside `<script>`) — pure vanilla, no frameworks. Key pieces:
   - `WINS` — hardcoded array of 8 winning index triples
   - `board` — flat 9-element array (`''` | `'X'` | `'O'`)
   - `checkWin()` — iterates `WINS`, returns the winning triple or `null`
   - `init()` — resets board state and DOM (does not reset `score`)
   - Click handler on each cell drives all game logic
   - `score` object (`{ X, O, D }`) persists across `init()` calls (in-memory only, resets on page reload)

## Git workflow

After every change: commit with a descriptive message and push to `origin/main`.

```bash
git add <files>
git commit -m "subject line

Body explaining what and why."
git push
```

GitHub repo: https://github.com/galshiran1993/tic-tac-toe
