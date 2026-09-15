---
title: Project Context
description: Stable project facts, structure, workflows, resources, and constraints.
doc_type: context
status: stable
created: 2026-09-15
updated: 2026-09-15
tags:
  - project-memory
  - context
  - durable-knowledge
audience:
  - agent
  - maintainer
related:
  - DECISIONS.md
  - TASKS.md
  - CHANGELOG_WORK.md
---

# Project Context

## Overview

- Project purpose: Publish official public resource bundles for `agentforge`.
- Primary users: AgentForge users installing the published bundles.
- Current status: The repository contains the `core` bundle; its manifest is at
  `bundles/core/agentforge.json`.

## Project Structure

- `bundles/core/agentforge.json` is the source manifest for the `core` bundle.
- `bundles/core/agents/` contains bundled agent definitions.
- `bundles/core/skills/` contains self-contained bundled skill directories.
- `catalog-v1.json` records published bundle artifacts, versions, and checksums.

## Key Workflows

- New skills are declared in `bundles/core/agentforge.json` and stored at the
  matching `directoryPath`.
- Skill structure can be checked with the Codex skill creator's
  `scripts/quick_validate.py`.
- The catalog is updated by release commits after a bundle artifact exists; do
  not invent catalog hashes for an unpublished manifest version.

## Constraints

- Do not assume framework, deployment, package manager, infrastructure, or domain
  details until verified from project evidence.
- Preserve unrelated working-tree changes when adding or updating bundle resources.
