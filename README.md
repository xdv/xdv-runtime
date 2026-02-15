# xdv-runtime

User Space Runtime for XDV OS.

## Overview

The XDV Runtime provides the user space environment for XDV OS, wrapping `dustlib` and `dustlib_k` to provide:

- I/O operations
- Memory management
- String utilities
- Process management
- Task scheduling
- File system interface
- Console I/O
- Init process (PID 1)

## Architecture

This runtime targets K-Domain operation on classical x86-64 hardware. Q and Phi domain requests are hardware-gated and return `ERR_DOMAIN_NOT_AVAILABLE (100)` when unavailable.

## Source Files

```text
src/
|- runtime_bridge.ds
|- runtime_init.ds
|- runtime_console.ds
|- runtime_io.ds
|- runtime_memory.ds
|- runtime_process.ds
|- runtime_scheduler.ds
|- runtime_fs.ds
|- runtime_string.ds
`- *_tests.ds
```

## Domain Support

| Domain | Status |
|--------|--------|
| K      | Full implementation |
| Q      | Hardware-gated (returns `ERR_DOMAIN_NOT_AVAILABLE` when unavailable) |
| Phi    | Hardware-gated (returns `ERR_DOMAIN_NOT_AVAILABLE` when unavailable) |

## Error Codes

- `0`: Success
- `1-99`: Module-specific errors
- `100`: Domain not available on this hardware

## Dependencies

- `dustlib` (`../dustlib`)
- `dustlib_k` (`../dustlib_k`)

## Version

`0.2.0`
