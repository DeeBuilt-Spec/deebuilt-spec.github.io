# deebuilt-spec.github.io — apex site for spec.deebuilt.co

This repo owns the **`spec.deebuilt.co`** subdomain and serves the landing page
that links out to each project spec. It is a plain static site — no build step.

## How the setup works

- **This repo** holds the `CNAME` (`spec.deebuilt.co`) and the landing page.
  It is the only repo in the org that carries the domain. It deploys from the
  branch root via GitHub Pages (Settings → Pages → Deploy from branch → `main`
  / `/root`).
- **Project repos** (e.g. `medical-provider`) each serve at a route under the
  domain — `spec.deebuilt.co/medical-provider/`. They set their Vite `base` to
  their repo name and **must not** contain a `CNAME` file.

## Adding a new project

1. Build the project repo with `base = "/<repo-name>/"`.
2. Add a `<a class="card">` entry to `index.html` pointing at
   `https://spec.deebuilt.co/<repo-name>/`.
3. Commit and push — Pages redeploys the landing page automatically.
