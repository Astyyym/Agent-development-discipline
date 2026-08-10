---
name: beginner-agent-development-rules
description: Use when an AI agent starts, changes, migrates, packages, open-sources, or delivers a software project. Guides requirement confirmation, staged verification, maintainable design, safe delivery, and cleanup.
version: 1.3.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [requirements, planning, development, testing, architecture, delivery, security]
    related_skills: [writing-plans, vibe-coding-spec]
---

# Beginner Agent Development Rules

## Overview

A cautious, composable workflow for AI coding agents. It keeps requirements, scope, source locations, verification, delivery, and cleanup explicit without forcing a particular issue tracker, interview ritual, commit policy, or framework.

> Understand first → make a small change → verify the real behavior → record the result → deliver honestly.

## When to Use

Use when an agent is asked to start, change, migrate, package, open-source, review, or deliver a software project. Do not treat an unconfirmed assumption as a requirement. If a decision materially changes architecture, platform support, data handling, user experience, or delivery scope, pause and confirm it.

## 1. Requirements Before Code

1. Restate the intended result in plain language.
2. Identify unclear points, missing use cases, technical/security/compatibility risks, and scope boundaries.
3. Ask only questions that materially affect implementation; recommend a reasonable default when appropriate.
4. Confirm architecture, supported platform, authoritative source location, data storage, delivery format, and development boundaries.
5. Record confirmed requirements before writing product code. Include agent boundaries, prohibited actions, implementation order, and completion criteria.
6. Write a short plan with exact files, tasks, and verification methods.
7. Follow the confirmed requirements without silently expanding scope.
8. Verify each meaningful change and then run an overall workflow check.

For a new requirement, repeat:

**understand → confirm → update requirements → update plan → implement → verify**

Previously confirmed decisions and test boundaries should be reused, not re-asked. New or disputed boundaries require confirmation.

## 2. One Authoritative Source

Every project must have one clearly identified authoritative source location. Do not maintain two independent long-term sources.

Choose the location according to the final runtime and toolchain. Clearly label build copies, test directories, release directories, temporary workspaces, and worktrees so they cannot be mistaken for the authoritative source.

Temporary copies and worktrees are allowed during development. Before removing one:

1. Identify accepted changes, documentation, tests, and useful artifacts.
2. Synchronize accepted changes to the authoritative source.
3. Verify the authoritative source is complete and runnable.
4. Run required tests and smoke checks from the authoritative source.
5. Remove only task-created temporary environments after successful verification.
6. Check for unsynchronized changes before deletion.

Never delete pre-existing backups, branches, worktrees, history, or the only source copy without authorization.

## 3. Short Plans and Project Context

Store a concise plan in the project’s established planning location. Each item states the goal, exact files, steps, verification, and relationship to confirmed requirements.

For long, multi-stage, or cross-session work, keep project context files with distinct responsibilities:

- `AGENTS.md`: long-term project rules, run/test commands, boundaries, and delivery notes;
- `task_plan.md`: current stages, blockers, decisions, and acceptance checks;
- `findings.md`: environment conclusions, pitfalls, and failed approaches;
- `progress.md`: short session-level record of changes, verification, and next step.

Do not create duplicate sources of truth. Product scope belongs in the requirements document; implementation details belong in the short plan; project rules belong in `AGENTS.md`.

## 4. Prototype-First Product Work

For new screens, changed user flows, information architecture, interaction behavior, or visible product states, create and validate a runnable interactive prototype before production implementation. A static screenshot is not an interaction prototype.

Do not manufacture a prototype for backend-only fixes, data migrations, CLI work, build configuration, or small changes with no user-facing behavior.

For product-facing work, use this order:

> intent and boundaries → interactive prototype → prototype acceptance → technical plan and acceptance criteria → staged implementation → real user-flow acceptance → update the prototype and plan

Treat the accepted prototype as the product baseline. When implementation changes visible structure, flow, or state, update the prototype first and keep it synchronized with production behavior. A design artifact does not replace architecture: after prototype acceptance, explicitly define implementation scope, data and permission boundaries, risks, test seams, and non-goals.

Agents may implement, test, reproduce, and repair. Humans retain responsibility for product trade-offs, material architecture decisions, acceptance criteria, and final delivery. Generated output is never sufficient evidence of completion.

## 5. Stages, Feedback Loops, and Vertical Slices

Split complex work into independently verifiable stages. Each stage defines its goal, entry condition, change scope, verification, pass criteria, temporary artifacts, and failure handling.

Use this order:

> confirm entry → execute current stage → verify immediately → record evidence → continue only after passing

A stage is **passed**, **failed**, **blocked**, or **deferred**. Do not enter the next stage, expand scope, or replace stage verification with a later overall test while the gate is not passed.

For multi-step, optimization, investigation, or cross-file work, state a minimal task contract before execution:

| Field | Required content |
|---|---|
| Goal | The real problem and the observable completed outcome |
| Scope | Allowed modules, non-goals, and permission boundaries |
| Acceptance | User flow, test command, benchmark, or observable result |
| Stop condition | When to finish or report a blocker instead of iterating indefinitely |
| Risk | Data, permissions, compatibility, rollback, and irreversible actions |

For performance or solution exploration, establish a comparable baseline before changing implementation, then remeasure and compare. Do not claim an improvement from intuition or a single unpaired observation.

Verification should provide a clear, repeatable, red-capable signal for the stage’s real goal. Prefer:

1. real user behavior or end-to-end flow;
2. behavior tests at an agreed public seam;
3. API/CLI requests with deterministic expected output;
4. browser flow, DOM state, console, and network assertions;
5. type, syntax, and static checks.

Low-level checks do not replace high-level acceptance: syntax passing does not prove a page works, a server starting does not prove business behavior, and a file being generated does not prove its contents or layout are correct.

For complex features, use vertical slices: one smallest real behavior chain at a time, **verification → minimal implementation → re-verification**. Do not first build large layers of frontend/backend/database work or batches of tests that are not tied to observed behavior.

## 6. Delivery Review: Two Separate Axes

Before delivery, review both axes separately.

**Requirements fit**

- Does the implementation satisfy confirmed requirements and stage acceptance criteria?
- Are there omissions, misunderstandings, or decisions that were contradicted?
- Is there unauthorized scope, premature future work, or unclassified new discovery?

**Engineering quality**

- Does it follow project rules and established conventions?
- Are there duplicate logic, debug remnants, temporary artifacts, secrets, or private data?
- Are module boundaries clear, without unnecessary pass-through layers or speculative abstractions?
- Do tests exercise public behavior rather than internal implementation details?

One axis passing does not replace the other. Do not automatically commit, push, package, or release merely because code appears complete; follow the requested delivery boundary.

## 7. Design with Restraint

Prefer deep modules: a small, stable interface that hides meaningful implementation complexity from callers and tests.

Before extracting or abstracting, ask:

- Can the interface be smaller and easier to use?
- Does deleting this module remove complexity, or merely spread it to callers?
- Is there a real variation point or a second adapter today?
- Does the abstraction serve a confirmed requirement rather than a hypothetical future?

Without a real variation point, do not add speculative plugin points, generic parameters, adapters, or middlemen. Record worthwhile architecture improvements as follow-up work instead of expanding the current stage.

## 8. Verification and Security Gate

Verification must match the product and target platform. Where relevant, run syntax/type checks, dependency/resource checks, tests, a real user-flow smoke test, packaging/startup checks, output-content checks, and `git diff --check`.

For visual outputs such as diagrams, tables, maps, or grids, confirm required labels and annotations remain readable in both preview and exported output. For desktop applications, verify the actual packaged executable and native flows when they are part of the deliverable; do not substitute a server-side test.

Before publication, scan tracked files and planned commits for:

- credentials, tokens, cookies, private keys, certificates, and `.env` files;
- personal, customer, health, financial, or business data;
- local absolute paths, usernames, logs, databases, backups, and machine-specific configuration;
- private information in screenshots, README files, prompts, comments, and examples;
- caches, virtual environments, dependencies, and build artifacts that should be ignored.

Use fictional data and portable placeholders. If a secret entered Git history, deleting the current file is not enough: rotate/revoke it and clean the affected history before publication.

## Prohibited Actions

- Coding before material requirements are confirmed.
- Treating guesses as confirmed requirements.
- Continuing with an obsolete plan after requirements change.
- Deleting the only source, useful history, or pre-existing backup without authorization.
- Publishing before scanning for secrets, personal information, local paths, and real data.
- Claiming success without running relevant verification.
- Calling a push a release or a static check a platform acceptance test.
- Forcing an external workflow’s issue, interview, commit, or plugin conventions onto a project where they do not fit.

## Completion Checklist

- [ ] Requirements, risks, scope, platform, and delivery format are confirmed.
- [ ] One authoritative source location is identified.
- [ ] A short implementation plan exists and was followed.
- [ ] Stages have clear gates and minimal evidence.
- [ ] Relevant tests and real workflow checks passed.
- [ ] Requirements fit and engineering quality were reviewed separately.
- [ ] The authoritative source was verified after synchronization.
- [ ] Public files were scanned for secrets, personal data, local paths, and real data.
- [ ] Repository, package, release, and platform-acceptance states are reported separately.
- [ ] Task-created temporary copies and worktrees were removed only after verification.