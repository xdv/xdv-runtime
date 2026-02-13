# xdv-runtime

User Space Runtime for XDV OS, following Implementation Plan v4.

## Overview

The XDV Runtime provides the user space environment for XDV OS, wrapping dustlib and dustlib_k libraries to provide:

- I/O operations
- Memory management
- String utilities
- Process management
- Task scheduling
- File system interface
- Console I/O
- Init process (PID 1)

## Architecture

This implementation follows the K-Domain only approach (classical x86-64 hardware), with Q/Φ domains stubbed to return ERR_DOMAIN_NOT_AVAILABLE (100).

## Source Files

```
src/
├── runtime_io.ds            # I/O (wraps dustlib_k::io)
├── runtime_io_tests.ds      # I/O tests
├── runtime_memory.ds        # Memory (wraps dustlib_k::memory)
├── runtime_memory_tests.ds  # Memory tests
├── runtime_string.ds        # String (wraps dustlib::str)
├── runtime_string_tests.ds  # String tests
├── runtime_process.ds       # Process (wraps dustlib_k::threading)
├── runtime_process_tests.ds # Process tests
├── runtime_scheduler.ds     # Scheduler
├── runtime_scheduler_tests.ds # Scheduler tests
├── runtime_fs.ds            # FS interface (wraps xdvfs)
├── runtime_fs_tests.ds       # FS tests
├── runtime_console.ds        # Console I/O
├── runtime_console_tests.ds  # Console tests
├── runtime_init.ds          # Init process (PID 1)
└── runtime_init_tests.ds    # Init tests
```

## Domain Support

| Domain | Status |
|--------|--------|
| K      | Full implementation |
| Q      | Stubbed (returns ERR_DOMAIN_NOT_AVAILABLE) |
| Φ      | Stubbed (returns ERR_DOMAIN_NOT_AVAILABLE) |

## Error Codes

- 0: Success
- 1-99: Module-specific errors
- 100: ERR_DOMAIN_NOT_AVAILABLE (Q/Φ domains)

## Dependencies

- dustlib (../dustlib)
- dustlib_k (../dustlib_k)

## Building

This project uses the DPL build system. Ensure dustlib and dustlib_k are available in sibling directories.

## Testing

Each module has corresponding test files. Run tests to verify functionality:

```bash
# Test files follow the pattern: *_tests.ds
```

## Version

0.2.0
