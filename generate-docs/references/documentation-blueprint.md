# Documentation blueprint

> **Authoritative reference:** Read this file in full before selecting documentation outputs.

Use this matrix to choose output files. Create only documents supported by the repository and useful to its likely readers.

## Baseline documents

| File | Create or update when | Required content |
|---|---|---|
| `README.md` | Almost always | Purpose, major capabilities, prerequisites, quick start, primary commands, links to deeper docs |
| `docs/getting-started.md` | Setup requires more than a few commands or external services | Prerequisites, install, configuration, first run, verification, common setup failures |
| `docs/project-structure.md` | The repository has multiple important directories or packages | Annotated tree, ownership/purpose of major paths, generated/vendor boundaries |
| `docs/development.md` | Contributors need build, test, lint, format, or local-service workflows | Commands from manifests/CI, test strategy, debugging, code generation, checks |
| `CONTRIBUTING.md` | The repo accepts or coordinates code contributions | Setup link, branch/commit/PR expectations evidenced by repo, required checks, reporting issues |

A small library or single-purpose script may need only a strong `README.md` and `CONTRIBUTING.md`.

## Conditional documents

| Signal in repository | Suggested document | Include |
|---|---|---|
| Multiple services, packages, layers, workers, or major adapters | `docs/architecture.md` | Context, components, boundaries, dependency direction, request/event flows, key source paths; an evidence-based diagram only when it improves comprehension |
| Public HTTP/RPC/GraphQL routes, OpenAPI, controllers, handlers | `docs/api-reference.md` | Base path, auth evidence, endpoint table, request/response source types, errors, examples clearly labeled |
| Environment variables, config loaders, config schemas, example env files | `docs/configuration.md` | Variable name, required/default status, effect, source path; never secret values |
| Database schemas, ORM models, migrations, protobuf schemas, domain entities | `docs/data-model.md` | Main entities, relationships, migration workflow, persistence boundaries; an ER diagram only for important evidenced relationships |
| Docker, Compose, Kubernetes, Terraform, deployment workflows, platform config | `docs/deployment.md` | Build artifact, runtime config, services, health checks, deployment flow, rollback evidence; topology diagram only when configuration proves it |
| Queues, cron, background jobs, event consumers/producers | `docs/operations.md` | Job/event catalog, triggers, retries if evidenced, observability paths, failure handling |
| Library exports or SDK surface | `docs/library-reference.md` or generated API docs | Installation, imports, public symbols, examples, compatibility only if evidenced |
| Authentication, authorization, encryption, security policy | `docs/security.md` | Trust boundaries, auth flow, permissions, secret handling, vulnerability reporting |
| Monorepo/workspaces | `docs/workspaces.md` | Package map, dependency relationships, shared tooling, package-specific commands |


## Diagram selection

After selecting documents, apply `diagram-guidelines.md` before drafting:

- Consider diagrams for architecture, deployment, data relationships, and non-trivial cross-component flows.
- Do not create a diagram merely because a document template contains a diagram location.
- Prefer tables, numbered flows, and annotated trees when they are clearer or evidence is incomplete.
- Do not duplicate an equivalent code-wiki diagram unless this documentation has a distinct human-facing purpose.

## Selection heuristics

- Prefer one focused document over many thin files.
- Keep task-oriented onboarding separate from explanatory architecture.
- Put API details near generated specifications when OpenAPI, GraphQL schema, protobuf, or typedoc-style output already exists; link rather than duplicate unstable detail.
- If a document would consist mostly of “unknown,” do not create it. Record the gap in the final report instead.
- For repositories with several applications, use `docs/<service>/` only when each service has substantial independent setup or architecture.

## Recommended navigation

Add a short Documentation section to the root README that links only to files that exist. Use descriptive link labels and relative paths.
