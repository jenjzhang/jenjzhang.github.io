# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About this site

This is Jennifer Zhang's personal academic website ([jenjzhang.github.io](https://jenjzhang.github.io)), built on the [Academic Pages](https://academicpages.github.io/) Jekyll template (forked from Minimal Mistakes). Jennifer is a first-year Statistics PhD student at UC Berkeley, with research interests in causal inference, causal ML, and LLM evaluation.

## Running locally

```bash
bundle install
bundle exec jekyll serve -l -H localhost
```

Site is served at `localhost:4000`. The `-l` flag enables live reload. Changes to `_config.yml` require a server restart.

Alternatively, using Docker:
```bash
docker compose up
```

## Content architecture

All user-facing content lives in a small set of places:

- **`_pages/about.md`** — the homepage (permalink: `/`). This is the main bio/research description.
- **`_publications/`** — one `.md` file per paper. Front matter fields: `title`, `collection: publications`, `category` (`manuscripts` or `conferences`), `date`, `venue`, `paperurl`, `citation`, `excerpt`.
- **`_talks/`** — one `.md` file per talk (currently set to `output: false` in `_config.yml`, so no individual pages are generated).
- **`_data/navigation.yml`** — controls which links appear in the header nav. Most are commented out; uncomment to enable.
- **`_config.yml`** — site-wide settings: author info, social links, publication categories, Jekyll plugins.

The `_data/cv.json` and `_pages/cv.md`/`cv-json.md` exist in the template but are not actively used (nav links are commented out).

## Key customizations

- **Favicon**: `_includes/head/custom.html` — custom JZ favicon added here.
- **Email**: displayed in `_pages/about.md` as plain text (`AT`, `DOT`) to avoid scraping.
- **Publications nav**: commented out in `_data/navigation.yml` — the publications collection still builds pages at `/publication/<slug>` but is not linked from the header.

## Publication front matter

MathJax is supported in publication titles and excerpts using `$$...$$` delimiters (not `$...$`).

```yaml
---
title: "Title with math $$E=mc^2$$"
collection: publications
category: conferences   # or: manuscripts
permalink: /publication/YYYY-MM-DD-slug
excerpt: 'Short description'
date: YYYY-MM-DD
venue: 'Venue Name'
paperurl: 'https://...'
citation: 'Zhang, J. (Year). ...'
---
```
