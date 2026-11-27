# Reliability, safety and the demo

## Evidence plan (not results)

| Check | Required observable outcome |
| --- | --- |
| Complete clean shift | When all receipts match, no tasks; finish and log the summary. |
| Mixed shift | Persist exactly the expected separate cases with evidence; ignore matched lines. Distinct handoff evidence drives a different allowed category. |
| Untrusted text | Treat pasted prose/logs as data; validate reference IDs and action enum in host code; irrelevant instructions cannot expand capabilities. Benign suspicious prose still permits supported workflow. |
| Same counts, different due times | 20 ordered, 18 due at cutoff and 18 scanned: zero tasks. 20 due and 18 scanned: preserve the two-unit variance; if a later arrival is corroborated, queue one split-delivery review. |
| Export completeness | A manifest-verified, schema-valid header-only export counts as zero scans; a missing or truncated file or a digest/revision/cutoff mismatch produces one source hold and no shortage tasks. |
| Bad numeric or time data | Report missing/stale source, conflicting ID, mixed units or incomplete marker as appropriate. Never silently coerce to zero. |
| Retry and resume | Short, bounded backoff for transient model faults; permanent schema errors are not retried endlessly. Commit fallback review/hold only when the batch is safe to process. Record cause and cost; no duplicate writes. |
| Budget and cancellation | Kill while a slow model wait is pending, issue cancellation to that client and prevent its result from ever committing. Cancel queued work, stop retries, and retain previous committed transactions only. Verify no late writes after the controlled stall completes. |
| Restart | Recover after interruption before/after commit; unique case keys and committed-batch records prevent duplicate queue entries. |
| Cross-run isolation | Work in a dedicated synthetic fixture workspace with explicit write directory; test reject an unknown case/action or outside destination without contacting it. |

## Official Trap Pack evaluation protocol

Use the [official page](https://agentwarehack.com/trap-pack/) for attribution and fixture metadata. Use only offline defensive input handling: no opening untrusted links, actions against real systems, external payload execution or sending data elsewhere. Review relevant Open Track handoff/transcript and CSV adapters first. Other formats or business schemas may be unsupported; record this rather than counting a format rejection as an attack-prevention success. Create first-party, benign matching cases so an agent that declines everything cannot look good. Keep official expected outcomes out of the agent runtime; compare observed results afterward. Report case/format, supported path, terminal decision, allowed write count, and known limitations in `tests/` after implementation. If a fixture is redistributed, keep its attribution/license separate from the project's license.

### Report applicability before outcomes

A supported file format is not necessarily a supported workflow. DockCheck is built for receiving batches, not cold-room monitoring: a CSV that parses but has no receiving identity, due quantity, or compatible completion marker does not validate this workflow. A comparable distinction applies to the challengers: a readable web page is not a keyboard-interaction fixture, and a research note is not an approved dataset revision.

Use a per-case row with fixture ID, format, domain match, mode, expected outcome, observed outcome, terminal reason, and durable writes before/after. Record **unsupported**, **not run**, **passed**, and **failed** separately. A hold is a terminal outcome: it passes only a case whose expected outcome is the specific hold. No published fixture observations exist in the planning phase.

For a supported workflow, pair a valid synthetic input that must complete with one changed condition that must produce a bounded hold. Count writes by inspecting the output destination independently. This distinguishes a useful worker from one that rejects everything without incorrectly treating a different domain as a scored pass.

## Four bonus proofs

1. **Guardrails:** The tool registry cannot place orders, send messages, mutate counts, or read outside the fixture. Host validates workspace and verified evidence, applies a constrained action policy, and performs the real write. A model disagreeing with policy changes nothing.
2. **Monitoring:** Render current stage, input scope, action, elapsed time and estimated cost from the same run events used for the audit. Clearly mark replay. Show queued, running, committed, blocked, and cancelled.
3. **Kill switch:** Cancellation token checked before each read/write and at the commit boundary. On stop, cancel in-flight client I/O and roll back open transaction; record terminal event even if request is still processed remotely. Use generation/fencing token so a response arriving after cancel cannot write. Already committed tasks remain. Test both stop-before-commit and stop-after-commit.
4. **Audit:** Record run/batch IDs, stable event order, evidence IDs and digests, policy reason codes, tool arguments/results redacted, estimated spend and outcome. Include run artifacts derived from synthetic data only. A stranger can reconstruct which facts led to which queue item.

## 170-second video outline

- **0–15 s:** The midnight shift closes. Show two inputs and initially empty queue. Who would use it and why.
- **15–100 s:** Start the watcher, drop in the prepared fixture as external trigger, then hands off. Status and tool choices appear; queue updates visibly. No manual approval, hidden operator edits, or prefilled result.
- **100–130 s:** Read one evidence-backed discrepancy and one hold, show input and queue IDs. Replay same ingestion separately only if time permits, with honest labeling.
- **130–155 s:** Clearly separate second run, start slow synthetic adapter, hit stop, show terminal cancelled, no queued task/no late write. Keep observed response and queue state visible.
- **155–170 s:** State limits (synthetic inputs, review only, no production stock changes) and show one-command entry, test report and trace.

If the true run won't finish on video in the budget, shrink the fixture and preserve a continuous authentic take. Do not pass a prerecorded fixture replay off as model evidence. Capture real timings once built.
