# AIIM

AIIM research workspace with a minimal crash-resilient Research OS.

> **Conversations are disposable. Research state is not.**

The only hard requirement is recovery: if a long ChatGPT research run is interrupted, a fresh conversation must be able to continue from Git without reconstructing the lost reasoning from scratch.

## Restart protocol

1. Read `RESEARCH_OS.md`.
2. Read `research/STATE.md`.
3. Continue from **NEXT EXACT ACTION**.
4. After any research progress that would be costly to reconstruct, update `research/STATE.md` before branching into more work.

Git history is the checkpoint history. Keep the system boring and durable.
