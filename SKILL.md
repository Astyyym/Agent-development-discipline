---
name: beginner-agent-development-rules
description: Use when an AI agent starts, changes, migrates, packages, open-sources, or delivers a software project. Guides requirement confirmation, isolated development, verified delivery, sensitive-data checks, and cleanup of temporary copies or worktrees.
version: 1.0.0
author: Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [requirements, planning, development, worktree, delivery, security]
    related_skills: [writing-plans, vibe-coding-spec]
---

# Beginner Agent Development Rules

## Overview

This skill defines a cautious development workflow for AI coding agents. It is intended for projects where requirements, file locations, isolated development, verification, delivery, and cleanup must remain explicit.

The central rule is: **understand first, modify deliberately, verify the authoritative copy, and clean up temporary development environments only after verification succeeds.**

## When to Use

Use this skill when an agent is asked to:

- start a new software project or feature;
- change, migrate, package, or deliver an existing project;
- create a branch, clone, temporary copy, or Git worktree;
- open-source a project or publish project files;
- review whether a project is ready for delivery.

Do not treat an unconfirmed assumption as a requirement. If a decision materially changes architecture, platform support, data handling, user experience, or delivery scope, pause and confirm it first.

## 1. Requirements Before Code

For a new project or requirement change:

1. Restate the intended result in plain language.
2. Identify unclear points, missing use cases, technical risks, compatibility concerns, security risks, and scope boundaries.
3. Ask only the questions that materially affect implementation. When a reasonable default exists, recommend it and explain why.
4. Confirm the architecture, supported platform, authoritative source location, data storage, delivery format, and development boundaries.
5. Record the confirmed requirements before writing product code. The requirements document should include:
   - execution principles;
   - prohibited actions;
   - implementation order;
   - completion checklist;
   - boundaries for AI-agent actions.
6. Write a short implementation plan containing exact files, tasks, and verification commands.
7. Follow the confirmed requirements and plan without silently expanding the scope.
8. Verify each meaningful change and then run an overall workflow check.

For new requirements, repeat this sequence:

**understand and identify questions → confirm → update requirements → update plan → implement → verify**

## 2. Authoritative Source and Development Locations

Every project must have one clearly identified **authoritative source location**. Do not maintain two independent copies as long-term sources of truth.

Choose the location according to the final runtime and toolchain:

- A small local application may use its target platform directory as the authoritative source.
- A project that needs a Linux toolchain may use a Linux/WSL repository as the primary source and use another platform only for packaging or smoke testing.
- A service or platform-specific plugin should remain in the environment where it is developed and run.
- If development starts in a temporary environment, migrate or synchronize the accepted changes to the authoritative source before delivery.

Clearly label build copies, test directories, release directories, and temporary workspaces. They must not be mistaken for the authoritative source.

### Temporary Copies and Git Worktrees

Temporary copies, branches, Git worktrees, and isolated directories are allowed during development. They are process environments, not permanent additional sources.

At the end of development:

1. Identify all accepted changes, documentation, tests, and useful artifacts.
2. Synchronize the accepted changes to the predetermined authoritative source.
3. Verify that the authoritative source is complete and runnable.
4. Run the required tests and smoke checks from the authoritative source.
5. Only after successful verification, remove the temporary copies and worktrees created for this task.
6. Before deletion, check for unsynchronized changes or valuable files.

Delete only temporary environments created for the current task. Do not delete pre-existing user backups, directories, branches, or worktrees without explicit authorization. Formal delivery artifacts such as release packages, installers, `dist` directories, and test reports may be retained according to the project’s delivery requirements.

## 3. Short Implementation Plans

Store a concise plan in the project’s established planning location, such as `docs/plans/`, `plans/`, or `development-plans/`. Each item should state:

- goal;
- exact files to create or modify;
- implementation steps;
- verification method;
- relationship to the confirmed requirements.

If a discovery changes the requirements, architecture, or user experience, stop and report it. Update the requirements and plan before continuing.

## 4. Minimum Verification

Verification must match the actual product and target platform. Do not claim a platform or workflow is supported based only on static inspection.

At minimum, perform the checks relevant to the project:

- syntax or type checks;
- dependency and resource-loading checks;
- unit or integration tests;
- one real user-flow smoke test;
- packaging and startup checks when a packaged application is delivered;
- file output checks, including headers, paths, names, dimensions, or content where applicable;
- `git diff --check` for Git repositories.

For visual outputs such as diagrams, tables, maps, or grids, verify that labels, numbers, and other required annotations remain readable in both preview and exported output. Do not silently omit required information to make a preview smaller.

For desktop applications, do not substitute a server-side test for native application acceptance. When applicable, verify the actual packaged executable, isolated test data, startup/restart behavior, native file dialogs, cancellation behavior, Unicode paths, and the final output in an appropriate viewer.

Report separately what was covered by automation, what was observed in the packaged application, and what still requires manual acceptance.

## 5. Open-Source Security Gate

Before making a repository public, scan tracked files and planned commits for:

- API keys, tokens, cookies, passwords, private keys, certificates, and `.env` files;
- real names, phone numbers, addresses, customer, health, financial, or business data;
- local absolute paths, usernames, logs, databases, backups, and machine-specific configuration;
- private information in screenshots, demonstrations, README files, prompts, comments, and examples;
- virtual environments, caches, dependency directories, and build artifacts that should be ignored.

Use fictional demonstration data and portable placeholders such as `<username>` or `/path/to/project`. Keep real configuration local and ignored; provide only safe examples such as `.env.example` when needed.

If a secret has entered Git history, deleting the current file is not enough. Rotate or revoke the secret and clean the affected history before publication.

## 6. Publishing a Clean Public Repository

When the original project contains private history or local-only data:

1. Keep the original project private until the public copy is verified.
2. Export only the intended tracked source, not the entire working directory.
3. Create the public copy in a separate directory without private Git history unless history preservation was explicitly required.
4. Sanitize source files, documentation, configuration examples, scripts, metadata, logs, and screenshots.
5. Run secret, path, data-file, syntax, and repository checks.
6. Create the public repository and push only after the checks pass.
7. Verify the repository visibility, default branch, commit history, and key files through the hosting service.
8. Read back the public README and important files through an unauthenticated URL when possible.
9. Keep the original private repository until the user explicitly authorizes its deletion or migration.

Do not describe `git push` as a release. Distinguish clearly between a pushed repository, a published release, a packaged artifact, and a completed platform acceptance test.

## 7. Review and Cleanup

When reviewing a completed project, classify findings as:

- must fix;
- recommended improvement;
- currently acceptable;
- requires user confirmation.

Separate automated evidence from platform-specific manual evidence. Do not modify unrelated issues merely because they exist, and do not delete historical files or a unique source copy just to make the directory look clean.

After delivery verification:

- confirm the authoritative source path;
- confirm the final Git status and relevant remote state;
- confirm accepted changes were not left only in a temporary workspace;
- remove only the temporary copies and worktrees created for the task;
- retain explicitly required release artifacts and reports.

## Prohibited Actions

- Coding before material requirements are confirmed.
- Treating guesses as confirmed requirements.
- Continuing with an obsolete plan after the requirements change.
- Deleting the only source copy or useful history before a verified replacement exists.
- Publishing before scanning for secrets, personal information, local paths, and real data.
- Claiming success without running the relevant verification.
- Deleting pre-existing backups or worktrees without authorization.
- Leaving task-created temporary copies indefinitely after successful delivery.

## Completion Checklist

- [ ] Requirements, risks, scope, platform, and delivery format are confirmed.
- [ ] An authoritative source location is identified.
- [ ] A short implementation plan exists and was followed.
- [ ] Relevant tests and real workflow checks passed.
- [ ] The authoritative source was verified after synchronization.
- [ ] Public files were scanned for secrets, personal data, local paths, and real data.
- [ ] Repository, package, release, and platform-acceptance states are reported separately.
- [ ] Required delivery artifacts were retained.
- [ ] Task-created temporary copies and worktrees were removed only after verification.
