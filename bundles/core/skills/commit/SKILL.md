---
name: commit
description: Create a focused local Git commit containing only the intended changes after inspecting, validating, and staging them safely. Use only when the user explicitly asks to create a commit.
---

# Commit

Create one local commit for the requested task while preserving every unrelated worktree and index change.

## Preconditions

- Confirm that the user explicitly requested a commit. Otherwise, do not invoke this workflow implicitly.
- Verify that the current location belongs to a Git repository and identify its root.
- Inspect the current branch and HEAD. Stop and report a detached HEAD unless the user explicitly authorizes committing in that state.
- Detect unresolved conflicts and in-progress merge, cherry-pick, revert, or rebase operations. Stop on conflicts; do not continue or alter the operation on the user's behalf.
- Inspect staged, unstaged, and untracked changes before making any index change. If there is nothing to commit, report that and stop.

## Determine Scope

- Derive the intended commit scope from the explicit task, the work completed for it, and repository evidence.
- Classify each changed path and, when necessary, each hunk as task-related, pre-existing, or unrelated.
- Treat any change whose ownership is uncertain as out of scope until clarified.
- Stop and ask for direction when the intended set cannot be determined reliably.
- If unrelated changes are already staged, do not commit, unstage, or rearrange them without explicit permission. Report the conflict between the existing index and the requested scope.

## Review Changes

- Inspect the complete unstaged and staged diffs for every candidate path before staging.
- Inspect the contents and purpose of candidate untracked files; do not include them based on their names alone.
- Exclude unrelated edits even when they share a file with intended work. Stage only the intended hunks when this can be done and verified safely; otherwise stop for clarification.
- Look for accidental outputs such as logs, caches, build products, dependency directories, editor files, large binaries, or temporary artifacts.
- Look for credentials, private keys, tokens, local environment files, personal data, or other sensitive material. Stop before staging anything suspicious.
- Confirm that the selected diff is complete for the task and contains no opportunistic cleanup.

## Validate

- Read the repository's applicable validation instructions and select checks proportionate to the changed components and risk.
- Run relevant focused checks before committing when the environment permits, then broaden them only when dependencies or risk justify it.
- Reinspect the worktree after checks that may generate or modify files. Do not include their outputs unless they are an intentional part of the task.
- Stop when a critical validation fails because of the intended changes, unless the user separately and explicitly authorizes committing despite that failure.
- Report pre-existing, environment-related, or out-of-scope failures separately and state any resulting limit on confidence.

## Stage

- Stage only explicitly selected paths or hunks. For whole paths, use path-specific Git operations with an explicit path separator.
- Never use `git add .` or `git add -A` as a default staging strategy.
- Inspect the final staged status, path list, statistics, and full diff before committing.
- Verify that the staged diff contains exactly the intended change, is internally complete, and excludes unrelated or sensitive content.
- If the staged result is empty, ambiguous, or differs from the approved scope, do not commit.

## Commit

- Inspect recent commit messages and applicable repository guidance to identify an observable message convention. Do not impose a convention the repository does not use.
- Write a short, descriptive message that states the completed change. Add a scope or body only when it improves clarity or matches repository practice.
- Create one local commit from the verified staged diff. Do not bypass hooks merely to make the commit succeed.
- If the commit fails, preserve the index, report the failure, and do not retry with weaker safeguards without explicit authorization.
- Verify the resulting commit hash, message, parent, and included paths immediately after creation.

## Report

- Report the commit hash and exact message.
- List the files included in the commit.
- List validations performed and their results, including any skipped or inconclusive checks.
- Summarize remaining staged, unstaged, and untracked changes without modifying them.
- State clearly that the commit remains local and was not pushed.

## Boundaries

- Never push or force-push.
- Never amend an existing commit unless the user makes a separate explicit request.
- Never rebase, reset, discard changes with checkout, clean untracked files, or rewrite history.
- Never absorb unrelated or uncertain changes into the commit.
- Never proceed through unresolved conflicts, ambiguous scope, suspicious content, or task-caused critical validation failures without the required user decision.
- Use Git and the inspection capabilities available in the current environment without depending on platform-specific tools or a particular shell.
