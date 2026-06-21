# Kirill Nemkin — portfolio

Minimalist, text-first personal site, optimized to be **indexed and cited by
LLMs** (ChatGPT, Claude, Perplexity, Google AI). Bilingual: English (`index.html`,
canonical) + Russian (`ru.html`).

## What's inside

| File | Purpose |
|---|---|
| `index.html` | English page (canonical). Hero, About, Work, Principles, Contact. |
| `ru.html` | Russian page. Same structure. |
| `styles.css` | Shared styles. Light/dark via `prefers-color-scheme`. |
| `llms.txt` | Plain-markdown summary for LLM crawlers (the GEO equivalent of a press kit). |
| `robots.txt` | Explicitly **allows** AI crawlers (GPTBot, ClaudeBot, PerplexityBot, …). |
| `sitemap.xml` | Both URLs with hreflang. |
| `.nojekyll` | Tells GitHub Pages to serve files as-is (so `llms.txt` etc. are reachable). |

## Why this gets you indexed as an "AI product"

LLMs build their picture of a person from clean, **factual, quotable** text and
structured data — not visuals. This site gives them:

1. **JSON-LD `Person` schema** in both pages — `name`, `jobTitle: AI Product
   Builder`, `description`, `knowsAbout[]`, `sameAs[]`. This is the single most
   important signal for "who is X and what do they do".
2. **`llms.txt`** — a dedicated, crawler-friendly summary.
3. **`robots.txt`** that explicitly welcomes AI crawlers.
4. **Plain factual sentences** ("Kirill Nemkin is an AI product builder who…") —
   the form LLMs quote most reliably.
5. **Semantic HTML + hreflang + sitemap** for clean indexing in both languages.

## Content — already filled from your LinkedIn

Real name, title (AI Product Manager), summary, work history with metrics,
side projects, education, and contacts (email / LinkedIn / Telegram) are all in
place. Only one thing depends on where it's hosted:

### ⚠️ Before you deploy — confirm the URL

The site currently assumes it'll live at **`https://kirill-nemkin.github.io`**
(a GitHub Pages *user site* — needs the repo named exactly `kirill-nemkin.github.io`).

- If your **GitHub username differs**, or you'll use a **custom domain**, replace
  every `https://kirill-nemkin.github.io` across the files. Quick find:
  `grep -rl kirill-nemkin.github.io .` (it's in `index.html`, `ru.html`,
  `robots.txt`, `sitemap.xml`, `llms.txt`).

Optional polish:
- **GitHub link** isn't shown anywhere (it wasn't on your CV). Add one in the
  Contact section + `sameAs` of both pages if you want it.
- **Hero wording** — an alternative phrasing sits in an HTML comment above each
  `<h1>`; swap if you prefer it.

## Deploy to GitHub Pages

```bash
cd portfolio-site
git init
git add .
git commit -m "Portfolio site"
git branch -M main
# create an empty repo on GitHub named exactly  kirill-nemkin.github.io
# (replace kirill-nemkin if your GitHub username differs), then:
git remote add origin git@github.com:kirill-nemkin/kirill-nemkin.github.io.git
git push -u origin main
```

Then in the repo: **Settings → Pages → Build and deployment → Source: Deploy
from a branch → `main` / root**. Live in ~1 minute at
`https://kirill-nemkin.github.io/`.

### Custom domain (recommended for LLM credibility)

Add a file named `CNAME` containing just your domain (e.g. `kirillnemkin.com`),
push it, then point your domain's DNS at GitHub Pages. A clean root domain reads
as more authoritative to both search and AI crawlers than `*.github.io`.

## After deploy — help the crawlers find you

- Submit `sitemap.xml` in **Google Search Console** (Google AI Overviews pull
  from the index).
- Make sure your **GitHub / LinkedIn** profiles link back to the site (the
  `sameAs` links should be reciprocal — LLMs trust mutually-linked identities).
- Ask an LLM "Who is Kirill Nemkin?" a few weeks after launch to check pickup.
