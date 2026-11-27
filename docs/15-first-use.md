# First-use walkthrough: what someone can do with the result

Three possible products, viewed from the moment someone opens the output rather than the moment the model responds. These are designs, not usability test results.

## DockCheck: can I decide what to do before I walk to the dock?

Start with one real case row, not charts or a chat box:

| Source references | Due / scanned | Next step | Why |
| --- | --- | --- | --- |
| Receipt X / Scan batch S | 20 / 18 | Confirm split delivery | Same-receipt arrival evidence gives a later window; the two units are still missing at cutoff. |

A person should be able to open the annotated source lines, tell the difference between a verified record and a handoff claim, and see what would have produced a recount instead. Present a source hold as “Totals unavailable for this shift,” not “zero received.” A queue with three tasks is useful only if the operator knows where to start and can independently reproduce the first decision. Keep reviewing/closing items outside the first build; the reviewed product is the unattended preparation step.

## Access Handoff: can I reproduce the keyboard behavior without asking for a video?

Show one issue with the route and release revision, a short keyboard sequence, the expected focus boundary, what actually got focus, and the affected component occurrences. Beside it show the correct modal control and any coverage gap. Use plain status labels and text evidence so the result itself is not visual-only. A developer should be able to repeat the exact observation on the fixture; no general “accessibility score” is needed.

## Deposit Draft: can I open the right files without learning a new app?

The result is a versioned folder with familiar file types, a short index and a manifest. The index explains why this revision was chosen, which dictionary applies, and where to find the more detailed source references. A failed or ambiguous assembly never appears as a ready draft. Show an independently checkable file list and hashes rather than declaring the data clean, anonymous or archived.

## Judge the first use, not feature count

Give a cold reader three tasks: find the useful output, verify one source-to-result claim, and tell whether anything happened outside the permitted workspace. Use success/failure and elapsed time; capture confusion instead of coaching. In the demo, if a reviewer cannot do those three things from one visible action and a quick trace, simplify the output rather than add a second screen.

Build-order implication: DockCheck's first UI is one queue view plus evidence; Access Handoff's is a reproducible interaction and one issue; Deposit Draft's is the actual artifact and a readable index. Save all three patterns as planning, then build just one after choosing. The likely winner is the concept whose output a stranger can verify without taking our word for it.
