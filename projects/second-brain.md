# Second Brain: Compiling Agent History into Cross-Project Memory

> Standalone note-taking apps fail at capture consistency; daily Agent conversations already capture what we read, debug, build, and correct.

**Status:** Local research prototype (`Python` / `SQLite`); source remains private.  
[Back to profile](../README.md)

---

## The Problem

Reading summaries, architecture discussions, experiment failures, and explicit human corrections all enter Agent transcripts every day. Because users actively filter and react inside those sessions, conversation history is unusually high-signal—yet stays trapped inside isolated project threads.

A mechanism built for one repo may solve a bottleneck in another, and a stalled experiment can become viable months later when tooling shifts. The challenge is compiling scattered Agent logs into **traceable, non-generic cross-project hypotheses** without turning into yet another unverified LLM summary feed.

## System Pipeline

I built a local CLI compiler around Codex and Claude conversation records rather than adding another manual capture UI:

1. **Structured Session Ingestion (`SQLite`)**: Retains source, event boundaries, and timestamps while decomposing raw threads into **Problem Episodes**, existing mechanisms, and verifiable evidence quotes.
2. **Evidence & Single-Source Ablation Gates**: Requires every cross-project candidate to state what each source uniquely contributes, why timing changed, and how to test it next. Quotation verification and independent single-source controls prune candidates that merely cluster similar keywords or rephrase advice already supported by one thread alone.
3. **Resumable Checkpoints & Explicit Feedback Loop**: Persists stage state for deterministic recovery and captures explicit user decisions (`useful`, `reject`, `known`, `later`) to steer future retrieval rather than trusting raw model confidence scores.

## Concrete Validation Logic (Synthetic Case)

- **Incoming signal**: Subtitle editors repeatedly dictate text into heterogeneous desktop editors.
- **Historical capability**: A macOS voice tool supports cursor insertion across custom fields, without validated target-user retention.
- **Compiled trial**: Pair the voice insertion path with a real subtitle-editing workflow and compare completion time plus manual edit rate. If edit overhead rises, drop the segment immediately.

Notice what makes this useful: **every synthesis terminates in a falsifiable experiment**, rather than vague "synergy" bullets.

## Two Complementary Modes of Iteration

- **Cross-project synthesis**: Recombine problems, primitives, and constraints from separate tracks to spot non-obvious transfers.
- **Use-driven adaptation**: Put an existing mature tool into real daily workflows, locate exact friction points through use, adapt the mechanism, and re-verify.

The SQLite prototype currently automates indexing, episode extraction, cross-source synthesis, and evidence checks for the first path, while the second guides my product and engineering iterations directly.
