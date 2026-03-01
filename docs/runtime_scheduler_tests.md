# runtime_scheduler_tests

- Source: `xdv-runtime/src/runtime_scheduler_tests.ds`
- Kind: Test Module
- Summary: Deterministic scheduler checks for priority bounds, task handling, and startup flow.

## Covered Areas
- Default priority value
- Priority bounds validation
- Null PID task rejection
- Schedule tick returns active task id
- Init/start/stop flow

## Entry
- `run_all_tests()`