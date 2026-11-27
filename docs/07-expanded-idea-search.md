# Reopened shortlist: what would you actually leave running?

This second round starts from the [Agentware brief](https://agentwarehack.com/brief/#explain-full), not from a favorite product. The brief rewards a narrow agent that takes a real action with a real tool, completes an unattended run, and can be inspected afterward. It does not give one track a scoring advantage. These are design candidates, not builds or test results.

## Most important filter

For an idea to advance, write down **who needs what completed, when it starts, what gets durably changed, why choosing a tool depends on evidence, and when it stops**. If the outcome is a chat reply or static report, or the same small rule solves every case, don't stretch it into an agent just to enter. If a proposed action has consequences a judge shouldn't have to accept, scope the job to a useful sandbox action instead of simulating the consequences or silently asking permission halfway through.

| Concept / track | Trigger, real action and stop | Decision the agent earns | Strongest objection |
| --- | --- | --- | --- |
| **Access Handoff / Browser Agent** | New version of a local fixture site → browser checks the changed pages and creates a prioritized manual verification queue with selectors and evidence → exits once queued, within a page and time budget. | Decide whether to examine keyboard behavior, accessible name, or nearby context for a concrete finding; distinguish one recurring component from unrelated issues. | A linter already flags many cases. Needs a real contextual interaction the linter cannot resolve, without claiming WCAG conformance. |
| **Citation Drift / Research & Study** | A bibliography gets a new version or the status snapshot changes → update an annotated local bibliography and mark impacted notes for re-verification → stop at the bounded set of affected references. | When a referenced result has changed, select the relevant section of the correction vs the quoted claim; don't claim all notes using that DOI are invalidated. | A DOI/status watcher is deterministic. Needs evidence that claim-level routing is useful and the source set can be judged without external access. |
| **Shift Cover / Inbox & Calendar** | Incoming absence in a fixture inbox → write a tentative block into a local test calendar for one eligible shift cover candidate → stop; never send an invite. | Identify which handoff clarification or roster fact is needed from the fixture to disambiguate the shift. Hard constraints remain deterministic. | Team consent, availability privacy, and time-zone correctness are substantial burdens. A synthetic calendar write is real, but does not demonstrate a staffing solution approved for live use. |
| **Release Handoff / Developer Workflow** | New release-candidate fixture arrives → persist a release-readiness checklist with a specific owner and evidence per item → stop after the checklist is committed. | Choose the next local evidence source based on contradictory changelog, CI summary, or manual test handoff; verify what passed on this exact candidate. | Generic CI documentation already covers access to run logs. Must add cross-source resolution without running untrusted code, changing branches, tagging a release or claiming compatibility. |
| **Grant Gate / Life Admin** | New opportunity bundle appears in a sandbox catalog → append a source-linked eligibility review entry and a local review reminder draft → stop without submitting. | Choose which eligibility clause or amendment resolves a contradiction in the fixture application profile. | False eligibility wastes effort. Criteria may be unambiguous enough for a rule; application preparation is not the MVP. |
| **Menu Revision Hold / Open** | New supplier spec appears → place the affected fixture menu items into a private verification queue → stop without editing an allergen declaration. | Resolve which old packaging/spec revision maps to the recipe and when to escalate an ambiguous change. | Safety-critical interpretation and potential reliance are disproportionate for a weekend demo. Reject; even a plausible hold queue should not imply an allergen decision. |
| **Room Turnover / Open** | New room turnaround handoff and booking fixtures → assign a bounded local inspection task list and flag conflicts → stop at a single facility's next block. | Decide whether a note concerns the next room assignment or the outgoing room; select the right corroborating occupancy/staging record. | Hard to show that this beats simple schedule rules; examples have to expose useful, objective divergence. |

Evidence of the recurring workflows, not of demand for these ideas: [W3C on the limits of automated accessibility evaluation](https://www.w3.org/WAI/test-evaluate/), [Crossref on deposited corrections and retractions](https://support.crossref.org/hc/en-us/articles/115000501246-Crossmark-registering-updates), [GitHub Actions workflow run tools](https://docs.github.com/en/rest/actions/workflow-runs), [Grants.gov applicant eligibility](https://grants.gov/learn-grants/grant-eligibility), and [UK government guidance on updating allergen information](https://www.gov.uk/running-food-business/allergies). Policy and domain references are research only; none authorizes running this on real accounts or data.

## Four finalists: same judge budget, same standard

Scores are comparative estimates (1–5 per the [official rubric](https://agentwarehack.com/brief/)), not actual performance. Weighted total = 6×autonomy + 5×usefulness + 4×reliability + 3×engineering + 2×demo. Score assuming the smallest credible version, not a polished future product.

| Finalist | Autonomy | Useful | Reliable | Engineering | Demo | Total | What changes the decision |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| DockCheck | 5 | 5 | 4 | 4 | 5 | 93 | If corroboration never changes a real routing decision, it is a reconciliation script, not a winning agent. |
| Access Handoff | 5 | 4 | 4 | 4 | 5 | 88 | Can win on visual evidence and reproducibility if the fixture proves a real keyboard/intent decision beyond a static scan. |
| Citation Drift | 4 | 4 | 4 | 4 | 4 | 80 | Can rise if one corrected finding affects multiple notes differently and the judge can see why without trusting model-generated citations. |
| Release Handoff | 4 | 4 | 4 | 5 | 3 | 81 | A practical fallback; unfamiliar judges may need more explanation, and routine checks should remain deterministic. |

The earlier 96 for DockCheck was a best-case design estimate. Its engineering score is 4 here because manifest verification, schedule handling and cancellation still need to be built and demonstrated. At autonomy 4 instead of 5 it drops to 87, below Access Handoff; treat the novelty test as a genuine decision gate.

## Pair every showpiece with an honest control

- **DockCheck:** 20 due, 18 scanned, later delivery corroborated versus 18 due and 18 scanned. The first pair tests schedule math. Hold the schedule and scans fixed for a second pair, and remove the later-arrival record; that tests whether the agent chooses a different, grounded next step.
- **Access Handoff:** Two repeated instances of the same component and one visually similar but differently functioning control. A run should produce one grounded component task where applicable, and not conflate the distinct control. Report keyboard observations separately from a WCAG verdict. Use local synthetic pages only.
- **Citation Drift:** One corrected table value referenced by two notes, one note relying on the changed value and one relying on unaffected context. Retain both source links and the prior status; queue only the impacted note if evidence supports that conclusion. Ambiguous notes go to explicit review, not removal.
- **Release Handoff:** A successful earlier CI run and a failing newer candidate. Persist the correct owner/action for the revision that is actually up for release. Swapping the candidate revision must change the result without running a workflow.

## Different eyes

- **Operator:** Which item will I act on tomorrow, and why? DockCheck's quantity, source row and next action are easier to scan than broad troubleshooting. Accessibility work is close when the task includes the browser evidence and an owner.
- **Judge:** Does the result change if I change one meaningful input? DockCheck and Access Handoff both have visible tests; the latter is more immediately visual, the former has a stronger deterministic correctness oracle.
- **Usability reviewer:** Can I see the saved change without a login? Require a one-screen queue and one detail/trace view. CLI and a readable fixture are enough; optional UI must not become a prerequisite.
- **Reliability reviewer:** Can I observe a safe refusal or stop without making it a no-op product? For each finalist the output persists in a manually inspectable local destination; the runtime cannot send a message, release anything, certify compliance or mutate a real system.

**Working recommendation, not the final sign-off:** DockCheck still leads under the event's weighted rubric. Access Handoff is the credible challenger, not a token backup. Before declaring a final choice, compare the exact tool sequence and demo for those two, and red-team each with an ordinary incomplete input and an ordinary valid case. No project code or entry submission in this pass.
