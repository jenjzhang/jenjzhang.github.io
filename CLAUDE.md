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

- **`_pages/about.md`** — the homepage (permalink: `/`), rendered by the custom `_layouts/home.html` + `assets/css/home.scss` (not the Academic Pages theme). The markdown body is the left-column About text; front matter holds the right-column `affiliation`, `email_text`, and `off_the_clock_title` / `off_the_clock` list. Name, photo, and link icons come from `author` in `_config.yml` (set `author.cv` to show the CV link).
- **`_publications/`** — one `.md` file per paper. Front matter fields: `title`, `collection: publications`, `category` (`manuscripts`, `conferences`, `workshops`, `posters`), `date`, `venue`, `paperurl`, `citation`, `excerpt`. Papers with `selected: true` appear under "Selected work" on the homepage, using `authors` (markdown; bold your name), `venue_short`, `summary`, `links` (list of `label`/`url`), and optional `thumbnail` (figure boxes only show when `paper_figures: true` in `_pages/about.md`; a `[figure]` placeholder fills any without a thumbnail).
- **`_talks/`** — one `.md` file per talk (currently set to `output: false` in `_config.yml`, so no individual pages are generated).
- **`_data/navigation.yml`** — controls which links appear in the header nav. Most are commented out; uncomment to enable.
- **`_config.yml`** — site-wide settings: author info, social links, publication categories, Jekyll plugins.

The `_data/cv.json` and `_pages/cv.md`/`cv-json.md` exist in the template but are not actively used (nav links are commented out).

## Key customizations

- **Favicon**: `_includes/head/custom.html` — custom JZ favicon added here.
- **Email**: displayed on the homepage as plain text (`[at]`, `[dot]`, from `email_text` in `about.md`) to avoid scraping.
- **Publications page**: `/publications/` and `/publication/<slug>` still build with the old theme but are not linked from the homepage.

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
