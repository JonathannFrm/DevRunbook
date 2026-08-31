# DevRunbook

**Practical workflows for safer AI-assisted software development.**

DevRunbook is a collection of production-minded playbooks for developers working with AI coding agents on real repositories.

This public repository is the **free sampler** for the first DevRunbook edition:

> **Coding Agents for .NET & Angular**  
> 35 practical workflows for repository analysis, implementation, debugging, testing, reviews, Angular, ASP.NET Core, Docker, CI/CD, PWA and production incidents.

The goal is not to provide "magic prompts". The goal is to give coding agents enough context, constraints and verification steps to produce smaller, safer and easier-to-review changes.

---

## What's included in this free sampler

| Workflow | Use it when... |
| --- | --- |
| [01 — Analyze before coding](workflows/01-repository-analysis.md) | You are giving an agent a task in an unfamiliar or existing repository. |
| [02 — Implement a feature safely](workflows/02-feature-implementation.md) | You want a scoped implementation without unrelated refactoring. |
| [03 — Fix the root cause of a bug](workflows/03-root-cause-bug-fix.md) | You want the agent to investigate before changing code and protect against regression. |
| [04 — Review a pull request](workflows/04-pull-request-review.md) | You want a risk-focused review rather than a style rewrite. |
| [05 — Diagnose a Docker / CI deployment](workflows/05-deployment-diagnosis.md) | A deployment fails and you want evidence-driven troubleshooting. |

Also included:

- [`AGENTS.example.md`](templates/AGENTS.example.md) — a repository-level instruction template you can adapt to your own project.
- [`LICENSE.md`](LICENSE.md) — terms for using the free sampler.

---

## Why use a workflow instead of a one-line prompt?

A vague instruction such as:

> Fix this bug and make sure everything works.

leaves too many decisions implicit. On a real codebase, that can lead to unnecessary refactoring, guessed architecture, weak validation or a large diff that is difficult to review.

A DevRunbook workflow explicitly asks the agent to:

1. inspect before editing;
2. identify the likely scope and risks;
3. preserve existing conventions;
4. make the smallest justified change;
5. add or update meaningful tests;
6. run relevant verification;
7. report what changed and what still needs manual checking.

The developer stays responsible for the engineering decision. The agent gets a much clearer operating envelope.

---

## How to use the workflows

1. Open the workflow matching your task.
2. Replace the placeholders such as `[TASK]`, `[BUG]` or `[TARGET]`.
3. Add any project-specific constraints that matter.
4. Give the complete workflow to your coding agent.
5. Review the proposed plan or diff before merging anything.

These workflows are intentionally tool-agnostic. They can be adapted to coding agents that can inspect and modify a repository, including Codex and similar tools.

---

## Example

Instead of:

```text
Add filtering to the users page.
```

use a scoped engineering brief:

```text
Implement the following feature:

Add filtering to the existing users page by surname and status.

Before editing:
- inspect the current component, service and API contract;
- identify existing filtering or query conventions in the repository;
- list the files you expect to change and the main regression risks.

Constraints:
- preserve the existing page layout and authorization behavior;
- do not refactor unrelated code;
- keep the API backward compatible unless the current design makes that impossible;
- reuse existing UI components and patterns where appropriate;
- add or adapt tests for the new behavior.

Before finishing:
- run the relevant backend tests;
- run the relevant frontend tests/build;
- review the final diff for unrelated changes;
- summarize what changed and anything that still needs manual validation.
```

The value is not the wording itself. It is the **engineering process encoded in the instruction**.

---

## Full edition

**DevRunbook — Coding Agents for .NET & Angular** expands this sampler to **35 workflows** and includes:

- repository analysis and implementation planning;
- feature development and refactoring;
- root-cause debugging and regression tests;
- PR review and merge preparation;
- MSTest and FluentAssertions;
- ASP.NET Core and Entity Framework Core;
- authentication and authorization;
- Angular, RxJS, forms and responsive UX;
- PWA, offline behavior and update flows;
- Docker and Docker Compose;
- GitHub Actions and TEST/PROD deployments;
- production incident investigation;
- security-oriented workflows;
- long-running autonomous agent tasks;
- reusable issue/task templates;
- an extended `AGENTS.md` starter;
- a prompt-design cheat sheet;
- bad-prompt → better-workflow examples;
- a 42-page reference guide plus individual Markdown files.

**The full edition is being prepared for release.** The purchase link will be added here when the store is live.

---

## Who this is for

DevRunbook is aimed at developers who already know how to build software and want to delegate useful work to coding agents **without giving up control of scope, architecture, testing and validation**.

The first edition is especially relevant to teams using:

- .NET / ASP.NET Core;
- Angular / TypeScript / RxJS;
- Git and GitHub;
- Docker;
- CI/CD;
- web applications and PWAs.

---

## Safety note

AI-generated code and recommendations can be wrong. Treat agent output like code from any other contributor: review it, test it and validate security-sensitive or production-critical changes before deployment.

---

## License

The free sampler may be used and adapted for your own development work, including commercial software projects. Republishing, reselling or redistributing the sampler itself (or a lightly modified version of it) is not permitted. See [`LICENSE.md`](LICENSE.md) for the full terms.

---

**DevRunbook** — practical playbooks for developers working with AI coding agents.
