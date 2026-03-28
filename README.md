# Profile — portfolio site

[![CI](https://github.com/OrithmicSoftware/profile/actions/workflows/ci.yml/badge.svg)](https://github.com/OrithmicSoftware/profile/actions/workflows/ci.yml)
[![Pages](https://github.com/OrithmicSoftware/profile/actions/workflows/deploy-github-pages.yml/badge.svg)](https://github.com/OrithmicSoftware/profile/actions/workflows/deploy-github-pages.yml)
[![Labels](https://github.com/OrithmicSoftware/profile/actions/workflows/sync-labels.yml/badge.svg)](https://github.com/OrithmicSoftware/profile/actions/workflows/sync-labels.yml)

Single-page résumé and portfolio for **Vladislav Sokolov** (software architect & technical lead), built with **React**, **TypeScript**, **Vite**, and **Tailwind CSS**.

**Repository:** [github.com/OrithmicSoftware/profile](https://github.com/OrithmicSoftware/profile) (under org [OrithmicSoftware](https://github.com/OrithmicSoftware)).

**Live site (project Pages):** **[https://orithmicsoftware.github.io/profile/](https://orithmicsoftware.github.io/profile/)**

### Turn on the correct Pages URL

Your app is built with **`base: '/profile/'`** so it only works at that path under the org’s GitHub Pages host (repo name = `profile`).

1. **Org Actions (if deploy fails):** [OrithmicSoftware organization settings](https://github.com/organizations/OrithmicSoftware/settings/actions) → **General** → allow **Actions**, and set **Workflow permissions** to **Read and write** (needed to push the `gh-pages` branch).
2. **Run deploy:** push to `main` or open **Actions → Deploy to GitHub Pages → Run workflow**. Wait until it finishes and the `gh-pages` branch exists.
3. **Point Pages at `gh-pages`:** In [profile → Settings → Pages](https://github.com/OrithmicSoftware/profile/settings/pages):
   - **Build and deployment** → **Source:** *Deploy from a branch*
   - **Branch:** `gh-pages` / **/(root)** → Save  
4. After a short wait, the site should load at **`https://orithmicsoftware.github.io/profile/`** (not `pun4drunk.github.io` and not `/CV/` — those are old hosts/paths).

**Preview like production Pages:** `npm run preview:pages`

## Scripts

| Command | Description |
|--------|-------------|
| `npm run dev` | Local dev server |
| `npm run build` | Typecheck + production build (`/profile/` base for Pages) |
| `npm run preview` | Preview production build locally (`/` base) |
| `npm run preview:pages` | Build + preview with **`/profile/`** base (same as GitHub Pages) |
| `npm run lint` | ESLint (warnings fail) |
| `npm run lint:fix` | ESLint with `--fix` |
| `npm run typecheck` | `tsc -b --noEmit` |
| `npm run check` | Lint → typecheck → build |

## GitHub Pages

- **Public URL:** `https://orithmicsoftware.github.io/profile/`
- **Source:** branch **`gh-pages`**, folder **`/` (root)** — content is published by [`.github/workflows/deploy-github-pages.yml`](.github/workflows/deploy-github-pages.yml) (lint, typecheck, `npm run build`, then [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages) pushes `dist/`).
- **Base path:** [`vite.config.ts`](vite.config.ts) uses `base: '/profile/'` in production. If you **rename the repository**, change `base` to `'/<new-repo-name>/'`.

## CI

[`.github/workflows/ci.yml`](.github/workflows/ci.yml) runs on pushes and pull requests to `main` / `master`: install, lint, typecheck, build.

## Issue labels

Label definitions live in [`.github/labels.yml`](.github/labels.yml). Sync them to the repo: **Actions → Sync labels → Run workflow**.

If the workflow fails with **403** or **Resource not accessible by integration**, the repository (or organization) default is probably **read-only** for `GITHUB_TOKEN`. Fix it under **Settings → Actions → General → Workflow permissions**: choose **Read and write permissions** and save, then re-run **Sync labels**. Issues do not need to be enabled for the Labels API to work.

## Requirements

- Node.js **22** (recommended; CI uses 22)

## License

Private / all rights reserved unless you add a license file.
