# Contrast branch: `demo/merge-pr1-only-on-beta`

This branch is **`upstream/beta` plus `docs/readme-rewrite` only** (no PR #3 tooling).

Use it to compare behavior against **`demo/merge-pr3-then-pr1`** (see `DEMO-MERGE-STRATEGY.md` there).

- **Windows:** `python setup.py sdist` / `build_pkg_info` can still hit **cp1252** on the new UTF-8 README.
- **CI:** `.ci.sh` still assumes **Apple Silicon** Homebrew for `libomp` unless fixed elsewhere.
