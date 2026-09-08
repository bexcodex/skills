# Spec Templates

Use these templates as defaults. Omit irrelevant sections rather than filling them with boilerplate.

## Repository paths and language

When a repository is writable, persist artifacts automatically using:

```text
docs/spec/<feature>/spec.md
docs/spec/<feature>/plan.md
docs/spec/<feature>/verification.md
```

Use a short lowercase kebab-case feature slug. Write all persisted artifact content in English even when the conversation is in another language. `spec.md` is the canonical behavioral source of truth.

## Full feature spec

```markdown
# [Feature / Change Name]

## 1. Goal
[Outcome and problem being solved.]

## 2. Scope
- ...

## 3. Non-goals
- ...

## 4. Current behavior
[Only for an existing system.]

## 5. Actors / definitions
- **Actor/term**: definition

## 6. Functional requirements
- **FR-1 — [Short name]**: The system MUST ...
- **FR-2 — [Short name]**: When ..., the system MUST ...

## 7. User / system flows
### Happy path
1. ...
2. ...

### Alternative / failure flows
- If ..., then ...

## 8. Contracts
### API / command / event
- Input: ...
- Output: ...
- Errors: ...
- Idempotency: ...

### Data / state model
- Entities/fields: ...
- State transitions: ...
- Invariants: ...

## 9. Edge cases and failure behavior
- ...

## 10. Non-functional requirements
- **NFR-1 — Security**: ...
- **NFR-2 — Reliability**: ...

## 11. Assumptions / open decisions
### Assumptions
- **A-1**: ...

### Open decisions
- **O-1**: ...

## 12. Acceptance criteria
- **AC-1** (FR-1): Given ..., when ..., then ...
- **AC-2** (FR-2): ...
```

## Compact spec

Use this for bounded changes that are not trivial but do not justify a full document.

```markdown
# [Change]

## Goal
...

## Required behavior
- **FR-1**: ...
- **FR-2**: ...

## Must preserve
- ...

## Edge cases
- ...

## Assumptions
- ...

## Acceptance criteria
- **AC-1**: ...
- **AC-2**: ...
```

## Micro-spec

```markdown
### Micro-spec
- Desired behavior: ...
- Must preserve: ...
- Acceptance: ...
```

## Implementation plan format

```markdown
# Implementation Plan

1. **[Step]** — satisfies FR-1, FR-2
   - Change: ...
   - Location: ...
   - Verification: ...
   - Depends on: ...

2. **[Step]** — satisfies FR-3
   - Change: ...
   - Location: ...
   - Verification: ...
```

## Verification matrix

```markdown
| Criterion | Requirement | Evidence | Status |
|---|---|---|---|
| AC-1 | FR-1 | `test_login_success` | PASS |
| AC-2 | FR-2 | Not executable in current environment | UNKNOWN |
```

## Example: payment callback

Weak requirement:

> Handle duplicate payment callbacks correctly.

Spec-driven version:

```markdown
- **FR-4 — Callback idempotency**: Receiving the same provider callback more than once MUST produce at most one successful payment state transition and MUST NOT duplicate financial side effects.
- **FR-5 — Callback acknowledgement**: A callback already processed successfully MUST return the provider-compatible acknowledgement response without repeating business side effects.

Acceptance criteria:
- **AC-7** (FR-4): Given the same valid callback payload and provider event ID is delivered three times, exactly one payment transition and one financial side effect are recorded.
- **AC-8** (FR-5): Subsequent deliveries of an already processed event receive the expected acknowledgement response.
```

The choice of database constraint, distributed lock, deduplication table, or cache belongs in the implementation plan unless constrained by the system.
