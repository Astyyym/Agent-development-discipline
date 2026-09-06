# Existing-project review checklist

Use when reviewing an already-developed project. Review first; do not change code until the scope is confirmed.

## 1. Requirements and plan

- Is there a current requirements source rather than only chat history or an execution prompt?
- Does the implementation match the confirmed architecture and boundaries?
- Are new ideas still outside scope until confirmed?
- Are the plan, exact files, verification, and acceptance clear?
- Are completed items recorded as history rather than presented as future work?

## 2. Source and environment

- Is the authoritative source distinct from build copies and delivery directories?
- Are independent clones, worktrees, and temporary copies accounted for?
- Is platform support distinguished from tests run in the agent's environment?

## 3. Public-release safety

Check the current tree and relevant Git history for:

- secrets, tokens, cookies, private keys, and real configuration;
- personal, customer, health, financial, or business data;
- local absolute paths and usernames;
- logs, databases, backups, screenshots, and generated files;
- `.gitignore` coverage for private runtime artifacts.

Interpret example values in context; do not label public test fixtures as secrets mechanically.

## 4. Evidence levels

Report the highest level actually completed:

1. static check;
2. unit/integration automation;
3. local runtime smoke test;
4. target-platform acceptance;
5. packaged artifact or release acceptance.

A script-content test does not prove native execution. A test in one environment does not prove support on another.

## 5. Review output

Classify findings as:

- **must fix**: security, requirement deviation, inability to deliver, or overclaim;
- **recommended**: maintainability, documentation, or usability improvement;
- **no change now**: already within the agreed boundary;
- **needs decision**: changes architecture, usage, platform support, or public commitment;
- **not verified**: evidence is missing.

End the review at the confirmation point. Implementation begins only after scope and decisions are confirmed.
