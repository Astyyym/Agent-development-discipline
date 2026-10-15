# Public repository sanitization

Use before open-sourcing or publishing a repository, package, or documentation set.

## Scan

Inspect tracked files, planned changes, relevant history, release assets, examples, screenshots, prompts, and configuration for secrets, credentials, personal/customer data, local paths, usernames, logs, databases, backups, caches, virtual environments, and generated artifacts.

Interpret test fixtures and public attribution in context; do not rely on keyword matching alone.

## Safe publication

Use fictional data, portable paths, and generic placeholders. Keep real configuration local and ignored; provide an example configuration when useful. If a secret entered history, removing the current file is insufficient: rotate/revoke it and address affected history and published artifacts.

## What belongs in a public repository

A public repository carries the product and what collaborators need — not the private working record.

- Publish: product code, tests, build and packaging scripts, usage and development docs, requirements and design documents, prototypes, changelog, readme, project instructions.
- Exclude: per-task execution plans, stage and status notes, findings and progress logs, internal retrospectives and backlog lists, temporary and intermediate artifacts.
- Judge by category, not total size. Mature projects publish `docs/` and even dedicated `rfc/` design-proposal directories, but not per-task execution records.
- Stopping future commits does not retract what is already public: history remains reachable by clone. To truly remove it, rewrite history and force-push, which breaks existing clones and release download links. That is an independent decision to confirm with the user first, never done silently.
- To stop publishing an already-tracked path, use `git rm -r --cached <path>` (which keeps local files) and add it to `.gitignore`; `.gitignore` alone does not untrack files.

## Scope and verification

The product's supported platform determines public documentation. The agent's execution environment and a maintainer's private paths do not automatically belong in public files.

Before reporting success, verify the published repository or artifact, visibility, expected files, and final remote state. Report repository push, package build, release publication, and platform acceptance separately.
