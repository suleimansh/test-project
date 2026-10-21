# Hello

A single static page (`index.html`) with no build step or dependencies.

Live at **https://suleimansh.github.io/test-project/**

## Edit

All markup and styles are inline in `index.html`. If you change the background
colour (`#0f172a`), update the fill in `favicon.svg` and regenerate
`favicon.ico` to match.

## Run locally

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy

Every push to `main` publishes to GitHub Pages via
`.github/workflows/deploy.yml`. Only `index.html`, `favicon.ico` and
`favicon.svg` are published; to ship another file, add it to the workflow's
`Stage site` step. The site is served from `/test-project/`, so keep asset links
relative (`favicon.ico`, not `/favicon.ico`).
