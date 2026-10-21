# Hello

A single static page (`index.html`) with no build step or dependencies.

Live at **https://suleimansh.github.io/test-project/**

## Edit

Everything lives in `index.html`: change the `<h1>` and `<p>`, then reload. If
you change the background (`#0f172a`), update the fill in `favicon.svg` and
regenerate `favicon.ico` to match.

## Run locally

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy

Every push to `main` publishes to GitHub Pages via `.github/workflows/deploy.yml`.
Only `index.html`, `favicon.ico` and `favicon.svg` are deployed; add any new file
to the workflow's `Stage site` step or it won't ship. The site is served from
`/test-project/`, so keep asset links relative (`favicon.ico`, not `/favicon.ico`).
