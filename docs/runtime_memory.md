# runtime_memory

- Source: `xdv-runtime/src/runtime_memory.ds`
- Kind: Runtime Module
- Summary: Runtime Memory - Wraps dustlib_k::memory

## Purpose
Runtime Memory - Wraps dustlib_k::memory

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeMemory` | 5 | 5 |
| `RuntimeMemoryErrors` | 6 | 0 |

## API By Forge
### RuntimeMemory

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `alloc` | `size: UInt32` | `UInt64` | Performs alloc operation. |
| `K` | `free` | `ptr: UInt64` | `UInt32` | Performs free operation. |
| `K` | `zero_alloc` | `size: UInt32` | `UInt64` | Performs zero alloc operation. |
| `K` | `copy` | `dest: UInt64, src: UInt64, size: UInt32` | `UInt32` | Performs copy operation. |
| `K` | `set` | `ptr: UInt64, value: UInt8, size: UInt32` | `UInt32` | Performs set operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `PAGE_SIZE` | `UInt32` | `4096` |
| `MAX_HEAP_SIZE` | `UInt64` | `16777216` |
| `NULL_PTR` | `UInt64` | `0` |
| `MEM_OK` | `UInt32` | `0` |
| `BYTES_NONE` | `UInt32` | `0` |

### RuntimeMemoryErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_ALLOC_FAILED` | `UInt32` | `1` |
| `ERR_FREE_FAILED` | `UInt32` | `2` |
| `ERR_INVALID_POINTER` | `UInt32` | `3` |
| `ERR_OUT_OF_MEMORY` | `UInt32` | `4` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |

## Runtime Dependencies
- Detected dependency call usage:
- `align_up(...)`
- `mem_alloc(...)`
- `mem_free(...)`
- `mem_zero_alloc(...)`
- `memory_init(...)`

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for production runtime linkage and direct use by xdv-os components.

## Example (DPL)
```dust
let status = alloc(512);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
