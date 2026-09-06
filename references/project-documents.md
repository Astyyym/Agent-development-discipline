# Project context documents

Use the project's existing documentation convention. File names below are examples, not requirements.

## Responsibilities

| Document | Responsibility |
|---|---|
| Requirements / PRD | Product scope, non-goals, acceptance, and confirmed decisions |
| Project instructions (`AGENTS.md` or equivalent) | Long-term rules, commands, boundaries, and delivery constraints |
| Short plan | How this change will be made: exact files, steps, and verification |
| Task state | Current stage, blockers, acceptance status, and next gate |
| Findings | Environment conclusions, pitfalls, and failed approaches |
| Progress | Concise session history |

## Creation threshold

- A one-line or low-risk change may use only the existing issue/diff and targeted verification.
- Normal changes need recorded requirements, acceptance, and a short plan.
- Cross-session, multi-stage, high-risk, or interruption-prone work may use task state, findings, and progress.
- Do not create a document merely because this table names it.

## Project-specific skill files

When a project has a stable, repeatable workflow that belongs only to that project:

- Put the skill at the project root: `skills/<skill-name>/SKILL.md`.
- Put long procedures and case material in that skill's `references/`.
- Record the skill entry point and applicable task types in `AGENTS.md`.
- Do not copy the project skill into Hermes's global skill directory.
- Do not create a skill for one-off tasks, temporary progress, personal configuration, or ordinary project facts.

Recommended `AGENTS.md` route:

```markdown
## Project skill routing

Before project work, read the matching files:

- Main project skill: `skills/<skill-name>/SKILL.md`
- Details: read matching files under `references/` as needed

Project-specific skills belong to this project and are not added to Hermes's global skill directory.
```

## Authority and synchronization

1. Product scope comes from requirements/PRD.
2. Long-term project rules come from project instructions.
3. Implementation steps and verification come from the short plan.
4. Current stage status comes from task state.
5. Findings and progress record evidence; they do not override normative decisions.

Before changing a requirement, update the requirements source, then the short plan, then task state and derived notes. If sources conflict, stop implementation, identify the files and claims, apply the project's declared authority order, ask for a decision when the order is unclear, and synchronize derived records after resolution.

Do not copy the same decision into several normative documents. Link to the authority instead. Mark historical notes as history and do not treat them as current instructions.
