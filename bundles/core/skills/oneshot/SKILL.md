---
name: oneshot
description: Implement one narrow, clearly defined change end to end with minimal scope and proportionate validation. Use for localized fixes, small features, or configuration changes whose success criteria can be established before editing.
---

# OneShot

Complete one focused task through scope, implementation, and validation. Use the repository, filesystem, documentation, editing, and verification tools available in the current environment.

## Establish Preconditions

- Read the applicable repository instructions before making changes.
- Inspect the worktree and identify staged, unstaged, and untracked changes before editing.
- Treat pre-existing changes as user-owned unless there is clear evidence that they belong to this task. Understand overlapping edits and work around them without discarding, overwriting, staging, or absorbing unrelated work.
- Restate the requested outcome as a narrow scope with observable success criteria.
- Stop and request a decision when the task combines independent outcomes, conflicts with repository constraints, or depends on a material choice that cannot be verified locally.

## Scope

- Locate the components that own the relevant behavior and inspect their immediate context, dependencies, tests, and established conventions.
- Read only the context needed to make the change safely. Expand the investigation when the affected boundary is shared, indirect, or high risk; do not target an arbitrary number of files.
- Verify uncertain APIs, behavior, and conventions from available source code or authoritative project documentation instead of relying on assumptions.
- Decide the smallest complete change that satisfies every success criterion, and choose validation appropriate to the affected components and risk.

## Implement

- Make the smallest coherent diff that fully delivers the requested outcome.
- Reuse existing abstractions and conventions when they are observable and suitable.
- Preserve behavior outside the defined scope. Do not add adjacent cleanup, broad refactoring, opportunistic renaming, or unrelated documentation.
- Reinspect the resulting diff to catch accidental edits, incomplete paths, and unintended interactions with pre-existing changes.

## Validate

- Run the closest relevant checks first, then widen validation only when dependencies or risk justify it.
- Check the implemented behavior against the success criteria, not only whether a command exits successfully.
- When a check fails, determine whether the change caused the failure before modifying more code. Address only failures within scope and report unrelated or pre-existing failures separately.
- Do not repeat the same approach after multiple failed attempts without new evidence. Stop and report the observations, attempted checks, and decision or information required to proceed.

## Report

- Summarize the delivered outcome and the files changed.
- List each validation performed and its result.
- Identify checks that were unavailable, intentionally omitted, or inconclusive, with the reason.
- State any remaining risk, blocker, or user decision without claiming unverified success.

## Boundaries

- Do not commit, push, alter remote state, or rewrite Git history unless the user explicitly requests that separate action.
- Do not discard, overwrite, or incorporate unrelated worktree changes.
- Do not invent repository conventions, interfaces, or requirements that cannot be verified.
- Do not expand the task into cleanup, redesign, or refactoring outside the agreed success criteria.
