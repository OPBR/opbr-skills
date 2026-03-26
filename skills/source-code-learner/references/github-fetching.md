# GitHub Repo Fetching Guide

## Fetching repo structure
```
GET https://api.github.com/repos/{owner}/{repo}/contents/
```
Returns a JSON array of files/dirs with `name`, `type` (file/dir), `path`, `download_url`.

## Fetching a specific file
```
GET https://raw.githubusercontent.com/{owner}/{repo}/main/{path}
```
Or use `download_url` from the contents API response.

## Fetching nested directories
Recursively call:
```
GET https://api.github.com/repos/{owner}/{repo}/contents/{dir_path}
```

## Priority files to fetch first (in order)
1. `README.md` — understand purpose and usage
2. `package.json` / `requirements.txt` / `go.mod` / `Cargo.toml` — deps & entry points
3. Entry point file (main.js, index.js, app.py, main.go, src/main.rs, etc.)
4. Core model/schema files
5. Config files

## Parsing entry points
- **Node.js**: `"main"` field in package.json, or `"scripts.start"`
- **Python**: look for `if __name__ == "__main__"` or `setup.py` entry_points
- **Go**: `func main()` in `main.go`
- **Rust**: `src/main.rs` or `src/lib.rs`

## Size limits
- Skip files > 100KB for initial read (binary, generated, vendored)
- Skip `node_modules/`, `vendor/`, `.git/`, `dist/`, `build/`
- Skip test files for the initial roadmap (include them in Stage 3+)