# SolidResume

**SolidResume** is a work-in-progress Hugo Module for building a **single-page CV** website.  
The goal is to provide a clean, responsive, and printable design that follows modern web standards and produces structured, machine-readable data where appropriate.

> ⚠️ This project is **under active development**. Expect breaking changes, incomplete features, and frequent iterations.

## Getting Started

### Using SolidResume as a Hugo Module

You can import SolidResume into your existing Hugo site as a module. This allows you to keep your CV content separate and benefit from updates to the SolidResume module.

1. Initialize your Hugo site (if you haven't already):
```bash
hugo new site MyCV
cd MyCV
hugo mod init github.com/<your-username>/MyCV
```

2. Add SolidResume as a module dependency in your site's `config/_default/hugo.toml`:
```toml
[module]
  [[module.imports]]
    path = "github.com/solids/resume"
```

3. Place your CV data (YAML/JSON) inside your site's `data/` directory. SolidResume reads CV content from the consuming project's data files, not from within the module itself.

4. Start the development server:
```bash
hugo server -D
```

Open http://localhost:1313 in your browser to see your CV.

### Local test site (exampleSite)

This repo includes an `exampleSite/` folder with dummy CV data for local testing only. The root module contains no example content; all placeholder data lives under `exampleSite/data/`.

Run the example site locally:

```bash
cd exampleSite
hugo server -D --cacheDir "$PWD/.hugo_cache"
```

## Theming

SolidResume supports multiple color palettes out of the box:

- **Default Light** / **Default Dark** (auto-mode follows system preference)
- **Solarized Light**
- **Solarized Dark**
- **Nord**

Themes are data-driven (`/data/themes/*.yaml`) and can be extended with your own palettes. The theming system is integrated via Hugo Modules and can be customized in your site's configuration.

### Configuration

In your `config/_default/hugo.toml`, set the default theme:

```toml
[params.themes]
default = "auto"
```

## Languages

SolidResume supports multilingual sites. Each language needs:

- A language entry in your `config/_default/hugo.toml` under `[languages]`.
- A corresponding CV data file at `data/cv/<lang>.yaml` (or `.json`/`.toml`).
- Optional: an i18n translation file at `i18n/<lang>.toml` for UI strings.

### Enable multiple languages

```toml
defaultContentLanguage = "en"
defaultContentLanguageInSubdir = true

[languages]
  [languages.en]
    languageName = "English"
    weight = 1

  [languages.nb]
    languageName = "Norsk"
    weight = 2

  # Add more languages as needed
  [languages.de]
    languageName = "Deutsch"
    weight = 3
```

### Add a new language’s content

1) Create a data file `data/cv/<lang>.yaml`, e.g. `data/cv/de.yaml`.
2) Include at least `profile.name` so the title renders. See “CV Data Format” below.
3) UI translations: if your language isn’t bundled, add `i18n/<lang>.toml` in your site with keys used by the theme (e.g., `about`, `experience`, `education`, `projects`, `skills`, `languages`, `contact`, `download_pdf`).

The language switcher shows all configured languages; the current language is not a link.

## Author Image

Place your avatar in `static/` and set:

```toml
[params.author]
image = "/img/author.jpg"  # absolute path or full URL
```

The image renders in the header. A square image works best.

## CV Data Format

Store CV data per language, e.g. `data/cv/en.yaml`, `data/cv/nb.yaml`. YAML example with supported sections and fields:

```yaml
profile:
  name: "Your Name"           # required (used for the page title)
  role: "Your Role"           # optional
  location: "City, Country"   # optional
  email: "you@example.com"    # optional
  url: "https://your-site"    # optional
  summary: |
    One or two short paragraphs about you.
  links:                       # optional; rendered inline
    - label: "LinkedIn"
      url: "https://linkedin.com/in/you"
    - label: "GitHub"
      url: "https://github.com/you"

experience:                    # optional list; omit to hide section
  - company: "Company A"
    role: "Senior Engineer"
    start: "2022-01"          # recommend ISO-8601 (YYYY or YYYY-MM)
    end: "2024-06"            # omit or remove for current role
    summary: "Short blurb of impact and scope."
    bullets:
      - "Achievement or responsibility one"
      - "Achievement two"

education:                     # optional list
  - school: "University X"
    degree: "B.Sc. in Y"
    start: "2018"
    end: "2021"

projects:                      # optional list
  - name: "Project Name"
    url: "https://project.example"
    summary: "What it is and your role."

skills:                        # optional flat list
  - "Go"
  - "Hugo"
  - "Accessibility"

spoken_languages:              # optional list
  - name: "English"
    level: "Native"
  - name: "German"
    level: "Professional"

contact:                       # optional; renders a simple list
  email: "you@example.com"
  website: "https://your-site"
```

Notes:
- Any top‑level section can be omitted; templates only render sections that are present and non‑empty.
- Dates are displayed as provided; use consistent ISO formats for clarity.
- Links in `profile.links` render inline with separators.
- Data is read from the consuming site, not from within the module.

## Roadmap

- [x] Basic Hugo module scaffolding
- [x] Data-driven CV content (YAML/JSON) in consuming project
- [x] Multilingual setup
- [x] Theming support via Hugo Modules
- [ ] Print stylesheet for PDF export
- [ ] SEO + structured data integration

## Contributing

Contributions, ideas, and feedback are welcome! Please note that the project is in an early stage, so discussions and issue reports are especially valuable.

## License

MIT © Even Roland Sollid
