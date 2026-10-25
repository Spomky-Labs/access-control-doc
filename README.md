# The documentation of Access Control

The public documentation of [Access Control](https://github.com/Spomky-Labs/access-control-framework),
authorization for PHP applications: the pure PHP component and the Symfony bundle.

Published with [MkDocs](https://www.mkdocs.org/) and
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) on GitHub Pages:
**<https://acf.spomky-labs.com/>**

## Writing

```bash
make install   # the toolchain, in .venv, from requirements.txt
make serve     # http://127.0.0.1:8000, rebuilt as you save
make check     # the strict build continuous integration runs
```

`make check` is the gate: a broken internal link, an anchor that does not exist, a page absent from the
navigation or a navigation entry without a page fails the build.

## Where things are

| Path | What it is |
|---|---|
| `mkdocs.yml` | The site: theme, extensions, plugins, and the whole navigation |
| `docs/` | The pages, one directory per section of the navigation |
| `docs/assets/stylesheets/` | The look: `slabs-tokens.css`, copied as it is from the Slabs design kit, and `slabs.css`, which applies the guidelines to the theme |
| `docs/assets/brand/`, `docs/assets/fonts/` | The logotype, the signature, the favicons and the share image of the design kit, and its typefaces (SIL Open Font License) |
| `docs/overrides/` | Theme partials, when a page needs more than CSS |
| `site-root/` | The root of the published site, copied to the root of the `gh-pages` branch: `CNAME`, and the `404.html` that sends the addresses of the former GitBook site to the latest version |
| `requirements.txt` | The toolchain, pinned. Continuous integration installs exactly this |
| `.github/workflows/check.yml` | The strict build, on every pull request |
| `.github/workflows/pages.yml` | The publication: one version per branch, through mike |
| `.github/workflows/default-branch.yml` | A new version branch becomes the default branch |
| `docs/SUMMARY.md`, `.gitbook.yaml` | The GitBook space, until the domain points to GitHub Pages |

## One branch per version

A branch of this repository is a version of the packages: `1.0`, `1.1`, and so on. A push to one of them
publishes it under its own name, and the newest one also carries the `latest` alias, which the root of the
site redirects to.

```bash
git switch -c 1.1 1.0          # from the version it continues
# in mkdocs.yml, point edit_uri at the new branch
git push -u origin 1.1         # publishes it, and moves "latest" and the default branch
```

## Licence

MIT, as the packages it documents.
