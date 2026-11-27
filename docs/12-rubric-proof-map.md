# Rubric proof map: what the judge can verify

[Agentware's official rubric](https://agentwarehack.com/brief/#explain-full) gives 55% to autonomy and usefulness together. That makes the core demonstration a job the operator no longer does manually, not the number of agents, integrations, or screens. These are proposed checks; none has been run.

| Official criterion | Evidence to capture after building | Evidence that would not count |
| --- | --- | --- |
| Autonomy, 30% | One continuous trigger-to-commit run, decision-dependent lookup, durable result, terminal status; zero operator inputs between trigger and completion | Manually selecting the case result or copying a model response into the destination |
| Usefulness, 25% | Compare the result to the exact handoff the operator would do; show an actionable next step, supporting evidence and what no longer needs manual searching | Generic report, invented customer impact, or benchmark against a script deliberately missing basic rules |
| Reliability, 20% | Benign pass, matched counterfactual, incomplete input, restart/redelivery, and honest supported/unsupported fixture outcomes | Treating inability to parse an input as a successful defense or reporting a simulated result as live |
| Engineering, 15% | Cold setup timed by a reader following the README; stable destination and evidence IDs; run works with documented dependency and model modes | A product only its builder can run, open credentials, or a hidden manual server setup |
| Demo, 10% | Show empty-to-persisted output in ≤3 minutes, ordinary positive case in the full real run, label any separate controlled stop | Hero animation, static prerecorded output posed as real interaction, or confusing the judge replay with the live run |

## One trace contract for three different products

Every run should answer six questions in a short readable trace: **what triggered it; which revision was accepted; what choice was made; which tool returned what evidence; what durable action occurred; why did it stop?** Put event and source IDs, terminal reason, and result reference in the trace. Include scrubbed arguments and observations, not raw prompts or private source material. A stable sequence counter is useful even when timestamps tie.

| Candidate | Easy yes case | One human-checkable result | Best honest differentiation |
| --- | --- | --- | --- |
| DockCheck | Compare due and scanned numbers, retrieve a relevant later-arrival record, preserve the variance and save the right task | Original receipt and record IDs appear beside one committed local case, no duplicate or adjusted stock | Shows useful evidence selection only if the ambiguous handoff beats or complements the typed-record baseline |
| Access Handoff | Open a scoped fixture, choose and perform a widget interaction, file one verified follow-up | Browser focus trace and preserved page revision support the saved issue | Visual and readily verifiable, but needs a case a scripted widget test wouldn't already catch |
| Deposit Draft | Select the approved dataset revision and stage the correct synthetic files | Open the new draft folder, verify manifest counts and hashes, inspect exclusions | Best artifact, but an explicit approved manifest solves the fully structured version; ambiguity must matter |

For the demo, keep the operator problem and real effect on the same screen, then give the judge a separate read-only result view if time permits. A demo cannot turn an otherwise unnecessary agent into a useful product.

## The four optional points require four observations

1. **Guardrails:** Show host enforcement on a benign disallowed action or invalid source. A prompt instruction alone is not evidence.
2. **Live monitoring:** Watch the current run in progress, not just inspect a log once it ends. Choose one display powered by the actual event stream.
3. **Kill switch:** Use a separate controlled pending operation; stop before its commit decision and verify no later result is written. Already committed work remains visible.
4. **Audit:** Starting from a saved result, independently reconstruct its trigger, evidence, tool outcome and policy decision. Verify the two claims “what changed” and “what never changed” in the actual destination.

Do not self-award points. A strong first build should make the yes case credible before spending on polish or optional sponsor integrations.
