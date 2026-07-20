# Hello

A single static page. No build step, no dependencies.

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | The whole page — markup and inline styles |
| `favicon.svg` | Favicon for modern browsers |
| `favicon.ico` | Fallback favicon for browsers that ignore the SVG |

## Run it locally

Open the file directly:

```sh
open index.html
```

Or serve it over HTTP, which matches production more closely (absolute paths like
`/favicon.ico` resolve the same way):

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

Deployment is GitHub Pages, driven by `.github/workflows/deploy.yml`. Every push to
`main` publishes the site; it can also be run by hand from the Actions tab.

One-time setup on the repository:

1. Push the repo to GitHub (this project has no remote configured yet).
2. **Settings → Pages → Build and deployment → Source: GitHub Actions.**

The workflow copies only `index.html`, `favicon.ico`, and `favicon.svg` into the
published artifact. The repository root is *not* deployed wholesale — anything not
in that list (for example `.the-framework/`, which holds internal run logs and
analysis notes) is never reachable from the public site. If you add a file that
should be served, add it to the `Stage site` step or it will not ship.
