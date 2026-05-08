# AGENTS.md

## Cursor Cloud specific instructions

This is an **Astro Blog** static site deployed to Cloudflare Workers. Single-package project, no monorepo, no databases, no backend services.

### Quick reference

| Task | Command |
|------|---------|
| Dev server | `npm run dev` (serves at `localhost:4321`) |
| Build | `npm run build` |
| Type check | `npx tsc --noEmit` |
| Full check | `npm run check` (build + tsc + wrangler deploy --dry-run) |
| Preview via Wrangler | `npm run preview` |

See `README.md` for the full commands table.

### Notes

- The dev server uses Astro's built-in HMR; file changes in `src/` are reflected immediately.
- Blog content lives in `src/content/blog/` as Markdown/MDX files with frontmatter validated by `src/content.config.ts`.
- The `@astrojs/cloudflare` adapter emits warnings during build about being unnecessary for static-only sites and about `sharp` not being available at runtime — these are expected and harmless.
- `npm run check` includes `wrangler deploy --dry-run` which requires Cloudflare credentials. For local-only validation, use `npm run build && npx tsc --noEmit` instead.
- Package manager is **npm** (lockfile: `package-lock.json`).
