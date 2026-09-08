---
name: spec-driven
description: Create, refine, review, plan, implement, and verify software work from an explicit specification that acts as the source of truth. Use when the user asks for spec-driven development, a technical/feature specification, requirements-to-spec conversion, acceptance criteria, implementation from a spec, gap analysis between code and a spec, or a disciplined workflow for complex/ambiguous/high-risk coding tasks. Also use when a coding request has enough ambiguity that defining behavior before implementation will materially reduce rework. Do not force a formal spec for trivial low-risk edits unless the user requests one.
---

# Spec-Driven Development

Turn software requests into an explicit behavioral contract, then use that contract to plan, implement, and verify the work.

## Operating principles

1. Treat the approved spec as the source of truth for intended behavior.
2. Separate **what must be true** from **how to build it**:
   - Spec = behavior, constraints, contracts, acceptance criteria.
   - Plan = implementation sequence, files/components, migrations, tests, rollout.
3. Do not hide ambiguity inside implementation decisions. Surface material ambiguities as assumptions, questions, or explicit choices.
4. Scale rigor to risk. Keep trivial changes lightweight; make complex, irreversible, security-sensitive, payment, data-integrity, permission, migration, or distributed-system work explicit.
5. Verify outcomes against acceptance criteria, not against whether the code merely compiles.
6. Preserve existing project conventions unless the spec explicitly requires changing them.
7. Write all persisted spec artifacts in English, regardless of the user's chat language. The conversational response may match the user's language.

## Workflow decision

Classify the request before proceeding:

- **Spec only**: The user wants a specification or requirements document. Produce/refine the spec and stop.
- **Spec + plan**: Produce/refine the spec, then create an implementation plan derived from it.
- **Implement from spec**: Read the provided spec and relevant codebase context, identify blockers or contradictions, plan the work, implement, then verify.
- **Review existing spec**: Find ambiguity, contradictions, missing edge cases, unverifiable requirements, and unnecessary implementation detail; propose concrete fixes.
- **Verify implementation**: Compare the implementation and tests against the spec; report pass/fail/unknown per acceptance criterion.
- **Trivial low-risk edit**: Use a compact micro-spec rather than a large formal document unless the user explicitly requests full rigor.

For the standard structure, you must read `references/spec-template.md`. For final quality checks, read `references/quality-checklist.md`.

## Repository artifact convention

When operating inside a writable repository, persist spec-driven artifacts automatically. Do not require the user to explicitly ask for file output.

Use this directory layout:

```text
docs/spec/<feature>/
├── spec.md
├── plan.md
└── verification.md
```

Apply these rules:

1. Derive `<feature>` from the feature/change name as a short lowercase kebab-case slug, (e.g. `checkout`, `password-reset`, `order-cancellation`).
2. Write `spec.md` whenever creating or materially revising a spec, including compact specs and micro-specs.
3. Write `plan.md` when an implementation plan is requested or needed for implementation.
4. Write `verification.md` when verifying an implementation against the spec.
5. Keep all persisted artifact content in English, including headings, requirements, assumptions, plans, and verification notes.
6. Keep requirement and acceptance-criterion IDs stable across revisions.
7. Update existing files in the same feature directory rather than creating duplicate timestamped or renamed copies unless the user explicitly requests versioned artifacts.
8. Treat `docs/spec/<feature>/spec.md` as the canonical source of truth for intended behavior once it exists. Read it before planning, implementation, or verification.
9. If the repository is not writable or file tools are unavailable, return the artifact in chat and state the intended repository path.
10. If the user explicitly requests a different path or filename, follow the user's path for that request while retaining English artifact content unless they explicitly override the language requirement.

## Phase 1: Build context

Before writing a spec for an existing codebase:

1. Inspect the relevant project files, tests, interfaces, schemas, conventions, and neighboring implementations when available.
2. Distinguish current behavior from requested behavior.
3. Reuse existing domain language and names instead of inventing parallel terminology.
4. Record constraints that are already imposed by the system, framework, API, database, or deployment environment.
5. Do not specify implementation details as requirements unless they are true constraints from the user or system.

For a greenfield request, infer only low-risk defaults. Mark material assumptions explicitly.

## Phase 2: Resolve ambiguity

Convert vague requests into decisions that can be tested.

### Ask versus assume

Ask a question when the answer can materially change one or more of:

- user-visible behavior;
- data model or persistence semantics;
- public API/interface contract;
- authorization/security boundary;
- money, inventory, quotas, billing, or irreversible effects;
- backward compatibility;
- migration strategy;
- failure/retry/idempotency behavior;
- acceptance criteria.

If progress should continue without waiting, choose the safest reasonable assumption and label it under **Assumptions / Open Decisions**. Never silently guess a material requirement.

Do not ask about details that can be discovered from available project context.

### Convert weak language into testable statements

Replace vague phrases such as:

- "fast" → measurable latency/throughput target when it matters;
- "secure" → concrete auth, authorization, validation, secret, or threat requirements;
- "handle errors" → named failure classes and required outcomes;
- "user friendly" → observable interaction behavior;
- "supports retries" → retry conditions, limits, backoff, and idempotency semantics.

If no justified numeric target exists, do not invent one. Mark the target as an open decision or state a qualitative requirement with a verification method.

## Phase 3: Write the spec

Use the smallest structure that fully captures behavior. Prefer the template in `references/spec-template.md`. In a writable repository, write or update the result at `docs/spec/<feature>/spec.md` before moving to planning or implementation.

A strong spec normally includes:

1. **Goal / problem** — what outcome is needed and why.
2. **Scope** — included behavior.
3. **Non-goals** — explicitly excluded behavior where confusion is likely.
4. **Current behavior** — only when modifying an existing system.
5. **Functional requirements** — numbered, atomic, testable requirements.
6. **User/system flows** — happy path plus meaningful alternative paths.
7. **Contracts** — API, events, data, state transitions, or UI behavior when relevant.
8. **Edge and failure cases** — validation, retries, duplicates, timeouts, concurrency, partial failure, empty states, permissions, etc.
9. **Non-functional requirements** — security, privacy, reliability, performance, accessibility, observability, compatibility, localization, or compliance only when relevant.
10. **Assumptions / open decisions** — unresolved points and chosen temporary assumptions.
11. **Acceptance criteria** — externally observable pass/fail conditions.

### Requirement rules

Write each important requirement so a reviewer can answer "pass" or "fail".

Prefer normative terms consistently:

- **MUST** = required for acceptance.
- **SHOULD** = strong preference with a legitimate exception.
- **MAY** = optional behavior.

Assign stable IDs when the spec is more than a few requirements:

```text
FR-1, FR-2 ...       functional requirements
NFR-1, NFR-2 ...     non-functional requirements
AC-1, AC-2 ...       acceptance criteria
```

Link acceptance criteria to requirement IDs where useful.

### Keep the spec implementation-agnostic

Specify implementation choices only when they are actual constraints or contracts. For example:

- Good requirement: "Duplicate payment callbacks MUST NOT create duplicate charges or state transitions."
- Implementation detail: "Use Redis SETNX for callback deduplication."

Put the second statement in the implementation plan unless Redis is mandated by the project.

## Phase 4: Run a spec review gate

Before planning or implementation, check the spec for:

- contradictions;
- undefined actors or states;
- missing authorization rules;
- missing validation/failure behavior;
- concurrency/idempotency issues where side effects exist;
- compatibility/migration implications;
- acceptance criteria that cannot actually be verified;
- requirements that smuggle in arbitrary implementation choices;
- scope that is larger than the stated goal requires.

Classify issues:

- **Blocker** — implementation should not begin safely without resolution.
- **Important** — proceed only with an explicit assumption.
- **Minor** — can be resolved during planning without changing externally observable behavior.

If no blockers remain, declare the spec **implementation-ready**. This is a quality gate, not a request for ceremonial user approval unless the user explicitly wants an approval checkpoint.

## Phase 5: Derive the implementation plan

Create the plan from the canonical `docs/spec/<feature>/spec.md`, not from generic best practices. In a writable repository, write or update the plan at `docs/spec/<feature>/plan.md`.

For each implementation step, state:

1. the requirement(s) it satisfies;
2. the likely component/file/module affected when project context is available;
3. the concrete change;
4. tests or verification that prove completion;
5. dependencies or migration/order constraints.

Order work to reduce risk:

1. contracts/schema/state model;
2. core domain behavior;
3. boundary integrations;
4. UI/client behavior;
5. observability and operational concerns;
6. migration/backfill/rollout where needed;
7. verification and cleanup.

Do not rewrite the spec as a plan. The plan explains **how** to satisfy it.

## Phase 6: Implement against the spec

When implementation is requested:

1. Keep requirement IDs visible in the working plan or notes.
2. Follow existing repository patterns unless they conflict with the spec.
3. Make the smallest coherent change that satisfies the spec.
4. Add or update tests for acceptance criteria and important failure modes.
5. If implementation reveals a contradiction or missing material behavior, update the spec/assumption explicitly before encoding a hidden decision in code.
6. Avoid unrelated refactors unless required for correctness or explicitly requested.

Do not claim a requirement is implemented merely because related code was changed.

## Phase 7: Verify with traceability

Create a compact verification matrix for non-trivial work. In a writable repository, write or update the verification report at `docs/spec/<feature>/verification.md`:


| Criterion | Requirement | Evidence | Status |
|---|---|---|---|
| AC-1 | FR-1 | test name / command / observed behavior | PASS / FAIL / UNKNOWN |

Verification evidence can include:

- automated tests;
- static/type checks;
- build results;
- targeted manual checks;
- API responses;
- migration validation;
- screenshots or UI inspection when relevant.

Never mark **PASS** without evidence. Use **UNKNOWN** when verification cannot be performed.

At the end, report:

- what was implemented;
- which acceptance criteria passed;
- failures or unknowns;
- deviations from the spec;
- remaining open decisions or follow-up work.

## Lightweight mode for small tasks

For a simple, local, low-risk change, use a micro-spec:

```markdown
### Micro-spec
- Desired behavior: ...
- Must preserve: ...
- Acceptance: ...
```

Persist this micro-spec as `docs/spec/<feature>/spec.md`, then plan/implement directly. Do not generate a long document for a one-line change unless requested.

## Review mode for an existing spec

When asked to review a spec, do not replace it immediately. First return:

1. **Critical gaps** — blockers and contradictions.
2. **Ambiguities** — decisions whose outcomes affect behavior.
3. **Missing edge cases** — likely failure scenarios.
4. **Unverifiable requirements** — statements that need measurable acceptance criteria.
5. **Over-specification** — implementation details that should move to the plan.
6. **Proposed revision** — only after explaining the material changes.

## Output discipline

- Prefer concise specs over exhaustive prose.
- Use tables only when they improve comparison or traceability.
- Keep IDs stable when revising a spec; do not renumber casually.
- Preserve user-stated constraints verbatim in meaning.
- Clearly distinguish **Known**, **Assumed**, and **Open** information.
- Provide concise rationale for material decisions; do not expose hidden chain-of-thought.
- Do not claim certainty when project context, tests, or runtime evidence is unavailable.
