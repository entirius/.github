# Contributing to Entirius

These guidelines apply to every repository in the `entirius` organization unless the
repository ships its own version.

## Open code, closed roadmap

Entirius is open source (MPL 2.0), built by a commercial team that runs e-commerce for a
living. That shapes the deal, so we write it down instead of pretending otherwise.

What we promise:

- Every issue and PR gets a first response from a human within a few business days.
- Every PR gets a real review from the maintainer of the module it touches.
- An accepted contribution ships in the next release of that module, credited to you.

What we don't promise:

- Building your feature request. The roadmap is set by the core team and is not up for
  a vote — good ideas influence it, issues don't steer it.
- Debugging your deployment. Issues are for defects in the platform, not for individual
  stores. Bug report with a traceback: yes. "My checkout doesn't work, please look": no.

If that deal works for you, welcome aboard.

## AI-first, human-led

We build Entirius with AI agents — not as a gimmick, as the default way code gets
written here. The platform is deliberately kept legible to them: every repo carries an
`AGENTS.md` with its architecture and gotchas, module boundaries are strict, the
OpenAPI spec is generated from code, and `entirius-zeno` runs the whole stack with one
`make up`. A codebase an agent can navigate is a codebase a newcomer can navigate —
the same clarity serves both.

The human is the designer: we decide what to build, how it should work, and whether
the result is right. The agent types. If you still write every line by hand, nobody
will stop you — but we'd rather you tried operating: state the intent, review the
diff, own the outcome. Same engineering, one level up.

Two rules keep this honest:

- **You own what you submit.** A PR is your work, whoever typed it. "The agent wrote
  it" is not a review response.
- **You don't need our tooling.** We ship our coding rules as a Claude Code plugin
  (`entirius-code`) — that's our convenience, not your requirement. Good code that
  passes the checks has full right to a PR — written with an agent, an IDE, or `ed`.

## Ground rules

- **License:** MPL 2.0. Every non-trivial source file carries the MPL header; keep it intact.
- **Language:** English only — code, comments, docs, commits, branches, PRs, issues.
- **Conduct:** [Code of Conduct](CODE_OF_CONDUCT.md). Short version: be a professional.

## Toolchain

- **uv** — environment, dependencies, lockfile (`uv.lock` is committed).
- **ruff** — linting and formatting.
- **pytest** (+ `pytest-django` where relevant) — tests.
- **pre-commit** — local gate: ruff, MPL header, secret scan.
- **make** — task runner; `make help` lists everything.

## Local setup

```bash
# 1. Fork, then clone your fork
git clone git@github.com:<you>/<repo>.git
cd <repo>

# 2. Dependencies and hooks
uv sync
uv run pre-commit install

# 3. See what the repo can do
make help
```

## Branching (git-flow)

| Branch | Purpose |
|---|---|
| `master` | production — always deployable |
| `develop` | integration — base for feature branches |
| `feature/<name>` | new work, branched from `develop` |
| `release/<semver>` / `hotfix/<semver>` | releases and urgent fixes |

- Open pull requests against **`develop`**. Feature branches are squash-merged.
- Branch names are lowercase, words separated by `-`.
- `master` and `develop` accept changes only via pull request. No exceptions,
  no "just this once."

## Before you open a pull request

```bash
make check   # lint + format
make test    # migration drift + tests
```

- pre-commit must pass. If the secret scan fires, fix it before pushing — never after.
- One purpose per commit, one purpose per PR. A PR that "also fixes" three unrelated
  things gets three times the review latency.
- Fill in the PR template. "What & why" is the part we actually read first.

## Bugs, ideas, vulnerabilities

Bugs and feature requests: use the issue templates in the module's repository.
Security vulnerabilities: **never** in a public issue — follow the
[Security Policy](SECURITY.md).
