# Clawman website

Jekyll site for the Clawman VS Code extension. Built on the brand system in [`../brand/`](../brand/).

## Run locally

```bash
cd Website
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>.

## Deploy

Pushing to `main` triggers `.github/workflows/pages.yml`, which builds this folder and publishes it to GitHub Pages.

**One-time setup:** in the repo, go to **Settings → Pages → Build and deployment**, and set the source to **GitHub Actions**.

The workflow passes the correct `--baseurl` automatically, so project sites at `username.github.io/clawman` work without editing `_config.yml`.

## Before you publish

Edit `_config.yml` and replace the placeholders:

```yaml
url: "https://your-github-username.github.io"
baseurl: "/clawman"
github_username: your-github-username
repo: https://github.com/your-github-username/clawman
marketplace: https://marketplace.visualstudio.com/items?itemName=...
```

For a custom domain, set `url` to the domain, leave `baseurl` empty, and add a `CNAME` file to this folder.

## Writing a blog post

Add a markdown file to `_posts/` named `YYYY-MM-DD-slug.md`:

```markdown
---
title: "1.5 — what changed"
version: "1.5.0"
tags: [release, detection]
lede: "One or two sentences. Shows on the blog index and the home page."
date: 2026-08-01 10:00:00 +0000
---

Body in markdown.
```

`layout: post` is applied automatically. `version`, `tags` and `lede` are all optional — `lede` falls back to the first paragraph.

Posts appear on `/blog/`, in the three most recent on the home page, and in `/feed.xml`. Nothing else needs updating.

Keep it in voice: dry, specific, no exclamation marks. See [`../brand/BRAND.md`](../brand/BRAND.md) §5.

## Structure

```
Website/
├── _config.yml           site settings and placeholders
├── Gemfile               jekyll + feed, seo-tag, sitemap
├── index.html            landing page
├── features.md           what Clawman does
├── docs.md               install and configure
├── blog.html             post index → /blog/
├── _posts/               one markdown file per post
├── _layouts/             default, page, post
├── _includes/            head, header, footer, mark
└── assets/
    ├── css/clawman.css   the whole stylesheet, tokens at the top
    ├── js/site.js        mobile nav only
    └── img/              favicon and logo
```

## Notes

- Dark mode is the only mode. Clawman lives in an editor.
- All colour and type tokens are declared at the top of `clawman.css` and match `../brand/tokens.css`.
- The claw mark is inlined via `_includes/mark.html` so it inherits CSS variables.
