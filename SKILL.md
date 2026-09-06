---
name: agent-development-discipline
description: Use when an AI agent starts, changes, migrates, packages, open-sources, or delivers a software project. Guides scoped planning, staged verification, safe delivery, and honest reporting without embedding user or project context.
version: 1.5.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [requirements, planning, development, testing, architecture, delivery, security]
    related_skills: [product-discovery, repository-engineering, product-acceptance]
---

# Agent Development Discipline

## Overview

A reusable, tool-agnostic workflow for AI coding agents. It contains portable methods only. Personal identity, persona, business context, machine paths, and project-specific platform rules belong in user memory, persona configuration, or the target project's instruction files—not in this skill.

Read supporting procedures from `references/` only when their trigger applies.

## When to Use

Use when an agent starts, changes, migrates, packages, open-sources, reviews, or delivers software. For a trivial read-only question or harmless one-line change, use the smallest sufficient profile rather than the full workflow.

## Task profiles

| Profile | Minimum process |
|---|---|
| **Micro fix** | Confirm scope/non-goals; make the smallest change; run a targeted check; inspect the diff and report evidence. |
| **Feature / normal change** | Record requirements and acceptance; write a short plan with exact files; implement in verifiable stages; run behavior checks and final review. |
| **Migration / release / high-risk** | Add recovery/rollback planning; verify source and target; scan secrets and sensitive data; validate the real platform and artifact; report final remote state. |

Escalate for irreversible actions, production data, permissions, public publication, compatibility migrations, or platform-specific artifacts.

## Core workflow

1. Understand the outcome, unclear points, risks, scope, non-goals, platform, and delivery boundary.
2. Ask only materially important questions.
3. Identify the authoritative source and project instructions.
4. Record confirmed requirements. For normal/high-risk work, write a short plan naming exact files, steps, acceptance, stop condition, and risks.
5. Implement the smallest verifiable slice without silently expanding scope.
6. Verify immediately using evidence matched to the real outcome.
7. Review requirements fit and engineering quality as separate axes.
8. Report `passed`, `failed`, `blocked`, `deferred`, and unverified work separately.

Requirement changes follow: **understand → confirm → update requirements → update plan → implement → verify**.

## Context authority

Use the project's existing context convention. A common division is: requirements/PRD for product decisions; `AGENTS.md` for long-term rules; a short plan for implementation; task state for current stage; findings for environment conclusions; progress for session history. These names are examples, not mandatory files.

Do not duplicate the same decision across files. If sources conflict, stop, report the files and claims, apply the project's declared authority order, and synchronize derived records after resolution. See `references/project-documents.md`.

## Project-specific skills and AGENTS.md routing

During project initialization or first formal development, determine whether the project has a stable, repeatable workflow that belongs only to that project.

- Use a Hermes global skill for methods reusable across projects.
- Put a stable project-only workflow under the project root at `skills/<skill-name>/`.
- Do not copy project-specific skills into Hermes's global skill directory.
- When creating a project-specific skill, add its route to the project's `AGENTS.md`.
- Keep project facts, boundaries, and skill entry points in `AGENTS.md`; do not copy the skill body into it.
- At the start of project work, read `AGENTS.md`, then read the matching project `SKILL.md` and references.
- Do not create a skill for a one-off task, temporary state, personal configuration, or ordinary project facts.

### Skill creation boundary

- Do not create, install, or modify a Hermes global skill unless the user explicitly requests it.
- A project skill may be created when the project has a stable, repeatable, clearly triggered workflow that is not reusable across projects.
- Do not keep the same project skill in both the project directory and Hermes's global skill directory.

## Stages and evidence

Normal and high-risk work is split into stages with entry conditions, goals, scope, verification, pass criteria, artifacts, and failure handling. Do not advance through a failed or blocked gate.

Record at least the action/command, inputs, expected result, actual result, evidence type, and one status: `passed`, `failed`, `blocked`, or `deferred`. Static-only, not-run, theoretical, and manual-pending states must remain explicit. See `references/phase-evidence-and-cleanup.md`.

## Parallel work and integration

Parallelize only independent work with non-overlapping files and stable interfaces. Give each worker the same baseline, allow-list, forbidden paths, acceptance checks, and report schema. A coordinator owns integration and conflict decisions.

After completion: verify claims from live files/tests; synchronize accepted changes to the authoritative source; inspect conflicts and scope; run integration checks; rerun affected real behavior; update one authoritative evidence record; classify the overall stage. An unverified worker claim leaves that workstream unverified and cannot make the overall stage passed. See `references/implementation-and-parallel-execution.md`.

## Verification and delivery

Prefer real user behavior/end-to-end tests, then public-seam behavior tests, deterministic API/CLI checks, browser/platform checks, and finally static/type/syntax checks. State what was not exercised. Before public delivery, scan tracked/planned files for secrets, personal/customer data, local paths, machine-specific configuration, logs, databases, caches, and build artifacts.

Do not call a push a release or a static check a platform acceptance test.

## Design restraint

Prefer small stable interfaces and abstractions backed by a current variation point or confirmed reuse. Put speculative improvements in follow-up work.

## Common pitfalls

1. Embedding user identity, persona, business facts, or machine paths in a reusable skill.
2. Using the full release process for a micro fix, or a micro process for risky work.
3. Treating syntax, process startup, file generation, or push as proof of behavior/release.
4. Letting context files become competing sources of truth.
5. Accepting worker success claims without integration verification.
6. Deleting the only source, history, backup, or recovery artifact without authorization.

## Verification checklist

- [ ] Profile and escalation triggers are identified.
- [ ] Requirements, scope, acceptance, stop condition, and risks are recorded when applicable.
- [ ] Authority order and one authoritative source are known.
- [ ] Project-specific skills, if any, live under the project root's `skills/` and are routed by `AGENTS.md`.
- [ ] No new Hermes global skill was created without an explicit user request.
- [ ] Stage evidence has repeatable actions and explicit status.
- [ ] Parallel work was integrated and re-verified when applicable.
- [ ] Requirements fit and engineering quality were reviewed separately.
- [ ] Real behavior/platform validation was completed when required.
- [ ] Security/sensitive-data scan was completed before public delivery.
- [ ] Repository, package, release, and platform states are reported separately.
- [ ] Temporary artifacts were cleaned only after synchronization and verification.
