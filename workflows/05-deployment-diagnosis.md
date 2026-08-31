# 05 — Diagnose a Docker / CI deployment failure

Use this workflow when a deployment is failing and you want evidence-driven troubleshooting instead of changing several things at once.

## Best for

- Docker / Docker Compose failures;
- GitHub Actions failures;
- TEST vs PROD configuration differences;
- container startup or health-check issues;
- “works locally, fails on server” incidents.

## Workflow

```text
Diagnose the following deployment problem:

[SYMPTOM_OR_ERROR]

Environment:
[LOCAL / TEST / PROD / OTHER]

Do not start by changing configuration blindly.

Use an evidence-first troubleshooting process.

1. Establish the failing layer
Determine whether the failure is most likely in:
- application build;
- frontend build;
- image build;
- registry/push/pull;
- CI runner;
- secrets or environment variables;
- Docker Compose configuration;
- networking / DNS / reverse proxy;
- volume or filesystem permissions;
- database/storage initialization;
- application startup;
- health checks;
- runtime communication between services.

2. Inspect the relevant configuration
Review only the files connected to the suspected path, such as:
- Dockerfile(s);
- compose files;
- environment templates;
- workflow YAML;
- reverse-proxy configuration;
- application startup/configuration;
- deployment scripts.

Never reveal secret values. You may identify missing/misnamed secret keys, but redact credentials, tokens and passwords from all output.

3. Build a short hypothesis list
For each plausible cause provide:
- evidence supporting it;
- evidence against it;
- the smallest command/check/log that can confirm or reject it.

Prioritize hypotheses rather than changing several variables at once.

4. Confirm the root cause
When tool access allows it, inspect the relevant build output or logs.
If you cannot confirm the cause, say what evidence is missing instead of presenting a guess as fact.

5. Implement the correction
Once the cause is sufficiently supported:
- make the smallest configuration/code change that fixes it;
- preserve environment separation;
- do not hard-code secrets;
- do not disable security checks, TLS verification, tests or health checks just to make deployment pass;
- do not delete persistent data/volumes unless explicitly requested and the impact is understood;
- avoid unrelated upgrades or refactoring during incident repair.

6. Verify end to end
Check the relevant sequence, for example:
- build succeeds;
- image is produced;
- container starts;
- health check becomes healthy;
- application can reach required dependencies;
- reverse proxy serves the expected endpoint;
- a minimal functional smoke test succeeds.

Final response:
- observed symptom;
- confirmed root cause, or strongest remaining hypothesis if not confirmed;
- evidence used;
- correction applied;
- verification performed and results;
- any remaining production/manual check.
```

## Why it works

Deployment debugging becomes expensive when several configuration values are changed at once. This workflow makes the agent narrow the failing layer, propose a confirmatory check, then modify only what the evidence supports.
