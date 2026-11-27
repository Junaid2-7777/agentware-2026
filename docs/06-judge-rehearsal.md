# Independent design challenge and judge rehearsal

This is a tabletop exercise, not a recorded run. The numeric examples below are a proposed fixture and expected outcome. No warehouse data, pre-existing project, external accounts or organizer payloads are used.

## Check whether the workflow is worth automating

[GS1's receiving advice specification](https://www.gs1.org/sites/default/files/docs/eancom/s4/recadv.pdf) describes recording discrepancies after receipt. [Business Central receiving](https://learn.microsoft.com/en-us/dynamics365/business-central/warehouse-how-receive-items) and [purchase receiving](https://learn.microsoft.com/en-us/dynamics365/business-central/purchasing-how-record-purchases) already support receipt workflows, including exceptional quantities. So the pitch isn't “ERP can't do this.” It's a low-permission helper for a team that has a scanner export and a handoff note outside the system of record. Demand, willingness to use it, and minutes saved aren't yet measured.

One new alternative worth comparing was **FridgeWatch**, a cold-room shift exception agent. It aligns more directly with the official cold-room CSV, but room telemetry demands a defensible domain threshold, missing-sample policy, and a careful boundary between an observed excursion and a handling recommendation. If scored at 4/4/4/4/5, that's 82 out of 100. DockCheck still wins on operational clarity, source corroboration, bounded writes, and usability. If a supported official fixture doesn't map to receiving semantics, that is an honest coverage limitation, not a reason to bolt on sensors.

## A judge-controlled scenario

The judge can start from a freshly seeded workspace, let a complete synthetic batch arrive, and inspect the resulting database. The fixture has no dependence on the current date: the simulated shift ID, event time, and cutoff are not wall-clock time. Runtime deadlines use a separate monotonic timer.

| Receipt | Trusted expectation | Observed evidence | Expected persistent effect |
| --- | ---: | --- | --- |
| A / location 1 / item X | 20 each | 18 distinct accepted units; receipt closed | One recount task, difference −2, two source coordinates. |
| B / location 1 / item Y | 20 each | 18 distinct accepted units; a shipment fact confirms a second arrival window | One check-split-delivery task, difference −2; the note cannot close it or edit units. |
| C / location 1 / item Z | 20 each | 20; exact scan redelivery repeats one event ID with identical values | None. Count exactly 20. |
| D / location 1 / item X | 7 each | 8; complete records | One overage review, difference +1. Never aggregate with receipt A. |

Separate batch: no valid completion marker by its known cutoff. **One source-level hold, zero per-receipt shortages.** Separate conflict fixture: one ID reused with different values, distinguish this from C; isolate the affected scope without adding or choosing either conflicting event by guesswork.

Counterfactual: same numbers as B, but change the corroborating shipment fact to unknown or replace the match with another receipt. B must become recount/unclassified review, never a confirmed split. Change order of rows or repeat the complete batch; outcome and active task count must remain stable. A newer verified marker with distinct evidence is a deliberate revision, not a redelivery; it adds history without duplicating the active task. Keep manual resolution intact.

## Show that the agent adds value

[Anthropic's agent design guidance](https://www.anthropic.com/research/building-effective-agents) distinguishes predetermined workflows from systems that dynamically choose tools. Use a workflow for arithmetic and writes. The model can select the next evidence lookup from bounded tools, or decide there is not enough evidence within the budget. Compare three paths on the same novel handoffs:

1. Deterministic baseline: count and queue a generic exception.
2. Agent: choose whether to retrieve a second relevant record and propose a supported next action.
3. Counterfactual: remove/replace the corroborating record and assert a safe change to the queue item, without editing quantities.

Report correct routing, evidence citations, duplicate tasks, completion and error reasons, missed valid work, wall time, and model calls/cost. Use measured values and explicitly label the synthetic sample. If the agent does not beat the baseline on any meaningful case, improve evidence selection before adding features; don't claim a win. No external benchmark, customer validation or pass rate is implied.

## Make stop observable, not cosmetic

The durable commit is the point of no return for a completed batch. Serialize cancellation intent and the final commit decision at the writer. If stop wins, roll back any uncommitted state and do not enqueue or retry. If commit already won, stop later work, keep the saved batch, and say it committed before cancellation rather than saying it rolled back. Enforce a maximum wait and log the stop acknowledgement. The local client may abort a request without being able to prove the remote service stopped compute or billing, so claim only the behavior observable locally. [SQLite transaction semantics](https://sqlite.org/lang_transaction.html) justify the atomicity of the local writer, not any remote guarantee.

Commit gate requires an active run generation, in-scope batch, validated evidence IDs, current operator configuration version, and no outstanding stop. Log the decision without leaking raw provider payloads. Run two observable stop tests with an isolated slow test adapter: before write (zero rows), after confirmed commit (only the already committed rows). Show one stop in the video and both in the test record.

## 15-minute judge checklist

- Minute 0–3: Confirm sample inputs and expected result; install only what the README names.
- Minute 3–6: Start the judge mode, watch local writes, inspect output and actual trace; expose whether the model was live or replayed.
- Minute 6–9: Try the second batch plus duplication; judge observes a legitimate result change and no duplicates.
- Minute 9–12: Run one controlled interruption and inspect terminal status / committed state.
- Minute 12–15: Open evidence report and limits; clearly distinguish official fixture runs, synthetic checks, unsupported formats and results not yet measured.

If no-credential mode is replay-only, make that obvious and include a clean live path with tested model availability and cost. A reviewer who cannot afford or configure live mode should still be able to reproduce local tool and policy behavior, but replay is not an independent confirmation of live model judgment.
