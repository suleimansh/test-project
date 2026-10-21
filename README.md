# Hello

A single static page. No build step, no dependencies. It shows a centered
heading, "Hello, and welcome.", with a short grey subtitle, "A test page.", under
it, on a dark slate background (`#0f172a`). The favicon is a white "H" on a
rounded square in the same dark colour as the page.

Live at **https://suleimansh.github.io/test-project/**

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | The whole page — markup and inline styles |
| `favicon.svg` | Favicon for modern browsers |
| `favicon.ico` | Fallback favicon for browsers that ignore the SVG |
| `.github/workflows/deploy.yml` | Publishes the page to GitHub Pages (see [Deploy](#deploy)) |
| `try-assets/` | Icons used in the agents' pull request comments; not part of the site |
| `test.md`, `test2.md`, `test5.md` | Scratch notes from test runs; not part of the site |

Only the first three are published. Everything else stays in the repository.

## Edit the page

All content and styling live in `index.html`; there is no stylesheet or script
to keep in step. Change the `<h1>` for the heading and the `<p>` under it for the
subtitle, then reload the page to check it. The page colours are set in the
`<style>` block (background `#0f172a`, heading `#f8fafc`) and inline on the
subtitle (`#94a3b8`). If you change the background, change the favicon's fill
in `favicon.svg` (and regenerate `favicon.ico`) so they keep matching.

## Run it locally

Open the file directly in a browser:

```sh
open index.html        # macOS
xdg-open index.html    # Linux
```

Or serve it over HTTP, which matches production more closely:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

Deployment is GitHub Pages, driven by `.github/workflows/deploy.yml`. Every push to
`main` publishes the site; it can also be run by hand from the Actions tab.

One-time setup is already done on `suleimansh/test-project`: the remote exists and
the Pages source is set to GitHub Actions (**Settings → Pages → Build and
deployment → Source: GitHub Actions**). A fresh fork or clone needs both steps
repeated before its first deploy will publish.

Because this is a *project* Pages site, it is served from the `/test-project/`
subpath rather than the domain root. Asset links in `index.html` are therefore
relative (`favicon.ico`, not `/favicon.ico`) — a root-absolute path resolves to
`suleimansh.github.io/favicon.ico` and 404s.

The workflow copies only `index.html`, `favicon.ico`, and `favicon.svg` into the
published artifact. The repository root is *not* deployed wholesale — anything not
in that list (for example `.the-framework/`, which holds internal run logs and
analysis notes) is never reachable from the public site. If you add a file that
should be served, add it to the `Stage site` step or it will not ship.

Fork try.
