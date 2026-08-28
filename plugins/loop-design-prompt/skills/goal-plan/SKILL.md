---
name: goal-plan
description: "Use when a request must be shaped into the prompt it deserves before any launch, especially when its size, acceptance surface, completion evidence, or approval boundary is still open."
---

# Goal Plan

Apply loop-design-prompt judgment to one request and return the prompt text it warrants. The outcome here is an ordinary prompt: whether it later becomes a durable objective is settled by `execute`, which reviews this inline context and launches it.

## Inputs

Use the request and the repository material in scope. Inspect enough current source and present instructions to ground the result. An empty or new project is valid current state, and the retrievable sources actually present define repository authority.

Keep these distinctions:

- User direction owns the requested outcome and the authorization.
- Current source and reproducible evidence own current facts, and that same source owns the design already in place — data shapes and types, routes, layout and naming conventions, existing empty and error states, and the dependency set — whether or not a design or product document records it.
- Repository instructions own local workflow, validation, and protected boundaries.
- The prompt names mutable authority and derives task order, commands, retry policy, and roles from the current version of that authority.

## Size the work before shaping it

A durable objective fits one finite outcome that needs more than a normal turn and has a verifiable end state. Three tests settle the common borderline cases:

- When one careful turn can both produce and verify the outcome, an ordinary prompt covers it; a durable objective earns its cost when reaching the outcome takes repeated produce-verify-repair passes whose progress must survive across turns. Size the work by the substance the outcome must carry rather than by the mechanics of writing it out: several interacting behaviors, or several distinct pieces of original content or analysis that each need drafting and revision, are checkpoints even when the delivery medium is one simple file. Repository size is not task size; a large codebase with one small change is still one turn.
- A conversion or migration objective is real only when the artifacts to convert exist in current state. When they are absent, the smallest suitable result is producing that source material first.
- A request for a design or strategy is fulfilled by the design artifact itself, and implementing what it designs is a separate objective with its own approval. That boundary governs scope rather than size: producing the design is itself durable work when it rests on analysing a real artifact or weighing several options, and its direction is human-owned whenever the request leaves it open.

## Keep the acceptance surface the user named

An objective and its stopping condition observe the surface the request names. When the available delivery medium can host only a demonstration or stand-in of that surface, the surface choice is a human decision to settle first.

A structural count or format the request names settles the shape of that surface but not its substance. Where the outcome's worth rests on original content or judgment the request leaves open — subject scope, audience, depth, or priorities — that specification is human-owned and belongs in an approval package, since an agent that supplies it is writing the criteria it will later grade itself against.

Prefer reconciliation against an external or current fact over self-authored assertions. Bind the expected value to a path independent of the code under test, so the comparison has two separate sides.

## Fit the design already in place

Current source answers two separate questions: how far the work has progressed, and how the thing is already built. Read it for both, and name what the code has already settled so new work lands inside it rather than beside it. Where the request can be met only by departing from that established design, the departure is a scope decision the human owns rather than a detail settled while building.

## Human decisions lead

When an unresolved human decision and a size answer both apply, the human decision leads the result, because resolving it can change which prompt fits. Resolving it is a gate rather than a destination, so name the primitive each choice would unlock and carry the contract that approval would authorize, letting the human see in one place whether approving turns the work into a durable objective. Ask for that approval once: the package is the request, and an approved package enters the contract as settled values rather than a second confirmation.

Human-owned product, policy, safety, and permission choices take precedence over eventual task size. A vague qualitative change to a protected surface such as login, authentication, authorization, payments, or destructive controls stays a human decision. Source absence by itself leaves an otherwise clear size answer unchanged.

For an approval package, offer the smallest complete set and only materially distinct alternatives, with three positive slots: the **requested acceptance surface** preserving the exact semantics and count of the stated observable outcomes, the **delegated implementation choices** covering observationally equivalent ways to realize them, and the **authorization effect** separating authority that approval activates from authority the human keeps.

## What to return

Return the result first, then its matching body:

- **Durable objective** — one cohesive inline instruction containing one outcome; named authority and precedence; dynamic next-checkpoint derivation; the established design new work stays within; current-state validation and protected boundaries; a verifiable stopping condition; and a closed list of pause and resume triggers, with every decision the human already approved carried as a settled value. Hand this to `execute`.
- **Ordinary prompt** — the single-turn request that covers the work, with its own observable done-criterion.
- **Approval request** — the decision needed, one recommended package, named alternatives, each choice's authorization effect and unlocked primitive, and the contract approval would authorize. Close with **Approval state: pending** and a direct request to approve or select.
- **Source first** — the artifact that must exist before the requested conversion becomes real.
- **Revision** — the concrete contract defect to correct.

Add **Review notes** only for concrete conflicts, unsupported scope, or missing evidence. Preserve the user's language and terminology, keep the result self-contained enough to hand to another agent, and leave mutable execution detail with its owner.

## Review test

A durable-objective result lets a fresh agent answer all of these from the instruction and its cited authority:

- What single outcome am I pursuing?
- What source wins when instructions disagree?
- How do I determine the next checkpoint from current state?
- Which design does the current source already establish for my work to fit, and what departure would belong to the human?
- What current evidence proves completion while verifier protections stay intact?
- Which action or decision requires me to pause for a human?

An approval request lets a non-developer choose by approving the recommendation or naming an alternative, with active authority, human-retained authority, and the unlocked primitive visible before selection.

Operational authorization is the intersection of the user's grant and the named authorities. Every remaining authority stays human-owned.
