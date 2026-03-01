# runtime_bridge

- Source: `xdv-runtime/src/runtime_bridge.ds`
- Kind: Runtime Module
- Summary: Boot/userspace bridge with ABI assertion and runtime call-path probes.

## Purpose
Bridge module used by kernel boot flow to initialize runtime services while preserving existing bridge contract compatibility.

## Contract
- `runtime_bridge_version()` remains `5`.
- Init path asserts HR-ABI major/minor compatibility.
- Init path probes:
  - capability/contract-aware runtime call path
  - replay hook readiness
  - telemetry hook readiness

## Key Procedures
- `init()`
- `start_userspace()`
- `bridge_runtime_init()`
- `bridge_runtime_main()`
- `runtime_abi_contract_assert()`
- `runtime_contract_capability_call_probe()`
- `runtime_replay_hook_online()`
- `runtime_telemetry_hook_online()`
- `shell_bootstrap()`

## Integration Notes
- Designed for codegen-safe boot runtime usage.
- Emits deterministic status logs for ABI and hook activation milestones.