# Copilot instructions for this repository

- This repository is a Jekyll-based academic personal website, not a typical app backend or SPA. Most work is content and static-site configuration.
- The main configuration is `_config.yml`: it defines collections (`_publications`, `_teaching`, `_portfolio`, `_talks`, `_pages`), site metadata, default layouts, plugins, and archive paths.
- Content is primarily Markdown with YAML front matter. Example: `_publications/2023_ARCSnake_TB1.md` and `_talks/2012-03-01-talk-1.md` include fields such as `title`, `collection`, `date`, `venue`, `permalink`, and `citation`.
- Pages that are not collection items live in `_pages/` (for example `_pages/mentoring.md`) and usually include `layout`, `title`, `permalink`, and `author_profile` in front matter.
- The site theme and reusable UI live in `_includes/` and `_layouts/`. Prefer updating shared templates there instead of duplicating markup across individual pages.
- `_data/*.yml` and `cv.json` are the data source for navigation, authorship, and CV content. Update those instead of hard-coding profile details in multiple places.
- `files/`, `images/`, and `assets/` are the static asset directories. Use paths like `/files/...` or `/images/...` in Markdown; do not hand-edit generated output under `_site/`.
- `README.md` is the authoritative local setup guide. Use `bundle install`, then `bundle exec jekyll serve -l -H localhost` for a local preview.
- Container-based preview is also supported: `docker compose up` serves the site at `http://localhost:4000`.
- `package.json` is not an app runtime; it only defines JS minification via `npm run build:js` / `npm run uglify` and the watcher `npm run watch:js`.
- Content generation scripts live in `markdown_generator/` and are the preferred way to produce consistent publication/talk entries from TSV data (`talks.tsv`, `publications.tsv`).
- `talkmap.py` is a one-off geocoding script for talk locations; it reads `_talks/*.md`, geocodes `location`, and writes output in `talkmap/`.
- This site uses Jekyll plugins from `_config.yml` (`jekyll-feed`, `jekyll-gist`, `jekyll-paginate`, `jekyll-sitemap`, `jekyll-redirect-from`, `jemoji`). Prefer plugin-compatible Markdown/Liquid patterns rather than introducing custom build tooling.
- Keep permalinks and collection names stable; many parts of the site assume URLs like `/publication/...`, `/talks/...`, and `/mentoring/`.
- The repository is a personal academic portfolio, so edits should preserve the existing structure and style instead of introducing a new framework or app architecture.
- When adding or changing content, match the existing front matter conventions used by neighboring files in each collection rather than inventing new YAML keys.
- If a page is a custom landing page, use the pattern from `_pages/*.md` and keep `layout: archive` or `layout: single` consistent with the surrounding site.
- Most changes are content-first: update a collection item, a page file, a YAML data file, or a shared include/layout, then preview with Jekyll.
