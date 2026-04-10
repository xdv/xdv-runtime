# runtime_string

- Source: `xdv-runtime/src/runtime_string.ds`
- Kind: Runtime Module
- Summary: Runtime String - Wraps dustlib::str

## Purpose
Runtime String - Wraps dustlib::str

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `RuntimeString` | 8 | 7 |
| `RuntimeStringErrors` | 5 | 0 |

## API By Forge
### RuntimeString

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `len` | `ptr: UInt64` | `UInt32` | Performs len operation. |
| `K` | `concat` | `a: UInt64, b: UInt64` | `UInt64` | Performs concat operation. |
| `K` | `compare` | `a: UInt64, b: UInt64` | `UInt32` | Performs compare operation. |
| `K` | `find` | `haystack: UInt64, needle: UInt64` | `UInt32` | Performs find operation. |
| `K` | `substring` | `ptr: UInt64, start: UInt32, end: UInt32` | `UInt64` | Performs substring operation. |
| `K` | `to_upper` | `ptr: UInt64` | `UInt64` | Performs to upper operation. |
| `K` | `to_lower` | `ptr: UInt64` | `UInt64` | Performs to lower operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `MAX_STRING_LEN` | `UInt32` | `65536` |
| `NULL_PTR` | `UInt64` | `0` |
| `LEN_EMPTY` | `UInt32` | `0` |
| `MATCH_FALSE` | `UInt32` | `0` |
| `MATCH_TRUE` | `UInt32` | `1` |
| `CMP_EQUAL` | `UInt32` | `0` |
| `CMP_LESS` | `UInt32` | `1` |
| `CMP_GREATER` | `UInt32` | `2` |

### RuntimeStringErrors

#### Procedures
- No `proc` entries in this forge.

#### Constants
| Constant | Type | Value |
|---|---|---|
| `ERR_OK` | `UInt32` | `0` |
| `ERR_INVALID_PTR` | `UInt32` | `1` |
| `ERR_OUT_OF_BOUNDS` | `UInt32` | `2` |
| `ERR_EMPTY_STRING` | `UInt32` | `3` |
| `ERR_DOMAIN_NOT_AVAILABLE` | `UInt32` | `100` |

## Runtime Dependencies
- Detected dependency call usage:
- `contains(...)`
- `split_at(...)`

## Integration Notes
- Runtime modules provide K-domain implementation with Q/Phi behavior gated by runtime availability policy where applicable.
- This module is intended for production runtime linkage and direct use by xdv-os components.

## Example (DPL)
```dust
let status = len(4096);
if status == 0 {
    emit "ok";
} else {
    emit "failed";
}
```
