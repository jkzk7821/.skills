---
name: loop-design-prompt
description: "Use when writing or reviewing a long-running /goal objective or autonomous agent loop whose stopping condition, authority, validation, retry behavior, or human approval boundary may be unclear, stale, gameable, or prone to runaway execution."
metadata:
  origin: jkzk7821
---

# Loop Design Prompt

> **Premise.** Codex `/goal` already provides persistence across turns. This skill designs the contract attached to that mechanism: one durable objective, authoritative context, verifiable completion, and safe pause boundaries. Do not recreate the persistence mechanism or copy an entire runbook into the goal prompt.

## When to use / not

**Use it when:**
- A finite task is too large for one normal turn and needs Codex to keep making scoped progress.
- You are reviewing a goal or autonomous loop for spinning, stale instructions, verifier gaming, or guessed policy decisions.

**Don't use it for:**
- A one-off task that fits in one turn.
- Indefinite monitoring or recurring maintenance with no terminal state; use a regulator, monitor, or schedule instead.
- A loose list of unrelated work; split it into separate goals.
- How to wire pipelines, DAGs, or recovery infrastructure; use the mechanism-layer skill for that.

## Two levels of control

| Level | Owner | Responsibility |
|---|---|---|
| **Operational execution** | agent + deterministic evidence | Work toward the stated objective, evaluate explicit completion criteria, stop, and report evidence. |
| **Goal and policy judgment** | **human** | Decide whether the objective is right, change policy or scope, approve unresolved choices, and authorize irreversible or externally visible actions. |

The agent may conclude that the operational stopping condition is met. It may not convert that conclusion into human acceptance, policy approval, merge, release, publication, spending, or another authority it was not given.

Everything the goal-and-policy row does not name is the agent's call. A question the objective, the named authorities, and current state can answer is operational: decide it, proceed, and record the decision in the report. A choice the human already made while approving this contract is settled — carry it as a value and do not re-open it.

---

## Action 1 — Write a goal contract

### Step 0 · Choose the right primitive

Use `/goal` only when all are true:

1. There is **one durable objective**, not an unrelated backlog.
2. The work is larger than one normal turn but has a finite end state.
3. Completion can be verified from commands, artifacts, current source, or another authoritative fact.
4. Codex has the tools and permission to make meaningful progress without continuous steering.

Otherwise use a normal prompt, split the work, resolve the missing human decision first, or use an ongoing monitor/schedule.

Three task-shape tests settle the common borderline cases:

- When one careful turn can both produce and verify the outcome, a normal prompt is the right primitive; `/goal` earns its cost when reaching the outcome takes repeated produce-verify-repair passes whose progress must survive across turns. Size the work by the substance the outcome must carry rather than by the mechanics of writing it out: several interacting behaviors, or several distinct pieces of original content or analysis that each need drafting and revision, are checkpoints even when the delivery medium is one simple file.
- A conversion or migration objective is real only when the artifacts to convert exist in current state; when they are absent, the smallest suitable alternative is producing that source material first.
- A request for a design or strategy is fulfilled by the design artifact itself, and implementing what it designs is a separate objective with its own approval. That boundary governs scope rather than size: producing the design is itself durable work when it rests on analysing a real artifact or weighing several options, and the direction it should take is human-owned whenever the request leaves it open.

When an unresolved human decision and a task-shape answer both apply, the human decision leads the report, because resolving it can change which primitive fits. Resolving it is a gate rather than a destination, so name the primitive each choice would unlock and carry the contract that approval authorizes, letting the human see in one place whether approving turns the work into a durable goal. Ask for that approval once: the package is the request, and an approved package enters the contract as settled values rather than a second confirmation.

### Step 1 · Identify authority before writing

Find the sources that own:

| Concern | Typical authority |
|---|---|
| Objective and scope | goal/spec/issue |
| Rules and protected boundaries | project instructions/policy |
| Current checkpoint | handoff/state/current source |
| Existing design | current source itself — data shapes and types, routes, layout and naming conventions, existing empty/error states, dependency set — together with any design or product document that records them |
| Verification | tests, build, reconciliation source, runtime evidence |

State their precedence when more than one exists. The goal prompt is an **index into these sources**, not a shadow copy of them.

- If an authoritative source already owns a mutable task list, phase order, command set, retry limit, or role contract, point to it instead of restating it.
- Tell Codex to derive the next checkpoint from the current authority and actual state.
- Current source answers two separate questions: how far the work has progressed, and how the thing is already built. Read it for both. Where the code itself already establishes a data shape, a route pattern, a styling or naming convention, an empty or error state, or a dependency set, that established design is authority for how new work fits, whether or not a document also records it. Where the request can be met only by departing from it, the departure is a scope decision the human owns rather than a detail settled while building.
- If no source owns a necessary constraint, put that constraint in the goal itself.

### Step 2 · Define one durable objective and stopping condition

A good contract has five fields:

1. **Objective** — one outcome Codex should achieve.
2. **Authority and current state** — what to read first and what wins over the prompt summary.
3. **Validation** — commands or artifacts that prove progress against the current source state.
4. **Boundaries** — what must not change or which actions remain unauthorized.
5. **Stop or pause** — the verifiable end state and the conditions requiring human input.

The acceptance surface is the one the user named: an objective and stopping condition observe that surface directly. When the available delivery medium can host only a demonstration or stand-in of the named surface, the surface choice is a human decision to resolve before the contract is rendered. A structural count or format the request names settles the shape of that surface but not its substance, so where the outcome's worth rests on original content or judgment the request leaves open — subject scope, audience, depth, or priorities — that specification is human-owned and belongs in an approval package, since an agent that supplies it is writing the criteria it will later grade itself against.

Prefer reconciliation against an external or current fact over self-authored assertions. “All tests pass” alone is gameable; “required checks pass, protected tests and boundaries remain intact, and current state matches the authority” is harder to game.

> **Self-check:** Can a fresh agent use the prompt plus its cited sources to determine the next checkpoint, whether the goal is complete, and when it must pause? If not, fix the contract before launch.

### Step 3 · Make validation resistant to Goodharting

- Bind evidence to the current source/environment state when stale results are possible.
- The builder may not delete, weaken, or rewrite acceptance conditions to make the verifier pass.
- Use deterministic commands or reconciliation where available; do not substitute “looks right.”
- Require a distinct reviewer only when the project authority or risk requires one. Independence can also come from an external deterministic verifier; do not force sub-agent topology into every goal.
- If the authority already defines implementation, verification, review, and recording order, reference that order rather than reproducing it.

### Step 4 · Add damping and human boundaries

- Use retry and repair limits defined by the authority. If none exist, add the smallest cap justified by an actually repeatable failure mode; do not invent a universal number.
- Write the pause triggers into the contract as a closed list, and pause only on one of them: repeated identical failure at the cap, a decision the contract itself names as still unsettled, an action outside granted permission, or scope beyond the approved objective. Anything not on that list is decided from the authorities and current state and recorded in the report, not escalated.
- A blocked report should state cause, impact, and the condition for resuming.
- Codex may stop when the operational end state is satisfied and report the evidence. Request final confirmation only where a named authority requires sign-off; otherwise the evidence report is the terminal state.
- Completion rests on the evidence the stopping condition names. When that evidence channel is unavailable, the accurate terminal state is a paused report carrying the cause and resume condition; weaker proxy evidence supports progress reporting, not completion.
- Never infer permission for merge, push, deployment, publication, spending, or destructive actions from permission to pursue the goal.

### Step 5 · Render the smallest sufficient `/goal`

Use this shape:

```text
/goal Read [instruction, objective, and current-state authorities] and continue [one durable objective] from [current checkpoint].
Treat [current source and named authorities] as authoritative over this summary, re-derive the next checkpoint from them, keep new work within the design they already establish, and treat [decisions already approved] as settled.
Stop only when [verifiable end state] and report the evidence[; request final confirmation only where a named authority requires sign-off].
Pause only at [closed list of remaining triggers] and report the cause, impact, and resume condition; decide everything else from the authorities and current state and record it.
```

Keep mutable workflow detail in its owning file. If the prompt becomes long, move the detail into a file and point the goal at that file. Consult current product documentation when command syntax or limits matter.

---

## Action 2 — Review a goal or loop

A red answer to any row sends the contract back for revision.

| # | Failure mode | Review question | Antibody |
|---|---|---|---|
| 1 | Wrong task shape causes endless work | Is this one finite objective, or a one-off task, indefinite monitor, or unrelated backlog? | Use the right primitive or split the goal. |
| 2 | Vague or self-judged completion | Can current evidence answer done/not-done without “looks right”? | Add a verifiable end state and deterministic evidence. |
| 3 | Verifier is gameable | Could the builder pass by weakening tests, boundaries, mocks, or acceptance criteria? | Pair the done criterion with protected boundaries and reconciliation. |
| 4 | Prompt becomes a stale shadow runbook | Does it duplicate mutable phases, task lists, commands, retry caps, or roles already owned elsewhere? | Point to the authority, define precedence, and derive from current state. |
| 5 | Agent guesses a human decision | Is any policy, approval, scope, permission, or irreversible action unresolved at launch or runtime? | Resolve known choices first; encode a pause boundary for the rest. |
| 6 | Acceptance surface drifts to a stand-in | Does the validated surface match the surface the user named, or a demonstration of it? | Re-anchor the objective and validation to the named surface, or return the surface choice to the human. |
| 7 | Loop stalls on decisions it owns | Is the pause trigger an open predicate ("when required", "any human decision"), or does it re-ask what approval already settled? | Close the pause list, carry approved decisions as settled values, and leave the remainder to the agent with the decision recorded. |
| 8 | New work drifts from the design already in place | Does the contract fit and name the data shapes, conventions, existing states, and dependency set the current source establishes, or does it read that source only for how far the work has got? | Anchor the work to the established design, or return the departure to the human as a scope decision. |

### Final review checklist

- [ ] One durable objective that provably exceeds one normal turn
- [ ] Deliverable type matches the request (a design request ends in a design artifact)
- [ ] Objective and validation stay on the user-named acceptance surface
- [ ] Named authority and precedence
- [ ] Current checkpoint derived dynamically
- [ ] New work fits the design the current source already establishes, or the departure is a human decision
- [ ] Verifiable end state bound to current evidence
- [ ] Protected boundaries cannot be weakened to pass
- [ ] Pause triggers are a closed list; approved decisions are carried as settled and everything else is the agent's call
- [ ] No authority for external or irreversible actions was silently added
- [ ] Human retains goal, policy, and final-risk judgment

---

## Worked example — repository work governed by live documents

**Bloated shadow contract:**

```text
/goal Complete phases A-E. Use one unit at a time, run commands X/Y/Z, use two sub-agents, retry three times...
```

This may be safe today, but it duplicates mutable instructions and can conflict with the repository tomorrow.

**Authority-driven contract:**

```text
/goal Read the project instructions, current goal, and handoff; continue the current objective from the handoff's next action.
Treat the actual source and those current documents as authoritative over this summary.
Stop only when no approved work remains, required current-state verification passes, and the handoff matches the checkout; report the evidence.
Pause only at a blocker, an action outside granted permission, or work beyond the approved scope, and report the resume condition; decide the rest from those documents and record it.
```

The second prompt keeps the durable target and stopping condition in `/goal`, while leaving changing execution details with their owners.

---

## One-line close

> A `/goal` prompt is an index card, not a runbook: one objective, live authority, verifiable stop, protected boundaries, and a human-owned decision edge.
