# What to build: DockCheck

**Recommendation: one Open Track entry.** At the end of a receiving shift, DockCheck reconciles what was due with what was scanned. For unresolved differences, it checks the relevant handoff evidence and saves a morning review queue. It doesn't adjust stock, place orders, or send messages. This is the final planning recommendation, not a shipped product.

## Why this beat the alternatives

- **Autonomy and usefulness:** The agent completes a recurring job a receiving lead would otherwise do by hand: decide which lines need a recount and which need a split-delivery follow-up. It starts when a completed batch arrives and leaves one durable, evidence-backed result with no operator action in the middle. Counts remain verifiable independently of the model.
- **Reliability and practicality:** One local workspace, synthetic inputs, one SQLite writer, one decision that needs context. Missing data becomes a source hold, not an invented shortage. A judge can inspect the same queue after a restart and see that no duplicate task was created. This requires fewer moving parts than a browser runtime or an external inventory integration.
- **Why not Access Handoff?** It has a stronger visual moment, and we would choose it if its context-dependent interaction could reliably beat a scripted keyboard check. For this build, the extra browser setup and more subjective interpretation make it a riskier route.
- **Why not Deposit Draft?** It produces the most tangible artifact, with low infrastructure cost. But a well-maintained approved manifest already handles much of the proposed workflow. The incremental benefit depends on ambiguous handoffs that still contain enough verifiable provenance.

This comparison weights the [official rubric](https://agentwarehack.com/brief/#explain-full), not visual polish or hypothetical adoption. See the [expanded shortlist](07-expanded-idea-search.md), [finalist tabletop](08-finalist-tabletop.md), [other artifact ideas](09-beyond-review-queues.md), and [originality check](13-originality-check.md) for what was ruled out and why.

## The first proof to build

1. Build one complete synthetic shift end to end. When 20 are due and 18 are scanned, save the two-unit discrepancy in the local queue. If 18 were due and 18 were scanned, save no shortage. An absent or mismatched scan export is a separate hold.
2. Keep counts and due schedule fixed for two actual agent runs. In one, an in-scope record corroborates a later delivery; in the other, it doesn't. Verify the queue's category, the original variance, and the cited records, and compare with a strong typed baseline under the same evidence budget. If the model adds no useful judgment, fix this before adding features.
3. Demonstrate duplicate handling and a real stop while a result is pending. Independently inspect the destination for no late write. Keep the next action and source references visible; add no dashboard until this works.

Start with the [build contract](03-build-contract.md), the [evaluation plan](10-evaluation-design.md), and the [build and submission sequence](05-build-and-submission.md). The [reliability and video plan](04-reliability-and-demo.md) separates an authentic unattended demonstration from an explicitly labeled, inexpensive offline replay. No live operational data, product implementation, fixture runs, demo recording, or contest submission occurred in this planning phase.
