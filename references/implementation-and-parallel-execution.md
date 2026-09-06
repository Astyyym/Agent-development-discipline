# Implementation planning and parallel execution

Use after requirements are confirmed.

## Plan shape

Each task names exact files or interfaces, one verifiable action, acceptance evidence, scope boundaries, stop conditions, and risks. Save a plan under the project's established convention. A plan-only request writes no product code.

## Parallel work

Parallelize only independent work with non-overlapping files and stable interfaces. Every worker receives the repository root, baseline revision, allowed paths, forbidden paths, acceptance checks, and the evidence schema.

A coordinator owns integration and conflict decisions. Workers must not independently rewrite shared planning, status, or evidence records unless explicitly assigned.

## Integration protocol

1. Freeze the baseline and collect each worker's changed paths, revision, tests, and limitations.
2. Verify every claim from live files and commands; a worker report is not evidence by itself.
3. Synchronize accepted changes into the authoritative source in a declared order.
4. Scan for conflict markers, unintended scope, duplicate logic, and interface drift.
5. Run integration, regression, and affected end-to-end checks from the authoritative source.
6. Update one authoritative task/evidence record and classify each workstream and the overall phase.
7. If a worker is unverified or fails integration, keep that workstream unverified/failed and do not mark the overall phase passed.

When conflict resolution changes requirements, interfaces, or scope, stop and obtain the required decision before continuing.

## Installation smoke check

After installing or updating a user-facing CLI, scan the repository for conflict markers and invoke the intended command through the real PATH or process-spawn path. Installation output alone is not success.
