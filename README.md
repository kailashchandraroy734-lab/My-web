# ARONX BOT WORLD

A presentation-first landing page for a four-bot Discord companion network. The site is intentionally frontend-only: bot data and configurable invite links live in `src/data/bots.ts`, with public Vite environment variables supplying Discord application IDs at build time.

## Local setup

```bash
npm install
npm run dev
```

Using pnpm:

```bash
pnpm install
pnpm dev
```

Copy `.env.example` to `.env.local` and set the values before running the dev server:

```bash
VITE_BOT1_CLIENT_ID=your-aron-application-id
VITE_BOT2_CLIENT_ID=your-cherry-application-id
VITE_BOT3_CLIENT_ID=your-guardian-application-id
VITE_BOT4_CLIENT_ID=your-quest-application-id
VITE_SUPPORT_SERVER=https://discord.gg/your-community
```

Invite URLs are generated in `src/data/bots.ts`. If an ID is empty, the UI shows a safe configuration message instead of linking to a fake or incomplete OAuth URL.

## Build

```bash
npm run typecheck
npm run build
```

The production bundle is emitted by Vite in `dist/`.

## Vercel deployment

1. Import this repository into Vercel and keep the framework preset as **Vite**.
2. Add the five `VITE_` variables from `.env.example` under Project Settings → Environment Variables.
3. Deploy. The static Vite output will be built with `npm run build`.

Because these variables are public frontend configuration, never place client secrets or bot tokens in them. Discord application client IDs and a public support invite are the only values this page needs.