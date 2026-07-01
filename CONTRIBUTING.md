# Contributing to Entirius

Thanks for your interest in contributing. These guidelines apply to every repository
in the `entirius` organization unless a repository overrides them with its own file.

## Ground rules

- **License:** contributions are made under the **Mozilla Public License 2.0**. Every
  non-trivial source file carries the MPL header; keep it intact.
- **Language:** English only — code, comments, docs, commits, branches, PRs, and issues.
- **Be respectful:** see our [Code of Conduct](CODE_OF_CONDUCT.md).

## Toolchain

- **uv** — environment, dependencies, and lockfile (`uv.lock` is committed).
- **ruff** — linting and formatting.
- **pytest** (+ `pytest-django` for Django code) — tests.
- **pre-commit** — local gate (ruff, license header, secret scanning).
- **make** — task runner; run `make help` to list tasks.

## Local setup

```bash
# 1. Fork the repository, then clone your fork
git clone git@github.com:<you>/<repo>.git
cd <repo>

# 2. Install dependencies and hooks
uv sync
uv run pre-commit install

# 3. See available tasks
make help
```

## Branching (git-flow)

| Branch | Purpose |
|---|---|
| `master` | production — always deployable |
| `develop` | integration — base for feature branches |
| `feature/<name>` | new work, branched from `develop` |
| `release/<semver>` / `hotfix/<semver>` | releases and urgent fixes |

- Branch names are lowercase, words separated by `-`.
- Open pull requests against **`develop`** (feature branches are squash-merged).
- `master` and `develop` accept changes only via pull request.

## Before you open a pull request

```bash
make check   # lint + format check
make test    # migration drift check + tests
```

- pre-commit must pass (ruff, MPL license header, secret scan).
- Never commit secrets or credentials — secret scanning runs locally and in CI.
- Keep commits focused; write clear, single-purpose messages.
- Fill in the pull request template and describe the change and its motivation.

## Reporting bugs and requesting features

Use the issue templates. For security vulnerabilities, do **not** open a public issue —
follow the [Security Policy](SECURITY.md).
