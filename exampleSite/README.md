# Example Site (Test Environment)

This folder is a minimal Hugo site wired to the SolidResume module for local development and testing.

## Prerequisites
- Hugo Extended v0.110+ installed and on PATH

## Run locally
```bash
cd exampleSite
hugo server -D --cacheDir "$PWD/.hugo_cache"
```

## Build static files
```bash
cd exampleSite
hugo -D --cacheDir "$PWD/.hugo_cache"
```

Notes:
- The module import points to the parent folder via `go.mod` `replace`.
- No network access is required; the build uses the local module.
- Build artifacts are ignored via `.gitignore` in this folder.
