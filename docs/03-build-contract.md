# DockCheck: selected design

**One line:** DockCheck turns the overnight receiving mess into a morning review queue, without touching stock or placing an order.

**Track:** Open. **Operator:** Receiving or inventory lead at a small warehouse that has separate expected-receipt exports, actual scan exports, and an informal shift handoff. **Trigger:** a complete batch arrives in a local inbox before the morning shift. **Output:** persistent tasks, a concise shift brief, and an auditable timeline. **Not a target:** general stock management, forecasting, voice recording, procurement, ERP sync, warehouse control, real personal data, or commercial deployment.

## What the run actually does

1. Detect a new batch with a trusted receipt marker. Import expected and observed records, timestamp and schema-check each file; reject malformed rows, retain evidence, and mark gaps. Unrecognized material is quarantined from processing; do not open linked destinations.
2. Reconcile per receipt + SKU + location over the same completed shift. Count scans once by source event ID, distinguish identical redelivery from conflicting duplicates, and never treat a missing receipt feed as zero received. Only previously configured exact item aliases and units map automatically.
3. For unresolved rows, the agent sees trusted facts plus explicitly untrusted handoff excerpts and chooses bounded evidence lookups. It returns a proposed reason, next step, and evidence IDs. A validator checks the bounded proposal and evidence before the only write tool used by the agent can queue a case.
4. Write append-only or idempotently upsert the task in local SQLite and generate the brief from persisted rows. A note that says a shipment will arrive later can change the classification to check split delivery, but cannot change a count or silently resolve a discrepancy. Unrecognized claims become review tasks. All actions run unattended in the default scenario.
5. Stop when the batch is committed, cancelled, timed out, or gated. Record a terminal state. Restart safely after a crash; repeating a completed batch must not duplicate tasks. Keep the observer readable after the run.

## Data contract

- Trusted operator settings: workspace ID, cutoff, timezone (fixture UTC; configurable), allowed integrations, case thresholds and decisions. The checked-in demo never suggests credentials or production permissions.
- Baseline receipt: receipt ID, SKU, location, quantity, unit, expected date/window. Event: ID, receipt ID, SKU, location, counted quantity, unit, UTC time. Batch receipt marker authenticates the local test stream by mechanism/configuration, not by any statement inside the CSV or note.
- Quantity comparisons use validated decimal or integer units; prefer integer base units for MVP. Do not guess a unit conversion, infer a missing count, or compare snapshots with different cutoffs. Store readable source coordinates, file digests, and decisions, not unrestricted input excerpts.
- Case types: `recount`, `check_split_delivery`, `investigate_overage`, `source_incomplete`, `conflicting_records`, and `unclassified_review`. No automatic closure from prose. State machine: observed → validated → task proposed → committed; blocked/cancelled are terminal per run, with retry a new logged attempt.
- Idempotency: unique canonical case key from workspace, shift, receipt, location/SKU, and stable discrepancy family. Update evidence only under a controlled newer observation; preserve manual operator decisions. Transactionally commit cases, event summaries, and the batch marker, or leave no partially committed queue state. Output refresh is derived from those rows so a failed render never reruns writes.

## Minimal architecture

| Component | Choice and rationale |
| --- | --- |
| Runner | Python 3 and SQLite; stdlib CSV/JSON/time handling. One process coordinates bounded runs. Ship no mandatory external service. |
| Sandbox | Local directory with synthetic feeds; SQLite is the actual destination. No email, shell tool, arbitrary path, inventory API, supplier endpoint, or network browser available to the agent. |
| Agent/model | Provider adapter limited to one explicitly configured model endpoint for synthetic demo data; structured, validated proposals only. Decision example: confirm arrival window before choosing recount vs split-delivery review. Set model version/tier/cost in AGENT.md when known. |
| Judge experience | Fast credential-free replay from a real trace, exercising the actual local writer; explicit replay badge. Separate live mode is required for the authentic agent demo. A canned deterministic classifier is a separate fallback/baseline, not evidence of model autonomy. |
| UI | Terminal-first live status/tail, human-readable queue and trace. Tiny local read-only queue view only after core gates. One stop action available without navigating. |
| Risk limits | Fixed allowlist and output schemas; cap at 20 items, two model calls per ambiguous case and an overall run limit; budget no more than USD 0.10 as a proposed live-run cap, enforce before requests after validating provider pricing and token bounds. Zero payment, notification, or stock-write capability. |

## Acceptance before polish

- A clean laptop starts the fixture and sees a saved queue in under 5 minutes target; contest limit under 15. No personal account.
- On a receipt expected for 20 and actually scanned 18 from a complete batch, persist a two-unit discrepancy with case reason/evidence. In a distinct case, confirmed late split context changes the case kind. Balanced lines create no task. A missing or inconsistent source creates one source-level hold, not a storm of SKU tasks.
- Replaying identical input twice keeps count steady. New simulated batch produces a different correct decision. Controlled interruption leaves no late task and records what was cancelled. Models never receive secrets.
- Demo conclusions must identify synthetic conditions and measured values; no claim of real warehouse validation. Cut hosted integration, dashboard and extra tracks before cutting reproducibility.
