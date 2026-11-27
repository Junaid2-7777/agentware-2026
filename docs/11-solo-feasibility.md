# Solo feasibility and what to cut first

This is capacity planning, not an estimate of contest placement or proof that any project runs. Plan on 10, 15, or 20 focused builder hours out of the 72-hour contest window. Reserve the last two focused hours for a clean setup rehearsal, honest video, and public submission checks before allocating stretch features.

| Candidate | Main dependency | First convincing run | Likely late risk | Cut without gutting the entry |
| --- | --- | --- | --- | --- |
| DockCheck | A local SQLite-capable Python installation, synthetic fixture and one model adapter for the live demonstration | A closed-shift batch starts processing automatically, follows an evidence trail, and writes a correctly scoped case | Correctness for partial receipt and file arrival; model might not beat a good baseline | Hosted queue, multiple formats, admin settings and full-screen UI |
| Access Handoff | Browser runtime and one small renderable fixture site, plus local writer | A real browser observes one keyboard-state regression and persists a grounded, deduplicated follow-up | Installing a reproducible browser cleanly; typed interactions may outperform model choice | More widget types, deployed fixture, screenshot gallery, cross-browser matrix |
| Deposit Draft | Filesystem and validated synthetic catalog; no browser | The right revision plus documentation appears in a new, verifiable folder; mismatches never enter it | A well-maintained approved manifest may remove the entire need for agent inference | Archives and archive standards support, repository submission, format inference |
| Caption Patch | Local player, edit metadata and preexisting synthetic VTT captions; no transcription | Updated VTT loads and one genuinely ambiguous cue mapping is held for review | Building a convincing time mapping without overstating observed audio | Rendering UI, translation, speaker inference, multi-language captions |

## Budget comparison

- **10 focused hours:** DockCheck or Deposit Draft has the most forgiving dependency graph. Keep one valid case plus one independent failure case, add no optional services, and do not call either complete without one measured real run. For Access Handoff, rule out install problems before building model features.
- **15 hours:** DockCheck has room for deduplication, deadline/stop checks, a stable baseline and a tiny read-only review screen if core gates pass. Access Handoff has room for a clean browser setup, two widget controls, and a real saved issue. Decide based on the strongest evidence of model value, not a pre-existing head start in the docs.
- **20 hours:** Spend additional time proving correctness on unlabeled fixtures, rehearsing cold start and demonstrating recovery. Do not use the extra time for a different track, external integrations, account setup, or two simultaneous products.

## First 90 seconds for a stranger

- **DockCheck:** Show “20 due, 18 counted” and an empty handoff queue. One batch lands. The terminal shows the agent request the corroborating record, then the persisted case explains both the missing units and why the action is “check the split delivery” rather than “recount now.” Show evidence IDs and no permission to move stock.
- **Access Handoff:** Show a keyboard interaction failing on one synthetic component and working on a relevant control during the run. Persist a single verification task with browser observations even if the same bug appears twice. Show the browser stopped and the unchanged fixture site. Avoid a compliance badge.
- **Deposit Draft:** Show two input revisions and an empty output folder. After the independent constraint check, open the staged files and the manifest; contrast them with an ambiguous input that did not produce a ready folder. This is tangible but less instantly legible than browser focus or a count discrepancy.
- **Caption Patch:** Show a sentence whose subtitle follows a cut to the right time. Open the actual draft in a local player and show the preserved unresolved region without fabricating a translation or transcription.

All clips must fit the organizer's separate requirement for an authentic full unattended run in a video of at most three minutes. The 90 seconds above is about legibility, not permission to cut out steps in that run.

## Setup and cut rules

1. Make the first-run command verify dependencies before writing anything. [Python's sqlite3 docs](https://docs.python.org/3/library/sqlite3.html) note that the module can be absent from an installation; detect it rather than implying that every Python build has it. [Playwright's browser docs](https://playwright.dev/python/docs/browsers) call out version-matched browser binaries; for Access Handoff, test clean installation including those assets and say whether network is required.
2. Keep a no-cost no-personal-credentials reviewer path. Live mode still needs the actual model choice and real tool action in the separate video. [Agentware's brief and FAQ](https://agentwarehack.com/brief/#faq) allow a cheaper mock/trace for expensive paths; state exactly what was replayed, what still ran locally, and what costs or keys would be needed for a live run.
3. Drop a nice-to-have as soon as it threatens clean setup, a visible completed task, or a demonstrated stop. If no concept beats its strong baseline at its narrowest scope, fix the input/problem or select another concept rather than fitting a model into a job that doesn't need one.

**Provisional takeaway:** DockCheck remains the most practical route to an explainable trustworthy demo. Access Handoff is the best visual alternative and Deposit Draft is the best low-infrastructure alternative. The actual decision still turns on the value of model-driven evidence selection, not on how many features can be squeezed in.
