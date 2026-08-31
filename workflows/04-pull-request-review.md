# 04 — Review a pull request for engineering risk

Use this workflow when you want an AI coding agent to review a PR like an engineer, not like a formatter.

## Best for

- checking a PR before merge;
- reviewing agent-generated changes;
- finding regressions, missing tests and security issues;
- separating blockers from optional improvements.

## Workflow

```text
Review the changes in this pull request against its target branch.

Context / intended change:
[PR_CONTEXT]

Review the actual diff and the surrounding code needed to understand it.

Focus on defects and engineering risk, especially:
- incorrect behavior or missed acceptance criteria;
- regressions in existing behavior;
- nullability and boundary cases;
- authentication/authorization mistakes;
- security or privacy problems;
- async/await, race-condition or concurrency issues;
- resource lifetime and error-handling problems;
- API or data-contract compatibility;
- Entity Framework query/tracking problems where relevant;
- Angular change-detection, state or lifecycle issues;
- RxJS subscription, cancellation or error-handling issues;
- PWA/cache/offline regressions where relevant;
- CI/CD or deployment risks;
- tests that are missing, weak or no longer meaningful;
- unrelated changes that increase the review surface.

Do NOT:
- suggest broad stylistic rewrites unless they hide a concrete defect;
- complain about formatting already handled by project tooling;
- recommend replacing established project conventions simply because another style exists;
- invent issues without evidence from the diff or surrounding code.

Classify findings as:

BLOCKING
A likely bug, regression, security problem, data-loss risk or requirement failure that should be fixed before merge.

IMPORTANT
A meaningful engineering concern that is not necessarily merge-blocking but should be addressed or consciously accepted.

OPTIONAL
A small maintainability or clarity improvement with low risk.

For every finding provide:
- severity;
- file and relevant location;
- concise description of the problem;
- why it matters / realistic failure scenario;
- recommended correction.

Also report:

1. Test coverage assessment
   Which changed behaviors are protected, which are not, and what specific tests would add value.

2. Scope assessment
   Whether the PR contains unrelated changes or suspiciously broad refactoring.

3. Final verdict
   One of:
   - ready to merge;
   - ready after minor fixes;
   - changes required.

If you find no meaningful issues, say so clearly instead of manufacturing findings.
```

## Why it works

A useful PR review is about likely failure modes, not the number of comments. This workflow explicitly gives the agent permission to return “no meaningful issues,” while forcing each reported issue to include a realistic impact.
