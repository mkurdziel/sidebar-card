# Repository Guidelines

## Project Structure & Module Organization
- `src/`: TypeScript source. Main entry is `src/sidebar-card.ts` (LitElement custom element `sidebar-card`).
- `dist/`: Build output. Primary artifact is `dist/sidebar-card.js` used by Home Assistant.
- `screenshots/`: Images used in the README.
- Root config: `rollup.config.js`, `tsconfig.json`, `eslint.config.mjs`, `package.json`, `hacs.json`.

## Build, Test, and Development Commands
- `npm install`: Install dependencies.
- `npm start`: Run Rollup in watch mode and serve `dist/` at `http://localhost:5005` with CORS. Edit `src/sidebar-card.ts`; output updates automatically.
- `npm run build`: Produce a production build in `dist/` (minified, no sourcemaps).
- `npm run lint`: Lint TypeScript files in `src/`.

Example local HA resource URL: `/hacsfiles/sidebar-card/sidebar-card.js` or `/local/sidebar-card.js` (if you copy from `dist/`).

## Coding Style & Naming Conventions
- Language: TypeScript (ES module output). Use LitElement patterns and Home Assistant helpers.
- Indentation: 2 spaces. Prefer single quotes; trailing semicolons OK.
- Filenames: kebab-case (e.g., `sidebar-card.ts`).
- Classes: PascalCase (e.g., `SidebarCard`); variables/functions: camelCase.
- Linting/formatting: ESLint + Prettier. Run `npm run lint` before pushing.

## Testing Guidelines
- Framework: None in-repo. Perform manual verification in Home Assistant.
- Steps: `npm run build`, add/update the resource in HA, and validate sidebar behavior, menu navigation, clock/date rendering, and styling across breakpoints.
- Tip: Use `?sidebarOff` to temporarily disable the sidebar for troubleshooting. Set `debug: true` in config to surface console logs.

## Commit & Pull Request Guidelines
- Commits: Use clear, scoped messages; Conventional Commits are encouraged (e.g., `fix(sidebar): restart clock on reconnect`).
- PRs: Include a concise description, linked issues, and screenshots/GIFs for UI changes. Note breaking changes in README if applicable.
- Build Artifacts: When modifying `src/`, run `npm run build` and include the updated `dist/sidebar-card.js` so manual installs remain usable.
- Style: Ensure `npm run lint` passes and avoid unrelated refactors. Keep changes narrowly focused.

