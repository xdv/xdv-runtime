# xdv-runtime Library Documentation

This directory contains markdown documentation for all `xdv-runtime/src` modules, including test modules.

| Module | Kind | Forges | Procedures | Summary |
|---|---|---:|---:|---|
| `runtime_bridge.ds` | Runtime Module | 1 | 6 | xdv-runtime bridge for xdv-os boot profile (codegen-safe subset). |
| `runtime_console.ds` | Runtime Module | 2 | 9 | Runtime Console - Console I/O |
| `runtime_console_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |
| `runtime_fs.ds` | Runtime Module | 2 | 12 | Runtime FS - File System Interface (wraps xdvfs) |
| `runtime_fs_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |
| `runtime_init.ds` | Runtime Module | 2 | 8 | Runtime Init - Init Process (PID 1) |
| `runtime_init_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |
| `runtime_io.ds` | Runtime Module | 2 | 4 | Runtime I/O - Wraps dustlib_k::io |
| `runtime_io_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |
| `runtime_memory.ds` | Runtime Module | 2 | 5 | Runtime Memory - Wraps dustlib_k::memory |
| `runtime_memory_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |
| `runtime_process.ds` | Runtime Module | 2 | 8 | Runtime Process - Wraps dustlib_k::threading |
| `runtime_process_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |
| `runtime_scheduler.ds` | Runtime Module | 2 | 9 | Runtime Scheduler |
| `runtime_scheduler_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |
| `runtime_string.ds` | Runtime Module | 2 | 7 | Runtime String - Wraps dustlib::str |
| `runtime_string_tests.ds` | Test Module | 1 | 1 | normalized test harness for parser compatibility. |

## Notes
- Generated from source signatures/constants in `xdv-runtime/src`.
- Regenerate after runtime API changes to keep docs synchronized.
