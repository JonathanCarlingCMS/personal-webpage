# personal-webpage

Static personal landing page for Jonathan Carling (Lead Software Engineer, Trimble), showcasing internal projects such as VFP PowerToys.

## Purpose

A single-page, dependency-free site (plain HTML + CSS, no build step) with an intro, links to LinkedIn and GitHub, and an "Internal Projects" section linking to the sibling repos (`vfp-powertoys`, dev script toolkit, Hangfire service installer).

## Prerequisites

| To... | You need |
|-------|----------|
| View locally (simplest) | Any web browser |
| Run via Docker | Docker Desktop / Docker Engine with Compose |
| Deploy | Push access to the GitHub repo with GitHub Pages enabled (Source: **GitHub Actions**) |

## Build

There is no build step. The site is the files in the repo root.

## Run locally

**Option 1 - open the file:** double-click `index.htm`.

**Option 2 - nginx in Docker** (serves the repo read-only, same as a real web server):

```powershell
docker compose up -d
```

Browse to <http://localhost:8080>. Stop with `docker compose down`. Edits to the files show on browser refresh (no rebuild needed).

## Deploy

Deployment is automated by `.github/workflows/static.yml`:

- Triggers on every push to `main` (or manually via **Actions → Deploy static content to Pages → Run workflow**).
- Uploads the whole repo as a Pages artifact and publishes it to GitHub Pages.
- The published URL is shown on the workflow run (`github-pages` environment).

One-time setup: **Settings → Pages → Build and deployment → Source: GitHub Actions**.

## Usage / editing content

| To change... | Edit |
|--------------|------|
| Text, links, project cards | `index.htm` (project cards live under the `#projects` section) |
| Look and feel | `styles.css` |
| Photo / logos / icons | `profile.jpg`, `images/`, `*-icon.svg`, `trimble-logo.svg` |
| Local server behaviour | `nginx.conf`, `docker-compose.yml` |

To add a project, copy an existing project card in `index.htm` and update its title, description, GitHub link and download link (`.../archive/refs/heads/main.zip`).

## Project layout

```text
index.htm               The page
styles.css              Styling
images/                 Screenshots and logos used by the page
*.svg, profile.jpg      Icons and profile photo
nginx.conf              nginx site config used by Docker
docker-compose.yml      Local nginx container (port 8080)
.github/workflows/
  static.yml            GitHub Pages deployment
```

## Related repos

- [`vfp-powertoys`](../vfp-powertoys) - the main project showcased on the page
