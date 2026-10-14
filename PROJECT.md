# Project Description

A minimal static website: one HTML page, no build step, no dependencies.

## What it is

`index.html` renders a single centered greeting — "Hello, and welcome." — on a
dark background. Two favicons sit alongside it (`favicon.svg` for modern
browsers, `favicon.ico` as a fallback). That is the entire site; the markup and
styles live inline in the one file.

## How it ships

Pushes to `main` are published to GitHub Pages by
`.github/workflows/deploy.yml`, which copies only the three site files into the
published artifact. The result is live at
https://suleimansh.github.io/test-project/ — a *project* Pages site, so it is
served from the `/test-project/` subpath and asset links are relative rather
than root-absolute.

## Layout

| Path | Purpose |
| --- | --- |
| `index.html` | The whole page — markup and inline styles |
| `favicon.svg` | Favicon for modern browsers |
| `favicon.ico` | Fallback favicon |
| `.github/workflows/deploy.yml` | GitHub Pages deployment |
| `.the-framework/` | Internal run logs and notes; never deployed |

See [README.md](README.md) for how to run it locally and the full deployment
setup.
