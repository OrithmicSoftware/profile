# CV — portfolio site

[![CI](https://github.com/pun4drunk/CV/actions/workflows/ci.yml/badge.svg)](https://github.com/pun4drunk/CV/actions/workflows/ci.yml)
[![Pages](https://github.com/pun4drunk/CV/actions/workflows/deploy-github-pages.yml/badge.svg)](https://github.com/pun4drunk/CV/actions/workflows/deploy-github-pages.yml)
[![Labels](https://github.com/pun4drunk/CV/actions/workflows/sync-labels.yml/badge.svg)](https://github.com/pun4drunk/CV/actions/workflows/sync-labels.yml)

Single-page résumé and portfolio for **Vladislav Sokolov** (software architect & technical lead), built with **React**, **TypeScript**, **Vite**, and **Tailwind CSS**.

**Live site:** [https://pun4drunk.github.io/CV/](https://pun4drunk.github.io/CV/) (after GitHub Pages is enabled for the `gh-pages` branch.)

## Scripts

| Command | Description |
|--------|-------------|
| `npm run dev` | Local dev server |
| `npm run build` | Typecheck + production build (`/CV/` base for Pages) |
| `npm run preview` | Preview production build locally |
| `npm run lint` | ESLint (warnings fail) |
| `npm run lint:fix` | ESLint with `--fix` |
| `npm run typecheck` | `tsc -b --noEmit` |
| `npm run check` | Lint → typecheck → build |

## GitHub Pages

- **Source:** deploy from branch **`gh-pages`** (root).
- **Workflow:** [`.github/workflows/deploy-github-pages.yml`](.github/workflows/deploy-github-pages.yml) — runs lint, typecheck, build, then pushes `dist/` via [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages).
- **Base path:** production builds use `base: '/CV/'` in [`vite.config.ts`](vite.config.ts). If you rename the repository, update `base` to match.

## CI

[`.github/workflows/ci.yml`](.github/workflows/ci.yml) runs on pushes and pull requests to `main` / `master`: install, lint, typecheck, build.

## Issue labels

Label definitions live in [`.github/labels.yml`](.github/labels.yml). Sync them to the repo: **Actions → Sync labels → Run workflow**.

If the workflow fails with **403** or **Resource not accessible by integration**, the repository (or organization) default is probably **read-only** for `GITHUB_TOKEN`. Fix it under **Settings → Actions → General → Workflow permissions**: choose **Read and write permissions** and save, then re-run **Sync labels**. Issues do not need to be enabled for the Labels API to work.

## Requirements

- Node.js **22** (recommended; CI uses 22)

## License

Private / all rights reserved unless you add a license file.
