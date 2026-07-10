# Computable AI

Source for the blog at <https://computable.ai/pages/>, built with
[Quarto](https://quarto.org) and published to GitHub Pages.

## Writing a post

Create a directory under `posts/` and put the post in it as `index.qmd`
(Markdown) or `index.ipynb` (Jupyter notebook):

```
posts/
  2026-07-09-hello-again/
    index.qmd
    thumbnail.png        # optional; referenced from front matter
```

Every post starts with YAML front matter:

```yaml
---
title: "Post Title"
description: "One-sentence summary shown on the home page and in the feed."
date: 2026-07-09
categories: [ml, engineering]
---
```

Notebook posts render from their **saved outputs** — run the notebook
locally, save it with outputs, and commit. CI never executes code
(`freeze` is enabled), so posts don't need their Python environments
reproduced at publish time. If you render executable `.qmd` posts
locally, commit the generated `_freeze/` directory too.

## Design

The look and feel matches the main site at <https://computable.ai>
(the Pelican/mg theme): `theme-light.scss` and `theme-dark.scss` carry
the design tokens (brand green `hsl(158,94%,31%)`, fonts, light/dark
palettes) lifted from its `theme/css/main.css`, and `images/` holds the
disc logo and favicon from the live site.

## Previewing locally

Install [Quarto](https://quarto.org/docs/get-started/), then:

```
quarto preview
```

## Publishing

Pushing to `master` triggers `.github/workflows/publish.yml`, which
renders the site and pushes it to the `gh-pages` branch. GitHub Pages
serves that branch. No secrets or deploy keys are required beyond the
default `GITHUB_TOKEN`.
