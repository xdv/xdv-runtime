# runtime_process_tests

- Source: `xdv-runtime/src/runtime_process_tests.ds`
- Kind: Test Module
- Summary: Deterministic tests for ABI handles, binding rules, call enforcement, replay override, and telemetry/event packing.

## Covered Areas
- Capability handle round-trip
- Resource contract active-window validation
- K-anchor enforcement for binding
- Contract-required enforcement for Q/Phi
- Capability authorization failures
- Replay override behavior on runtime call paths
- IPC packed result field validation
- Syscall result packing/unpacking
- Transition attestation requirement
- Process context creation and K-anchor verification

## Entry
- `run_all_tests()`