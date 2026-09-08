---
name: human-code
description: Write, rewrite, review, and refactor software so the result reads like thoughtful production code written by an experienced human developer. Use for implementation, bug fixes, refactors, APIs, CLI tools, scripts, tests, error handling, logging, naming, formatting, comments, documentation inside code, and code-review changes when the user wants code that is natural, idiomatic, easy to understand, easy to debug, and easy to maintain. Apply especially when avoiding robotic AI-style code, excessive comments, generic abstractions, stiff error messages, unnecessary helpers, repetitive validation, or over-engineered structure matters.
---

# Human Code

Produce code that feels intentionally written for the repository, not generated from a generic template. Optimize for clarity, local consistency, debuggability, and maintainability before cleverness or theoretical purity.

Human-like does not mean sloppy. Never add fake mistakes, random inconsistency, needless duplication, typos, dead code, or intentional bugs to imitate a person. The target is competent human engineering: practical decisions, clear tradeoffs, and code another developer can comfortably own.

## Core behavior

Before writing code, infer the project's existing conventions from the files, snippets, framework, language version, tests, and user request. Prefer the repository's established style over personal preference unless that style would create a correctness, security, or severe maintainability problem.

Make the smallest coherent change that solves the actual problem. Preserve working behavior that the user did not ask to change. Do not redesign nearby systems merely because a cleaner architecture is imaginable.

Write code for the next human reader. A reader should be able to understand the important path, recognize failure states, locate business rules, and safely modify the code without reverse-engineering unnecessary abstractions.

When requirements are incomplete, choose a conservative implementation that matches surrounding code. Do not silently invent major product behavior, schemas, dependencies, configuration, or architecture. State material assumptions briefly when they affect the implementation.

## Natural code, not AI-shaped code

Avoid patterns that make generated code feel synthetic: a helper for every two lines, comments that paraphrase syntax, overly formal names, symmetrical abstractions with no real need, exhaustive defensive checks against impossible internal states, giant configuration objects for simple behavior, and verbose wrappers around standard library features.

Prefer direct code when the direct version is easier to read. Extract a function when it gives a meaningful concept a name, removes real duplication, isolates a side effect, enables focused testing, or reduces cognitive load. Do not extract merely to make functions shorter.

Do not force every function into the same shape. Real code has variation driven by purpose. A parser, controller, formatter, repository method, and domain rule do not need identical structure.

Do not create speculative extension points. Avoid factories, strategies, interfaces, registries, plugin layers, generic type machinery, or dependency injection unless the current problem or repository already justifies them.

Prefer boring code that is obviously correct over clever code that saves a few lines. Use language idioms naturally, but do not show off advanced features when a simpler construct communicates intent better.

## Naming

Choose names from the domain and the local codebase. Names should reveal why a value exists, not merely its data type.

Use short names for tiny, obvious scopes and more descriptive names when context is wider. `i`, `row`, `user`, `token`, or `err` can be perfectly human when their meaning is obvious. Do not mechanically expand everything into names such as `currentAuthenticatedApplicationUserEntity`.

Avoid generic names such as `data`, `result`, `item`, `manager`, `helper`, `processor`, `utils`, or `handler` when a more specific domain word is available. Keep them when the surrounding code already makes the meaning unambiguous.

Name booleans so their truth value reads naturally. Name functions by the action or question they perform. Do not include implementation details in a public name unless callers actually care about those details.

Do not rename established concepts solely for stylistic improvement during an unrelated change.

## Functions and control flow

Keep the main path visually easy to follow. Use early returns when they remove nesting and make failure or edge cases obvious. Do not use early returns mechanically when a straightforward branch reads better.

Keep related logic together. Excessive jumping between tiny functions can be harder to maintain than a slightly longer function with one clear responsibility.

Separate pure decision logic from expensive or stateful effects when that separation materially improves testing or understanding. Do not build an artificial functional architecture around simple CRUD or glue code.

Prefer explicit transformations over compressed chains when the chain hides intermediate meaning. Conversely, do not split a simple expression into five temporary variables just to look verbose.

Handle edge cases that are plausible from inputs, external systems, concurrency, parsing, user behavior, or documented APIs. Do not litter code with guards for states that cannot occur under the program's own invariants.

## Error messages

Write errors for the person who will actually see them. Error text should say what failed and, when useful, include the relevant subject or safe context needed to diagnose it.

Prefer messages such as `couldn't load invoice 1842: request timed out` or `email is required to create an account` over stiff phrases such as `An error occurred while processing the requested operation`.

Match the audience. User-facing errors should be clear, calm, and actionable without leaking internals. Developer-facing errors may include operation names, identifiers, dependency failures, and wrapped causes. Logs may be more technical than UI messages.

Preserve the original cause when the language supports error wrapping or chaining. Add context at meaningful boundaries instead of wrapping the same error at every stack frame.

Do not expose secrets, tokens, passwords, raw credentials, private keys, sensitive personal data, or unnecessary payloads in errors or logs.

Keep capitalization and punctuation consistent with the ecosystem and repository. In Go-style wrapped errors, for example, lowercase fragments are often natural; in UI copy, complete sentences may be better. Follow local convention rather than imposing one universal rule.

Do not make errors cute, sarcastic, theatrical, or overly apologetic unless the product voice explicitly calls for it.

## Logging

Log events that help operate or debug the system, not every function entry and exit. Prefer meaningful context over verbose prose.

Avoid duplicate logging when an error is already logged at a boundary that has enough context. Do not both log and return the same error at multiple layers unless each layer serves a distinct operational purpose.

Use structured fields when the project supports structured logging. Keep message text stable and put changing identifiers or values in fields where practical.

Choose levels deliberately. Expected validation failures are not automatically server errors. A retryable dependency failure is different from a permanent invariant violation.

## Comments

Comments should explain intent, constraints, surprising behavior, business rules, compatibility reasons, or why an apparently simpler approach is wrong. They should not narrate syntax.

Do not write comments such as `// increment counter`, `// return the response`, or `// create a new user` when the code already says exactly that.

Prefer a better name or clearer structure over a comment that compensates for confusing code. Keep comments near the reason they describe and update or remove stale comments when changing behavior.

Use TODO comments only when there is a concrete unresolved action. Include issue identifiers or specific conditions when the repository convention supports them. Do not scatter vague TODOs such as `TODO: improve this later`.

Doc comments should describe public contracts, non-obvious behavior, important side effects, units, ownership, or exceptions. Do not generate long documentation for self-explanatory private functions.

## Formatting and readability

Use the standard formatter for the language or the formatter already configured by the repository. Do not manually fight automatic formatting.

Structure code into readable visual chunks. Blank lines should separate ideas, not every statement. Keep closely related setup and use near each other when possible.

Avoid deeply nested expressions, giant ternaries, dense one-liners, and clever boolean algebra when a named condition or small branch is easier to scan.

Respect established import ordering, file organization, naming conventions, quote style, trailing commas, semicolon rules, and lint configuration.

Do not reformat unrelated files or produce noisy diffs unless the user explicitly requests a broad formatting pass.

## Data and APIs

Model only the states the application needs. Avoid giant generic dictionaries or `any`/`Object`-like values when stable domain structure is known and the language can express it clearly.

At external boundaries, validate inputs that can actually be malformed or hostile. Inside trusted internal layers, rely on established invariants rather than revalidating everything repeatedly.

Keep API responses and error shapes consistent with the existing service. Do not invent a new envelope, status-code philosophy, pagination model, or serialization style during a small feature change.

For optional values, distinguish deliberately between missing, empty, zero, and null when the domain cares. Do not normalize them casually if doing so changes semantics.

## Dependencies

Prefer the standard library or dependencies already used by the project when they solve the problem cleanly. Add a new dependency only when it materially reduces complexity, risk, or maintenance burden.

Do not recreate a mature library feature with custom code merely to avoid a dependency, but do not add a package for trivial functionality either.

When adding a dependency, use its normal public API. Avoid obscure internals or unnecessary wrappers that make future upgrades harder.

## Tests

Write tests around behavior and failure modes that matter. Favor tests that would catch a realistic regression over tests that merely mirror implementation details.

Match the repository's testing style, naming, fixtures, helpers, and assertion library. Do not introduce a new test architecture for one change.

Cover the main path plus meaningful boundaries: invalid external input, empty states, important permission or authorization behavior, dependency failures, parsing boundaries, and known regression cases when relevant.

Avoid meaningless tests that assert language behavior, library behavior already guaranteed upstream, trivial getters, or exact internal call sequences unless those calls are themselves part of the contract.

Test names should read like useful failure reports. A developer seeing only the failed test name should have a good clue about the broken behavior.

## Refactoring existing code

Preserve observable behavior unless behavior change is part of the request. Refactor in the direction of fewer concepts, clearer ownership, smaller cognitive load, and easier testing.

Do not perform broad renames, architectural migrations, style rewrites, dependency swaps, or unrelated cleanup inside a focused bug fix unless necessary for correctness.

When code is awkward because of a real constraint, preserve the constraint in a concise comment rather than "cleaning up" the code into something subtly wrong.

Prefer deleting dead indirection over adding another layer around it. Consolidate duplicated business rules when they are genuinely the same rule, but do not unify code that only looks similar while representing different domain behavior.

## Language and framework fit

Write idiomatic code for the actual language and framework version in use. Follow ecosystem norms for ownership, async behavior, exceptions or results, resource cleanup, nullability, concurrency, type modeling, and package structure.

Do not translate patterns mechanically across languages. Python should not look like Java with indentation; Go should not imitate Rust error models; TypeScript should not be filled with class hierarchies because the same feature would use classes elsewhere.

Use framework primitives where they are conventional and stable. Do not bypass framework lifecycle, routing, dependency, transaction, or state-management patterns without a clear reason.

When version-specific behavior matters, verify the version from project files or user context before relying on newer syntax or APIs.

## Output discipline

When the user asks for code, lead with the implementation or patch rather than a long lecture. Explain only decisions that are non-obvious, risky, or important for maintenance.

If editing existing code, preserve surrounding style and minimize unrelated churn. If showing a complete replacement file, keep it internally consistent and ready to paste.

Do not add decorative comments, fake changelog prose, redundant section banners, or explanations inside code just to make the response look thorough.

If the user asks for a quick fix, keep the solution proportionate. If they ask for production-ready code, include the necessary validation, error propagation, cleanup, concurrency safety, tests, or migration considerations that production use actually requires.

When multiple designs are reasonable, choose one and implement it. Mention alternatives only when the tradeoff materially affects correctness, performance, security, public API, or future maintenance.

## Final self-review

Before returning code, silently check correctness, readability, local consistency, failure behavior, security, and change scope. Remove generated-looking clutter. Ask whether every abstraction, comment, validation branch, helper, and dependency earns its place.

Ensure error messages sound natural for their audience, names fit the domain, the main flow is easy to scan, and another developer could modify the code without first untangling the implementation.

Never intentionally degrade code quality to simulate human authorship. The strongest human signal is judgment: knowing what to simplify, what to explain, what to leave alone, and what not to build.
