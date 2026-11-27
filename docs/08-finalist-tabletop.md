# Finalist tabletop: DockCheck vs Access Handoff

Planning exercise only. Durations are design allocations, not measured runtime. No browser fixture, live model, or external system was used for the run designs below.

## DockCheck: the shift has ended but the discrepancy isn't self-explanatory

**User:** An inventory lead opens the morning queue before adjusting anything. Today they must decide which discrepancies deserve a recount and which need a follow-up on a split delivery. The job is preparing that queue, not counting boxes or certifying stock.

- **Trigger:** A trusted done manifest arrives for a specific shift revision. Receipt schedule, scan export and handoff are all present. A shortened fixture has one balanced line, one shortfall and one second shipment record.
- **Observed path:** Validate exports → count and calculate variance → model chooses to inspect the shipment against that receipt and time window → validator verifies the record → local writer saves a split-delivery review with the original variance → terminal summary.
- **Contrast:** Keep due quantity, scan records and note unchanged; in one fixture the shipment record matches the affected receipt, in the other it belongs to a different receipt. The lookup should still happen, but the second has no corroboration and the resulting review must say so. A different case with no later-shipment lead must not need an extra lookup.
- **Hold:** The manifest is present but a required file is absent. Stop before calling the model for affected work, save one source hold and no shortage tasks. A verified header-only scans file is explicitly different.
- **Proof beyond the baseline:** Compare against (1) arithmetic plus generic tasks and (2) a simple always-look-up rule. A bounded agent only earns its complexity if it routes an ambiguous fixture correctly or saves a needless lookup while retaining support and correctness. Do not compare only to a deliberately weak baseline.
- **Workflow fit:** A shift cutoff and one queue entry are familiar even without warehouse experience. Existing ERPs handle stock and backorders; the demo should visibly show the hard part of reconciling cross-source handoff evidence before touching ERP. Customer demand remains unvalidated.

## Access Handoff: a release check has a real browser job, not a compliance badge

**User:** A frontend release owner needs actionable manual follow-ups when a changed interactive component fails a small keyboard check. The job is creating deduplicated follow-ups with proof, not certifying accessibility or editing production.

- **Trigger:** A local sandbox “candidate build ready” record names a fixed set of fixture URLs. The fixtures are hand-authored, network-free, and contain no real sessions, credentials, user data or remote redirects.
- **Observed path:** Open one scoped fixture page → read the control description and role → select a keyboard check appropriate to its declared interaction → observe focus before and after → persist one issue with route, stable selector, observed sequence, expected behavior and proposed verification step → close browser and stop. A second instance of the same component adds evidence rather than another task.
- **Concrete contrast:** In two instances of a genuine modal, the expected behavior is that focus remains within while open. A visually similar disclosure is not modal and should not be held to that rule. Include a positive-control modal that behaves correctly. Use the [W3C modal pattern](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/#keyboard-interaction) as a reference for scope, not a blanket judgment or legal claim.
- **Hold:** The release manifest names pages not present in the fixture. Mark coverage incomplete; don't claim the release passed. Limit instance count, dialog depth, browser commands and elapsed time.
- **Proof beyond the baseline:** Compare against an ordinary static scan and a small scripted check keyed by control type. The scripted control-type check likely beats the model when markup is explicit. The model only helps if it identifies a legitimate, documentable verification choice when the component pattern or repeated instance is ambiguous. Otherwise do not use a model to rubber-stamp the scripted result.
- **Workflow fit:** Strongest visual demo: show focus movement and then the saved task. Weaker clean-start cost: a browser runtime/packaged fixture must be genuinely proven on an empty machine. A transcript or screenshot alone cannot verify keyboard behavior. The judge replay cannot substitute for the live local browser path.

## Decision gate

| Litmus test | DockCheck | Access Handoff |
| --- | --- | --- |
| Is the useful baseline strong? | Yes. Arithmetic and generic exception queue can ship without AI; model must resolve or clarify the handoff. | Yes. A scripted focus interaction may cover the entire useful MVP; model must improve context-sensitive selection. |
| Can judge recompute truth? | Counts, cutoffs, and corroborating IDs can be compared directly. | Event sequence is observable; correctness still depends on interpreting intended component behavior. |
| Is guardrail visible? | Show only local writes, stop during a pending lookup and verify no late change. | Show restricted local navigation, no external destinations and browser stop with no later issue creation. |
| What could sink it? | Agent shown doing nothing but classifying preloaded prose; missing-export behavior creates fake shortages. | Agent appears as an accessibility linter wrapper; browser setup fails; findings overclaim standards. |
| Lowest-cost first build after planning | One verified synthetic batch and one committed case, then evidence choice. | One real local page with two controls, one reproducible keyboard issue and one durable follow-up. |

Both concepts fit the [same official scoring rubric](https://agentwarehack.com/brief/). DockCheck remains the working lead because its expected result is easier to prove and its judge path has fewer dependencies. Access Handoff is a genuine runner-up because the browser interaction is easier for a stranger to see. Choose neither based on how attractive a dashboard might look. The strongest winner case is a real unattended run, a control that changes the correct outcome, a visible stop without late writes and a small clean install.
