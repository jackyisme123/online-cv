# Online CV / Resume

A personal, single-page **online CV** built with [Jekyll](https://jekyllrb.com/) and hosted on **GitHub Pages**.
It renders a clean two-column resume (profile + dark sidebar) straight from one YAML file, and includes an
A4-optimized print/PDF view.

- **Live site:** <https://jackyisme123.github.io/online-cv/>
- **Printable version:** <https://jackyisme123.github.io/online-cv/print>

> Theme attribution: this site is based on the *Orbit* resume template designed by
> [Xiaoying Riley](http://themes.3rdwavemedia.com/) (Jekyll port by
> [sharu725/online-cv](https://github.com/sharu725/online-cv)).

---

## Features

- **Single data source** — every piece of content lives in `_data/data.yml`; no HTML editing needed.
- **A4 print layout** — the `/print` page and `@media print` stylesheet produce a print-ready, two-column A4 CV.
- **Right sidebar sections** — Education, Core Competencies, Languages, Interests, Volunteer, Referee.
- **CI/CD deployment** — a GitHub Actions workflow builds and deploys the site to GitHub Pages on every push.
- **Theme skins** — choose between 6 colour schemes (blue, turquoise, green, berry, orange, ceramic) in `_config.yml`.
- **Local preview via Docker** — one command spins up a live-reload server.
- **Dark, cross-platform installs** — requires only Docker (and optional Ruby for local hosting).

---

## Architecture

### How a page is rendered

```
 browser request
      │
      ▼
┌─ index.html / print.html (Liquid templates)
      │  references the `default` / `print` layout
      ▼
┌─ _layouts/default.html or print.html
      │   includes sidebar + main content + footer
      ▼
┌─ _includes/*.html               ┌─ _data/data.yml
      │   pull sections via           (the only file to edit
      │   site.data.data.<section>      for content changes)
      ▼
┌─ _sass/*.scss + assets/plugins  ──►  assets/css/main.css (compiled by Jekyll)
      ▼
  static HTML + CSS site  ──►  GitHub Pages / localhost
```

The sidebar is a separate component (`_includes/sidebar.html`) shown on **every** page (both
`index.html` and `print.html`). `sidebar.education` (also `sidebar.skills`, `sidebar.about`)
toggles whether those blocks render in the sidebar or in the main column.

### File map

```
online-cv/
├── _config.yml              # Site title, URL, baseurl, theme skin, Sass settings
├── _data/
│   └── data.yml             # ★ ALL resume content is edited here
├── _includes/               # Liquid partials (career-profile, experiences, sidebar, skills…)
│   ├── sidebar.html         # right-column layout container
│   ├── education.html       # education block (sidebar or main, per data.yml flag)
│   ├── skills.html          # Core Competencies block
│   └── ….
├── _layouts/
│   ├── default.html         # on-screen page shell (sidebar + main-wrapper)
│   └── print.html           # print / PDF page shell
├── _sass/
│   ├── _base.scss           # main styling
│   ├── _print.scss          # ★ A4 print stylesheet (@media print + @page)
│   ├── _responsive.scss     # mobile rules
│   └── skins/               # the 6 colour schemes
├── assets/                  # css, js, images, plugins (Bootstrap, Font Awesome)
├── index.html               # home page (lists sections)
├── print.html               # printable page (lists sections for print)
├── .github/workflows/jekyll.yml   # GitHub Actions deploy pipeline
├── docker-compose.yml       # local Docker preview (Jekyll 3.8)
├── Gemfile / Gemfile.lock   # Jekyll + GitHub Pages gem versions
└── favicon.ico
```

---

## How content flows into the site

1. Jekyll loads `_data/data.yml` into `site.data.data` at build time.
2. `index.html`/`print.html` call the section includes (e.g. `career-profile.html`, `experiences.html`, `projects.html`).
3. Each include looks up its data key and renders it with the selected layout and Sass styles.

> **Tip:** there is no database or backend. Rebuild / pushes = refresh the content.

---

## How to use

### 1. Edit your resume — `_data/data.yml`

All content lives here:

| Key | What it controls | Example |
|---|---|---|
| `sidebar` | name, tagline, links, language, interests, volunteer, and flags `education` / `skills` / `about` | `education: true` → rendered in the sidebar box |
| `career-profile` | intro summary paragraph | 4-line summary |
| `education` | education & certificates list | `time: 2012 - 2014` |
| `experiences` | work history (`role`, `time`, `company`, `details` bullets) | details use `-` bullet lines |
| `projects` | project assignments (`title`, `link`, `tagline`) | — |
| `skills` | Core Competencies list (`name`, `text`, `level`) | `text:` lists the sub-tools |

> **YAML gotcha:** `time: 9999` is rendered as **"No expiry"** (handled by the include). Keep every
> field indentation consistent — a YAML error breaks the whole site.

### 2. Site-wide settings — `_config.yml`

```yaml
title:    Platform Engineer & SRE
url:      https://jackyisme123.github.io
baseurl:  /online-cv            # matches the repository name
theme_skin: blue               # blue | turquoise | green | berry | orange | ceramic
```

`url` + `baseurl` must match the GitHub Pages settings of your own repository before deploying.

### 3. Colours — choose a skin

Set `theme_skin` (see above). Skins live in `_sass/skins/`.

---

## Local preview (Docker)

Requires Docker only. Ruby is not needed on your machine.

### Run the dev server (live reload)

```sh
docker compose run --rm --service-ports -d jekyll jekyll serve --force_polling
```

- `-d` runs it in the background.
- `--force_polling` picks up edits to `_data/data.yml` automatically (no restart).
- Check it at **http://localhost:4000/online-cv/** (note the `/online-cv/` base path).
- Print/PDF view: **http://localhost:4000/online-cv/print**

Stop it with `docker stop <container-name>` (find it via `docker ps`).

### Build only (no server)

```sh
docker compose run --rm jekyll jekyll build
# outputs the static site to ./_site and validates data.yml / SCSS
```

Tip: the first start installs the bundled gems and can take a minute. Wait for
`Server running… press j to stop.` in the container logs before opening the browser.

### Without Docker (local Ruby)

```sh
bundle install
bundle exec jekyll serve
# open http://localhost:4000/online-cv/
```

## Generating the A4 PDF

The `_sass/_print.scss` applies an A4 layout (`@page … size: A4`, 2-column grid, compact typography)
only when printing. Two ways to get a PDF:

1. **Browser:** open <https://jackyisme123.github.io/online-cv/print>, `Ctrl+P / Cmd+P`, pick “Save as PDF”, enable `Background graphics`.
2. **Headless Chrome (from a local preview):**
   ```sh
   chrome --headless --disable-gpu --no-pdf-header-footer \
     --print-to-pdf="cv.pdf" "http://localhost:4000/online-cv/print"
   ```

Keep a fresh `yuan-cv.pdf` and point the sidebar `pdf:` link at it if you reference one.

## Deployment (GitHub Pages)

`.github/workflows/jekyll.yml` auto-deploys:

- On every `push` to `master`.
- Manually from the **Actions** tab (`workflow_dispatch`).

It builds Jekyll on `ubuntu-latest`, uploads the `_site` artifact and reports it to GitHub Pages —
no third-party token needed (OIDC-managed permission).

Status badge: add a badge pointing to your Actions tab if you want one.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Site doesn't change after editing `data.yml` | commit → the workflow triggers automatically; or run the build locally to confirm YAML is valid |
| Layout breaks | check indentation in `data.yml` (YAML is strict; two-space indent for nesting) |
| PDF shows the sidebar empty / wrong order | in printing, enable **Background graphics** (browser default turns off background colours) |
| Local assets missing | make sure you already open `http://localhost:4000/online-cv/` (base url path) not the root |
| Gems fail to build | `bundle install` again with a Ruby 3.x (as used by the workflow) |

## Credits

- Theme: *Orbit* by [Xiaoying Riley](http://themes.3rdwavemedia.com/) — Jekyll port by [sharu725/online-cv](https://online-cv.webjeda.com).
- Icons: Font Awesome, Bootstrap.