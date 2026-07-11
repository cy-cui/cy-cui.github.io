# AGENTS.md - Jekyll Hux Blog Guidelines

## Overview
Personal blog built with Jekyll and Hux Blog theme. Static site generated from Markdown files. Primary language: Chinese (zh-CN).

## Build Commands

### Local Development
```bash
./bin/dev                          # Preferred: auto Ruby PATH + bundle + serve
# or
bundle install
bundle exec jekyll serve --livereload  # http://localhost:4000
```

### Build for Production
```bash
./bin/build
# or
bundle exec jekyll build
```

### Testing & Validation
```bash
bundle exec htmlproofer ./_site --allow-hash-href --disable-external
```

### GitHub Actions CI/CD
- `.github/workflows/pages-deploy.yml` - build, test, deploy on push to main/master

## Writing Posts
See [WRITING.md](WRITING.md). Posts live in `_posts/YYYY-MM-DD-title.md` with Hux front matter (`layout: post`, `header-img`, `tags`, etc.).

## Code Style Guidelines

### General
- UTF-8 encoding with LF line endings (enforced by .editorconfig)
- Trim trailing whitespace (except in .md files)
- Always end files with a newline
- Max line length: 120 characters

### YAML Configuration
- 2-space indentation for .yml/.yaml files
- No tab characters
- Use kebab-case for keys
- Quote special string values

### Markdown Content
- Standard kramdown syntax
- Code blocks use rouge
- Use Chinese punctuation (，。、；：？！"") in Chinese content

### Directory Structure
- `_posts/` - Blog posts (Markdown)
- `about.html` / `archive.html` - Static pages
- `_layouts/` / `_includes/` - Hux theme templates
- `css/` `js/` `img/` - Theme assets
- `_site/` - Generated static site (gitignored)

### Naming Conventions
- Posts: `YYYY-MM-DD-slug.md`
- Images: lowercase with hyphens

## Theme Configuration (_config.yml)
- `lang`: zh-CN
- `timezone`: Asia/Shanghai
- `paginate`: 10
- Comments: Giscus (optional, see `giscus` in `_config.yml`)
- Search: Simple Jekyll Search (`search.json`)

## Dependencies
- jekyll (~> 4.4)
- jekyll-paginate, jekyll-feed
- html-proofer (~> 5.0)
- Ruby gems in Gemfile; prefer Ruby 3.3 locally

## Troubleshooting
- Serving fails: `bundle exec jekyll clean` then `./bin/dev`
- Port 4000 conflict / blank CSS: kill old `jekyll serve` processes, keep only one
- Gem conflicts: delete Gemfile.lock, run `bundle install`
