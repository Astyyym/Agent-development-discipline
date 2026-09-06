# Public repository sanitization

Use before open-sourcing or publishing a repository, package, or documentation set.

## Scan

Inspect tracked files, planned changes, relevant history, release assets, examples, screenshots, prompts, and configuration for secrets, credentials, personal/customer data, local paths, usernames, logs, databases, backups, caches, virtual environments, and generated artifacts.

Interpret test fixtures and public attribution in context; do not rely on keyword matching alone.

## Safe publication

Use fictional data, portable paths, and generic placeholders. Keep real configuration local and ignored; provide an example configuration when useful. If a secret entered history, removing the current file is insufficient: rotate/revoke it and address affected history and published artifacts.

## Scope and verification

The product's supported platform determines public documentation. The agent's execution environment and a maintainer's private paths do not automatically belong in public files.

Before reporting success, verify the published repository or artifact, visibility, expected files, and final remote state. Report repository push, package build, release publication, and platform acceptance separately.
