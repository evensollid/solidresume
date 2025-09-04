# Example Site (Test Environment)

This folder is a minimal Hugo site wired to the SolidResume module for local development and testing. It is not included when you import the module into your own site.

## Prerequisites
- Hugo Extended v0.110+ installed and on PATH

## Run locally (clone required)
```bash
git clone https://github.com/evensollid/SolidResume.git
cd SolidResume/exampleSite
hugo server -D --cacheDir "$PWD/.hugo_cache"
```

## Build static files
```bash
cd exampleSite
hugo -D --cacheDir "$PWD/.hugo_cache"
```

Notes:
- `go.mod` uses `replace github.com/evensollid/SolidResume => ../`, so the example expects to live inside a clone of the repo.
- To use this example outside the repo, remove the `replace` line and run:
  ```bash
  hugo mod get github.com/evensollid/SolidResume@latest
  hugo mod tidy
  ```
- No network access is required when running inside the clone; the build uses the local module.
- Build artifacts are ignored via `.gitignore` in this folder.
