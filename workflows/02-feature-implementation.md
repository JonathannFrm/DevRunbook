# 02 — Implement a feature without scope drift

Use this workflow when the task is already clear enough to implement and you want a focused change that respects the existing application.

## Best for

- adding a feature to an established codebase;
- issue-driven development;
- keeping an agent from “cleaning up” unrelated code;
- backend + frontend changes that still need a controlled diff.

## Workflow

```text
Implement the following feature:

[FEATURE]

Before editing:
- inspect the current implementation and the files directly involved;
- identify existing components, services, helpers and conventions that should be reused;
- identify relevant tests;
- confirm the smallest reasonable change surface.

Implementation constraints:
- respect the existing architecture and coding conventions;
- keep the diff focused on this feature;
- do not refactor unrelated code;
- do not rename or reorganize unrelated files;
- preserve existing public behavior unless the feature explicitly requires a change;
- preserve backward compatibility where practical;
- reuse existing abstractions before introducing new ones;
- do not add a dependency unless there is a clear need and no suitable existing solution;
- preserve existing authorization and security rules unless the task explicitly changes them;
- add or update meaningful tests for the new behavior.

For UI work:
- preserve the visual language of the application;
- consider desktop, mobile and touch interactions where relevant;
- handle loading, empty, error and disabled states if the feature introduces them;
- avoid redesigning unrelated parts of the screen.

For API/data work:
- validate inputs at the appropriate boundary;
- avoid silent breaking changes to contracts;
- consider concurrency, nullability and failure paths where relevant;
- do not expose data beyond the permissions already expected by the application.

Before finishing:
1. run the relevant backend build/tests;
2. run the relevant frontend build/tests if applicable;
3. inspect the final diff for accidental or unrelated changes;
4. verify the acceptance criteria one by one;
5. report any check you could not perform.

Final response:
- summarize the implementation;
- list the main files changed;
- list tests/builds executed and their result;
- list any manual checks still recommended;
- mention any assumption that could affect behavior.

Acceptance criteria:
[ACCEPTANCE_CRITERIA]
```

## Why it works

Coding agents often interpret “improve this while you're there” too broadly. Explicitly defining scope, preservation rules and finish criteria makes the result much easier to review.

## Tip

If the task is large, run the repository-analysis workflow first and paste the approved plan into `[FEATURE]` or reference it directly.
