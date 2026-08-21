# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository state

This repository now contains a single-file web game:

- `index.html` — a self-contained 2048 game (HTML + CSS + vanilla JS, no build step, no
  dependencies). Open it directly in a browser, or serve the directory with any static file
  server (e.g. `python3 -m http.server`).
- `README.md` and `readme.md` — two separate, case-differing placeholder files left over from
  the repo's initial auto-generated scaffolding. They hold "Unique Commit" stub content, not
  real documentation, and are unrelated to the game.
- Earlier git history includes auto-generated "Auto commit for 115691 - N" commits.

There is no build, lint, or test tooling — `index.html` is plain HTML/CSS/JS run directly by
the browser. Do not assume a framework or bundler is present.

## Architecture (index.html)

Everything lives in one file, structured top to bottom as:

- **Styles**: CSS custom properties (`--bg`, `--board-bg`, tile colors) drive the theme; the
  board uses two overlapping grids — `.grid-bg` (static empty-cell background) and
  `.tile-layer` (absolutely-positioned tiles animated via `top`/`left` transitions).
- **Game state**: a single IIFE holds `grid` (4x4 array of tile objects or `null`), `score`,
  `best` (persisted in `localStorage` under `2048-best`), and flags (`won`, `over`,
  `keepPlaying`).
- **Core loop**: `move(dir)` walks the grid in the right traversal order for the direction
  (`traverse`/`vector` helpers), slides/merges tiles, then calls `addRandomTile()` and
  `render()`. Win/loss is detected after each move (`isGameOver`) and shown via the
  `.overlay` element.
- **Input**: arrow keys / WASD via `keydown`, plus touch swipe detection on the board
  container for mobile.

When editing the game, keep it dependency-free and in a single file unless the user asks for a
build setup — that's a deliberate choice for a small, self-contained deliverable.
