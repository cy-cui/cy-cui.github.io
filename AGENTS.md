# AGENTS.md - Jekyll Chirpy Blog Guidelines

## Overview
This is a personal blog built with Jekyll and the Chirpy theme. It's a static site generated from Markdown files. The site uses Chinese (zh-CN) as the primary language.

## Build Commands

### Local Development
```bash
bundle install          # Install Ruby dependencies
bundle exec jekyll serve --livereload  # Start dev server at localhost:4000
```

### Build for Production
```bash
bundle exec jekyll build    # Build static site to _site/
```

### Testing
```bash
bundle exec htmlproofer ./_site --allow-hash-href --allow-empty-relative-links  # Validate HTML links
```

## Code Style Guidelines

### General
- Use UTF-8 encoding with LF line endings (enforced by .editorconfig)
- Trim trailing whitespace (except in .md files)
- Always end files with a newline

### YAML Configuration
- Use 2-space indentation for .yml/.yaml files
- Follow key-value format in _config.yml
- No tab characters allowed in YAML files
- Use kebab-case for YAML keys

### Markdown Content
- Use standard Markdown syntax compatible with kramdown
- Code blocks use rouge syntax highlighting: ```ruby, ```python, etc.
- Posts go in _posts/ with format: YYYY-MM-DD-title.md
- Use front matter with layout: post, comments: true, toc: true
- Maximum line length: 120 characters for readability
- Use Chinese punctuation (，。、；：？！"") in Chinese content

### Directory Structure
- _posts/ - Blog posts (Markdown)
- _drafts/ - Draft posts (not published)
- _tabs/ - Static pages (about, categories, tags, archives)
- assets/ - CSS, JS, images
- _data/ - Site data (locales, navigation, etc.)

### Naming Conventions
- Post filenames: YYYY-MM-DD-slug.md (e.g., 2026-03-26-welcome.md)
- Tab filenames: lowercase with hyphens (e.g., about.md)
- Image filenames: lowercase with hyphens
- Category/tags: lowercase, use hyphens instead of spaces

### Jekyll Front Matter
Required fields for posts:
```yaml
---
title: "Post Title"
date: YYYY-MM-DD HH:MM:SS +0800
categories: [category]
tags: [tag]
---
```

Optional fields:
- layout: post (default)
- comments: true (enable comments)
- toc: true (table of contents)
- permalink: /custom/path/
- published: false (draft mode)

### Liquid Templates
- Use Liquid tags for includes: {% include toc.html %}
- Reference assets with {{ site.baseurl }} prefix
- Use relative URLs where possible
- Test all Liquid template logic locally

### CSS/Sass
- Style is compressed in production (sass/style: compressed)
- Custom styles go in assets/css/
- Follow BEM naming for custom classes if needed

### JavaScript
- PWA enabled with cache support
- Custom JS goes in assets/js/
- Minified in production

### Git Workflow
- Work on content in feature branches
- Commit messages in Chinese or English
- No build artifacts (_site/) committed
- Keep .gitignore items excluded

## Editor Configuration
The project uses .editorconfig with these settings:
- charset: utf-8
- end_of_line: lf
- insert_final_newline: true
- trim_trailing_whitespace: true (except .md files)
- YAML indent: 2 spaces

## Theme Configuration

### _config.yml Settings
- theme_mode: dark (supports dark/light/system)
- comments: provider (disqus/utterances/giscus)
- analytics: google, goatcounter, umami, matomo, cloudflare, fathom
- pwa: enabled with cache configuration
- toc: enabled by default for posts

### Social Links
Configure in social: section with name, email, fediverse_handle, links array

## Common Tasks

### Add New Post
1. Create _posts/YYYY-MM-DD-title.md
2. Add front matter with required fields
3. Write content in Markdown
4. Test locally with `bundle exec jekyll serve`

### Add New Page/Tab
1. Create file in _tabs/ directory
2. Use layout: page in front matter
3. Add to navigation in _data/navigation.yml if needed

### Modify Theme Settings
Edit _config.yml - supports dark mode, comments, analytics, PWA

### Local Preview
Run `bundle exec jekyll serve` and visit http://localhost:4000
Use --livereload for automatic refresh on changes

## Testing

### Link Validation
```bash
bundle exec htmlproofer ./_site --allow-hash-href --allow-empty-relative-links
```

### Build Verification
```bash
bundle exec jekyll build && ls -la _site/
```

## Dependencies
- jekyll-theme-chirpy (~> 7.5)
- html-proofer (~> 5.0) - for testing
- Ruby gems defined in Gemfile