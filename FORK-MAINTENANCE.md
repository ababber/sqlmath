# Fork maintenance (`ababber/sqlmath`)

This repository is a **public mirror** of [sqlmath/sqlmath](https://github.com/sqlmath/sqlmath). Keep commits publishable.

## Do not commit here

| Item | Where it belongs |
|------|------------------|
| `.route-cursor` with kit/shadow navigation | Private **`ababber/shadow-sqlmath`** |
| Shadow-architecture, trust, focus, `ckexpand` vocabulary | **`ababber/shadow-sqlmath`** |
| Internal workflow docs, evaluation notes | **`ababber/shadow-sqlmath`** |

## Pre-commit guard (required)

```bash
git config core.hooksPath .githooks
chmod +x .githooks/pre-commit
```

Or from the kit workspace:

```bash
ababber/shadow-sqlmath/install-publishable-hooks.sh
```

Commits that stage forbidden paths or phrases are **blocked** unless `SKIPPUBLISHABLEGUARD=1` (emergency only).

## Server-side guard

GitHub Actions workflow at `.github/workflows/publishable-guard.yml` provides server-side enforcement. Pushes and PRs with internal vocabulary will fail CI.

## Upstream sync

```bash
git fetch upstream --prune
git merge upstream/beta
git push origin beta
```

Internal workflow: **`ababber/shadow-sqlmath/UPSTREAM-SYNC-STATUS.md`**.
