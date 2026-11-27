# What “leave it running” means in operation

An unattended agent is not a CLI that waits for someone to approve every action, or a process that never exits. The [Agentware brief](https://agentwarehack.com/brief/#explain-full) asks for a useful run with a real action and a clear stop. Here the listener and the run have different lifetimes: the listener waits within a configured session, and each input starts one bounded run. The demo shows one full run. No long soak, production readiness, or runtime test is claimed.

## The operator contract

Before starting, an operator sets one known workspace, one allowed destination, a bounded run duration, and whatever is permitted to write. They can stop the session, inspect previous outputs, and check whether a run failed, cancelled, or succeeded. They don't select a case, reinterpret a prompt, accept a recommendation, or move the output during a normal run.

At the end of a run, one plain-language state appears:

| State | Meaning | Required observable result |
| --- | --- | --- |
| Completed | The permitted output is committed, including the valid case with no exceptions. | A result reference and exact count, even when zero. Read from the destination, not from model text. |
| Needs review | A real in-scope uncertainty was persisted for the operator. The run finished. | Case with source evidence, missing fact and proposed next check. No pending tool action. |
| Blocked | Input completeness, configuration or policy made the work unsafe to proceed. | Reason and affected scope; no partial business change. Only a verified new revision or corrected configuration starts new work. |
| Cancelled | Stop won before a pending result committed. | No late write. Preserve unrelated and already committed work. |
| Failed | Runtime or storage made the result unavailable. | Explicit visible failure and no success receipt. A new logged attempt follows the bounded retry policy, not a silent loop. |

“Needs review” can be an output of a successful run even if no review was performed in the moment. It must not be used to evade completion for a routine positive example.

## Three finalists, same stop test

- **DockCheck:** Change only sandbox case storage. Receipt facts are read-only. A complete shift with a genuine unresolved discrepancy writes one case with expected/observed quantities; an incomplete export creates a source hold. Cancellation cannot turn missing input into zero counts.
- **Access Handoff:** Read the local fixture page, run one scoped browser interaction, and persist a verified work item without editing the page. Stop closes the run's browser context and prevents a delayed interaction result from writing a follow-up. Do not confuse early close or unsupported fixture coverage with a passing scan.
- **Deposit Draft:** Read only explicitly allowed source files; write a new local draft folder. Check all approved selected files and hashes before activating the draft. Cancel or fail before activation leaves the preceding completed draft intact and no partial draft presented as ready.

## Two follow-up arrivals to prevent a demo-only design

1. **Duplicate event:** The same manifest ID, revision and digest arrives again. The terminal record says it was redundant, and the destination is unchanged.
2. **Correction:** A new trusted revision arrives after a finished run. It starts another bounded run; the previous record is preserved and the reviewer can see which output is current. In DockCheck, a corrected source updates evidence for an existing case rather than making a second active copy. In Access Handoff and Deposit Draft, each published revision remains attributable.

For the first build make these explicit local test cases, not a promise to leave the agent on around real systems. Measure what actually happened in a clean workspace before publishing the demo. If a candidate cannot meet the shutdown and output contract with its dependency budget, it loses to the one that can.
