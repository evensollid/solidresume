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