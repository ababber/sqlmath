# Demo: merge order for PR #3 then PR #1

This file exists on **`demo/merge-pr3-then-pr1`** only (not intended for upstream merge as-is). It explains how **Ankit’s fork** models the recommended integration order for Kai.

## Pull requests (upstream)

| PR | Branch (fork) | Role |
|----|---------------|------|
| [sqlmath/sqlmath#3](https://github.com/sqlmath/sqlmath/pull/3) | `fix/windows-utf8-and-ci` | `setup.py` UTF-8 for Windows `sdist` / `PKG-INFO`, `.ci.sh` libomp + LightGBM paths, Node `waitAsync` + V8 coverage spawn |
| [sqlmath/sqlmath#1](https://github.com/sqlmath/sqlmath/pull/1) | `docs/readme-rewrite` | README rewrite (large UTF-8 document) |

## Recommended order

1. **Merge #3 into `beta` first** — fixes Windows `UnicodeDecodeError` in `build_pkg_info`, Intel Homebrew `libomp`, and local/CI Node coverage quirks before the big README lands.
2. **Then merge #1 into `beta`** (or rebase `docs/readme-rewrite` onto updated `beta`) — README picks up the fixed tooling automatically.
3. **Regenerate `PKG-INFO`** after the README merge if you keep it in git (`python -c "from setup import build_pkg_info; build_pkg_info()"` or your release step).

## Branches on `ababber/sqlmath` (demo)

- **`demo/merge-pr3-then-pr1`** — `upstream/beta` → merge **#3** → merge **#1** → `PKG-INFO` regenerated from merged `README.md`. **Use this to run CI or `python setup.py sdist` as the “happy path”.**
- **`demo/merge-pr1-only-on-beta`** — `upstream/beta` → merge **#1** only (no #3). **Contrast:** Windows / CI can still hit the old `setup.py` / `.ci.sh` issues with the new README.

## Verify locally (fork)

```sh
git fetch origin
git checkout demo/merge-pr3-then-pr1
# optional: shadow workspace helper
/path/to/shadow-sqlmath/run-staging-ci.sh
```

---

*Branch and doc for reviewer demo; close or delete after upstream merges.*
