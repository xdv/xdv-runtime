# runtime_console_tests

- Source: `xdv-runtime/src/runtime_console_tests.ds`
- Kind: Test Module
- Summary: normalized test harness for parser compatibility.

## Purpose
normalized test harness for parser compatibility.

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeConsoleTests` | 0 | 1 |

## API By Forge
### RuntimeConsoleTests

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `run_all_tests` | `(none)` | `UInt32` | Performs run all tests operation. |

#### Constants
- No constants declared in this forge.

## Runtime Dependencies
- No external call sites detected.

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for validation/test execution and should not be linked as primary runtime surface.

## Example (DPL)
```dust
let status = run_all_tests();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
