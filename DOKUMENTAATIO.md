# Hupli.fi Blogi — Dokumentaatio

## Yleiskatsaus

Blogi on rakennettu **Astro**-staattisella sivustogeneraattorilla. Sisältö on Markdown-muodossa, ja Vercel hoitaa hostauksen.

**Teknologiat:**
- Astro 5 (staattinen sivustogeneraattori)
- Tailwind CSS 4 (tyylit)
- Vercel (hosting)
- GitHub (versionhallinta, automaattinen deploy)

**URL:** https://hupli-blog.vercel.app  
**GitHub Repo:** https://github.com/huplifi/hupli-blog

---

## Sisällön rakenne

```
workspace-blog/
├── src/
│   ├── content/
│   │   └── blog/           ← Markdown-tiedostot tänne
│   │       ├── harkinnanvaraisuus.md
│   │       └── yksinaisyyden-talous.md
│   ├── layouts/
│   │   └── Layout.astro    ← Pohjasivu (header, footer, theme toggle)
│   ├── pages/
│   │   ├── index.astro     ← Etusivu (blogilista)
│   │   ├── about.astro     ← Tietoa-sivu
│   │   ├── 404.astro       ← Virhesivu
│   │   ├── tags/
│   │   │   └── index.astro ← Tagien lista
│   │   └── blog/
│   │       └── [slug].astro ← Yksittäisen postauksen sivu
│   └── styles/
│       └── global.css      ← Globaalit tyylit
├── astro.config.mjs
└── package.json
```

---

## Uuden postauksen lisääminen

### 1. Luo Markdown-tiedosto

Luo tiedosto: `src/content/blog/[slug].md`

**Huom:** `slug` on URL-polku, käytä pieniä kirjaimia ja väliviivoja.

### 2. Frontmatter (pakollinen metadata)

```yaml
---
title: "Postauksen otsikko"
description: "Lyhyt kuvaus joka näkyy blogilistassa"
pubDate: 2026-05-23
tags: ["yhteiskunta", "filosofia", "neuropsykologia"]
---
```

**Tuetut kentät:**
| Kenttä | Pakollinen | Kuvaus |
|--------|------------|--------|
| `title` | ✅ | Postauksen otsikko |
| `description` | ✅ | Lyhyt kuvaus |
| `pubDate` | ✅ | Julkaisupäivä (YYYY-MM-DD) |
| `tags` | Ei | Tagit (lista merkkijonoja) |

### 3. Sisältö

Kirjoita sisältö Markdown-muodossa. Tuetut muodot:

```markdown
## Alaotsikko

Kappaleen tekstiä.

**Lihavoinnin** voi tehdä näin.

*Kursiivinen* teksti.

- Lista
- Toinen kohta

> Lainaus

---

Erotinta käytetään näin.

### Pienempi alaotsikko

1. Numeroitu lista
2. Toinen kohta
```

---

## Obsidian-integraatio

### Käsinkirjoittaminen

1. **Obsidianissa:** Kirjoita postaus
2. **Kopioi sisältö** Markdown-tiedostoksi
3. **Liitä** `src/content/blog/[slug].md`
4. **Pushaa** GitHubiin

### Obsidian Template (vapaaehtoinen)

Voit luoda Obsidianiin templaten uusille blogipostauksille:

```
---
title: "{{TITLE}}"
description: "{{DESC}}"
pubDate: {{DATE}}
tags: []
---

# {{TITLE}}

Kirjoita tähän...
```

### Obsidian → Blogi -workflow

1. Kirjoita Obsidianissa
2. Vie sisältö päähän:
   - copy/paste suoraan tiedostoon
   - tai käytä Obsidianin "Export to Markdown" -pluginia
3. Pushaa: `git add . && git commit -m "Uusi postaus: [otsikko]" && git push`
4. Vercel buildaa automaattisesti (~30s)

---

## Git-komennot

```bash
# Siirry projektikansioon
cd ~/.openclaw/workspace-blog

# Lisää uusi tiedosto
git add .

# Tee commit
git commit -m "Uusi postaus: [otsikko]"

# Pushaa (Vercel deployaa automaattisesti)
git push
```

**tai** jos haluat tehdä commitin ja pushin yhdessä:
```bash
git add . && git commit -m "Uusi postaus: [otsikko]" && git push
```

---

## Theme (vaalea/tumma)

Sivustolla on light/dark-toggle oikealla ylhäällä.

**Oletus:** Tumma (dark)

**Vaihtaminen:** Paina ☀/☾ -nappia

**Tietoa:** Valinta tallennetaan selaimen localStorageen.

---

## Vercel Deploy

Deploy tapahtuu automaattisesti GitHub pushista.

**Build-komennon tulos:**  
`npm run build` → `dist/`-kansio

**Jos build epäonnistuu:**
1. Katso lokit: Vercel Dashboard → Deployments → Logs
2. Korjaa virhe
3. Pushaa uudelleen

---

## Lisenssi ja oikeudet

© 2026 Samu Hupli. Kaikki oikeudet pidätetään.

---

*Päivitetty: 2026-05-23*