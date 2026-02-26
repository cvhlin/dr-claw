# Release Notes — Vibe Lab v0.1.0

**Status**: Released  
**Date**: 2026-02-21

## What's New

- **Vibe Lab** — Desktop and mobile UI for Claude Code, Cursor CLI, and Codex, with an integrated **Research Lab** for AI-driven research automation.
- **Research Lab** — Dashboard for source papers, generated ideas (Markdown + LaTeX), pipeline status, and cache artifacts.
- **InnoFlow Skills** — Built-in research pipeline skills (orchestrator, prepare-resources, idea generation, code survey, experiment dev/analysis, paper writing).
- **Responsive UI** — Chat, terminal, file tree, Git explorer, session management; works on desktop, tablet, and mobile.
- **CLI** — Single command `vibelab` (or `npx vibelab`) to start the server; `vibelab status`, `vibelab help`, `vibelab version`, `vibelab update`.

## Scope and Limits (v0.1.0)

- Idea/Experiments/Paper boards may use a single data source or placeholder in this release.
- Multi-language docs are aligned with README first; further localization may follow.
- No history rewrite; public repo is a clean fork with attribution (see NOTICE).

## How to Upgrade

- **New install**: Clone `https://github.com/bbsngg/VibeLab-beta`, then `npm install` and `npm run dev` (or `vibelab` if installed globally).
- **From upstream (Claude Code UI)**: This is a fork with a different name and repo; re-clone and configure from this repo.

## Known Issues

- Update check (`vibelab update` / npm) will work only after the package is published to npm under the name `vibelab`; until then, updates are via git pull.

## Attribution and License

- GPL-3.0. See [LICENSE](../LICENSE) and [NOTICE](../NOTICE). This project is based on [Claude Code UI](https://github.com/siteboon/claudecodeui).
