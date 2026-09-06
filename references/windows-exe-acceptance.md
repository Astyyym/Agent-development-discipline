# Native desktop artifact acceptance

Use when the deliverable depends on a native desktop executable, embedded webview, system dialog, or another platform-specific artifact.

A server-side test, source build, or generated document does not replace acceptance of the actual artifact.

1. Build from the intended clean source using the project's documented command.
2. Start the actual artifact with isolated test data and no production data.
3. Exercise the affected native and application flows, including error, cancel, restart, path, and output cases relevant to the requirement.
4. Test browser or alternate modes separately when they are also supported.
5. Report automation, observed native behavior, and pending manual checks separately.

A packaged artifact is only accepted when the required real flow passes; otherwise report partial, failed, blocked, or unverified status.
