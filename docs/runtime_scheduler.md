# runtime_scheduler

- Source: `xdv-runtime/src/runtime_scheduler.ds`
- Kind: Runtime Module
- Summary: Runtime Scheduler

## Purpose
Runtime Scheduler

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeScheduler` | 6 | 9 |
| `RuntimeSchedulerErrors` | 5 | 0 |

## API By Forge
### RuntimeScheduler

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `init` | `(none)` | `UInt32` | Performs init operation. |
| `K` | `start` | `(none)` | `UInt32` | Performs start operation. |
| `K` | `stop` | `(none)` | `UInt32` | Performs stop operation. |
| `K` | `add_task` | `pid: UInt32, priority: UInt32` | `UInt32` | Performs add task operation. |
| `K` | `remove_task` | `pid: UInt32` | `UInt32` | Performs remove task operation. |
| `K` | `set_priority` | `pid: UInt32, priority: UInt32` | `UInt32` | Performs set priority operation. |
| `K` | `get_current_task` | `(none)` | `UInt32` | Performs get current task operation. |
| `K` | `schedule` | `(none)` | `UInt32` | Performs schedule operation. |
| `K` | `default_priority` | `(none)` | `UInt32` | Performs default priority operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `MAX_PRIORITY` | `UInt32` | `10` |
| `MIN_PRIORITY` | `UInt32` | `0` |
| `DEFAULT_PRIORITY` | `UInt32` | `5` |
| `TIME_SLICE_MS` | `UInt32` | `10` |
| `NULL_PID` | `UInt32` | `0` |
| `THREAD_OK` | `UInt32` | `0` |

### RuntimeSchedulerErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_NO_TASKS` | `UInt32` | `1` |
| `ERR_INVALID_PRIORITY` | `UInt32` | `2` |
| `ERR_SCHEDULER_NOT_RUNNING` | `UInt32` | `3` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |

## Runtime Dependencies
- Detected dependency call usage:
- `clamp_u32(...)`
- `getpid(...)`
- `next_thread_id(...)`
- `process_init(...)`
- `thread_join(...)`
- `thread_sleep(...)`

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for production runtime linkage and direct use by xdv-os components.

## Example (DPL)
```dust
let status = init();
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
