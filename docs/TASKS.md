---
title: Current Tasks
description: Current tasks, blockers, verification state, and recommended next actions.
doc_type: task_state
status: active
created: 2026-09-15
updated: 2026-09-15
tags:
  - project-memory
  - tasks
  - current-state
audience:
  - agent
  - maintainer
related:
  - PROJECT_CONTEXT.md
  - DECISIONS.md
  - CHANGELOG_WORK.md
---

# Tasks

## Recommended Next Action

- Package and publish the `core` 0.1.3 bundle when release is requested, then
  update `catalog-v1.json` with the real artifact URL and checksum.

## Current

- [ ] Package and publish `core` 0.1.3 when requested.

## Verification

- `app-documentation` passes the skill creator's structural validation.
- The bundle manifest is valid JSON; all 12 declared resource paths and skill
  entrypoints exist.
- Project memory metadata validation and `git diff --check` pass.

## Blockers

- None recorded.

## Done

- [x] Added and registered the `app-documentation` skill for creating,
  restructuring, and reviewing application documentation.
