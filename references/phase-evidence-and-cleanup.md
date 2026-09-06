# Phase evidence and cleanup

## Phase execution

For normal and high-risk work, each phase defines its entry condition, goal, allowed scope, verification, pass criteria, temporary artifacts, and failure handling.

Fixed order:

> confirm entry → execute → verify immediately → record evidence → continue only after passing

A phase is `passed`, `failed`, `blocked`, or `deferred`. Do not replace a failed gate with a later overall test.

## Evidence record

Use one record per phase. Markdown is sufficient; YAML or JSON may be used when automation consumes the record.

```yaml
phase: "name"
goal: "observable outcome"
scope: ["allowed/path"]
action: "command or user action"
inputs: "relevant input or fixture"
expected: "expected observable result"
actual: "observed result"
evidence_type: "e2e | behavior_test | api_cli | browser | platform | static | manual"
status: "passed | failed | blocked | deferred"
artifacts: ["path or URL, if any"]
limitations: "what was not exercised"
next_step: "follow-up or none"
```

`static`, `theoretical`, `not_run`, and `manual_pending` evidence must not be represented as a successful behavior or platform acceptance. Preserve the command, input, and actual output when they are needed to reproduce the claim.

## Final delivery report

At minimum report:

- requested scope and non-goals;
- changed files or artifacts;
- requirements-fit result;
- engineering-quality result;
- phase statuses and evidence links;
- tests and real user/platform flows run;
- failed, blocked, deferred, and unverified items;
- repository, package, release, and platform states separately;
- cleanup and rollback status.

## Failure handling

1. Record the symptom and reproduction.
2. Classify code, requirement, environment, or verification-method cause.
3. Change only the current phase scope.
4. Rerun the complete phase verification.
5. Update evidence before proceeding.

## Cleanup

Register task-created temporary directories, worktrees, test data, logs, caches, services, ports, screenshots, and build artifacts. After synchronization and verification, close task-created services, remove only disposable artifacts, and confirm the authoritative source and formal outputs remain usable. Never remove a pre-existing backup, only source, history, or recovery artifact without authorization.
