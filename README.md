# Hello

A single static page ("Hello, and welcome.") with no build step or dependencies.

Live at **https://suleimansh.github.io/test-project/**

## Files

- `index.html` — the whole page, markup and inline styles
- `favicon.svg`, `favicon.ico` — favicon (keep its fill matching the page background, `#0f172a`)
- `.github/workflows/deploy.yml` — GitHub Pages deploy

## Run locally

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy

Every push to `main` publishes to GitHub Pages (Pages source: GitHub Actions).

- The site is served from `/test-project/`, so asset links must be relative
  (`favicon.ico`, not `/favicon.ico`).
- Only `index.html`, `favicon.ico` and `favicon.svg` are published. To ship a new
  file, add it to the workflow's `Stage site` step.
