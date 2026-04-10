# runtime_process

- Source: `xdv-runtime/src/runtime_process.ds`
- Kind: Runtime Module
- Summary: Hybrid Runtime ABI bindings, capability/contract-aware call layer, replay/telemetry hooks.

## Purpose
`runtime_process` provides the process/domain ABI surface required for hybrid user-space execution:
- Process context + lifecycle validation
- Capability and resource contract handle validation
- Explicit cross-domain call validation (`runtime_xdv_call`, IPC, transition)
- Replay override hooks and deterministic telemetry/event emission

## Key APIs
- ABI and features:
  - `runtime_abi_init()`
  - `hr_abi_version_major/minor/patch()`
  - `hr_abi_feature_flags()`

- Capability handles:
  - `pack_capability_handle(...)`
  - `capability_handle_domain(...)`
  - `capability_handle_flags(...)`
  - `capability_handle_raw_id(...)`

- Resource contract handles:
  - `pack_resource_contract_handle(...)`
  - `contract_is_active_at(...)`
  - `validate_contract_for_target(...)`

- Process context:
  - `pack_process_context(...)`
  - `process_context_*` accessors
  - `runtime_create_hybrid_process_context(...)`

- Cross-domain runtime calls:
  - `runtime_bind_process_domain(...)`
  - `runtime_transition_request(...)`
  - `runtime_xdv_call(...)`
  - `runtime_send_cross_domain_ipc(...)`
  - `runtime_syscall(...)`

- Replay and telemetry:
  - `runtime_record_event(...)`
  - `runtime_emit_telemetry(...)`
  - `runtime_apply_replay_outcome(...)`

## Compatibility Wrappers
Legacy process wrappers are retained with parser-safe names:
- `spawn_process(...)`, `join_process(...)`, `exit_process(...)`
- `get_pid()`, `sleep_process(...)`, `yield_process()`
- `spawn_process_with_limit(...)`, `validate_pid(...)`

## Error Model
Includes deterministic runtime-domain errors:
- capability/contract invalid or unauthorized
- transition rollback
- domain unauthorized
- decoherence/coherence violations
- replay/telemetry invalid signaling

## Integration Notes
- Q/Phi calls require active contract handles in target domain.
- Capability flags are enforced at every call boundary.
- Replay mode can deterministically override runtime outcomes without changing call flow.