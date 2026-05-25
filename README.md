# Access Training

Marketing site for Access Training, built with Astro + Tailwind CSS v4 and deployed automatically to Cloudflare Pages.

## Tech stack

- [Astro 5](https://astro.build) — static site generator
- [Tailwind CSS v4](https://tailwindcss.com) — utility-first styling, CSS-first config
- Design tokens in `src/tokens/` (colors, typography, spacing on a 2px grid)
- Deploy: GitHub Actions → Cloudflare Pages via Wrangler

## Local development

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # output -> dist/
npm run preview  # serve dist/
```

## Project structure

```
src/
  tokens/         # CSS variables: colors, typography, spacing
  styles/         # global.css — imports tokens + Tailwind v4 @theme
  layouts/        # Layout.astro — shared page shell
  components/     # Astro components (Header, Footer, Hero, sections...)
  pages/          # routes (index.astro)
public/           # static assets
```

## Design system

- Figma (work file): https://www.figma.com/design/vxECrM5S8i6ywTUOvBSvre
- Figma (design system): https://www.figma.com/design/iFkgV6kWJkLOlD9Zp44WQC
- Color variables follow `brand/*`, `neutral/*`, `bg/*` convention.
- Spacing is on a strict 2px grid (`--space-1 = 2px`).
- Component names are kebab-case, atomic naming.

## Deployment

Every push to `main` triggers `.github/workflows/deploy.yml`, which:

1. Installs deps with `npm ci`
2. Runs `npm run build` → `dist/`
3. Deploys `dist/` to Cloudflare Pages project `access-training`

### Required GitHub secrets

| Secret | Where to get it |
|---|---|
| `CLOUDFLARE_API_TOKEN` | https://dash.cloudflare.com/profile/api-tokens (needs Pages: Edit) |
| `CLOUDFLARE_ACCOUNT_ID` | https://dash.cloudflare.com/ → right sidebar |

Production URL: https://access-training.pages.dev
