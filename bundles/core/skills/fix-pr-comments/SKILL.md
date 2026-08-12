---
name: fix-pr-comments
description: Review and address actionable pull request feedback with explicit classification, scoped changes, and traceable validation. Use only when the user explicitly asks to process comments, reviews, or requested changes on a pull request.
---

# Fix PR Comments

Evaluate pull request feedback against the current code, apply only justified changes, and preserve a traceable link from each comment to its outcome. Do not publish the result automatically.

## Preconditions

- Confirm that the user explicitly requested processing of pull request feedback and identify any requested subset.
- Verify that the current location belongs to a Git repository and identify its root.
- Resolve the GitHub repository and pull request from an explicit reference or a verified association with the current branch. Ask for the missing identity when multiple pull requests remain plausible.
- Verify the pull request head, base, current branch, and local HEAD. Do not switch branches or modify history implicitly when the worktree does not match the pull request state to be edited.
- Inspect staged, unstaged, and untracked changes before editing. Record and preserve all pre-existing work, especially overlapping files or hunks.
- Detect unresolved conflicts and in-progress merge, cherry-pick, revert, or rebase operations. Stop without altering them.
- Do not commit, push, stage changes, submit reviews, or resolve threads as part of this workflow.

## Collect Feedback

- Inspect the documented capabilities of the available GitHub CLI or integration before choosing how to retrieve feedback. Do not assume a subcommand or field exists.
- Retrieve pull request metadata and the current head commit so every feedback item can be interpreted against the correct revision.
- Collect submitted reviews, general pull request comments, inline review comments, and relevant review threads when the available API exposes them.
- Follow pagination and retain stable identifiers, URLs, authors, timestamps, review states, file paths, line or position data, commit references, reply relationships, and resolved or outdated state when available.
- Use documented GitHub REST or GraphQL endpoints when higher-level commands do not expose a required feedback type.
- Deduplicate representations of the same feedback without collapsing distinct replies or review events.
- Report any category that could not be retrieved because of permissions, authentication, or tool limitations. Stop if the missing data prevents a reliable treatment of the requested scope.

## Classify Feedback

Assign one primary classification to every collected item and record the supporting evidence:

- `actionable`: a clear request still applies to the current code and belongs to the pull request scope;
- `already-resolved`: the current code already satisfies the request, whether through an earlier change or another comment;
- `obsolete`: the referenced code or premise has been removed, replaced, or superseded;
- `ambiguous`: the intended outcome cannot be determined reliably from the comment and available context;
- `conflicting`: the request contradicts another review item, an explicit requirement, or a verified repository constraint;
- `informational / no-change-needed`: the item communicates context, approval, or a non-actionable observation.

Do not equate unresolved thread state, reviewer authority, or imperative wording with an automatic requirement to edit code.

## Build Checklist

- Create one traceable checklist entry per feedback item, including its identifier or URL, origin, current file or area, classification, decision, and justification.
- For actionable items, record the smallest intended change and the validation needed to demonstrate that it addresses the feedback.
- For items that require no change, record the current-code evidence supporting that conclusion.
- Link duplicate, dependent, or conflicting items while preserving an outcome for each original comment.
- Order work by dependency and risk, grouping compatible corrections only when doing so does not lose comment-level traceability.

## Apply Changes

- Before each correction, read the current target context, the relevant pull request diff, and any overlapping local changes.
- Reconfirm that the feedback still applies to the current head and that the proposed correction respects repository conventions and pull request scope.
- Apply the smallest complete change justified by the evidence. Do not treat a suggested patch as authoritative without checking its context.
- Preserve pre-existing user work and avoid adjacent cleanup, opportunistic refactoring, or unrelated fixes.
- Pause ambiguous or conflicting items and request a decision when repository evidence cannot resolve them. Continue only with independent items that remain safe to address.
- Update the checklist after each decision or edit without marking an item addressed prematurely.

## Validate

- Run focused validations for each compatible group of corrections, followed by broader checks only where affected dependencies or risk justify them.
- Verify the requested behavior or concern directly; a passing general test alone does not prove that a specific comment was addressed.
- Check plausible regressions and inspect the final diff for unintended changes or interference with pre-existing work.
- Distinguish failures caused by the corrections from pre-existing, environmental, or out-of-scope failures.
- Mark an actionable item addressed only when its correction and relevant validation are complete. Record any validation limitation instead of claiming success.

## Report

For every feedback item, report:

- its origin and stable identifier or URL;
- its classification;
- the decision and justification;
- the change made, or the reason no modification was appropriate;
- the validation performed and its result.

Then summarize the files modified, global validations, remaining open items, and feedback requiring a human decision. State explicitly that no commit, push, review mutation, or thread resolution was performed.

## Boundaries

- Do not commit or push automatically.
- Do not resolve or close GitHub threads, submit or edit reviews, or post replies unless the user requests that separate action explicitly.
- Do not apply feedback literally without verifying its current context, correctness, and scope.
- Do not hide ambiguity, disagreement, missing feedback, failed validation, or incomplete treatment.
- Do not modify out-of-scope code, discard user work, or broaden corrections into cleanup or refactoring.
- Use documented capabilities of an available GitHub CLI or integration without depending on platform-specific or proprietary agent tools.
