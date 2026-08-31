# AGENTS.md — starter template

Use this as a starting point for persistent repository-level instructions to an AI coding agent. Replace placeholders and delete sections that do not apply.

---

# Repository instructions

## Project overview

[Briefly describe the application, its users and its main architecture.]

Example:

- Backend: ASP.NET Core Web API
- Frontend: Angular
- Database: SQL Server / SQLite / PostgreSQL
- Deployment: Docker / Docker Compose
- CI/CD: GitHub Actions

## Primary rule

Understand the existing implementation before changing it.

Prefer the smallest coherent change that satisfies the task. Do not use a scoped task as an opportunity for unrelated cleanup or architectural redesign.

## Before editing

For non-trivial tasks:

1. inspect the files directly involved;
2. inspect nearby code for existing patterns and conventions;
3. identify relevant tests;
4. identify likely regression risks;
5. state assumptions when the repository does not provide enough evidence.

If the requested behavior is ambiguous in a way that materially changes implementation or user behavior, surface that ambiguity before making a broad assumption.

## Scope discipline

- Stay within the requested issue/task.
- Do not refactor unrelated code.
- Do not rename or reorganize unrelated files.
- Do not introduce a new abstraction when an established project pattern already solves the problem.
- Do not add dependencies without a concrete need.
- Keep diffs easy to review.

## Existing behavior

- Preserve existing public behavior unless the task explicitly changes it.
- Preserve API compatibility where practical.
- Preserve authorization boundaries.
- Do not silently relax validation or error handling.
- Do not remove tests or disable checks merely to make a build pass.

## Backend conventions

[Customize this section.]

Example rules:

- Follow nullable-reference-type conventions already used by the project.
- Use async APIs consistently; do not block on tasks with `.Result` / `.Wait()`.
- Validate data at the appropriate boundary.
- Keep controllers/endpoints thin when the existing architecture expects business logic elsewhere.
- Avoid returning internal exception details to clients.
- Consider authorization whenever an endpoint reads or mutates user/group-owned data.

## Entity Framework Core

[Remove if not applicable.]

- Match the repository's existing tracking/no-tracking conventions.
- Avoid accidental N+1 queries.
- Do not materialize large datasets unnecessarily.
- Make schema/data migrations explicit when a model change requires them.
- Do not delete or recreate production data as a shortcut.

## Frontend / Angular conventions

[Remove if not applicable.]

- Reuse existing components, services and design patterns.
- Keep observable/subscription lifecycles safe.
- Preserve loading, empty and error states.
- Consider desktop and mobile behavior for user-facing changes.
- Avoid broad visual redesign during a functional task.
- Keep accessibility behavior at least as good as before the change.

## PWA / offline behavior

[Remove if not applicable.]

When changing caching, authentication, service workers or offline features:

- reason explicitly about stale data and update behavior;
- verify whether the feature must work without a network connection;
- do not cache private data more broadly than intended;
- test update/reload behavior where practical.

## Tests

Use the existing test stack and conventions.

For changed behavior:

- add or adapt tests that protect meaningful behavior;
- prefer externally observable behavior over implementation-detail assertions;
- include important failure and boundary cases;
- for bug fixes, add a regression test when practical;
- do not weaken an existing assertion just to make the suite pass.

Project-specific commands:

```text
Backend build:   [COMMAND]
Backend tests:   [COMMAND]
Frontend build:  [COMMAND]
Frontend tests:  [COMMAND]
Lint/typecheck:  [COMMAND]
```

## Security

- Never commit secrets, credentials, tokens, private keys or production connection strings.
- Never print secret values in final output.
- Treat authentication, authorization, file access and user-controlled input as security-sensitive boundaries.
- Do not disable TLS/certificate verification or security checks as a troubleshooting shortcut.

## Git / pull requests

- Do not rewrite unrelated history.
- Do not force-push unless explicitly requested and appropriate.
- Keep commits/diffs scoped to the task.
- Before finishing, inspect the final diff for accidental files or unrelated edits.

## Definition of done

Before declaring a task complete:

1. requested behavior is implemented;
2. relevant tests are added or updated;
3. relevant build/tests/checks have been run where available;
4. the final diff has been reviewed for scope drift;
5. remaining manual checks are identified;
6. assumptions or unresolved risks are reported clearly.

## Final response format

Provide a concise summary containing:

- what changed;
- main files/areas changed;
- tests/builds/checks run and results;
- anything not verified;
- remaining manual checks or risks.
