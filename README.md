# xdv-runtime

Hybrid user-space runtime for XDV OS.

## Specification Alignment
- `XDV-020` Hybrid Process Model
- `XDV-021` Cross-Domain IPC
- `XDV-022` Domain Transition Protocol
- `XDV-023` Domain Resource Contracts
- `XDV-052` Hybrid Runtime ABI
- `XDV-081` Hybrid Runtime Reference

## Implemented Runtime Contracts

### 1) Process / Domain ABI bindings
- Stable runtime ABI version exports (`hr_abi_version_*`, feature flags)
- K-anchored hybrid process context encoding/decoding
- Lifecycle-state and transition validation
- Explicit process-domain binding validation

### 2) Capability / Contract-aware runtime calls
- Capability-handle packing and validation (domain + flags + raw id)
- Resource-contract handle packing and active-window checks
- Explicit `runtime_xdv_call(...)` and `runtime_send_cross_domain_ipc(...)`
- Deterministic `runtime_syscall(...)` result packing
- Contract enforcement for Q/Phi domain invocation

### 3) Replay + telemetry hooks
- Deterministic runtime event recording (`runtime_record_event`)
- Replay override path (`runtime_apply_replay_outcome`)
- Runtime telemetry emission (`runtime_emit_telemetry`)
- Transition and IPC call paths instrumented with telemetry/event hooks

## Source Layout
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

## Runtime Bridge Compatibility
- `runtime_bridge_version()` remains `5` for current kernel contract compatibility.
- Bridge init now asserts runtime ABI contract and probes capability/contract call path.

## Build
`dust check xdv-runtime/src`

## Test
`dust test xdv-runtime/tests`

## Notes
- This runtime models deterministic contract/capability enforcement without exposing raw Q/Phi state.
- Domain-specific failures use stable error-code semantics in `runtime_process.ds`.