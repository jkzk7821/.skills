---
name: execute
description: "Use when an inline contract prepared by goal-plan must be reviewed and then launched as a durable Codex objective, especially when its stopping condition, authority, or approval boundary should be checked before it starts running."
---

# Execute

Review the inline context received from `goal-plan`, then launch it as a durable objective. Review comes first: a contract that starts running carries its defects across every turn it survives.

## Review the inline context

Each row below is answered against the contract as written and the current state it names. A clear answer on every row is the launch condition; a red answer sends the contract back with the concrete defect named.

| # | Failure mode | Review question | Antibody |
|---|---|---|---|
| 1 | Wrong task shape causes endless work | Is this one finite objective, or a single-turn task, an indefinite monitor, or an unrelated backlog? | Return it to `goal-plan` for the right primitive or a split. |
| 2 | Vague or self-judged completion | Can current evidence answer done or not-done without resting on “looks right”? | Add a verifiable end state bound to deterministic evidence. |
| 3 | Verifier is gameable | Could the builder pass by weakening tests, boundaries, mocks, or acceptance criteria? | Pair the done criterion with protected boundaries and reconciliation. |
| 4 | Prompt becomes a stale shadow runbook | Does it duplicate mutable phases, task lists, commands, retry caps, or roles already owned elsewhere? | Point to the authority, state precedence, and derive from current state. |
| 5 | A human decision is guessed | Is any policy, approval, scope, permission, or irreversible action still open at launch or at runtime? | Settle known choices first and encode a closed pause list for the rest. |
| 6 | Acceptance surface drifts to a stand-in | Does the validated surface match the one the user named, or a demonstration of it? | Re-anchor objective and validation to the named surface, or return the surface choice to the human. |
| 7 | Loop stalls on decisions it owns | Is the pause trigger an open predicate ("when required", "any human decision"), or does it re-ask what approval already settled? | Close the pause list, carry approved decisions as settled values, and leave the remainder to the agent with the decision recorded. |
| 8 | New work drifts from the design already in place | Does the contract fit and name the data shapes, conventions, existing states, and dependency set the current source establishes, or does it read that source only for how far the work has got? | Anchor the work to the established design, or return the departure to the human as a scope decision. |

Checklist before launch:

- [ ] One durable objective that provably exceeds one normal turn
- [ ] Deliverable type matches the request
- [ ] Objective and validation stay on the user-named acceptance surface
- [ ] Named authority and precedence
- [ ] Current checkpoint derived dynamically
- [ ] New work fits the design the current source already establishes, or the departure is a human decision
- [ ] Verifiable end state bound to current evidence
- [ ] Protected boundaries hold even when weakening them would pass the verifier
- [ ] Pause triggers are a closed list; approved decisions are carried as settled and everything else is the agent's call
- [ ] Authority for external or irreversible actions is the same as before launch
- [ ] The human keeps goal, policy, and final-risk judgment

## The shape that launches

A reviewed contract carries four semantic sentences:

```text
/goal Read [relevant authorities] and continue [one durable objective] from [current checkpoint or its derivation rule].
Treat [actual current state and named authorities] as authoritative over this summary, re-derive the next checkpoint from them, keep new work within the design they already establish, and treat [decisions already approved] as settled.
Stop only when [verifiable current-state end condition] and report the evidence[; request final confirmation only where a named authority requires sign-off].
Pause only at [closed list of remaining triggers] and report the cause, impact, and resume condition; decide everything else from the authorities and current state and record it.
```

| Sentence | Contains |
|---|---|
| 1 | Retrievable authority names; one outcome-only objective; current checkpoint or its derivation rule |
| 2 | Precedence, next-checkpoint re-derivation, and the established design new work stays within |
| 3 | Verifiable stopping condition and completion report |
| 4 | Pause, permission, and resume boundary |

Map each input detail once. A live source owns it, so represent it by that authority's name; an approved human decision owns it, so place the approved value in its matching slot; mutable mechanics owned elsewhere stay represented through their live authority. Execution cadence stays with its owning authority, and the objective slot carries one outcome. An explicitly approved recommendation supplies contract values and operational authority exactly as approved, with human-retained authority visible at its boundary.

Where a constraint has no owning source, it belongs in the contract itself. Keep the rest of the runbook with its owner and point at it.

## Launch and report

Launch once the review is clear, then let the contract govern: the next checkpoint comes from the authority it names rather than from the summary that started it.

Completion rests on the evidence the stopping condition names. When that evidence channel turns out to be unavailable, the accurate terminal state is a paused report carrying cause, impact, and resume condition; weaker proxy evidence supports progress reporting rather than a completion claim.

Retry and repair limits come from the authority when it defines them. Otherwise the smallest cap justified by an actually repeatable failure mode fits, expressed as the condition that repeats rather than as a universal number.

The agent may conclude that the operational stopping condition is met and report the evidence. Human acceptance, policy approval, merge, release, publication, spending, and other authority it was not given remain with the human, and permission to pursue the objective leaves those unchanged.

Outside that boundary and the contract's own pause list, the agent decides. A question the objective, the named authorities, and current state can answer is operational: decide it, proceed, and record the decision in the report. A choice the human settled while approving the contract is carried as a value, not re-confirmed.
