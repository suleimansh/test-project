# Hello

A single static page with no build step or dependencies: one centered greeting
on a dark background. `index.html` holds the markup and styles; `favicon.svg`
and `favicon.ico` are the icons.

## Run locally

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy

Live at **https://suleimansh.github.io/test-project/**, published to GitHub Pages
by `.github/workflows/deploy.yml` on every push to `main`.

- The site is served from `/test-project/`, so keep asset links relative
  (`favicon.ico`, not `/favicon.ico`).
- Only `index.html`, `favicon.ico`, and `favicon.svg` are deployed. To ship a new
  file, add it to the workflow's `Stage site` step.
