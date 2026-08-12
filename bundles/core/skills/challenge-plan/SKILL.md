---
name: challenge-plan
description: Challenge a plan or idea with targeted questions to resolve material decisions, assumptions, and trade-offs before execution. Use when an existing proposal has consequential ambiguity, conflicting constraints, fragile assumptions, or unresolved choices that could change the implementation approach.
---

# Challenge Plan

Test an existing idea, plan, or decision until it is sufficiently determined for planning or execution. Ask only questions whose answers can materially change the approach.

## Establish Context

- Identify the proposal being challenged, its intended outcome, scope, non-goals, and stated success criteria.
- Inspect applicable repository instructions, implementation context, configuration, tests, and available documentation before asking for information.
- Extract answers already present in the request or repository. Do not ask the user to repeat or discover facts that can be verified locally.
- Note gaps between the proposal and the observed repository context without treating either as correct by default.

## Map Decisions

- Maintain a working decision register with separate entries for verified facts, hard constraints, preferences, hypotheses, confirmed decisions, and open decisions.
- Attach evidence to facts and identify how each hypothesis could be verified.
- Trace dependencies between decisions so prerequisite choices are resolved before downstream details.
- Prioritize open decisions by their effect on scope, architecture, compatibility, risk, reversibility, cost, and validation.
- Flag contradictions, missing dependencies, and assumptions whose failure would invalidate the proposal.

## Challenge

- Select the smallest useful group of related, high-impact questions from the open decisions. Let the uncertainty determine the group size; do not follow a fixed questionnaire.
- Ask a question only when its answer can alter the approach and cannot be established from available evidence.
- Give enough context to make each choice meaningful. When presenting options, explain their material consequences and state a recommendation only when evidence supports one.
- Present only credible choices. Allow a direct answer when the real decision is not captured by known options.
- Keep the tone neutral and precise. Wait for the answers before pursuing dependent branches.

## Reconcile

- Update the decision register after each response, distinguishing a confirmed decision from a preference or an unverified assumption.
- Propagate each answer through dependent choices and identify any new contradiction or material uncertainty it creates.
- Do not reopen settled decisions without new evidence or a newly exposed conflict.
- Continue with another targeted group only while an unresolved answer could materially change the proposal.
- Stop questioning when the intended outcome, constraints, and major trade-offs determine a coherent direction, with no unresolved decision-critical contradiction or dependency.

## Decision Brief

Produce a concise brief containing:

- the clarified objective, scope, non-goals, and success criteria;
- confirmed decisions and the rationale or evidence supporting them;
- hard constraints and invariants that the eventual plan must preserve;
- remaining assumptions, their impact, and how they can be verified;
- genuinely open points, why they remain open, and what would resolve them;
- consequences for the next planning step, without constructing the implementation plan itself.

Hand the brief to `planner` when an ordered implementation plan is needed. Keep `challenge-plan` focused on resolving ambiguity rather than replacing planning.

## Boundaries

- Do not implement, rewrite, or silently expand the challenged proposal.
- Do not modify repository files by default. Record the brief in a file only when the user explicitly requests that separate action.
- Do not commit, push, stage files, alter branches, rewrite history, or otherwise mutate Git state.
- Do not invent repository facts, user preferences, constraints, dependencies, or artificial alternatives.
- Do not ask filler questions, pursue low-impact details, or continue after the stopping criteria are met.
- Use the inspection and communication capabilities available in the current environment without relying on platform-specific tools or invocation syntax.
