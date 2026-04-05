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

**Styles**: Tailwind CSS is loaded via CDN (`?plugins=typography`) in `_includes/head.html`. The Tailwind typography `prose` class is used for all post/page/project body content. `css/main.scss` compiles only `_sass/_syntax-highlighting.scss` (for Rouge code blocks) plus legacy image utility classes (`.project-image`, `.project-image-medium`, etc.).

**Projects index** (`projects.md`): Iterates `site.projects`, showing only entries where `sub_page` is null or false, rendering a thumbnail image and link.

## Content conventions

- Images for a post are stored in the `images/` directory at the root and **must** be referenced with an absolute path: `/images/filename.jpg`. Relative paths (`images/filename.jpg`) break when posts are served at category-prefixed URLs.
- Project images live alongside the project's `.md` file in its subdirectory.
- `_config.yml` sets `future: true` so posts with future dates are still built.
- Markdown renderer is kramdown.
