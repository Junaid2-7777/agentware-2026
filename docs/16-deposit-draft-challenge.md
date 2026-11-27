# Challenger deep dive: Deposit Draft

Can a finalist that finishes a usable artifact beat a workflow that creates review tasks? This is an independent design, not a second build or tested claim.

**Job:** Assemble the correct local handoff for one research dataset revision after a correction, even when the curator's plain-language note does not use the file names in the catalog. A recipient can open the resulting folder, verify it, and rerun the analysis preparation without asking which files belong together. It is a draft handoff, not anonymization, certification, or publication.

## Actual run

1. A trusted synthetic catalog revision and a handoff packet arrive in one workspace. The catalog names allowed sample file IDs, versions, and data-dictionary compatibility. A handoff sentence may identify a needed correction but never authorizes access or release.
2. Planner chooses one or two scoped reads from the candidate descriptions and data dictionary. It returns proposed file IDs, never source or output paths. The host verifies membership, compatibility, the exact source checksums, and any trusted instruction that pins a revision.
3. The writer stages the selected files plus a concise index and integrity manifest. Inspect the folder independently, then make the staged draft visible as a single version. If the input is ambiguous or checks fail, only a hold exists; don't expose a ready-looking folder. Same revision and approved content on rerun produce the same file set.
4. Record what was included, excluded, why, and the terminal state. Stop at one packet. The next event must carry a valid new revision.

## Three steelman checks

| Case | Output oracle | Why it matters |
| --- | --- | --- |
| A later file corrects a naming convention but a different revision fixes the data transformation; the handoff describes the intended correction, not filenames. | Include the transformation revision and its compatible dictionary; exclude the naming-only file. Source IDs, actual files, and digests agree. | An evidence-based choice has an opportunity to beat newest-file selection. |
| A trusted explicit manifest already lists the exact desired files. | Skip the model and build exactly that manifest's allowed draft. | A good tool does not use AI to replace known structured intent. |
| Different notes imply different versions of the same synthetic input and no trusted revision resolves them. | Preserve previous draft and write one unambiguous hold explaining the conflicting references. | Avoids publishing an arbitrary choice. |

The real baseline is not “copy newest.” It is explicit manifest validation plus exact matching on revision and typed relationships, or a bounded deterministic browse of candidate descriptions where possible. The model must resolve a genuinely contextual case that those methods would leave for manual work without introducing false selections. The demo should show the new folder and verifier output, not merely a narrated catalog.

## Matched revision-provenance test

Use two valid synthetic CSV revisions with identical headers. Each has a capture manifest; the more recently modified file is the wrong revision. The decisive record ties the intended transformation to a specific verified capture and data dictionary, including units or the missing-value convention. The judge verifies files and digests in the activated local draft. Remove only that corroborating record: the agent should leave the previous ready draft alone and record one actionable review item, not pick based on a timestamp. Give the typed baseline full credit whenever it makes either decision correctly. If all necessary relationships are explicit, the model is unnecessary.

[Dryad's README generator](https://datadryad.org/help/submission_steps/readme) already imports file and variable names, and its [data guidance](https://datadryad.org/help/guides/best_practices) addresses how to document data. [BagIt](https://www.rfc-editor.org/rfc/rfc8493.html) already provides packaging integrity checks. Don't claim those functions as novelty. This design's only proposed value is choosing which approved revision belongs in the handoff when plain-language and typed records must be reconciled.

## Does it replace the front-runner?

- **Against DockCheck:** More tangible and no database or browser is needed. But the value recurs only for teams whose handoffs omit tied-down IDs. The positive case may look like smart packaging, where a disciplined team can simply maintain a manifest.
- **Against Access Handoff:** Easier offline setup and exact output oracle; less engaging on camera. The trigger, conflicts, and decision must be legible in a ten-second before/after.
- **Practical call:** Keep as the low-infrastructure finalist. Its pitch is strongest as a handoff artifact, not a repository or an agent that makes sensitive release decisions. It wins only if the nontrivial contextual selection example is both realistic and transparent enough for a cold judge.
