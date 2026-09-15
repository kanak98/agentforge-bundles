---
name: app-documentation
description: Create, restructure, or review user-facing documentation for a software application using Diataxis. Use for tutorials, task guides, CLI/API/configuration reference, conceptual explanations, documentation architecture, and audits of existing app docs. Do not use for code comments or internal project memory.
---

# App Documentation

Produce application documentation that is accurate, easy to navigate, and shaped around what readers need to do or understand.

## Establish the documentation contract

Infer the product, audience, goal, output location, language, version, and existing documentation conventions from the request and repository. Ask a concise clarifying question only when a missing answer would materially change the deliverable; otherwise state a reasonable assumption and proceed.

Treat source code, schemas, command help, tests, configuration, and observed application behavior as evidence. Do not invent features, defaults, prerequisites, commands, responses, screenshots, or compatibility claims. Mark unverifiable details as assumptions or explicit placeholders.

Preserve the user's requested format and scope. When editing an existing documentation set, match its language, terminology, linking style, and file organization unless restructuring is part of the request.

## Choose the reader need

Classify each page by its primary purpose:

- **Tutorial:** a beginner learns by completing a guided, successful experience.
- **How-to guide:** a capable user completes a specific task.
- **Reference:** a user looks up precise facts about an interface.
- **Explanation:** a user builds conceptual understanding and learns why the system works as it does.

Keep each page centered on one type. Cross-link related pages instead of mixing long conceptual digressions, exhaustive reference tables, and task steps into one document.

For the detailed patterns and validation checks for each type, read [references/diataxis-patterns.md](references/diataxis-patterns.md).

## Build the documentation

1. Inspect the relevant product evidence and existing docs before drafting claims.
2. Identify the audience's starting state and the observable outcome the page must deliver.
3. Select the page type, or propose a small information architecture when the request covers several needs.
4. Write the shortest complete path for that reader need, using the application's real terminology.
5. Include prerequisites, commands, examples, expected results, warnings, and recovery guidance only where they help the reader complete or understand the goal.
6. Link to adjacent documentation types where the reader may need background, task guidance, or exact interface details.

When designing a documentation set, prefer a task-oriented landing page and group pages by reader need. Do not force four visible Diataxis sections when the product is too small or the existing navigation uses a clearer structure.

## Review existing documentation

Report concrete issues before suggested rewrites. Check for:

- claims that conflict with current product evidence;
- unclear audience, goal, prerequisites, or expected outcome;
- mixed documentation types that interrupt the reader's flow;
- missing steps, hidden state, ambiguous commands, or absent verification;
- inconsistent names, duplicated content, dead or circular navigation;
- reference entries that omit types, defaults, constraints, errors, or examples when those facts exist;
- inaccessible headings, links, tables, code samples, or image alternatives.

Prioritize findings by reader impact. Preserve accurate material and make the smallest structural change that solves the documented problem.

## Validate before delivery

Verify code samples and commands when the environment permits safe local checks. Confirm internal links and navigation when tooling exists. Re-read the result from the target reader's starting point and apply the type-specific success test in the reference.

Summarize the pages created or changed, the evidence verified, and any assumptions or unverified items that remain. Do not claim the documentation is complete when relevant product behavior could not be inspected.
