# test-project

A one-page static site and a sandbox for trying out AI coding agents. The page
has no build step and no dependencies; GitHub Pages publishes it on every push
to `main`.

**Live:** https://suleimansh.github.io/test-project/

Who's behind it: see [ABOUT.md](ABOUT.md).

## What the page shows

A centred heading, "Hello, and welcome.", with a grey subtitle, "A test page.",
on a dark slate background (`#0f172a`). The favicon is a white "H" on a rounded
square in the same colour.

## Repository layout

| Path | What it is | Published? |
| --- | --- | --- |
| `index.html` | The whole page: markup and inline styles | Yes |
| `favicon.svg` | Favicon for modern browsers | Yes |
| `favicon.ico` | Fallback favicon for browsers that ignore the SVG | Yes |
| `.github/workflows/deploy.yml` | GitHub Pages deploy (see [Deploy](#deploy)) | No |
| `.agents/skills/`, `.claude/skills/` | Skills the coding agents load (triage, planning, review, replies, …) | No |
| `skills-lock.json` | Pins the source and hash of installed skills | No |
| `.the-framework/` | Internal run logs and analysis notes | No |
| `ABOUT.md` | About the maintainer | No |
| `test*.md` | Scratch notes left by test runs | No |

Only the first three files are deployed; nothing else in the repository is
reachable from the public site.

## Editing the page

Everything lives in `index.html`; there is no separate stylesheet or script.

- **Heading:** the `<h1>`.
- **Subtitle:** the `<p>` under it.
- **Colours:** background `#0f172a` and heading `#f8fafc` in the `<style>`
  block; subtitle `#94a3b8` inline on the `<p>`.

If you change the background, update the fill in `favicon.svg` and regenerate
`favicon.ico` so the icon still matches.

## Running locally

Open the file directly:

```sh
open index.html        # macOS
xdg-open index.html    # Linux
```

Or serve it over HTTP, which is closer to production:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

`.github/workflows/deploy.yml` publishes to GitHub Pages on every push to `main`,
and can also be run by hand from the **Actions** tab.

- **Only listed files ship.** The `Stage site` step copies `index.html`,
  `favicon.ico` and `favicon.svg` into the artifact. A new file that should be
  served must be added to that step, or it won't be published.
- **Links must be relative.** This is a project Pages site served from
  `/test-project/`, so `favicon.ico` works but `/favicon.ico` resolves to
  `suleimansh.github.io/favicon.ico` and 404s.
- **Forks need setup.** Set **Settings → Pages → Build and deployment → Source**
  to **GitHub Actions** before the first deploy. This is already done on
  `suleimansh/test-project`.
