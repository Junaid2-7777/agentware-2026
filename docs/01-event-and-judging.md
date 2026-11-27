# Event and judging

## Pass 1: Event rules and deliverables

- [Homepage](https://agentwarehack.com/): free, online, software-only, 72 hours; 1–4 builders; individual registration. Discord membership is not registration. November 27, 18:00 UTC through November 30, 18:00 UTC (both 23:30 IST). The judging period runs November 30–December 10, winners announced December 11.
- [Brief](https://agentwarehack.com/brief/): fresh project during the window, one track, public OSI-licensed source at submission, one team member submits, judge setup under 15 minutes. No personal credentials, secrets in git, unsolicited messages, harmful real-world writes, or uncontrolled spending. General frameworks and AI coding assistance allowed; document models and tools. No recycled project. Record the run from trigger through result, not a staged mock presented as live.
- [Plain-English full explanation](https://agentwarehack.com/brief/#explain-full): the same event, not a second set of rules. Practical test: can someone run it, watch it finish, and reconstruct what happened? Prefer a narrow useful job to a sprawling assistant.
- [Trap Pack page](https://agentwarehack.com/trap-pack/): 20 fixtures across six tracks, including benign controls. Keep answer key and manifest out of runtime inputs. Report tested behavior and failures in `tests/`; don't treat unsupported formats as passes. Planning reviewed the public overview and fixture index, not the archive's hostile contents or answer key.
- [Kickoff announcement corroboration](https://agentwarehack.com/brief/#timeline): submit by November 30, 23:30 IST; changes may be resubmitted before freeze and the organizer grades the latest. Verify exact form fields before submitting. Demo must be accessible without an account; no slide deck or deployed site is required.
- Cash $1,800: $800/$400/$200, $100 Best Kill Switch, three $100 Near Miss write-ups. Optional write-ups close December 7 at 23:30 IST. Partner prizes are separate; credits aren't cash. No partner integration is a prerequisite. Skip optional credit sign-ups, hosting or install scripts for the core build. Payout arrangements, identity checks and India receipt logistics are separate from building; the rules say no country is excluded.

## Pass 2: What each judge will actually look for

| Criterion | Weight | Evidence to produce |
| --- | ---: | --- |
| Autonomy | 30% | One scheduled/arrival-triggered run, durable workspace write, zero hands-on steps from trigger to result. |
| Usefulness | 25% | Name the operator, repetitive task, and exactly what they see next morning; compare with manual triage. |
| Reliability | 20% | Relevant Trap Pack observations, benign controls, duplicate/restart and malformed/incomplete input handling, results and known limitations. |
| Engineering | 15% | Clean-start run, limited permissions, small tool schema, reproducible setup without personal accounts. |
| Demo | 10% | One real continuous run, audible/readable result, uncropped enough to verify. |
| Bonus | +4 max | Runtime enforcement, live run and cost status, demonstrable stop, trace that reconstructs the decision and resulting action. |

Aim for all four bonus behaviors but never self-award points or promise a placement. No fake benchmarks, support for formats we didn't run, or confidence scores without evidence.

## Pass 3: Reconcile the apparent tensions

- **Real action vs safe action:** create persistent, actionable work in the sandbox; do not send, order, or change real inventory. Make the resulting rows observable on rerun.
- **Unattended vs human approval:** finish the normal run without approval. An exception may be queued for the morning; that's an output, not a blocking question during the run.
- **Determinism vs genuine agent:** deterministic parsing, limits, and policy; bounded agent makes an evidence-dependent next-tool decision. Judge sandbox is real and local; offline replay is explicitly labeled as replay.
- **Private planning vs public project:** final user direction is public now. Write only publishable planning; omit private context, links, test secrets, and unlicensed source. Root README is an event guide now; replace it with run instructions only once implemented.
- **Recorded video vs canned mock:** the submission video records an actual live run. A replay may help judges inspect evidence but is not the main autonomy proof.
