# Four jobs with an output you can open

A design critique of the first rounds: too many ideas end in “file a review task.” That's a valid real action, but a completed draft artifact can be easier to trust and demonstrate. This round asks what can be produced locally, checked independently, and opened immediately after an unattended run. Nothing below is built or tested.

## 1. Caption Patch: fix a draft caption file after an edit

**Track:** Open. **Operator:** A video editor who already has captions and just received a revised cut. **Trigger:** A local draft-revision bundle arrives: old captions, new clip timestamps, and a short editor handoff. **Output:** A new versioned WebVTT file plus a diff and a review list, leaving the previous file unchanged. **End:** Atomically save one valid draft or stop with a specific unresolved mapping.

- **Agent decision:** Choose which short cue groups need review when there are two plausible alignment candidates, and look up neighboring timestamps and text. The deterministic writer validates chronology, overlap policy, track identity and candidate alignment before changing a cue. Do not invent acoustic observations from text or invent lines because a cue is missing. Uncertain regions remain untouched and are flagged.
- **Judge proof:** Show a caption before and after a simple trim, then a section where repeated spoken text makes the match ambiguous. A correct draft loads in a local player. A global-offset script serves as baseline; an edit-decision-list rebaser is the stronger baseline. If the latter can match every supported case, don't choose this build as an agent.
- **Tradeoff:** Strong visual output and easy onboarding for a creator. Avoid rebuilding transcription, audio inference, or a browser video editor. The tiny initial scope may not leave enough non-deterministic work; plausible fallback, not a winner without a counterexample.
- **Sources:** [W3C prerecorded captions guidance](https://www.w3.org/WAI/WCAG22/Understanding/captions-prerecorded) establishes what captions convey; [YouTube caption file workflows](https://support.google.com/youtube/answer/2734796) show that a separate file is a usable artifact. A timing repair is not a conformance claim or publication action.

## 2. Deposit Draft: assemble one reproducible research handoff

**Track:** Research & Study. **Operator:** A lab member preparing the handoff for one synthetic dataset revision. **Trigger:** A bundle with sample files, a plain-language researcher note, and an explicit allowlist arrives. **Output:** A fresh local draft directory with the right data, dictionary, evidence index, and integrity manifest. **End:** Write the staged artifact and verification report, or leave no release draft when a mandatory file or permission is unclear.

- **Agent decision:** Decide whether the note's phrase “analysis inputs” refers to the raw readings or a corrected export. Retrieve only the two catalog entries and their accompanying documentation, then resolve based on supplied scope and revision. An allowlisted, explicitly approved file is necessary even if the model is confident; never copy a file classified as sensitive or outside the synthetic workspace.
- **Judge proof:** In a second fixture with indistinguishable revisions, generate a refusal and leave the ready folder unchanged. Compare against packaging all allowlisted files and against an explicit approved manifest. If the manifest can already declare exactly what is required, prefer that baseline. The useful niche is assembling a handoff from incomplete, dispersed evidence within previously approved boundaries.
- **Tradeoff:** Better persisted output than a citation queue. Setup is small, but the payoff is not as easy to explain visually as an accessibility failure. Do not claim anonymization, consent, standards conformance, or submission to a real archive.
- **Sources:** [UK Data Service deposit preparation](https://ukdataservice.ac.uk/help/deposit-data/prepare-your-data-for-deposit/) documents validation and README needs; [BagIt RFC 8493](https://datatracker.ietf.org/doc/html/rfc8493) is background for useful manifests, not a promise of a compliant implementation.

## 3. Copy Desk: reconcile a form in a local training portal

**Track:** Browser Agent. **Operator:** A back-office worker who already has an approved record and wants its fields entered into a separate portal. **Trigger:** A synthetic signed-off revision appears. **Output:** A real saved draft in a local training app, not a screenshot or a copied text answer. **End:** Reopen the draft to verify persisted values and leave nothing final-submitted.

- **Agent decision:** Compare two contextual descriptions to choose which read-only help page explains an ambiguous label, then propose mapping from the limited schema. Host validates exact field constraints and checks source revision. Require the target draft ID, and never overwrite a field edited by a person since the last read.
- **Judge proof:** One normal save, one intentional near-duplicate with a different revision, and a changed-label counterfactual. Reopen the saved draft to verify exact values. Baseline is an explicit mapping per schema revision; if that suffices, don't ship a browser agent for this workflow.
- **Tradeoff:** The most obvious demonstration of real browser action, but you're building a second app just to demo the first, and fake forms can feel contrived. No application, payment, identity data, customer record, external browser destination or real submission.

## 4. Handoff Board: update a shared plan without silently moving commitments

**Track:** Life Admin. **Operator:** A small volunteer group preparing for a room booking or delivery. **Trigger:** A synthetic booking revision and handoff note land together. **Output:** Persist a versioned local board with only pre-authorized preparation tasks moved, and expose any source conflict. **End:** Commit the bounded plan, then stop; no message or real calendar write.

- **Agent decision:** Which relative reference in the note actually refers to the revised slot? Check the corresponding booking entry or leave the conflicting task untouched if it can't be resolved. Hard minimum intervals, time zones, owners and immovable events are host-enforced.
- **Judge proof:** Shift two linked prep tasks while preserving the volunteer's unrelated commitment and immutable venue slot. Compare against a rule-based scheduler with the same constraints; it already handles structured inputs. Test a trusted cancellation as distinct from a tentative note.
- **Tradeoff:** Useful day-to-day and a visible board change, but roster/privacy and scheduling rules can become a product before proving an agent. Only use synthetic data and one small group in the demo.

## Ranking consequence

Caption Patch has the strongest new artifact demo, and Deposit Draft has the lightest infrastructure requirements. Neither replaces DockCheck or Access Handoff on paper: each has a very capable deterministic baseline and depends on carefully chosen, realistic ambiguous cases. Keep both as comparisons, not additional builds. If either can demonstrate that its strong baseline leaves frequent useful work undone while the host still verifies every saved change, rerank before freezing.
