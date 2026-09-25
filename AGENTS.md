# AGENTS.md

This repository is the publish target for
[hostwarden.github.io](https://hostwarden.github.io) and
[hostwarden.github.io/docs](https://hostwarden.github.io/docs). It
holds a one-pager and a workflow; it holds no documentation content
of its own. See README.md for the full picture before editing
anything.

## What to edit here

`index.html`, `impressum.html`, `datenschutz.html`, `style.css`, and
`.github/workflows/publish.yml`. Nothing else — `docs-site/`, `img/`,
`fonts/` and `_site/` are the workflow's own working area, rebuilt
and partly gitignored; do not hand-edit or commit into them outside
what the workflow itself does.

## What never happens here

- No documentation content is written in this repository. Docs
  content lives in `hostwarden/hostwarden`'s `website/` directory,
  edited there, in the same pull requests as the code it describes.
- `impressum.html` and `datenschutz.html` stay placeholders until
  Julian replaces them with real text — do not remove the
  placeholder notice or invent legal content.
- GitHub Pages is not enabled for this repository until that
  replacement has happened.
