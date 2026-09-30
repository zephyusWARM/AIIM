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

## Checkpoint rule

Do not use GitHub as a token-by-token scratchpad. Research first.

Checkpoint when losing the current state would materially waste work, especially:

- after resolving a meaningful sub-question;
- after finding a high-value source, contradiction, or synthesis that would be hard to rediscover;
- before starting another large research branch;
- before switching tools, chats, or research directions;
- when the current run may end before the whole task is finished.

A checkpoint means updating `research/STATE.md` and committing it to Git.

## Recovery protocol

When starting or resuming deep research:

1. Read this file.
2. Read `research/STATE.md`.
3. Treat everything under **COMPLETED / DURABLE FINDINGS** as already done unless verification is explicitly needed.
4. Resume from **NEXT EXACT ACTION**.
5. Do not restart the survey from zero merely because the prior chat is gone.

If the previous run died mid-branch, mark that branch as interrupted/uncertain in `STATE.md`; preserve what is known and continue from the closest durable checkpoint.

## Writing discipline

The state file should be compact enough that a fresh model can load it quickly, but detailed enough that 20+ minutes of work are not lost.

Prefer precise statements over narrative. Preserve URLs, paper titles, identifiers, query terms, numerical results, and unresolved contradictions when they are needed to reproduce or continue the work.

Git history provides older checkpoints, so `STATE.md` should describe the best current state rather than becoming an endless diary.

## Success criterion

Research OS is working if an interrupted deep-research session can be resumed in a new conversation with only this repository and negligible duplicated research.
