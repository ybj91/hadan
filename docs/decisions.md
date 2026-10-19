# Design Decisions (Draft)

| Decision | v0.1 approach | Trade-off |
|---|---|---|
| Peer roles | No permanent server/client hierarchy | Per-task coordinators still needed |
| Capability classes | Channel, LLM and device access as capabilities | Dedicated adapters implement different I/O modes |
| Planning | Head + Tail sequential decomposition | Parallel DAG workflows postponed |
| Task result | SUCCESS / FAILED / STOPPED | WAITING_INPUT is a nonterminal task state |
| Scheduling | Global definition replicas; single assigned trigger | Offline trigger may be missed; no automatic failover |
| Storage | SQLite + local files | No automatic strong global consistency |
| Replication | Selective metadata replication | Conflicting edits need explicit authority/version policy |
| Safety | Per-executor authorization and bounded delegation | Needs threat-model testing |
| Decision model | Optional, rules as fast path | Model bids need calibration |

## Open questions

1. What is the smallest interoperable wire-level contract?
2. Which membership/pairing protocol minimizes configuration burden?
3. How should schedule mutations be authorized and versioned while peers are offline?
4. What kind of workflow compiler, if any, should sit alongside Head + Tail?
5. What is the minimal useful mobile client given platform background limits?
