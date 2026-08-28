---
name: goal-plan
description: "Use when a long-running Codex objective must be designed or reviewed from user input or repository evidence before producing a /goal command, especially when scope, authority, completion, or approval boundaries are unclear."
---

# Goal Plan

Design or review one durable goal contract and return a verdict with its matching inline body.

## Inputs

Use the user's request and relevant repository material in scope. Inspect enough current source and present governing instructions to ground the contract. An empty or new project is valid current state; the retrievable sources actually present define repository authority.

Keep these distinctions:

- User direction owns the requested outcome and authorization.
- Current source and reproducible evidence own current facts.
- Repository instructions own local workflow, validation, and protected boundaries.
- The inline contract names mutable authority and derives its task order, commands, retry policy, and execution roles from the current version of that authority.

## Decide before drafting

Use a durable goal for one finite outcome that needs more than a normal turn and has a verifiable end state. Other shapes return `NOT_GOAL` with the smallest suitable alternative: a normal task, separate goals, a monitor, or a prior human decision. A migration or conversion with zero current artifacts also returns `NOT_GOAL` with the artifact needed to make the objective real.

The acceptance surface comes from the user's stated outcome and named authority. A missing product policy, approval, project default, or scope choice that materially changes the result returns `HUMAN_DECISION_REQUIRED` before launch.

Verdict precedence gives human-owned product, policy, safety, and permission choices priority over eventual task size. A vague qualitative change to a protected surface such as login, authentication, authorization, payments, or destructive controls therefore returns `HUMAN_DECISION_REQUIRED`. Source absence by itself leaves an otherwise clear task-shape verdict unchanged.

For `HUMAN_DECISION_REQUIRED`, propose the smallest complete approval package and only materially distinct alternatives. The recommended package has three positive slots: **requested acceptance surface** preserving the exact semantics and count of the user's stated observable outcomes, **delegated implementation choices** covering observationally equivalent ways to realize those outcomes, and **authorization effect** separating authority activated by approval from authority retained by the human. Choices that change product semantics stay human-owned. For “employees submit leave requests and managers approve them,” those two behaviors form the entire acceptance surface while their minimum role representation, technical implementation, and evidence are delegated choices.

A qualitative protected-surface request keeps its success criterion as a human decision. When current implementation evidence is unavailable, the recommended package activates read-only diagnosis and an evidence-backed option proposal; implementation authority follows the user's selected option.

For a new or empty project, the recommendation can delegate ordinary implementation choices. Product policy, completion, safety, and permission choices stay human-owned. In the absence of repository instructions, the recommended default activates repository file changes and local verification after approval; broader operational authority stays human-owned.

## Output contract

Return the verdict first, followed by the matching body:

- **`READY` — Inline goal instruction:** one cohesive instruction containing one durable objective; named authority and precedence; dynamic next-checkpoint derivation; current-state validation and protected boundaries; a verifiable stopping condition; and pause and resume conditions.
- **`HUMAN_DECISION_REQUIRED` — Approval request:** the decision needed, one named recommended approval package, named alternatives, and each choice's authorization effect. Close with **Approval state: pending** and a direct request to approve the recommendation or select an alternative.
- **`NOT_GOAL` — Suitable alternative:** the smallest normal task, separate goal, monitor, or prior decision that fits.
- **`REVISION_REQUIRED` — Revision:** the concrete contract defect that must be corrected.

Add **Review notes** only for concrete conflicts, unsupported scope, or missing evidence.

Preserve the user's language and terminology. Keep the instruction self-contained enough to hand to another agent, but leave mutable execution detail with its owner.

## Review test

A `READY` contract lets a fresh agent answer all of these from the instruction and cited authority:

- What single outcome am I pursuing?
- What source wins when instructions disagree?
- How do I determine the next checkpoint from current state?
- What current evidence proves completion while verifier protections remain intact?
- Which action or decision requires me to pause for a human?

A `HUMAN_DECISION_REQUIRED` response lets a non-developer choose by approving the recommendation or naming an alternative, with active authority and human-retained authority visible before selection.

Operational authorization is the intersection of the user's grant and named authorities. Every remaining authority stays human-owned.
