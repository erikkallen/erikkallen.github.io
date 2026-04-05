# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal Jekyll blog/portfolio site deployed to GitHub Pages at `erikkallen.nl`. Uses the `github-pages` gem to stay compatible with GitHub Pages' Jekyll environment.

## Common commands

```bash
# Install dependencies
bundle install

# Serve locally with live reload
bundle exec jekyll serve

# Build the site
bundle exec jekyll build
```

## Architecture

**Collections** (defined in `_config.yml`):
- `_posts/` — Blog posts, named `YYYY-MM-DD-title.md` or `.markdown`. Front matter uses `title`, `date`, `categories`, `tags`, `image`.
- `_projects/` — Project pages. Each project lives in its own subdirectory (e.g. `_projects/3d_printer/`). The main project page sets `sub_page: false` (or omits it); sub-pages set `sub_page: true` so they're excluded from the projects index.
- `_uploads/` — Static upload files.

**Layouts** (`_layouts/`):
- `default.html` — Base layout wrapping `head.html`, `header.html`, `footer.html` includes.
- `post.html` — For blog posts.
- `page.html` — For standalone pages.
- `project.html` / `project_sub.html` — For project pages and their sub-pages.

**Styles** (`_sass/`): Sass partials compiled into site CSS. `_variables.scss` holds shared variables; `_base.scss` holds global styles; `_syntax-highlighting.scss` handles code blocks.

**Projects index** (`projects.md`): Iterates `site.projects`, showing only entries where `sub_page` is null or false, rendering a thumbnail image and link.

## Content conventions

- Images for a post are typically stored in an `images/` directory at the root and referenced as `images/filename.jpg` in Markdown.
- Project images live alongside the project's `.md` file in its subdirectory.
- `_config.yml` sets `future: true` so posts with future dates are still built.
- Markdown renderer is kramdown.
