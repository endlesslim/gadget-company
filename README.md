# 가제트 컴퍼니 (Gadget Company)

Next.js + TypeScript on Vercel. Boring tech first: App Router, Tailwind CSS, static-first rendering. No novelty tax until there's a durable reason.

## Local dev

```bash
npm install
npm run dev
```

Opens at [http://localhost:3000](http://localhost:3000).

## Stack

| Layer | Choice | Why |
|---|---|---|
| Framework | Next.js 16 App Router | Server Components, file-based routing, zero-config Vercel deploy |
| Language | TypeScript | Catches mistakes at build time, not in prod |
| Styling | Tailwind CSS v4 | Utility-first; no runtime overhead |
| Deploy | Vercel | Git-integrated preview deploys out of the box |

## Deploy pipeline

- **Production**: push to `main` → Vercel auto-deploys to `https://default-ten-opal.vercel.app`
- **Preview**: push to any branch → Vercel creates a unique preview URL per commit

The Vercel project (`_default`) is linked to this repo via `.vercel/project.json`.

## Environment variables

**Rule: never commit secrets. Use `vercel env` for anything shared.**

```bash
# Add a variable to all environments
vercel env add MY_SECRET

# Add to a specific environment (production | preview | development)
vercel env add DATABASE_URL production

# Pull all env vars to a local .env.local (gitignored)
vercel env pull .env.local

# List all vars
vercel env ls
```

Variables set via `vercel env` are available in CI, preview deploys, and production automatically — no manual copy-paste across environments.

For local-only overrides, use `.env.local` (already in `.gitignore`). Never put secrets in `.env`, `next.config.ts`, or committed files.

## Lint / typecheck

```bash
npm run lint      # ESLint
npx tsc --noEmit  # TypeScript
```
