# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Project

Arcade Vault — a platform for playing games online and competing for the highest score ("Es una plataforma para jugar online y competir por la mayor cantidad de puntos").

The repo is currently a freshly scaffolded `create-next-app` project (App Router, TypeScript, Tailwind CSS v4) with no product code written yet — `app/page.tsx` and `app/layout.tsx` still contain the default starter content.

## Next.js version warning

This project pins `next@16.2.10` and `react@19.2.4` — newer than what you likely know from training. Per `AGENTS.md`, **read the relevant guide under `node_modules/next/dist/docs/` before writing code that touches routing, data fetching, caching, or config**, and heed any deprecation notices found there. Do not assume older Next.js App Router APIs/conventions still apply without checking. Key doc locations:
- `node_modules/next/dist/docs/01-app/01-getting-started/` — routing, layouts/pages, data fetching, caching, revalidation, route handlers
- `node_modules/next/dist/docs/01-app/02-guides/` — task-specific guides
- `node_modules/next/dist/docs/03-architecture/` — architectural concepts

## Commands

```bash
npm run dev      # start dev server
npm run build    # production build
npm run start    # run production build
npm run lint     # eslint (flat config via eslint.config.mjs)
```

There is no test suite configured yet.

## Spec Driven Design workflow

This project follows spec-driven development using the `/spec` and `/spec-impl` workflow from the [fernando-skills](https://github.com/Klerith/fernando-skills) skill pack:

```bash
npx skills@latest add Klerith/fernando-skills
```

Prefer writing/updating a spec before implementing non-trivial features, then implement against that spec, per the practices documented in that skills repo.

## Architecture notes

- App Router only (`app/` directory) — no `pages/` router.
- Styling via Tailwind CSS v4 through `@tailwindcss/postcss` (see `postcss.config.mjs`), with global styles in `app/globals.css`.
- Path alias `@/*` maps to the repo root (`tsconfig.json`).
- ESLint uses the flat config format (`eslint.config.mjs`), extending `eslint-config-next`'s `core-web-vitals` and `typescript` rule sets.
