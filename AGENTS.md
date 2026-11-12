# Working on eduard.io

This is Eduard Giménez's personal website and product design portfolio. Eduard is a software engineer turned product designer. Treat the site as a carefully designed representation of his work, not a generic portfolio template. Read `README.md` before making changes.

## Ownership and approvals

- Eduard owns the visual design. Preserve the current design as the baseline. You may propose changes to layout, typography, color, spacing, imagery, crops, animation, or other visible design details, but **get Eduard's approval before implementing them**. An explicit request to make a particular design change counts as approval for that change; don't expand its scope silently.
- Ask before changing career history, roles, dates, project outcomes, numbers, first-person statements, or other claims about Eduard or his work. Do not invent or embellish details. `src/data/` contains the current site content, but it is not independent verification; if Eduard provides a future source of truth, use it and flag any conflicts rather than guessing.
- Do not commit, push, deploy, change hosting/domain settings, or publish content on Eduard's behalf. Make local changes and report what you changed and validated so he can review and release them.
- Keep changes focused. Do not remove or rewrite existing assets or copy merely because they look unused or could be simplified.

## Project map

- Astro 7 static site with TypeScript, plain CSS, and no client framework. Node 24.8.0 (`.nvmrc`) and npm; `package-lock.json` is the lockfile.
- `src/pages/` defines routes; `src/pages/index.astro` assembles the homepage. `src/layouts/BaseLayout.astro` owns shared metadata, canonical URLs, fonts, analytics, and the skip link.
- `src/components/` contains the page sections and shared UI. Keep section-specific CSS scoped with its component. `src/styles/tokens.css` contains design tokens; `src/styles/global.css` contains global styles.
- `src/data/site.ts` holds identity, contact, and metadata; `src/data/projects.ts` holds ordered project copy and images; `src/data/experience.ts` holds employment details. Update the relevant data file rather than duplicating content in markup where practical.
- `src/assets/projects/` contains project images processed into responsive WebP by Astro. `public/images/v4/` contains the current design's SVG exports; preserve their proportions and intended crops. `public/stylesheets/`, `public/javascript/`, and other older public assets may be legacy but are tracked: don't clean them up without a specific request.
- `public/typefaces/mori/` contains licensed PP Mori fonts. The build checks for Regular, Semibold, and Black weights; don't replace, redistribute, or move them without authorization.

## Implementation principles

- Prefer accessible, semantic HTML and Astro's static output. Preserve keyboard focus, the skip link, meaningful image alt text, heading hierarchy, and reduced-motion support. Avoid adding client-side dependencies or JavaScript unless a requested feature needs them.
- Keep copy direct and specific rather than promotional. Do not add unsupported metrics, testimonials, client details, or case-study claims. Confirm whether new work is public before publishing it.
- Respect the existing responsive layout: project cards stack below 700px, use two columns from 700px to 1099px, and become image/text rows from 1100px. Layouts should accommodate content rather than rely on fixed Figma frame heights. Any intentional visual change still needs approval.
- Preserve the existing Netlify deployment boundary: `netlify.toml` builds to `dist/`; `astro.config.mjs` generates noindex headers and disallow-all robots rules for non-production builds. `BaseLayout.astro` adds preview noindex metadata and loads Umami only when `CONTEXT=production`. Canonical URLs point to `https://eduard.io`. Do not accidentally expose previews to search engines or add production analytics to previews.
- Treat `dist/`, `_site/`, `node_modules/`, and `.astro/` as generated or ignored output, not source files. Keep formatting consistent with `.prettierrc`.

## Validation and handoff

- For relevant changes, run `npm run check`, `npm run fmt:check`, `npm run build`, and `npm test`. `npm test` builds production, deploy-preview, and branch-deploy outputs and checks key site and indexing behavior. Run `npm run dev` or `npm run preview` for visual review when appropriate.
- If a command cannot run, explain why; don't claim an unrun check passed. For visible changes, check mobile, tablet, and desktop behavior and ask Eduard to approve the proposed design before implementing it.
- Summarize changed files, checks performed, remaining risks, and any decision Eduard needs to make. Never treat passing tests as permission to publish.
