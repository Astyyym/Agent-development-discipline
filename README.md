# Agent Development Discipline

A reusable, tool-agnostic development and delivery workflow for AI agents that build, modify, review, package, or publish software.

This repository is intended for general-purpose coding agents, regardless of the model, platform, orchestration layer, IDE, CLI, or agent framework they use.

## What It Provides

The workflow helps an AI agent to:

- confirm material requirements before coding;
- identify scope, non-goals, risks, and acceptance criteria;
- keep one authoritative source location;
- make small changes in independently verifiable stages;
- use real feedback loops and vertical slices;
- review requirements fit separately from engineering quality;
- avoid speculative abstractions and unnecessary process overhead;
- verify the authoritative copy before cleaning temporary worktrees;
- scan for secrets, personal information, local paths, and real data before publication;
- distinguish repository pushes, releases, packages, and platform acceptance tests;
- report completed, failed, deferred, and blocked work honestly.

## How to Use It

Read [`SKILL.md`](SKILL.md) as the primary workflow definition. Use the supporting procedures in [`references/`](references/) when their topics apply.

The workflow can be adopted in several ways:

- **Agent skill:** place or link `SKILL.md` in the agent's instruction or skills directory;
- **Repository guidance:** copy the relevant rules into `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, or the equivalent project instruction file;
- **Prompt or system policy:** include the applicable sections in the agent's persistent instructions;
- **Human review checklist:** use the completion checklist and verification gates during development and delivery.

The exact integration mechanism is platform-specific. The rules themselves do not depend on a particular vendor or tool.

## Scope

Use this workflow when an AI agent starts, changes, migrates, packages, open-sources, reviews, or delivers a software project.

It is a compact workflow, not a mandatory issue tracker, interview ritual, commit policy, branching model, or framework. Adapt the planning files, testing seams, and delivery gates to the project while preserving the evidence and safety rules.

## Core Principle

> Understand first → make a small change → verify the real behavior → record the result → deliver honestly.

Generated code, a passing syntax check, a successful process start, or a completed push is not by itself proof that the software is complete. Verification must match the real user behavior and delivery requirements.

## Repository Contents

- [`SKILL.md`](SKILL.md): the primary development and delivery workflow;
- [`references/`](references/): supporting procedures for project review, planning, staged execution, runtime validation, platform delivery, and public release hygiene.

## License

MIT
