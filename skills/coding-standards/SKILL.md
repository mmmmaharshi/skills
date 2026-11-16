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
- **No Backward Compatibility.** Delete the retired code path in the same change. Keep one shape per behavior. Add shims, fallbacks, and migrations only when the requirement names them.
- **Dependency Management.** Prefer libraries already in the tree. Read their types and docs before reaching past them. Add a package when its benefit outweighs its maintenance, security, and complexity cost.
- **Reference Implementation Review.** When a feature has a known shape and you do not know it, review two reference implementations first. Identify the contract and the edge cases, not code to paste. Stop once you can name both. Then write the smallest change that fits this codebase.
- **Incremental Development.** Land small, verified steps. Keep the system working at every one.
- **Separation of Concerns (SRP).** Give each module, function, and component one clear responsibility. Keep unrelated concerns in separate places.
- **Rationale Comments.** Comment the constraint, trade-off, or non-obvious decision the code cannot show. The code carries the what.
- **Atomic Commits.** One logical change per commit. No unrelated refactoring or formatting.
- **Conventional Commits.** Follow the Conventional Commits specification.
- **Behavioral Testing.** Test observable behavior. Give each test a failure reason no sibling test shares.
- **No Change Detector Tests.** A test fails when behavior breaks, not when code moves. Assert outputs, not internal calls, their order, or snapshots of internals.
- **Acceptance Criteria.** Cover the cases the specification names. Keep existing tests green unless the change requires updating them.
- **Evidence-Based Verification.** Reproduce the bug before fixing it. Verify the fix through a real workflow, screenshot, or measurement. Claim success with evidence in hand.
- **DRY (Don't Repeat Yourself).** Keep each piece of business knowledge in one place. Extract shared logic where it improves clarity and maintainability.
- **Single Source of Truth (SSOT).** When a value or decision is defined in two places, name one authoritative owner before changing either. Check config, types, constants, docs, and validation for the same fact. Point consumers at the owner instead of copying the value. Leave generated code, test fixtures, and boundary DTOs alone.
- **Design System Extraction.** When the same UI pattern appears in three or more places, list every occurrence and the props that vary. Prefer patterns that changed together in past commits. For each, decide: extract, keep, or wait. Extract one component with explicit variants, and keep existing callers working.
- **Explicit over Implicit.** Make behavior, dependencies, and defaults visible at the call site.
- **Fail Fast.** Validate inputs at the boundary. Reject invalid states early and report the error where it originated.
- **Least Surprise.** Follow established conventions so behavior matches what the reader expects.
- **Minimal API Surface.** Expose only the APIs, configuration, and interfaces callers need.
- **Stable Function Signatures.** Keep signatures stable so a change does not churn every caller. Prefer a named option over a boolean flag. Break a signature deliberately when the requirement demands it.
- **Command-Query Separation (CQS).** A function either changes state and returns nothing, or answers a question and changes nothing.
- **Type Safety.** Let the type system carry the contract. Keep casts, assertions, and untyped values out of the code.
- **Error Handling.** Handle each error at the boundary that can act on it. Report success only for a verified operation.
- **Security by Default.** Validate untrusted input. Enforce access controls. Keep secrets and sensitive data out of logs and client code.
- **Observability.** Log, measure, or trace where it diagnoses a real operational problem. Keep the signal free of redundant noise.
- **Deterministic Testing.** Make tests repeatable. Do not depend on execution order, live services, or arbitrary delays.
- **Regression Testing.** Fix a bug with a focused test that fails before the fix and guards the same failure afterward.
- **Documentation Accuracy.** Update documentation in the same change that makes it wrong.
- **Principle Precedence.** Correctness, security, and explicit requirements outrank simplicity. When principles conflict, choose the solution that meets the requirement with the least unnecessary complexity.
- **Evidence-Based Performance Optimization.** Profile real user journeys. Find the bottleneck and form a hypothesis. Make the smallest safe change. Benchmark before and after. Keep only measurable improvements and add a guardrail for each. Repeat until the target is met.
- **Defer Concurrency Until Measured.** Parallelize independent I/O only when profiling shows it is the bottleneck. Preserve error and ordering semantics.
- **Make Illegal States Unrepresentable.** Model lifecycle and status as explicit states with no illegal combination. Give the model a clear transition table. Use it in place of scattered booleans, strings, or phase checks.
- **Design Out, Don't Patch.** Find the root cause before adding a guard, retry, catch-and-ignore, flag, or fallback. Change the design so the line is not needed. Remove the error or illegal state rather than detecting it. When you touch existing compensating code, name the cause it covers. If the cause is in this codebase, remove the cause and delete the compensation in the same change. If the cause is external and the failure is transient, keep the compensation and record its cause and expiry. Know why old compensating code exists before you delete it.
- **Entity Identity.** Give every entity one ID and assign it once. Refer to the entity by that ID, never by name, position, or a copy of its attributes. Leave value objects without IDs.
- **Deep Modules.** Give each module a small interface that hides a lot of work. Keep what a caller must know to a minimum. Make the common call the simplest. Take complexity into the module, not onto its callers. A deep module has one purpose. Merge or remove a layer that adds no hidden work.
- **Evidence-Based Engineering.** For facts about this codebase or its runtime, read the file, run the probe, or call the tool before you conclude. Every conclusion must name the data behind it. Assumptions are not facts. Speculation is not validation. Unverified claims do not count.
- **Invariant Enforcement.** Find every implicit system constraint. Enforce it through boundary validation, type safety, and automated tests so invalid states and runtime failures cannot occur.
- **Dependency Isolation.** Wrap external dependencies behind interfaces and adapters. Keep communication, failure handling, and resilience under central control.
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
