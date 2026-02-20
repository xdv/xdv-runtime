# runtime_bridge

- Source: `xdv-runtime/src/runtime_bridge.ds`
- Kind: Runtime Module
- Summary: xdv-runtime bridge for xdv-os boot profile (codegen-safe subset).

## Purpose
xdv-runtime bridge for xdv-os boot profile (codegen-safe subset).

## Forge Overview
| Forge | Constants | Procedures |
|---|---:|---:|
| `XdvRuntimeBridge` | 3 | 6 |

## API By Forge
### XdvRuntimeBridge

#### Procedures
| Domain | Procedure | Parameters | Returns | Description |
|---|---|---|---|---|
| `K` | `init` | `(none)` | `UInt32` | Performs init operation. |
| `K` | `start_userspace` | `(none)` | `UInt32` | Performs start userspace operation. |
| `K` | `bridge_runtime_init` | `(none)` | `UInt32` | Performs bridge runtime init operation. |
| `K` | `bridge_runtime_main` | `(none)` | `UInt32` | Performs bridge runtime main operation. |
| `K` | `runtime_bridge_healthcheck` | `(none)` | `UInt32` | Performs runtime bridge healthcheck operation. |
| `K` | `shell_bootstrap` | `(none)` | `UInt32` | Performs shell bootstrap operation. |

#### Constants
| Constant | Type | Value |
|---|---|---|
| `BRIDGE_VERSION` | `UInt32` | `5` |
| `RUNTIME_OK` | `UInt32` | `0` |
| `SHELL_OK` | `UInt32` | `0` |

## Runtime Dependencies
- Detected dependency call usage:
- `shell_bridge_init(...)`
- `shell_bridge_launch(...)`

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
