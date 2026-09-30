# AI Engineer Notes

Personal notes learning AI engineering, node by node from
[roadmap.sh/ai-engineer](https://roadmap.sh/ai-engineer). Written by
[MD Ariful Islam Protik](https://github.com/arifulprotik).

Live book: <https://ArifulProtik.github.io> (served from the `gh-pages`
branch by `.github/workflows/mdbook.yml`).

## Local preview

```bash
cargo install mdbook                  # one-time
mdbook serve --open                   # preview at :3000
mdbook build                          # output in book/ (gitignored, never commit)
```

## Layout

- `book.toml` — mdBook config
- `src/SUMMARY.md` — chapter index, single source of truth
- `src/preface.md` — unnumbered first page
- `PROGRESS.md` — per-node checklist, updated on every completion
