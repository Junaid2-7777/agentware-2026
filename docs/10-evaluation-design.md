# Evaluation design: can the agent beat the useful script?

An honest comparison, not an evaluation result. The [brief](https://agentwarehack.com/brief/) asks judges to verify what the agent did, not how plausible the story sounds. Test the decision the model is actually responsible for. Keep input validation, quantity arithmetic, permission checks, persistence, and ordered audit evidence identical across modes.

## Candidate comparison

- **Baseline A, generic:** Compute trustworthy discrepancies and write an explicit generic review for each. Missing or untrusted input becomes a hold. This establishes worker value without a model.
- **Baseline B, typed evidence:** Use exact receipt IDs, scheduled windows, and predeclared document kinds; query each permitted relevant source within the same limits as the agent. Queue a split-delivery review only when the later record supports it. This is the competitor to beat, not a brittle keyword straw man.
- **Agent:** Same fact computation, tools, budget, validation and write policy. Propose which evidence to gather based on the actual handoff, then a scoped next action. It cannot change a variance, rely on evidence it didn't fetch, or use narrative to widen access.
- **Access Handoff comparator:** A static scan and a scripted interaction keyed by the declared widget type are the two baselines. Do not give the agent credit for focus behavior already found by the scripted check; the extra job is choosing or deduplicating a meaningful check when component context differs.

| Receiving control | Exact expected behavior | What it tests |
| --- | --- | --- |
| 18 of 20 due; no contextual lead | Preserve −2; generic recount/review; no claim of a confirmed split. | Safe default, not an AI win. |
| 18 scanned, 18 due, 2 already due later | Create no shortage item. Do not classify via model. | Calculation gate; easy case must remain cheap. |
| 18 of 20 due, verified later shipment for the same receipt | Classify the one case as split-delivery review, keep −2 and attach the supporting record. | Typed baseline already succeeds on this one. |
| Same note and numbers, later shipment belongs to a different receipt | Preserve −2; generic recount/review, no confirmed split. | Entity grounding; similar prose is not evidence. |
| Handoff names two distinct receipt events by meaningful reference rather than formal ID; only one scoped check can resolve the disputed line | Choose the line's evidence source within budget and cite verified IDs; otherwise retain generic review. | Whether the model makes fewer unnecessary lookups or routes useful work beyond Baseline B. If typed data is sufficient, count it as a tie. |
| Clear positive case paired with unsupported/contradictory evidence | Positive case still writes; unsupported case holds that classification, not all work. | Separates reliability from refusing everything. |
| Missing required export, or stop wins before commit | Missing export: one hold, no shortage. Stop: zero new business tasks. | Host guarantees; outcome must not depend on the model. |

For Access Handoff, use a genuine modal, a nonmodal lookalike, and a correct modal as separate browser controls. Include two instances with verified shared component identity and one similar-looking but independent control. Pass criteria are correct observed focus trace, stable deduplication, and no unsupported standards claim. Compare exact case-level outputs and number of interactions, not subjective scoring of the issue wording.

## What the evaluator may know

- Freeze expected outcomes separately from runtime inputs. Avoid sentinel filenames or result-shaped labels leaking the answer; use neutral IDs. Swap identifiers and reorder rows in matched runs. Keep judge-editable inputs documented, with a clear difference between a legitimate revision and accidental malformed data.
- Record case ID, expected versus observed outcome, reason code, durable write count before/after, support evidence and tool/cost use. Capture whether the run was live, replayed, or a deterministic test. Mark not run and unsupported separately from fail or pass.
- Measure two benefits separately: **correctly supported next actions** and **useful outcomes per lookup**. A smaller call count is not a win if cases are missed or evidence becomes weaker. Judge setup, elapsed time, model calls and spend are measured in the build phase only.
- Decision rule: retain the agent if it has at least one legitimate, independently explainable improvement over the strong baseline without degrading count safety or required controls. If neither finalist shows one, revisit the assumptions before implementing more features.
