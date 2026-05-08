# Portfolio

This is my personal portfolio site, built with [Hugo](https://gohugo.io/) and the `hugo-profile` theme.

It is structured as a content-first static site: most of the public-facing information lives in Hugo content files, data files, image assets, and a small set of layout overrides.

## What this repo contains

- My homepage and portfolio content
- Project case studies
- Career, education, and certification details
- Custom styling and layout overrides
- A vendored copy of the `hugo-profile` theme under `themes/hugo-profile`

## Stack

- Hugo static site generator
- `hugo-profile` theme
- Custom CSS in `assets/css/site.css` and `static/style.css`
- Content and data in `content/` and `data/`

## Requirements

- Hugo `0.68.0` or newer
- A modern browser for local preview

## Project structure

- `hugo.toml` - site configuration, branding, colors, and theme parameters
- `content/` - homepage and project content
- `data/portfolio.toml` - structured portfolio data used by the theme
- `assets/css/` - site-level styling
- `layouts/` - custom template overrides
- `static/` - images, icons, and other static files
- `themes/hugo-profile/` - the bundled theme source

## Run locally

1. Install Hugo if you do not already have it.
2. Start the local server:

```bash
hugo server -D
```

3. Open the local URL Hugo prints in the terminal.

## Deploying on AWS

This portfolio is deployed as a static Hugo site on AWS.

The production DNS path is:

- Route 53 hosted zone for `albertocanaveral.com`
- CloudFront distribution in front of the site
- Amazon S3 origin serving the generated static files

The repo itself does not include deployment automation, so the release flow is the standard static-site pattern:

1. Build the production site:

```bash
hugo --gc --minify
```

2. Upload the generated `public/` directory to the S3 bucket used by the site.
3. Invalidate the CloudFront cache so the new files are served globally.
4. Route 53 continues to point `albertocanaveral.com` and `www.albertocanaveral.com` at CloudFront.

## How to customize this site

If you want to use this repo as your own portfolio, these are the main files to edit:

### 1. Update site identity

Edit `hugo.toml`:

- `baseURL` - your production domain
- `title` - your name or site title
- `params.title` and `params.description` - site metadata and search snippets
- `params.hero` - hero section text and image
- `params.about`, `params.experience`, `params.education`, `params.achievements` - the main homepage sections

### 2. Replace personal data

Edit `data/portfolio.toml`:

- `name`
- `role`
- `location`
- `email`
- `resume`
- social links
- highlights
- projects
- experience entries

### 3. Replace content

Edit files under `content/`:

- `content/_index.md` - homepage front matter
- `content/projects/*.md` - individual project pages

### 4. Replace images and brand assets

Update files under `static/images/` and `static/`:

- profile photo
- project thumbnails
- certification badges
- favicon

### 5. Adjust styles if needed

Use `assets/css/site.css` and `static/style.css` for visual tweaks without modifying the theme directly.

## Forking this repo for your own site

If you fork this repository, the fastest path is:

1. Fork the repo on GitHub.
2. Clone your fork locally.
3. Change `baseURL`, title, and branding in `hugo.toml`.
4. Replace the portfolio data in `data/portfolio.toml`.
5. Replace project pages in `content/projects/`.
6. Swap in your own images under `static/images/`.
7. Run `hugo server -D` until the site looks right.
8. Build the production site with:

```bash
hugo --gc --minify
```

9. Publish the generated `public/` directory with your host of choice, such as S3 and CloudFront.

## Notes for forked sites

- The bundled theme is already included in the repository, so you do not need to initialize a submodule before running the site.
- If you want to keep the same structure but change the visual identity, start with `hugo.toml` and the image assets before touching theme templates.
- If you want a completely different layout, the custom overrides in `layouts/` are the safest place to extend the theme.
- Remember to update external links, certification URLs, and contact information so the fork does not point back to my profile.

## Content guidelines

This portfolio is meant to show technical work clearly and concisely. For new project entries, a good pattern is:

- what the project is
- what problem it solves
- what architecture or tools it uses
- what is interesting about the implementation
- a link to the source repo or live demo

## License

This repository is licensed under MIT. The vendored theme source in `themes/hugo-profile` is also MIT licensed.
