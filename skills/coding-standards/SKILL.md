---
name: coding-standards
description: Coding standards for every code change. Use when writing or editing code, and before calling a change done.
---

# Coding standards

## Completion criterion

List every rule this diff touches and the evidence that it is satisfied. Only checked rules count.

## Rules

- **YAGNI.** Build only what the current requirement needs. Every abstraction must pay for itself now.
- **KISS.** Choose the simplest implementation that fully meets the requirement. Keep it readable and short.
- **No Backward Compatibility.** Delete an obsolete code path in the change that retires it. Keep one shape per behavior. Add compatibility layers, fallbacks, and migrations only when the requirement names them.
- **Dependency Management.** Use the libraries already in the tree. Read their types and docs before reaching past them. Add a package when its benefit outweighs the maintenance, security, and complexity it brings.
- **Incremental Development.** Land small, verified steps. Keep the system working at every one.
- **Separation of Concerns (SRP).** Give each module, function, and component one clear responsibility. Keep unrelated concerns in separate places.
- **Rationale Comments.** Comment the why the code cannot show: a non-obvious decision, a constraint, a trade-off, a workaround. The code carries the what.
- **Atomic Commits.** One logical change per commit. No unrelated refactoring or formatting.
- **Conventional Commits.** Follow the Conventional Commits specification.
- **Behavioral Testing.** Test what a caller can observe. Give each test a failure reason no sibling test shares.
- **No Change Detector Tests.** A test fails when behavior breaks, not when code moves. Assert what a caller sees, not the calls made inside, their order, or a snapshot of internals.
- **Acceptance Criteria.** Cover the cases the specification names. Keep existing tests green unless the change requires updating them.
- **Evidence-Based Verification.** Reproduce the bug before fixing it. Confirm the fix through a real workflow, screenshot, or measurement. Claim success with the evidence in hand.
- **DRY (Don't Repeat Yourself).** Keep each piece of business knowledge in one place. Extract shared logic where it improves clarity and maintainability.
- **Explicit over Implicit.** Make behavior, dependencies, and defaults visible at the call site.
- **Fail Fast.** Validate inputs at the boundary. Detect invalid states early and report the error where it originated.
- **Least Surprise.** Follow established conventions so behavior matches what the reader expects.
- **Minimal Surface Area.** Expose only the APIs, configuration, and interfaces callers need.
- **Stable Function Signatures.** Keep signatures stable so a change does not churn every caller. Prefer a named option over a boolean flag. Break a signature deliberately when the requirement demands it.
- **Command-Query Separation.** A function either changes state and returns nothing, or answers a question and changes nothing.
- **Type Safety.** Let the type system carry the contract. Keep casts, assertions, and untyped values out of the code.
- **Error Handling.** Handle an error at the boundary that can act on it. Report success only for an operation that succeeded and was verified.
- **Security by Default.** Validate untrusted input. Enforce access controls. Keep secrets and sensitive data out of logs and client code.
- **Observability.** Log, measure, or trace where it diagnoses a real operational problem. Keep the signal free of redundant noise.
- **Deterministic Testing.** Make tests repeatable. Do not depend on execution order, live external services, or arbitrary delays.
- **Regression Testing.** Fix a bug with a focused test that fails before the fix and guards the same failure afterward.
- **Documentation Accuracy.** Update documentation in the same change that makes it wrong.
- **Principle Precedence.** Correctness, security, and explicit requirements outrank simplicity. When principles conflict, choose the solution that meets the requirement with the least unnecessary complexity.
- **Evidence-Based Performance Optimization.** Measure real user journeys. Find the highest-impact bottleneck and form a hypothesis. Make the smallest safe change. Benchmark before and after. Keep only measurable improvements and add a guardrail for each. Repeat until the target is met.
- **Defer Concurrency Until Measured.** Parallelize independent I/O only when measurement shows it is the bottleneck. Preserve error and ordering semantics.
- **Make Illegal States Unrepresentable.** Model lifecycle and status as explicit states with no illegal combination. Give the model a clear transition table. Use it in place of scattered booleans, strings, or phase checks.
- **Design Out, Don't Patch.** Before adding a guard, retry, catch-and-ignore, flag, or fallback, find why the problem exists. Change the design so the line is not needed. Remove the error or illegal state rather than detecting it. When the cause lies outside the tree, mark the workaround with its cause and an expiry. Know why old compensating code exists before you delete it.
- **Stable Canonical Identity.** Give every object that outlives one call, or that another object refers to, one ID. Assign it once and never change it. Refer to the object by that ID only, never by name, position, or a copy of its attributes. Leave value objects without IDs.
- **Deep Modules.** Give each module a small interface that hides a lot of work. Keep what a caller must know to a minimum. Make the common call the simplest. Take complexity into the module, not onto its callers. A deep module has one purpose. Merge or remove a layer that adds no hidden work.
- **Evidence-Based Engineering.** Every decision, implementation, optimization, and technical conclusion must rest on verifiable data, reproducible tests, and measured results. Assumptions are not facts. Speculation is not validation. Unverified claims do not count.
- **Invariant Enforcement.** Find every implicit system constraint. Enforce it through boundary validation, type safety, and automated tests so invalid states and runtime failures cannot occur.
- **Dependency Isolation.** Wrap external dependencies behind well-defined interfaces and centralized control. Use them to keep communication, failure handling, and system resilience consistent.
- **Verifiable Delivery.** Define measurable acceptance criteria. Establish baseline behavior. Validate changes through reproducible tests. Keep objective evidence of correctness, performance, and regression safety before declaring completion.
- **Multi-Stakeholder Design.** Optimize each interface for user experience (UX), developer experience (DX), and agent experience (AX). Keep it usable, maintainable, and safe to change later. Do not trade one for another.

## Slop indicators

- implicit coupling
- layer-first folders
- duplication
- representable illegal states
- god files
- shotgun surgery
- layering violations
- pass-through wrappers
- errors / validation not at the boundary
- change detector tests
- compensating code over a known cause
- workarounds without a cause and an expiry
