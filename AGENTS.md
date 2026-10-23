# AGENTS.md

This file defines guidelines and guardrails for AI coding agents working in this repository.

## Security Guidelines

AI coding agents must follow these rules at all times when working in this repository.

### Protect Sensitive Data

- Do not read, log, print, or commit secrets, credentials, API keys, tokens, passwords, or TLS private key material — even partially or in truncated form.
- Do not hardcode credentials, certificate private keys, or connection strings into source files, configuration files, or tests. Reference environment variable names only (e.g., `$SECRET_NAME`), never their values.
- Do not expose or transmit personally identifiable information (PII) or customer data outside the application's defined data boundaries.
- Do not add logging statements that output sensitive fields such as private keys, passphrases, session tokens, or customer details.
- Treat any value sourced from environment variables or external secret stores as confidential.

### Prevent Unauthorized Deployments

- Do not push commits directly to `main`, `master`, or any production-targeting branch without explicit human approval.
- Do not trigger, modify, or bypass CI/CD pipelines or deploy jobs that target production or staging environments without explicit instruction from a human reviewer.
- Do not create or push git tags that follow release naming conventions (e.g., `v*`) unless explicitly instructed.
- Do not modify Kubernetes manifests or Heroku configuration (`app.json`, `Procfile`) in a way that would cause an immediate or automatic deployment to a live environment without explicit approval.
- Do not approve or merge pull requests autonomously.

### Avoid Destructive Operations

- Do not force-push (`git push --force`) to any branch under any circumstances.
- Do not delete remote branches, tags, or remote refs.
- Do not delete or overwrite TLS certificate data, infrastructure definitions, or any data stored outside version control.
- Do not run commands that are difficult or impossible to reverse (e.g., bulk data deletion, infrastructure teardown) without explicit human sign-off.
- Prefer additive, reversible changes over destructive ones wherever possible. When in doubt, stop and ask for human confirmation before proceeding.
