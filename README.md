# Samu Hupli - Blogi

Staattinen blogi rakennettu Astro + Tailwind CSS:llä.

## Setup

```bash
npm install
npm run dev   # Kehityspalvelin
npm run build # Build production
```

## Sisällön lisääminen

Lisää uusi postaus tiedostoon `src/content/blog/`:

```markdown
---
title: Otsikko
description: Kuvaus
pubDate: 2026-05-22
tags: [tagi1, tagi2]
---

Sisältö tähän...
```

## Deploy Verceliin

1. GitHubiin: `git init && git add . && git commit -m "Initial commit"`
2. Vercel.com → Import Project → valitse repo
3. Domain: `hupli.fi`
4. Build command: `npm run build`
5. Output directory: `dist`

## Projektin rakenne

```
src/
├── content/
│   └── blog/         # Blogipostaukset (.md)
├── layouts/
│   └── Layout.astro  # Pääsivu
├── pages/
│   ├── index.astro   # Etusivu
│   └── blog/
│       └── [slug].astro  # Yksittäinen postaus
└── styles/
    └── global.css
```
