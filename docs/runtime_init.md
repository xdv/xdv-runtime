# runtime_init

- Source: `xdv-runtime/src/runtime_init.ds`
- Kind: Runtime Module
- Summary: Init process startup with ABI binding and replay/telemetry hook activation.

## Purpose
Init process (`PID 1`) startup sequence now includes hybrid runtime contract initialization:
1. Console + scheduler + FS init
2. Process/domain ABI binding initialization
3. Replay/telemetry hook activation
4. Shell spawn path

## Key Procedures
- `main()`
- `init_fs()`
- `init_scheduler()`
- `init_console()`
- `init_runtime_abi_bindings()`
- `init_runtime_hooks()`
- `spawn_shell()`
- `wait_for_child(...)`
- `handle_signal(...)`

## Notes
- ABI init validates K-anchored process context creation.
- Hook init ensures deterministic event + telemetry emission is online before shell launch.