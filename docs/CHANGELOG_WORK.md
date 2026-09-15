---
title: Work Changelog
description: Dated notes on changed files, deliverables, tooling, checks, and verification.
doc_type: work_log
status: active
created: 2026-09-15
updated: 2026-09-15
tags:
  - project-memory
  - changelog
  - work-log
  - verification
audience:
  - agent
  - maintainer
related:
  - PROJECT_CONTEXT.md
  - DECISIONS.md
  - TASKS.md
---

# Work Changelog

## 2026-09-15

- Initialized project memory files.
- Added `bundles/core/skills/app-documentation/` with evidence-based workflow,
  Diataxis routing, type-specific page patterns, review criteria, and UI metadata.
- Registered the skill and advanced the `core` manifest from `0.1.2` to `0.1.3`.
- Left `catalog-v1.json` unchanged because no `core` 0.1.3 release artifact or
  checksum has been created.
- Verified the skill with `quick_validate.py`, checked JSON parsing and all
  declared resource paths, validated project-memory metadata, and ran
  `git diff --check`.
