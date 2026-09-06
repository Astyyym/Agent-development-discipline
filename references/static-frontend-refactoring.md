# Static frontend refactoring minimum

Use when refactoring a static HTML/CSS/JS tool.

1. Keep structure, styles, data, and interaction logic at clear boundaries; remove duplicate definitions and stale comments.
2. If an old entry remains as a regression baseline, identify the official entry and why the old file remains.
3. Do not add a launcher script unless it performs real server startup or environment work that is in scope.
4. Keep displayed counts, labels, and explanations derived from one source of truth.
5. For cropping or coordinate work, calculate against the actual displayed rectangle and test both wide and tall inputs.
6. Minimum validation is script syntax, resource loading, and the real affected browser flow.
7. Visual artifacts must preserve required labels and annotations in both preview and exported output.
