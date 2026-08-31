# 01 — Analyze the repository before coding

Use this workflow when you are about to give an agent a task in an existing repository and you want it to understand the codebase before touching files.

## Best for

- unfamiliar repositories;
- mature applications with established conventions;
- tasks that may cross backend/frontend boundaries;
- repositories where a large speculative diff would be risky.

## Workflow

```text
I need you to work on the following task:

[TASK]

Do not modify any file yet.

First, inspect the repository and build a task-specific understanding of the codebase.

Identify:
- the relevant solution/projects/packages;
- the architecture and boundaries involved in this task;
- the existing conventions that should be preserved;
- the current implementation related to the requested behavior;
- relevant tests and test conventions;
- configuration, CI/CD or deployment concerns if they are directly relevant;
- authentication/authorization implications if applicable.

Then provide:

1. Current behavior
   Explain how the relevant path works today, using concrete files/classes/components where possible.

2. Likely change surface
   List the files or areas you expect would need to change. Separate required changes from files that only might need changes.

3. Reuse opportunities
   Point out existing components, services, helpers, patterns or tests that should be reused instead of creating parallel implementations.

4. Risks
   Identify realistic regression, compatibility, security, data or UX risks introduced by this task.

5. Implementation plan
   Propose the smallest coherent implementation plan, ordered step by step.

6. Verification plan
   State which builds, tests or manual checks should be performed after implementation.

Constraints:
- do not edit files during this analysis phase;
- do not propose unrelated refactoring;
- do not assume a framework convention exists if you have not found evidence of it in the repository;
- distinguish facts found in the codebase from assumptions;
- if the task is ambiguous in a way that materially changes the implementation, call that out explicitly.
```

## Why it works

The common failure mode is letting the agent infer architecture from the task description alone. This workflow forces repository evidence to come before implementation.

It is particularly useful before a long autonomous run: you can review the plan, correct a mistaken assumption, and only then ask the agent to implement it.

## Useful follow-up

After you approve the plan, continue with:

```text
Proceed with the implementation using the plan above.

Keep the diff limited to the approved scope. If you discover evidence that materially invalidates the plan, stop and explain what changed before broadening the implementation.
```
