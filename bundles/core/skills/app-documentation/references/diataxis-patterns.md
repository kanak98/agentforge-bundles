# Diataxis Page Patterns

Use the pattern matching the page's primary reader need. These are decision aids, not mandatory templates; adapt headings to the product and existing documentation conventions.

## Tutorial: learning through a successful experience

Use when the reader is new and needs to learn by doing.

- Title: an inviting outcome such as `Build your first workflow`.
- Opening: say what the reader will build, what they will learn, and the visible final result.
- Shape: goal, minimal prerequisites, ordered steps, observable result after meaningful steps, recap, next step.
- Writing: give exact actions, keep choices limited, and introduce only the concepts needed to maintain momentum.
- Avoid: unexplained branches, exhaustive options, production hardening, and long conceptual detours.
- Success test: a beginner can complete it end to end without outside help and can tell when each major step worked.

## How-to guide: completing a task

Use when the reader understands the application and has a concrete outcome to achieve.

- Title: a task such as `Configure single sign-on`.
- Opening: state the outcome and relevant assumptions.
- Shape: prerequisites and starting state, concise ordered procedure, verification, relevant failure recovery, related links.
- Writing: optimize for task completion; include alternatives only when they affect a common path.
- Avoid: teaching the whole system, restating reference material, and presenting one example as the only valid approach.
- Success test: the target user can complete and verify the task without backtracking or resolving hidden assumptions.

## Reference: looking up facts

Use for APIs, CLI commands, configuration keys, schemas, permissions, events, error codes, or other interfaces.

Use a consistent entry shape appropriate to the interface. Include facts that exist in product evidence, such as:

- name and purpose;
- syntax, path, method, or signature;
- type, required status, default, allowed values, and constraints;
- inputs, outputs, side effects, permissions, errors, and compatibility;
- a minimal valid example and its result.

Keep instructions minimal and link to how-to guides for full procedures. Add version or availability information only when it is known and relevant.

Success test: a user can find a specific fact quickly and distinguish required behavior from examples or assumptions.

## Explanation: understanding concepts and design

Use when the reader wants to understand how or why something works.

- Title: a concept such as `How synchronization works` or `Why projects are isolated`.
- Shape: context and motivating question, mental model, important mechanisms, alternatives or trade-offs, consequences, related pages.
- Writing: connect details into a coherent model and explain rationale supported by evidence.
- Avoid: turning the page into a setup procedure or exhaustive interface catalog.
- Success test: the reader can explain the concept, its consequences, and the relevant design trade-offs in their own words.

## Documentation-set integration

Use explicit links to bridge reader needs:

- tutorials link to reference for optional parameters and to how-to guides for next tasks;
- how-to guides link to reference for exact interface details and to explanations for background;
- reference links to task examples without embedding long procedures;
- explanations link to tutorials or how-to guides for practical application.

Use one canonical page for each fact that is likely to change. Other pages should link to it instead of duplicating it.
