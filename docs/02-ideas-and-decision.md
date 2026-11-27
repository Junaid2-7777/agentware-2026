# Ideas and decision

Baseline: one capable solo builder, no new vendor accounts, 72-hour contest clock but a much smaller practical build budget. Scores are design estimates (1–5), not measured outcomes or judge forecasts. Weighted total is the sum of weights times rating divided by five; safety bonus excluded.

| Candidate | Track | Autonomy 30 | Useful 25 | Reliable 20 | Eng 15 | Demo 10 | Score |
| --- | --- | ---: | ---: | ---: | ---: | ---: | ---: |
| DockCheck: receiving exception queue | Open | 5 | 5 | 4 | 5 | 5 | 96 |
| Evidence Ledger: weekly reading/citation queue | Research & Study | 4 | 4 | 4 | 4 | 4 | 80 |
| Inbox Handoff: route unanswered service requests to a sandbox queue | Inbox & Calendar | 4 | 4 | 3 | 4 | 4 | 76 |
| CI First Aid: assign an owner and file a diagnostic work item | Developer Workflow | 4 | 4 | 4 | 4 | 3 | 78 |
| Quote Compare: supplier quote watch with local purchase shortlist | Browser Agent | 4 | 4 | 3 | 3 | 4 | 73 |

## Five competing pitches

- **DockCheck:** After receiving closes, compare expected goods, actual scans, and shift handoff. Create one evidence-backed review or recount task for each unresolved discrepancy in a local work queue. Buyer: operations lead at a team working across exports and handoff notes. Failure risk: false shortfall from an incomplete feed; solve with an explicit completion signal and hold ambiguous cases.
- **Evidence Ledger:** Keep a research reading queue and a weekly brief with provenance, deduplication, and correction history. Useful but easy to mistake for a familiar summarizer; duplicate/withdrawal handling and storage must be demonstrably real.
- **Inbox Handoff:** Sweep a test inbox for unowned operational requests, route them to a local work queue and draft replies. Legible, but Gmail OAuth and unattended permission boundaries erode the sprint. Keep it independent of people's real inboxes if revisited separately.
- **CI First Aid:** Classify ordinary build/format/test failures into a sandbox triage queue, without changing branches or source. Familiar workflow with strong tests, but close to generic developer tooling; no reuse of previous projects. Avoid executing untrusted code.
- **Quote Compare:** Compare approved fixture supplier listings and persist a shortlist with supporting quotes and constraints. Browser adapter work and evidence freshness could overwhelm the useful result. Neither cart changes nor financial actions are needed or permitted for this design comparison.

## Four perspectives

- **Operator:** DockCheck is only worth using if it shortens the morning handoff. Show the line, expected-versus-received, source records, and next step in one row. The operator cannot be asked to reinterpret a model essay. Evidence Ledger produces a similar queue, but does not demonstrate operational urgency as clearly.
- **Judge:** DockCheck's difference is visible in one run: a real queue write, a deferred discrepancy that would otherwise be a false positive, and no change to inventory. Your own fixtures must distinguish success from canned behavior.
- **Usability reviewer:** One command, no login, a status and a reason for each case, keyboard-accessible actions, plain-language statuses, focused defaults. A dashboard does not save an unclear record shape.
- **Engineer:** Keep business identifiers, unit conversions, deduplication and storage outside the model. Limit agent decisions to fetching evidence and choosing a constrained review category. If the same one-line deterministic rule covers every case, demonstrate why the free-text handoff evidence changes the task or cut the model's responsibility further.

## Existing tools and the gap

[Odoo inventory adjustments](https://www.odoo.com/documentation/18.0/applications/inventory_and_mrp/inventory/warehouses_storage/inventory_management/count_products.html) already supports physical counts and reasoned adjustments; [Shopify inventory adjustment history](https://help.shopify.com/en/manual/inventory-and-locations/adjusting-inventory/adjustment-history) records stock changes. Don't pitch either feature as novel. DockCheck is the step **before** someone adjusts stock: reconcile multiple exports plus a current handoff and assign a review task with source evidence. No ERP integration is promised.

## Decision

**Initial pick: DockCheck, Open Track.** See the [reopened shortlist](07-expanded-idea-search.md) for the current comparison. It fits a small operator workflow, has a visible real side effect with no financial or inventory write, and can be judged offline. It borrows domain familiarity, not source code or data. The 96 estimate is upside, not certainty: reducing autonomy and usefulness to 4 makes it 85. If evidence is too weak to justify classification, retain the same project and scope to fewer exception types rather than pivoting or pretending. The final build scope is in [03](03-build-contract.md).
