# Spec-Driven Quality Checklist

Use this before declaring a non-trivial spec implementation-ready and again before declaring implementation complete.

## Artifact convention

- Spec artifacts are stored under `docs/spec/<feature>/`.
- `spec.md` exists and is treated as the canonical behavioral source of truth.
- `plan.md` and `verification.md` are created when those phases occur.
- Persisted artifact content is written in English.
- The feature directory uses a short lowercase kebab-case slug.

## Spec readiness

- Goal is concrete and consistent with scope.
- Non-goals prevent likely scope confusion.
- Important terms, actors, states, and ownership boundaries are defined.
- Each MUST requirement is testable or has a stated verification method.
- Happy path is complete.
- Validation and meaningful error paths are specified.
- Authentication and authorization are distinguished where relevant.
- Side effects define retry and idempotency behavior where relevant.
- Concurrency/race behavior is defined where shared mutable state is involved.
- State transitions and invariants are explicit where state machines exist.
- Data retention/deletion/privacy behavior is covered when personal or sensitive data is involved.
- Compatibility and migration expectations are covered for existing systems.
- Observability requirements exist for operationally important behavior.
- Performance targets are measurable only when justified; arbitrary numbers are not invented.
- Accessibility/localization concerns are included when relevant to the interface.
- Open decisions are visible and categorized by severity.
- Acceptance criteria cover the critical behavior, not just the happy path.
- Implementation details are kept out of requirements unless they are actual constraints.

## Plan readiness

- Every major MUST requirement maps to at least one implementation step.
- Risky migrations or irreversible operations have sequencing/rollback considerations.
- Tests are planned alongside behavior, not deferred generically to the end.
- Dependencies and integration boundaries are explicit.
- Plan follows existing repository patterns where known.
- Unrelated refactors are excluded unless necessary.

## Implementation verification

- Each acceptance criterion has PASS, FAIL, or UNKNOWN status.
- PASS has concrete evidence.
- Automated tests cover critical behavior and meaningful failure cases.
- Build/type/lint/static checks are run when relevant and available.
- Migration/data changes are validated where applicable.
- Security/authorization boundaries are explicitly checked where applicable.
- No material behavior was invented during implementation without updating assumptions/spec.
- Deviations from the spec are listed.
- Unknowns are not disguised as passes.
