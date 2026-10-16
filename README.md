# test-project

A single static page — one centered greeting on a dark background. No build
step, no dependencies, no JavaScript.

**Live:** https://suleimansh.github.io/test-project/

[![Deploy to GitHub Pages](https://github.com/suleimansh/test-project/actions/workflows/deploy.yml/badge.svg)](https://github.com/suleimansh/test-project/actions/workflows/deploy.yml)

---

## What it is

`index.html` is the entire site: markup and styles in one file. It renders the
heading "Hello, and welcome." and nothing else. The favicon is a white "H" on a
rounded square in the same dark colour as the page.

## Files

Published to the site:

| Path | Purpose |
| --- | --- |
| `index.html` | The whole page — markup and inline styles |
| `favicon.svg` | Favicon for modern browsers |
| `favicon.ico` | Fallback favicon for browsers that ignore the SVG |

Repository-only, never served (see [Deploy](#deploy)):

| Path | Purpose |
| --- | --- |
| `.github/workflows/deploy.yml` | The GitHub Pages deploy workflow |
| `.the-framework/` | Internal run logs and analysis notes |
| `test.md` | Scratch note, not part of the site |

## Run it locally

Open the file directly — fine for a quick look:

```sh
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

Or serve it over HTTP, which matches production more closely:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

Prefer the HTTP route when touching anything path-related: `file://` and a web
server resolve relative links differently, so a broken asset path can look fine
opened directly and 404 once deployed.

## Making a change

1. Edit `index.html` — copy, layout, and styles all live there.
2. Check it locally over HTTP (above), including the favicon in the tab.
3. Push to `main`. The deploy runs on its own; watch it in the Actions tab.

The palette is inline in the `<style>` block: `#0f172a` for the background,
`#f8fafc` for text. `favicon.svg` repeats both, so a colour change needs
editing in both files to stay consistent.

## Deploy

Deployment is GitHub Pages, driven by `.github/workflows/deploy.yml`. Every push
to `main` publishes the site; it can also be run by hand from the Actions tab.

Two things to know before changing anything here:

**Only three files ship.** The `Stage site` step copies `index.html`,
`favicon.ico`, and `favicon.svg` into the published artifact. The repository root
is *not* deployed wholesale, so nothing outside that list — `.the-framework/`
included — is reachable from the public site. If you add a file that should be
served, add it to the `Stage site` step or it will not ship.

**Asset links must be relative.** This is a *project* Pages site, so it is served
from the `/test-project/` subpath rather than the domain root. Links in
`index.html` are therefore relative (`favicon.ico`, not `/favicon.ico`) — a
root-absolute path resolves to `suleimansh.github.io/favicon.ico` and 404s.

One-time setup is already done on `suleimansh/test-project`: the remote exists and
the Pages source is set to GitHub Actions (**Settings → Pages → Build and
deployment → Source: GitHub Actions**). A fresh fork or clone needs both steps
repeated before its first deploy will publish.
