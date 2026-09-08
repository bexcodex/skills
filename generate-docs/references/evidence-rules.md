# Evidence rules

> **Authoritative reference:** Read this file in full before evaluating or writing repository claims.

## Evidence hierarchy

Use the strongest available source for each claim:

1. Executable configuration and schemas: manifests, CI workflows, route declarations, config schemas, migrations, container or infrastructure files.
2. Current implementation and exported interfaces.
3. Tests and fixtures that demonstrate intended behavior.
4. Existing documentation and examples.
5. Naming conventions or directory structure alone.

Lower-ranked evidence must not override stronger evidence without noting the conflict.

## Claim ledger

Before drafting a substantial document, maintain a compact internal ledger:

| Claim | Status | Evidence |
|---|---|---|
| Development server uses port 3000 | verified | `config/default.ts`, line or key |
| Worker processes emails asynchronously | inferred | queue dependency plus `workers/email.*` |
| PostgreSQL is required in production | unknown | Compose uses PostgreSQL, production config absent |

Do not include the ledger in repository docs unless the user asks for it.

## Source references in prose

- Mention source paths naturally: “Routes are registered in `src/http/routes.ts`.”
- For tables, add a `Source` column when claims may change frequently.
- Use line numbers only when the environment provides stable references and the repository is not actively changing.
- Link to source files with relative Markdown links when practical. Otherwise use backticked paths.
- Avoid citing generated files when an authoritative source file exists.

## Commands

Classify commands before documenting them:

- **Declared:** present in a package script, Makefile, task runner, CI workflow, or existing verified instructions.
- **Derived:** a conventional invocation inferred from tooling but not declared.
- **Executed:** run successfully in the current environment.

Present declared commands normally and state in the completion report whether they were executed. Do not present derived commands as guaranteed; label them as suggested and explain the basis.

## Conflicts and uncertainty

- When README and code disagree, prefer current executable configuration and flag the README as stale.
- When dev and production configuration differ, document both scopes explicitly.
- When optional integrations are detected only through dependencies, do not claim they are active.
- When route extraction is ambiguous, inspect the registering file and handler before documenting the endpoint.
- When architecture rationale is absent, describe structure and behavior, not intent.

## Secret handling

Never include:

- Values from `.env`, secret stores, credentials, access tokens, cookies, private keys, connection strings containing credentials, or CI secret expansions.
- Real personal data from fixtures, dumps, logs, screenshots, or examples.

Document variable names and expected formats only when supported by example files, schemas, or code references. Replace any unavoidable sensitive-looking example with an obvious placeholder such as `YOUR_API_TOKEN`.


## Diagram evidence

Treat each diagram element as a material claim:

- Every node or participant must correspond to an evidenced actor, process, module, store, external system, entity, or state.
- Every edge, direction, event, and transition must have supporting implementation, schema, test, configuration, or deployment evidence.
- Do not place inferred or merely conventional relationships in a diagram. Describe them as inference in prose instead.
- When evidence supports a component but not its runtime deployment, label the view as configured or statically observed rather than deployed.
- Keep source paths in companion text or tables so readers can verify the visual model.
