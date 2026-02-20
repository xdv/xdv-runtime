# runtime_io

- Source: `xdv-runtime/src/runtime_io.ds`
- Kind: Runtime Module
- Summary: Runtime I/O - Wraps dustlib_k::io

## Purpose
Runtime I/O - Wraps dustlib_k::io

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeIo` | 6 | 4 |
| `RuntimeIoErrors` | 8 | 0 |

## API By Forge
### RuntimeIo

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `open` | `path: UInt64, mode: UInt32` | `UInt64` | Performs open operation. |
| `K` | `read` | `fd: UInt64, buffer: UInt64, size: UInt32` | `UInt32` | Performs read operation. |
| `K` | `write` | `fd: UInt64, buffer: UInt64, size: UInt32` | `UInt32` | Performs write operation. |
| `K` | `close` | `fd: UInt64` | `UInt32` | Performs close operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `MAX_OPEN_FILES` | `UInt32` | `64` |
| `MODE_READ` | `UInt32` | `0` |
| `MODE_WRITE` | `UInt32` | `1` |
| `MODE_APPEND` | `UInt32` | `2` |
| `NULL_HANDLE` | `UInt64` | `0` |
| `IO_OK` | `UInt32` | `0` |

### RuntimeIoErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_OPEN_FAILED` | `UInt32` | `1` |
| `ERR_READ_FAILED` | `UInt32` | `2` |
| `ERR_WRITE_FAILED` | `UInt32` | `3` |
| `ERR_CLOSE_FAILED` | `UInt32` | `4` |
| `ERR_INVALID_HANDLE` | `UInt32` | `5` |
| `ERR_NOT_IMPLEMENTED` | `UInt32` | `6` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |

## Runtime Dependencies
- Detected dependency call usage:
- `file_close(...)`
- `file_open(...)`
- `file_read(...)`
- `file_write(...)`

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for production runtime linkage and direct use by xdv-os components.

## Example (DPL)
```dust
let status = open(1, 1);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
