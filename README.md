# Research website (Zensical)

A minimal personal website for researchers and students, built with
[Zensical](https://zensical.org). Content is written in Markdown. The
layout is a small set of templates and one stylesheet.

**Sections:** Home · Projects · Publications · Notes · CV

- Portfolio pages (Home, Projects, Publications, CV) use a compact single
  column.
- Notes use the full documentation layout: sidebar, table of contents,
  search, math, and code highlighting.
- Light and dark mode follow the system setting and can be toggled in the
  header.
- No JavaScript framework and no web fonts. KaTeX loads only on pages that
  contain math.

## Quick start

Requires [uv](https://docs.astral.sh/uv/), which also installs the Python
version pinned in `.python-version`. With plain pip (Python 3.10 or later),
see the note below.

```bash
uv sync                    # install Zensical into .venv
uv run zensical serve      # preview at http://localhost:8000/<repo>/
uv run zensical build      # build the static site into site/
```

The preview server reloads when you save a file. If you activate the virtual
environment (`.venv\Scripts\activate` on Windows, `source .venv/bin/activate`
elsewhere), the commands are simply `zensical serve` and `zensical build`.

> **Using pip instead:** `pip install zensical==0.1.0`, then use the same
> `zensical` commands.

## Make it yours

| What                      | Where                                          |
| ------------------------- | ---------------------------------------------- |
| Site name, URL, menu      | `zensical.toml`: `site_name`, `site_url`, `nav` |
| Footer links, copyright   | `zensical.toml`: `[[project.extra.social]]`, `copyright` |
| Name, affiliation, links  | `docs/index.md` (front matter)                 |
| Introduction, interests   | `docs/index.md` (body)                         |
| Projects                  | `docs/projects/index.md`                       |
| Publications              | `docs/publications.md`                         |
| CV                        | `docs/cv.md` and `docs/assets/cv.pdf`          |
| Notes                     | `docs/notes/`                                  |
| Colors and fonts          | `docs/stylesheets/site.css` (section 1)        |

Social links are shown as icons. Each link in `docs/index.md` and each
`[[project.extra.social]]` entry takes an `icon` such as
`fontawesome/brands/github` (see Zensical's
[icon list](https://zensical.org/docs/authoring/icons-emojis/)). A home-page
link without `icon` is shown as text, like the CV link.

All placeholder text is marked as such; search the repository for
`placeholder`, `your-username`, `you@example.com`, and `20XX`.

### Add a project

Add an entry to the `projects:` list at the top of `docs/projects/index.md`:

```yaml
  - title: My New Project
    period: 2025 – present
    summary: Two or three plain-text sentences about the project.
    thumbnail: assets/images/projects/my-project.jpg   # optional
    tags: [Robotics, Control]
    page: projects/my-project.md                       # optional detail page
    links:                                             # optional
      - { label: GitHub, url: "https://github.com/you/repo" }
      - { label: Video, url: "https://youtu.be/..." }
    selected: true      # also show on the home page
```

Only `title` is required. Entries appear in the order written.

- **Thumbnail:** a 16:10 image, about 640×400 px, under 100 KB (JPEG or
  WebP), saved in `docs/assets/images/projects/`. Entries without one simply
  span the full width.
- **Detail page (optional):** create `docs/projects/my-project.md` starting
  with the front matter below, then add the file to the `Projects` list in
  `nav` (`zensical.toml`) so the Projects tab stays highlighted on it.

  ```yaml
  ---
  template: page.html
  back: { label: Projects, url: projects/index.md }
  ---
  ```

### Add a publication

Add an entry to `publications:` in `docs/publications.md`. Entries are
grouped by year, newest first. Your name, set in `highlight_author`, is
shown in bold.

```yaml
publications:
  - title: Title of the paper
    authors: [First Author, Kota Uchida, Last Author]
    venue: Conference or journal
    year: 2026
    note: Oral                      # optional
    links:
      - { label: PDF, url: assets/papers/paper.pdf }
      - { label: arXiv, url: "https://arxiv.org/abs/xxxx.xxxxx" }
      - { label: DOI, url: "https://doi.org/..." }
      - { label: Code, url: "https://github.com/you/repo" }
```

While the list is empty, the page shows `empty_message`.

### Add a note

1. Create a Markdown file, e.g. `docs/notes/control/pid-tuning.md`.
2. Add it under `Notes` in `nav` (`zensical.toml`). Sub-lists become sidebar
   groups.
3. Optionally add `date: 2026-11-01` to its front matter so it appears under
   *Recent notes* on the home page.

Notes support `$math$`, fenced code with highlighting, admonitions
(`!!! note`), tabs, Mermaid diagrams, footnotes, and relative links between
`.md` files. See `docs/notes/guides/writing-notes.md`.

### Replace the CV

Overwrite `docs/assets/cv.pdf` with your own file. The CV page uses Markdown
definition lists: a date line, then a line starting with `:   `.

## Deploy to GitHub Pages

1. Push the repository to GitHub.
2. In `zensical.toml`, set `site_url` to the public address:
   - project site: `https://<user>.github.io/<repo>/`
   - user site (repository named `<user>.github.io`): `https://<user>.github.io/`
3. In the repository, go to **Settings → Pages → Build and deployment →
   Source** and choose **GitHub Actions**.
4. Push to `main`. The workflow in `.github/workflows/docs.yml` builds the
   site and publishes it. You can also run it manually from the **Actions**
   tab.

Pages use relative links, so the site works under a repository subpath.
`site_url` is used for absolute links: the 404 page, the sitemap, and
canonical URLs. `zensical serve` also previews under the same subpath.

> The workflow pins `zensical==0.1.0`, the version in `uv.lock`. To upgrade,
> run `uv lock --upgrade-package zensical`, check the site locally, then
> update the version in the workflow.

## How it works

```
zensical.toml              site settings and navigation
docs/                      content (Markdown, images, PDF, CSS)
  index.md                 home page (front matter = profile)
  projects/index.md        project list (front matter = data)
  publications.md          publication list (front matter = data)
  cv.md                    CV
  notes/                   technical notes (documentation layout)
  stylesheets/site.css     design tokens, layout, light/dark colors
overrides/                 template overrides (Zensical custom_dir)
  main.html                removes the tab row; loads KaTeX on math pages
  page.html                single-column layout for portfolio pages
  home.html                profile + selected projects + recent notes
  projects.html            renders the `projects` list
  publications.html        renders the `publications` list
  partials/header.html     compact top bar built from `nav`
  partials/footer.html     minimal footer
  partials/portfolio.html  shared macros for entries and links
```

A page picks its layout with `template:` in its front matter. Without it, a
page uses the standard documentation layout. Templates read data only from
front matter and `zensical.toml`, so you never need to edit HTML to change
content.

## Using this as a template

On GitHub, enable **Settings → General → Template repository**. To start a
new site from it, update `zensical.toml` (name, URL, social links), the
front matter of `docs/index.md`, and replace the placeholder entries.
