# hostwarden.github.io

The one-pager at [hostwarden.github.io](https://hostwarden.github.io)
and the workflow that publishes
[hostwarden.github.io/docs](https://hostwarden.github.io/docs), the
Docusaurus documentation site whose source lives in
[hostwarden/hostwarden](https://github.com/hostwarden/hostwarden)'s
`website/` directory. Why the site is split this way is recorded in
that repository's
[docs/adr/20260925-docs-stay-in-repo-thin-publish.md](https://github.com/hostwarden/hostwarden/blob/main/docs/adr/20260925-docs-stay-in-repo-thin-publish.md).

## What's here

- `index.html`, `legal-notice.html`, `privacy-policy.html`,
  `style.css` — the one-pager. Hand-edited, reviewed like any other
  page.
- `.github/workflows/publish.yml` — the only thing that ever writes
  to `docs-site/`, `img/`, `fonts/` or `_site/`. It runs on a
  `repository_dispatch` from `hostwarden/hostwarden` (`docs-updated`
  on every push to `website/**`, `release-cut` when a release tags),
  or by hand (`workflow_dispatch`).
- `docs-site/` — an ephemeral Docusaurus checkout the workflow
  rebuilds from `hostwarden/hostwarden`'s `website/` on every run.
  Only `versioned_docs/`, `versioned_sidebars/` and `versions.json`
  are committed here; everything else is regenerated and gitignored.

Nothing under `docs-site/`, `img/`, `fonts/` or `_site/` is hand-edited.
A pull request touching those paths outside what the workflow itself
commits is a mistake, not a contribution.

## Setup

- GitHub Pages → Build and deployment → Source: **GitHub Actions**
  (done).
- A repository secret `DOCS_DISPATCH_TOKEN` in
  **hostwarden/hostwarden** (not here) — a fine-grained PAT scoped
  to this repository, `Contents: write` (done).
