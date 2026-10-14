# Hello

A single static page. No build step, no dependencies. It renders one centered
greeting — "Hello, and welcome." — on a dark background, and nothing else. The
favicon is a white "H" on a rounded square in the same dark colour as the page.

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

Or serve it over HTTP, which matches production more closely:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

Live at **https://suleimansh.github.io/test-project/**

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

## Recorded test

This section was added as part of a recorded test run.
It exists only to verify that README edits commit and push cleanly.
It can be removed once the test has been reviewed.
No other files were changed as part of this test.
