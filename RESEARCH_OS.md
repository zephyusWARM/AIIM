# AIIM Research OS

## One purpose

Prevent long-horizon AI research from being lost when a chat, stream, browser session, or model execution is interrupted.

This is **not** primarily a knowledge-management framework. It is a crash-recovery protocol.

## Core invariant

> A fresh ChatGPT conversation must be able to recover the current research state from this repository without needing the previous conversation.

## Canonical recovery surface

`research/STATE.md` is the single canonical restart file.

It must always make these questions answerable:

- What are we researching?
- What has already been completed?
- What are the strongest findings so far?
- Which sources/results matter enough not to lose?
- What remains uncertain?
- What is the **next exact action**?

## Sparse checkpoint rule

**Do not use GitHub as a live research log.** Search, read, compare, and reason for a substantial stretch before writing.

Default behavior is to keep working in the current run and batch multiple related discoveries into one checkpoint.

A checkpoint is justified only when at least one of these is true:

- a substantial sub-question has been resolved;
- a high-value synthesis, contradiction, source trail, or decision would be costly to reconstruct;
- the research is about to branch into a substantially different direction;
- the current run is approaching a natural handoff / stopping boundary;
- there is a realistic risk that losing the current state would waste a meaningful amount of work.

A single search, paper discovery, duplicate result, tentative idea, or minor clarification is **not** enough to justify a write.

When a checkpoint is justified, update `research/STATE.md` once with the accumulated epistemic delta and commit it as one coherent batch.

The goal is **minimum sufficient durability**: few writes, high information density, low recovery cost.

## Recovery protocol

When starting or resuming deep research:

1. Read this file.
2. Read `research/STATE.md`.
3. Treat everything under **COMPLETED / DURABLE FINDINGS** as already done unless verification is explicitly needed.
4. Resume from **NEXT EXACT ACTION**.
5. Do not restart the survey from zero merely because the prior chat is gone.

If the previous run died mid-branch, preserve what is known, mark uncertainty honestly, and continue from the closest durable checkpoint.

## Writing discipline

The state file should be compact enough that a fresh model can load it quickly, but detailed enough that a long interrupted run does not have to be repeated.

Prefer precise statements over narrative. Preserve URLs, paper titles, identifiers, query terms, numerical results, and unresolved contradictions only when they materially help reproduction or continuation.

Do not append a diary. Rewrite `STATE.md` into the best compact representation of the current state; Git history already preserves older checkpoints.

## Success criterion

Research OS is working if an interrupted deep-research session can be resumed in a new conversation with negligible duplicated research **without creating noisy, high-frequency Git writes during normal research.**
