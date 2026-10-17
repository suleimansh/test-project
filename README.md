# Hello

A single static page — one centered greeting on a dark background. No build step,
no dependencies.

| Path | Purpose |
| --- | --- |
| `index.html` | The whole page — markup and inline styles |
| `favicon.svg` | Favicon for modern browsers |
| `favicon.ico` | Fallback for browsers that ignore the SVG |

## Run it locally

```sh
open index.html
# or, closer to production:
python3 -m http.server 8000   # http://localhost:8000
```

## Deploy

Live at **https://suleimansh.github.io/test-project/**, published by
`.github/workflows/deploy.yml` on every push to `main` (or by hand from the
Actions tab). Setup is already done here; a fresh fork needs Pages set to
**Settings → Pages → Source: GitHub Actions**.

Two things to know before changing files:

- It is a *project* Pages site served from `/test-project/`, so asset links must
  be relative (`favicon.ico`, not `/favicon.ico`).
- The workflow's `Stage site` step copies only `index.html`, `favicon.ico`, and
  `favicon.svg`. Nothing else ships — add new files to that step or they will not
  be served.
