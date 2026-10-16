# Project Description

A single static web page — no build step, no dependencies, no framework.

## What it is

`index.html` is the entire site: one centered greeting, "Hello, and welcome.",
set in the system sans-serif on a dark slate background (`#0f172a`). The markup
and styles live in that one file. Two favicons sit beside it — a white "H" on a
rounded square in the page's own dark colour — one SVG for modern browsers and
an ICO fallback for the rest.

## Layout

| Path | Purpose |
| --- | --- |
| `index.html` | The whole page — markup and inline styles |
| `favicon.svg` | Favicon for modern browsers |
| `favicon.ico` | Fallback favicon for browsers that ignore the SVG |
| `.github/workflows/deploy.yml` | GitHub Pages deployment |

## Running it

Open `index.html` directly, or serve it over HTTP to match production:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deployment

The site is published to GitHub Pages at
**https://suleimansh.github.io/test-project/** on every push to `main`, and can
also be deployed by hand from the Actions tab.

Because it is a *project* Pages site, it is served from the `/test-project/`
subpath rather than the domain root, so asset links are relative
(`favicon.ico`, not `/favicon.ico`).

The workflow stages only `index.html`, `favicon.ico`, and `favicon.svg`. The
repository root is not deployed wholesale, so a new file that should be served
has to be added to the workflow's `Stage site` step.

See `README.md` for the fuller write-up.
