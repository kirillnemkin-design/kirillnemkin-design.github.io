# Kirill Nemkin — portfolio (Jekyll)

Editorial personal site, optimized to be **indexed and cited by LLMs**, with a
Markdown blog. Bilingual: English (`/`) + Russian (`/ru.html`). Built with
**Jekyll** (GitHub Pages builds it automatically — no local tooling needed).

Live: **https://kirillnemkin-design.github.io/**

## ✍️ How to add a blog post (the main thing)

Create a Markdown file in `_posts/` named `YYYY-MM-DD-slug.md`. Easiest way:
on GitHub → open the `_posts` folder → **Add file → Create new file**. Paste:

```markdown
---
lang: en          # en or ru — controls which blog index it appears in
title: "My post title"
date: 2026-07-01
description: "One sentence for search engines and LLMs."
---

Write the post in **Markdown**. Headings with `##`, lists, `> quotes`, links.
```

Commit. GitHub rebuilds in ~1 minute and the post appears automatically on
`/blog/` (or `/ru/blog/` for `lang: ru`), in the homepage "Posts" teaser, and
in the RSS feed `/feed.xml`. No HTML, nothing else to touch.

## Structure

| Path | What |
|---|---|
| `_config.yml` | Site settings (title, URL, plugins). |
| `_layouts/` | `default` (head + JSON-LD + nav + footer), `page`, `post`. |
| `_includes/nav.html` | Header / nav (EN + RU). |
| `index.html` / `ru.html` | Home pages (hero, about, work, path, posts, contact). |
| `blog.html` / `blog-ru.html` | Post indexes (`/blog/`, `/ru/blog/`). |
| `_posts/` | Blog posts in Markdown. |
| `assets/styles.css` | All styling. |
| `llms.txt`, `robots.txt` | LLM/GEO layer (sitemap + feed are auto-generated). |

## Tweaking the look

`assets/styles.css`, top `:root` block:
- `--accent` — the one accent color (currently vermilion `#c0392b`).
- `--serif` — heading font; `--sans` — body font.
- `--bg`, `--text`, `--muted` — base colors.

Hero wording lives in `index.html` / `ru.html`.

## LLM / GEO layer

- JSON-LD `Person` + `WebSite` in `_layouts/default.html` (jobTitle, knowsAbout,
  sameAs, address, alumniOf).
- `llms.txt` — crawler-friendly summary.
- `robots.txt` — explicitly allows GPTBot, ClaudeBot, PerplexityBot, etc.
- `sitemap.xml` (jekyll-sitemap) and `feed.xml` (jekyll-feed) are generated on build.

## Deploy

Repo is the GitHub Pages user-site `kirillnemkin-design.github.io` → served at
the root URL. Pages auto-builds on every push/commit to `main`. After deploy,
in Google Search Console submit `https://kirillnemkin-design.github.io/sitemap.xml`,
and add the site link to your LinkedIn so the identity is mutually linked.

## Local preview (optional)

Needs Ruby ≥ 2.7: `bundle install && bundle exec jekyll serve` → http://localhost:4000
