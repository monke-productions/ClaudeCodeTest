# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the project

No build step or dependencies. Open `tictactoe.html` directly in a browser:

```bash
open tictactoe.html
```

## Architecture

The entire app is a single self-contained file (`tictactoe.html`) with no external dependencies. HTML, CSS, and JS all live in that one file.

**Game state** lives in three module-level variables:
- `board` — 9-element array (`null | 'X' | 'O'`), indexed 0–8 left-to-right, top-to-bottom
- `current` — whose turn it is (`'X'` or `'O'`)
- `scores` — `{ X, O, tie }` object, persists across rounds (reset only on page reload)

**Win detection** (`getWin`) checks all 8 winning lines defined in the `WINS` constant against the current `board` array.

**DOM updates** happen directly inline in the click handler and in `updateScores`/`resetGame` — there is no rendering layer or state sync abstraction. CSS classes drive visual state: `.taken` blocks re-clicks, `.win` triggers the pulse animation, `.x`/`.o` set player colors.

## Git workflow

- Commit after each meaningful change with a concise message describing *what changed and why*
- Push to `origin/main` after each commit to keep GitHub in sync
- Use `git log --oneline` to review history before starting new work
