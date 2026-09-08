# Diagram guidelines

> **Authoritative reference:** Read this file before deciding whether repository documentation needs diagrams and before creating, editing, or auditing any diagram.

Use diagrams as evidence-based explanatory aids. Prefer no diagram over a decorative, speculative, duplicated, or unreadable diagram.

## Diagram decision gate

Create or retain a diagram only when all conditions are met:

1. The subject contains a non-trivial relationship, lifecycle, topology, state transition, or data flow that prose, a table, or a directory tree does not explain as clearly.
2. Every node, participant, relationship, and direction is supported by repository evidence.
3. The diagram has a specific reader task, such as understanding system boundaries, following a critical runtime flow, reviewing deployment topology, or seeing entity relationships.
4. The result remains readable at normal Markdown width. Split a large diagram by concern rather than shrinking it into an exhaustive graph.
5. The target documentation system can render Mermaid, or the repository already uses another text-based diagram convention.

When any condition fails, use prose, a table, a numbered sequence, or an annotated tree instead.

## Preferred notation

Prefer Mermaid because it is text-based, reviewable, and version-controlled.

Choose the smallest suitable type:

- `flowchart` for system context, component relationships, dependency direction, deployment topology, and data movement.
- `sequenceDiagram` for ordered interactions across actors or components.
- `erDiagram` for evidenced entity relationships.
- `stateDiagram-v2` for meaningful lifecycle or state transitions.

Do not introduce image assets or generated binaries unless the user explicitly requests them or the repository already maintains diagrams that way.

## Evidence and companion text

Every diagram must:

- have a descriptive heading and one or two sentences explaining what it shows;
- be accompanied by a relationship table, numbered sequence, entity descriptions, or source-path list when the underlying facts matter operationally;
- use repository terminology rather than invented generic names;
- omit components and edges that are merely plausible;
- distinguish configured topology from runtime deployment when only static evidence is available;
- avoid secret values, internal credentials, personal data, and sensitive infrastructure details.

A diagram is not evidence by itself. The surrounding document must identify the source files, schemas, configuration, tests, or deployment definitions that support it.

## Placement guidance

Use diagrams primarily in:

- `docs/architecture.md` for system context, component boundaries, and important request or event flows;
- `docs/deployment.md` for evidenced build and runtime topology;
- `docs/data-model.md` for important entity relationships;
- flow-specific documentation for multi-component authentication, checkout, webhook, ingestion, synchronization, or asynchronous processing.

Usually avoid diagrams in:

- endpoint catalogs;
- simple setup instructions;
- configuration-variable tables;
- small directory structures;
- trivial CRUD descriptions;
- pages where a diagram would merely repeat an adjacent table.

## Size and readability

- Prefer focused diagrams with roughly 12 or fewer primary nodes or participants.
- Group only when the grouping is meaningful and evidenced.
- Avoid crossing-edge call graphs, exhaustive import graphs, and one-node-per-file diagrams.
- Use multiple small diagrams when different readers need different views.
- Keep labels short; explain detail in prose or tables.

## Update and audit rules

When updating documentation:

1. Revalidate every changed node and edge against current repository evidence.
2. Update companion text and tables together with the diagram.
3. Remove stale diagrams when they no longer clarify the current system.
4. Preserve an accurate existing diagram even if its style differs from these examples.
5. Flag unsupported or syntactically broken diagrams during audit-only work.

## Completion reporting

State which diagrams were created, updated, retained, removed, or intentionally omitted. For omission, give a short reason such as “the repository is small,” “the relationship is clearer as a table,” or “available evidence is insufficient.”
