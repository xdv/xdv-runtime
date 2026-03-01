# xdv-runtime Library Documentation

This directory documents the current `xdv-runtime/src` modules.

## Core Runtime Contract Modules
- `runtime_process.ds`: Hybrid Runtime ABI, capability/contract call enforcement, replay + telemetry hooks.
- `runtime_bridge.ds`: Boot/userspace bridge with ABI assertion and runtime call probes.
- `runtime_init.ds`: Init process startup including ABI binding + hook activation.

## Supporting Modules
- `runtime_console.ds`
- `runtime_fs.ds`
- `runtime_io.ds`
- `runtime_memory.ds`
- `runtime_scheduler.ds`
- `runtime_string.ds`

## Test Modules
- `runtime_process_tests.ds`
- `runtime_init_tests.ds`
- `runtime_scheduler_tests.ds`
- `runtime_console_tests.ds`
- `runtime_fs_tests.ds`
- `runtime_io_tests.ds`
- `runtime_memory_tests.ds`
- `runtime_string_tests.ds`

## Notes
- Function names in FS/IO/Memory compatibility layers use parser-safe identifiers (`*_file`, `*_mem`, etc.).
- Runtime bridge contract version remains pinned for kernel compatibility.