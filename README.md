# Beginner Agent Development Rules

A reusable Hermes Agent skill for cautious software development and delivery.

It covers:

- confirming requirements before coding;
- maintaining one authoritative source location;
- using temporary copies and Git worktrees safely;
- verifying the authoritative copy before cleanup;
- scanning for secrets, personal information, local paths, and real data before publication;
- distinguishing repository pushes, releases, packages, and platform acceptance tests.

## Installation

Copy `SKILL.md` into your Hermes skills directory, for example:

```text
~/.hermes/skills/software-development/beginner-agent-development-rules/SKILL.md
```

The skill is intentionally generic and contains no project-specific credentials, personal data, or machine-specific paths.

## License

MIT
