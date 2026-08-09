# Beginner Agent Development Rules

A reusable, framework-agnostic Hermes Agent skill for cautious software development and delivery.

It helps an AI agent:

- confirm material requirements before coding;
- keep one authoritative source location;
- work in small, independently verifiable stages;
- use real feedback loops and vertical slices;
- review requirements fit separately from engineering quality;
- avoid speculative abstractions and unnecessary process overhead;
- verify the authoritative copy before cleaning temporary worktrees;
- scan for secrets, personal information, local paths, and real data before publication;
- distinguish repository pushes, releases, packages, and platform acceptance tests.

## Installation

Copy `SKILL.md` into your Hermes skills directory, for example:

```text
~/.hermes/skills/software-development/beginner-agent-development-rules/SKILL.md
```

The skill is intentionally generic. It contains no project-specific credentials, personal data, or machine-specific paths.

## Design principles

This skill is a compact workflow, not a mandatory issue tracker, interview ritual, commit policy, or framework. Adapt the planning files, testing seams, and delivery gates to the project while preserving the evidence and safety rules.

## License

MIT
