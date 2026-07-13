# Repository Guidelines

## Project Structure & Module Organization

This repository is a dependency-free static dashboard. `index.html` is both the source and the deployable artifact: it contains all markup, styles, World Cup team/player data, index calculations, and interaction code. `preview.png` is the README screenshot and should be refreshed after visible UI changes. `README.md` documents the data snapshot, formulas, local use, and GitHub/Cloudflare Pages publishing. `.nojekyll` keeps GitHub Pages from applying Jekyll processing.

Keep changes focused within these files; do not introduce a build system solely to edit the dashboard. In `index.html`, preserve the separation between shared CSS, dashboard markup, the main data/rendering IIFE, and tooltip behavior.

## Build, Test, and Development Commands

No install or build step is required.

- `python3 -m http.server 8000` serves the repository locally.
- `open http://localhost:8000` opens that server on macOS.
- `git diff --check` detects whitespace errors before committing.
- `git status --short` confirms that only intended files changed.

Opening `index.html` directly also works, but a local server more closely matches static hosting.

## Coding Style & Naming Conventions

Use two-space indentation in HTML, CSS, and JavaScript, and follow the style of the surrounding block. Use `camelCase` for JavaScript functions and state fields, kebab-case for CSS classes, and the existing `wc-` prefix for dashboard IDs. Scope dashboard rules beneath `#wc26-efficiency`, reuse the root CSS variables, and keep Russian UI copy consistent. When rendering data into HTML strings, pass dynamic text through `esc()`.

Keep team and player object fields stable because sorting, filtering, and index calculations depend on them. If adding an external asset origin, update the Content Security Policy deliberately.

## Testing Guidelines

There is currently no automated test suite or coverage requirement. Manually smoke-test both tabs, sorting, filters, search, pagination, team selection, chart resizing, tooltips, theme switching, and reset controls. Check desktop and narrow mobile widths, keyboard focus, and the offline font fallback. For data updates, verify displayed totals and calculated rankings against the cited snapshot sources, then update `README.md` and `preview.png` when applicable.

## Commit & Pull Request Guidelines

History uses short, capitalized, imperative subjects, for example `Update match data and responsive layout`. Keep each commit focused on one data, design, or documentation concern. Pull requests should explain the user-visible effect, identify data sources and snapshot dates, list manual checks, and include before/after screenshots for visual changes. Link related issues when available.
