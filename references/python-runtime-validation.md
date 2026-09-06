# Python runtime and protocol validation

Use when a project contains Python runtime dependencies or a protocol server.

## Dependency and API checks

Declare runtime dependencies in the project, reproduce them in a clean environment, and inspect the installed API signature before relying on version-sensitive parameters. Do not infer compatibility from a global environment or old examples.

## Layered validation

Separate evidence for:

1. source syntax/import and dependency resolution;
2. protocol startup and request/response behavior;
3. external runtime, integration, or target-platform behavior.

A successful import, registration, or process start does not prove the external integration works.

## Protocol smoke test

For a stdio JSON-RPC server, send real initialization and capability/list requests using the protocol version supported by the installed implementation. Check the response schema and deterministically record failures, timeouts, and missing external prerequisites. Do not label an external-runtime timeout as a protocol failure without evidence.

Final reporting must name the layer tested and the layer not tested.
