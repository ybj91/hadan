# HADAN MVP Plan

## Phase 0 — protocol sketch
- Define Agent ID, Host Profile, Capability Descriptor, UnitTask, Bid, ExecutionResult and Message Envelope.
- Specify authorization and execution side-effect classes before permitting remote shell or file modification.

## Phase 1 — two-peer execution
- Connect PC and VPS as peers using authenticated transport.
- Discover capabilities and basic host telemetry.
- Run a read-only unit on a remote peer and return a result.
- Persist task and attempt state using SQLite on each peer.

## Phase 2 — orchestration
- Implement Head + Tail decomposition (static demo first), local full/candidate/unable assessment, bid ranking and retry limits.
- Compare against simple fixed/rules-based routing.
- Implement at-least-once message delivery plus deduplication, avoiding claims of exactly-once side effects.

## Phase 3 — automation
- Replicate a schedule definition to three authorized peers.
- Assign one trigger peer at creation; its local database prevents duplicate logical runs after restart.
- When assigned peer is unreachable, record suspected missed trigger. Do not migrate automatically.

## Phase 4 — intelligence and user experience
- Add CLI channel and optional LLM as capabilities.
- Demonstrate a scheduled news summary / GPU task sent between nodes.
- Measure task latency, setup time, routing overhead, memory, token usage and task completion rates.

## Exit criteria (targets, not measured results)
- Set up two peers with one straightforward pairing flow.
- No LLM calls for known capability routing.
- Task history persists across restart.
- Deterministic safety and authorization checks on executor.
- Publish reproducible comparison against a baseline.
