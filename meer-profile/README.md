## Automatic deploys with GitHub Actions

This repository is configured to auto-deploy the static site to GitHub Pages when you push to `main` (or `master`).

### One-time setup

1. Push this repo to GitHub.
2. In GitHub, go to `Settings` → `Pages`.
   - Source: `GitHub Actions`.
   - Ensure the custom domain is set to `meerjada.dpdns.org` (GitHub will use the `CNAME` file in the repo).
3. Ensure DNS for `meerjada.dpdns.org` points to GitHub Pages per GitHub’s docs.

### How it works

- Workflow file: `.github/workflows/deploy.yml`.
- On push to `main`/`master`, it:
  - Checks out the repo
  - Copies all static files into `dist/`
  - Preserves `CNAME` and creates `.nojekyll`
  - Uploads artifact and deploys via `actions/deploy-pages`

### Make a change and deploy

1. Edit files (e.g., `index.html`).
2. Commit and push to `main`.
3. Check the `Actions` tab for the "Deploy static site to GitHub Pages" workflow run.
4. Your site will update at `https://meerjada.dpdns.org/`.

No additional build step is required since this is a static site.

