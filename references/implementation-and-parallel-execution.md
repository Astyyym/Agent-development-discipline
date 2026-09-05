# Implementation planning and parallel execution

Use after requirements are confirmed.

## Plan shape
Each task names exact files, one verifiable action, acceptance evidence, and scope boundary. Save a plan under the project convention (`docs/plans/`, `开发短计划/`, or equivalent). A plan-only request writes no product code.

## Parallel agents
Use only when workstreams have non-overlapping files/interfaces and no dependency on each other's unfinished output. Every agent gets repository root, baseline branch, allowed paths, forbidden paths, acceptance checks, and reporting format. Verify every returned claim from live files/tests before accepting it.

## CLI installation smoke check
After installing/updating a user-facing CLI: scan the repository for conflict markers, then invoke the intended command through the real PATH/spawn path. Installation output alone is not success.
