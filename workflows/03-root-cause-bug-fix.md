# 03 — Fix a bug by finding the root cause

Use this workflow when you want the agent to investigate first, avoid symptom-only workarounds, and leave a regression test behind when possible.

## Best for

- intermittent or confusing bugs;
- regressions after a recent change;
- bugs with several plausible causes;
- issues where a “quick fix” could hide a deeper problem.

## Workflow

```text
Investigate and fix the following bug:

[BUG_DESCRIPTION]

Do not start by editing code.

First, establish the failing path.

1. Reconstruct the scenario
- identify the entry point and the expected behavior;
- trace the relevant code path through the repository;
- identify state, data, configuration and environment assumptions;
- look for recent or nearby code that could plausibly explain the symptom.

2. Gather evidence
- inspect relevant tests, logs, guards, error handling and data transformations;
- if the repository provides a reproducible test or local command, use it;
- distinguish observed evidence from hypotheses.

3. State the root cause
Before implementing the fix, explain:
- what is actually failing;
- why it fails;
- why the proposed change addresses the cause rather than only the visible symptom.

4. Protect against regression
When practical, add or update a test that fails for the bug before the fix and passes after it.

The regression test should exercise externally meaningful behavior rather than implementation details.

5. Implement the smallest correct fix
Constraints:
- do not introduce a workaround when the root cause can be corrected cleanly;
- do not weaken validation, authorization, error handling or tests merely to make the scenario pass;
- do not catch and ignore exceptions without a justified recovery behavior;
- do not add arbitrary delays/retries unless the root cause is genuinely timing or transient-failure related;
- avoid unrelated refactoring;
- preserve existing behavior outside the bug scenario.

6. Check neighboring cases
Inspect the closest related scenarios that could be affected by the same code path, especially:
- null/empty values;
- unauthorized/forbidden cases;
- duplicate or repeated operations;
- async/concurrency behavior;
- boundary values;
- mobile/offline behavior if relevant.

Before finishing:
- run the most relevant tests and builds;
- review the final diff for scope drift;
- state whether the original scenario is now covered automatically or still needs manual verification.

Final response:
- root cause;
- fix applied;
- regression coverage added or reason it was not practical;
- tests/builds run and results;
- remaining manual checks or risks.
```

## Why it works

A coding agent can often make a symptom disappear quickly. That is not the same as fixing the defect. Requiring a causal explanation and regression protection before closing the task raises the bar from “the example works” to “the defect is understood and contained.”
