# runtime_init

- Source: `xdv-runtime/src/runtime_init.ds`
- Kind: Runtime Module
- Summary: Runtime Init - Init Process (PID 1)

## Purpose
Runtime Init - Init Process (PID 1)

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeInit` | 8 | 8 |
| `RuntimeInitErrors` | 7 | 0 |

## API By Forge
### RuntimeInit

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `main` | `(none)` | `UInt32` | Performs main operation. |
| `K` | `init_fs` | `(none)` | `UInt32` | Performs init fs operation. |
| `K` | `init_scheduler` | `(none)` | `UInt32` | Performs init scheduler operation. |
| `K` | `init_console` | `(none)` | `UInt32` | Performs init console operation. |
| `K` | `spawn_shell` | `(none)` | `UInt32` | Performs spawn shell operation. |
| `K` | `wait_for_child` | `pid: UInt32` | `UInt32` | Performs wait for child operation. |
| `K` | `reap_zombies` | `(none)` | `UInt32` | Performs reap zombies operation. |
| `K` | `handle_signal` | `sig: UInt32` | `UInt32` | Performs handle signal operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `INIT_PID` | `UInt32` | `1` |
| `INIT_STACK_SIZE` | `UInt32` | `8192` |
| `ROOT_DEVICE` | `UInt64` | `1` |
| `ROOT_MOUNT_POINT` | `UInt64` | `1` |
| `NULL_PID` | `UInt32` | `0` |
| `SIG_NOP` | `UInt32` | `0` |
| `SIG_REAP` | `UInt32` | `1` |
| `SIG_TERM` | `UInt32` | `15` |

### RuntimeInitErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_INIT_FAILED` | `UInt32` | `1` |
| `ERR_FORK_FAILED` | `UInt32` | `2` |
| `ERR_EXEC_FAILED` | `UInt32` | `3` |
| `ERR_WAIT_FAILED` | `UInt32` | `4` |
| `ERR_SIGNAL_UNSUPPORTED` | `UInt32` | `5` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |

## Runtime Dependencies
- Detected dependency call usage:
- `console_init(...)`
- `join(...)`
- `mount(...)`
- `process_init(...)`
- `runtime_init(...)`
- `spawn(...)`

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for production runtime linkage and direct use by xdv-os components.

## Example (DPL)
```dust
let status = main();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
