# Repository normalization and platform scope

Use when reorganizing an existing repository without implementing new product features.

## Scope

- clarify the authoritative source, build copies, and delivery directories;
- record current scope and non-goals;
- normalize repository structure and runtime artifacts;
- align public documentation with the product's actually supported platforms;
- test, review, and deliver the current baseline.

Do not implement roadmap items merely because they appear in issues or notes.

## Recommended order

1. Confirm whether the task is documentation-only, repository normalization, or a structural migration.
2. Record requirements, non-goals, source authority, privacy boundary, and delivery boundary.
3. Write a short plan with exact paths and verification.
4. Identify platform claims separately from the execution environment used by the agent.
5. Search references, scripts, configuration, examples, and documentation before moving or renaming anything.
6. Stop processes that hold files or ports before changing their location.
7. Synchronize accepted changes to the authoritative source and update valid references.
8. Verify behavior, packaging, and platform-specific acceptance where applicable.
9. Scan tracked files for secrets, personal data, local paths, logs, databases, and generated artifacts.
10. Report repository, package, release, and platform acceptance states separately.

## Pitfalls

- Treating a mounted or temporary path as a second authoritative repository.
- Deleting logs before preserving evidence needed to diagnose failures.
- Treating static script checks as native lifecycle acceptance.
- Confusing the agent's execution environment with the product's supported platform.
- Moving a repository without checking local configuration and documentation references.

## Acceptance checklist

- [ ] Scope and non-goals are recorded.
- [ ] Authoritative source is explicit.
- [ ] Public platform claims match actual support.
- [ ] References and scripts were searched before structural changes.
- [ ] Behavior and applicable platform checks passed.
- [ ] Sensitive-data and generated-artifact scans passed.
- [ ] Temporary artifacts and services were safely handled.
