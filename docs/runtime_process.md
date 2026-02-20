# runtime_process

- Source: `xdv-runtime/src/runtime_process.ds`
- Kind: Runtime Module
- Summary: Runtime Process - Wraps dustlib_k::threading

## Purpose
Runtime Process - Wraps dustlib_k::threading

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeProcess` | 7 | 8 |
| `RuntimeProcessErrors` | 8 | 0 |

## API By Forge
### RuntimeProcess

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `spawn` | `entry: UInt64, stack_size: UInt32` | `UInt32` | Performs spawn operation. |
| `K` | `join` | `pid: UInt32` | `UInt64` | Performs join operation. |
| `K` | `exit` | `pid: UInt32, code: UInt32` | `UInt32` | Performs exit operation. |
| `K` | `getpid` | `(none)` | `UInt32` | Performs getpid operation. |
| `K` | `sleep` | `ms: UInt32` | `UInt32` | Performs sleep operation. |
| `K` | `yield` | `(none)` | `UInt32` | Performs yield operation. |
| `K` | `spawn_with_limit` | `entry: UInt64, stack_size: UInt32, pid_limit: UInt32` | `UInt32` | Performs spawn with limit operation. |
| `K` | `is_valid_pid` | `pid: UInt32` | `UInt32` | Performs is valid pid operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `MAX_PROCESSES` | `UInt32` | `256` |
| `INIT_PID` | `UInt32` | `1` |
| `MIN_STACK_SIZE` | `UInt32` | `4096` |
| `MAX_STACK_SIZE` | `UInt32` | `1048576` |
| `PID_BASE_SEED` | `UInt32` | `17` |
| `NULL_PID` | `UInt32` | `0` |
| `THREAD_OK` | `UInt32` | `0` |

### RuntimeProcessErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_SPAWN_FAILED` | `UInt32` | `1` |
| `ERR_JOIN_FAILED` | `UInt32` | `2` |
| `ERR_INVALID_PID` | `UInt32` | `3` |
| `ERR_PROCESS_NOT_FOUND` | `UInt32` | `4` |
| `ERR_OUT_OF_PIDS` | `UInt32` | `5` |
| `ERR_SLEEP_FAILED` | `UInt32` | `6` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |

## Runtime Dependencies
- Detected dependency call usage:
- `process_init(...)`
- `thread_join(...)`
- `thread_sleep(...)`
- `thread_spawn(...)`

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for production runtime linkage and direct use by xdv-os components.

## Example (DPL)
```dust
let status = spawn(1, 512);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
