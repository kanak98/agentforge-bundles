---
name: deep-think
description: Analyze complex decisions using evidence, explicit constraints, alternatives, risks, and validation criteria. Use for consequential, cross-cutting, ambiguous, or difficult-to-reverse technical decisions that require more than a direct implementation plan.
---

# Deep Think

Reach a defensible decision through a bounded, evidence-driven analysis. Scale the depth of each section to the decision's consequences, uncertainty, and reversibility.

## Frame

- State the decision to be made, the desired outcome, the scope, and the explicit non-goals.
- Translate the request into concrete decision criteria. Separate required outcomes from preferences.
- Identify who or what is affected and how far the effects may propagate.
- Determine whether the decision is actually ambiguous. If one verified approach plainly satisfies the constraints, analyze it directly instead of manufacturing alternatives.

## Evidence

- Inspect applicable repository instructions, relevant implementation paths, configuration, tests, documentation, and observable conventions before drawing conclusions.
- Classify material statements as facts, inferences, or hypotheses. Tie facts to their source and explain the reasoning behind inferences.
- Verify claims that can be checked locally. Record unresolved hypotheses only when they matter to the decision.
- Highlight missing or conflicting evidence and state whether it blocks a sound decision.

## Constraints and Invariants

- List hard constraints, compatibility requirements, operational limits, and behaviors that must remain unchanged.
- Distinguish true invariants from current implementation details that may be changed.
- Resolve apparent conflicts between constraints or expose the trade-off when they cannot all be satisfied.
- Rank softer criteria so they do not outweigh mandatory requirements implicitly.

## Alternatives

- Start with the simplest approach that could fully satisfy the constraints.
- Develop additional approaches only when they represent credible, materially different choices. Do not add weak options to create an artificial comparison.
- For each viable option, describe its mechanism, affected boundaries, prerequisites, and consequences.
- Compare options consistently across implementation cost, ongoing complexity, risk, reversibility, compatibility, and ease of validation.
- Include retaining the current behavior only when it is a genuine option with understood consequences.

## Failure Analysis

- Examine how each leading option can fail during normal operation, error handling, boundary conditions, partial completion, and recovery.
- Trace effects across shared components, state transitions, external dependencies, and upgrade or rollback paths when relevant.
- Estimate impact and likelihood using available evidence; do not present speculative possibilities as established risks.
- Identify mitigations and determine whether they reduce risk or merely move complexity elsewhere.

## Decision

- Select the simplest option that satisfies all hard constraints and provides acceptable control of material risks.
- Explain why it is preferred and why the other credible options were rejected.
- State assumptions and unknowns that could change the choice. Request user input only when one of them is decision-critical and cannot be resolved from available evidence.
- Stop the analysis when the chosen option is supported by evidence, respects the invariants, has no unresolved unacceptable risk, and can be validated. Do not continue searching for marginal refinements without a new decision-relevant question.

## Validation

- Define observable signals that would confirm the chosen approach meets each required outcome.
- Specify focused checks for normal behavior, important edge cases, failure handling, and preserved invariants.
- Add broader checks only where affected dependencies or risk justify them.
- Identify what cannot be validated before implementation and how it should be verified afterward.

## Boundaries

- Produce analysis and a decision by default, not implementation. Modify files only when the user explicitly requests implementation as a separate part of the work.
- Do not commit, push, stage files, alter branches, rewrite history, or otherwise mutate Git state.
- Do not invent repository facts, APIs, constraints, or documentation.
- Do not replace missing evidence with confidence, prolong analysis after the stop criteria are met, or multiply alternatives without decision value.
- Use the inspection and reasoning capabilities available in the current environment without depending on platform-specific tools or invocation syntax.
