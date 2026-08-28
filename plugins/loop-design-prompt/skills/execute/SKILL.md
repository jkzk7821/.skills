---
name: execute
description: "Use when a finite long-running objective must be converted into a concise Codex /goal prompt from user instructions or repository evidence, especially when mutable workflow detail must remain with its authority."
---

# Execute Goal Prompt

Render the smallest sufficient `/goal` prompt from a complete approved contract. Other verdicts retain their matching inline body.

## Source the contract

Use the user's input and relevant repository material present in scope. An empty or new project is valid current state. Present repository instructions participate as live authority, and approved human decisions supply contract values. Retrievable sources receive authority names; user input supplies values directly.

Resolve only these fields:

1. One durable objective.
2. The authorities and their precedence.
3. The current checkpoint or how to derive it from actual state.
4. Current-state evidence that proves completion.
5. Active operational authority and human-retained authority.
6. Conditions that require a human decision or other resume event.

An incomplete objective or stopping condition renders `HUMAN_DECISION_REQUIRED`: the decision needed, the smallest recommended package whose acceptance surface matches the user's stated outcomes, materially distinct alternatives, each choice's authorization effect, **Approval state: pending**, and a direct selection request.

An approved `NOT_GOAL` plan retains that verdict and its suitable alternative.

## Render four closed slots

When the contract is complete, output only one prompt with these four semantic sentences:

```text
/goal Read [relevant authorities] and continue [one durable objective] from [current checkpoint or its derivation rule].
Treat [actual current state and named authorities] as authoritative over this summary, and re-derive the next checkpoint from them.
Stop only when [verifiable current-state end condition]; report the evidence and request final human confirmation when required.
At [blocker, permission, approval, policy, or scope boundary], pause and report the cause, impact, and resume condition.
```

Each sentence has a closed responsibility:

| Sentence | Contains |
|---|---|
| 1 | Retrievable authority names; one outcome-only objective; current checkpoint or its derivation rule |
| 2 | Precedence and next-checkpoint re-derivation only |
| 3 | Verifiable stopping condition and completion report |
| 4 | Pause, permission, and resume boundary |

Fill the bracketed noun phrases inside the four-sentence grammar. Map each input detail once:

- A live source owns it → represent it with that authority's name.
- An approved human decision owns it → place the approved value in its matching slot.
- Mutable mechanics owned elsewhere → represent them through their live authority.

User input supplies contract values, while live authority names refer to retrievable sources. Execution cadence stays with its owning authority; the objective slot carries one outcome.

An explicitly approved recommendation supplies contract values and operational authority exactly as approved. Human-retained authority remains visible at its boundary.

The completed prompt contains exactly four semantic sentences.

The acceptance surface and operational authority match the approved contract.

Before returning, confirm the prompt has one objective, names live authority, derives current state dynamically, has a non-gameable stop, preserves the human decision edge, and carries one related body of work.
