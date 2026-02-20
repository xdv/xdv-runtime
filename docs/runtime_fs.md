# runtime_fs

- Source: `xdv-runtime/src/runtime_fs.ds`
- Kind: Runtime Module
- Summary: Runtime FS - File System Interface (wraps xdvfs)

## Purpose
Runtime FS - File System Interface (wraps xdvfs)

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeFs` | 7 | 12 |
| `RuntimeFsErrors` | 14 | 0 |

## API By Forge
### RuntimeFs

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `mount` | `device: UInt64, mount_point: UInt64` | `UInt32` | Performs mount operation. |
| `K` | `umount` | `mount_point: UInt64` | `UInt32` | Performs umount operation. |
| `K` | `open` | `path: UInt64, flags: UInt32` | `UInt64` | Performs open operation. |
| `K` | `read` | `fd: UInt64, buffer: UInt64, size: UInt32` | `UInt32` | Performs read operation. |
| `K` | `write` | `fd: UInt64, buffer: UInt64, size: UInt32` | `UInt32` | Performs write operation. |
| `K` | `close` | `fd: UInt64` | `UInt32` | Performs close operation. |
| `K` | `stat` | `path: UInt64, stat_buf: UInt64` | `UInt32` | Performs stat operation. |
| `K` | `mkdir` | `path: UInt64, mode: UInt32` | `UInt32` | Performs mkdir operation. |
| `K` | `rmdir` | `path: UInt64` | `UInt32` | Performs rmdir operation. |
| `K` | `unlink` | `path: UInt64` | `UInt32` | Performs unlink operation. |
| `K` | `readdir` | `dir: UInt64, entry: UInt64` | `UInt32` | Performs readdir operation. |
| `K` | `is_supported_flag` | `flag: UInt32` | `UInt32` | Performs is supported flag operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `MAX_OPEN_FILES` | `UInt32` | `64` |
| `MAX_PATH_LEN` | `UInt32` | `256` |
| `FILE_FLAG_READ` | `UInt32` | `0` |
| `FILE_FLAG_WRITE` | `UInt32` | `1` |
| `FILE_FLAG_APPEND` | `UInt32` | `2` |
| `NULL_HANDLE` | `UInt64` | `0` |
| `IO_OK` | `UInt32` | `0` |

### RuntimeFsErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_MOUNT_FAILED` | `UInt32` | `1` |
| `ERR_UMOUNT_FAILED` | `UInt32` | `2` |
| `ERR_OPEN_FAILED` | `UInt32` | `3` |
| `ERR_READ_FAILED` | `UInt32` | `4` |
| `ERR_WRITE_FAILED` | `UInt32` | `5` |
| `ERR_CLOSE_FAILED` | `UInt32` | `6` |
| `ERR_NOT_FOUND` | `UInt32` | `7` |
| `ERR_EXISTS` | `UInt32` | `8` |
| `ERR_IS_DIRECTORY` | `UInt32` | `9` |
| `ERR_NOT_DIRECTORY` | `UInt32` | `10` |
| `ERR_PERMISSION` | `UInt32` | `11` |
| `ERR_NO_SPACE` | `UInt32` | `12` |
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
let status = mount(1, 1);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
