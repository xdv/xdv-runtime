# runtime_init_tests

- Source: `xdv-runtime/src/runtime_init_tests.ds`
- Kind: Test Module
- Summary: Startup tests for ABI binding init, hook activation, and signal handling.

## Covered Areas
- Runtime ABI binding initialization
- Replay/telemetry hook initialization
- Supported signal handling (`NOP`, `REAP`, `TERM`)
- Unsupported signal deterministic error path

## Entry
- `run_all_tests()`