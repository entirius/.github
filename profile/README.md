# Entirius

Open-source e-commerce platform: Django backend, PWA frontends, everything behind a
versioned REST API. MPL 2.0.

The backend — **Volkanos** — is a modular monolith. Not microservices (we don't hate
ourselves), but not a single blob either: one deployable unit, ~25 Django modules with
strict boundaries, each released as its own package from its own repository. That's why
this organization looks like a lot of repos — it's one platform in small,
independently versioned pieces.

## Finding your way around

| Prefix | What it is |
|---|---|
| `entirius-django-*` | Volkanos modules — PIM, checkout, accounts, email, matrix, ... |
| `entirius-py-*` | Python SDKs for external services |
| `entirius-pwa-*` | Frontends — storefront (Next.js / React), CMS (Vue 3), admin |
| `entirius-service-*` | Service shells that compose modules into a deployable backend |
| `entirius-zeno` | Docker harness — the whole platform running with one `make up` |
| `entirius-test-package-*` | Demo data + the BDD suite that runs on it |

## AI-first, human-led

Entirius is written by AI agents operated by humans, and the platform is deliberately
kept legible to them: every repo carries an `AGENTS.md`, module boundaries are strict,
the API spec is generated from code, the whole stack runs with one `make up`. A codebase
an agent can navigate is a codebase you can navigate — the same clarity serves both.

Standing up a solid e-commerce platform is table stakes — a store that runs itself
is the point. Agents build it. Agents will run it. We (human) design it.

## Start here

- Want to **see it run**? Clone [entirius-zeno](https://github.com/entirius/entirius-zeno)
  and follow its README — infrastructure, service, demo data, tests, all via `make`.
- Want to **read first**? [docs.entirius.com](https://docs.entirius.com) — architecture,
  module docs, API reference.
- Want to **contribute**? [CONTRIBUTING](https://github.com/entirius/.github/blob/master/CONTRIBUTING.md).
  The deal is "open code, closed roadmap" — spelled out there, no fine print.

Built by a commercial team that runs e-commerce for a living; developed in the open
because that's how platform code should live.
