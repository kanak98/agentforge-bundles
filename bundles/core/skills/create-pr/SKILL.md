---
name: create-pr
description: Create or reuse a GitHub pull request from a verified branch after reviewing its commits, diff, and validation status. Use only when the user explicitly asks to create or publish a pull request.
---

# Create PR

Create or reuse one GitHub pull request from the verified current branch. Treat the explicit request as permission to push that branch only, not to create commits or perform any other history-changing action.

## Preconditions

- Confirm that the user explicitly requested creation or publication of a pull request.
- Verify that the current location belongs to a Git repository and identify its root.
- Confirm that HEAD points to a named branch. Stop on a detached HEAD rather than inventing or switching branches.
- Detect unresolved conflicts and in-progress merge, cherry-pick, revert, or rebase operations. Stop without altering those operations.
- Inspect staged, unstaged, and untracked changes. Do not commit, stage, discard, or clean them.
- If task-related changes remain uncommitted, stop because they cannot be part of the pull request. Leave clearly unrelated changes untouched and report them; stop whenever local state makes the pull request scope or validation ambiguous.

## Resolve Repository Context

- Enumerate configured remotes and their URLs, then identify the remote and GitHub repository associated with the current branch. Do not assume the remote is named `origin`.
- Resolve ambiguous remotes, forks, or repository identities before any push or pull request creation.
- Determine the current head branch and its upstream relationship without changing either.
- Query GitHub for an open pull request whose head matches the current branch, including the head repository or owner when needed to distinguish forks.
- Determine the actual base branch from that pull request when it exists, otherwise from GitHub repository metadata. Use remote HEAD information only when it reliably identifies the same repository; never assume `main` or `master`.
- Confirm that the head and base branches are different and that both belong to the intended repository relationship.

## Review Changes

- Identify the commits reachable from the head branch but not from the resolved base branch, using current remote information.
- Compare head against the merge base with the verified base branch and inspect the complete pull request diff, not only its summary.
- Stop if there are no commits or no effective changes to propose.
- Verify that the commit set and diff form one coherent scope and contain no accidental, generated, unrelated, unexpectedly large, or unexplained files.
- Inspect for credentials, private keys, tokens, local environment data, personal information, or other sensitive material. Stop before publishing anything suspicious.
- Derive the title and description from the actual commits and diff rather than from the branch name alone.

## Validate

- Read applicable repository instructions and identify the checks required for the changed components.
- Review validations already performed and determine whether they cover the current head commit. Do not treat stale or unrelated results as sufficient.
- Run relevant missing checks when the environment supports them, expanding beyond focused checks only when dependencies or risk justify it.
- Make failures and unavailable checks explicit. Separate failures caused by the pull request from pre-existing, environmental, or out-of-scope failures.
- Stop when a critical validation fails because of the proposed changes unless the user separately and explicitly authorizes publication with that known failure.
- Account for local uncommitted changes that could affect validation; do not claim a clean result when the tested state differs materially from the branch being published.

## Publish Branch

- Verify read and write access to the selected GitHub repository and confirm authentication through an available GitHub CLI or integration before pushing.
- Determine whether the remote head is absent, behind, or already equal to local HEAD.
- Push only the current head branch to the explicitly resolved remote. Set its upstream only when appropriate and do not include other branches or tags.
- Never force-push. If the remote branch has diverged or rejects a normal push, stop and report the state without rebasing, resetting, or rewriting history.
- After a successful push, verify that the remote head resolves to the intended local commit.

## Create Pull Request

- Recheck for an existing open pull request after publication. If one exists for the same head, do not create a duplicate; return its verified details.
- Write a concise title that describes the actual change and follows observable repository conventions when available.
- Write a description containing a summary, the principal changes, validations and their results, and material risks, limitations, or unverified items.
- Create the pull request in the resolved GitHub repository from the verified head branch to the verified base branch.
- Verify the returned URL, number, state, base, and head after creation.
- Do not enable merge, auto-merge, squash, or any automatic integration behavior.

## Report

- Return the pull request URL and identify whether it was created or already existed.
- Report the base and head repositories and branches.
- List the commits included in the pull request.
- Summarize validations performed, failed, skipped, or unavailable.
- State remaining risks, limitations, local changes, or follow-up decisions explicitly.

## Boundaries

- Do not create an implicit commit, amend, rebase, reset, clean the worktree, discard changes, or rewrite history.
- Do not force-push, publish other branches or tags, modify unrelated branches, or guess a remote or base branch.
- Do not publish sensitive or unexplained content.
- Do not create a pull request from an ambiguous branch or duplicate an existing open pull request.
- Do not merge the pull request or enable automatic merge behavior.
- Use GitHub CLI or another available GitHub integration without depending on platform-specific tools or unnecessary shell syntax.
