# CLAUDE.md — Project Context

This repo is a **personal learning knowledge base + AI tutor** for mastering
**backend engineering from first principles**, aimed at reaching top-tier
backend / systems / HFT roles. It is documentation, not an application — there is
no build/test/run step.

## The learner

A motivated self-directed learner rebuilding CS fundamentals from the ground up,
targeting **top-tier backend / systems / HFT roles**. New to the systems layer (computer
networks, OS, computer architecture). **Precision matters more than
hand-holding** — a wrong simplification is worse than a hard truth.

## Repository map

| Folder | Purpose |
|--------|---------|
| `ROADMAP.md` | The master plan: two-track path (applied backend + core systems fundamentals) toward the HFT/core-backend goal. Start here. |
| `kb/` | Curated, rigorous topic files (index: `kb/README.md`). Canonical source of truth. Each meets the `kb/01` standard: TL;DR → problem → smallest-true-model → concepts → lifecycle fit → beginner/intermediate/senior pitfalls ladder → "how frameworks hide this" → self-check. |
| `foundations/` | Plain-English vocabulary (read 01→15 in order). The on-ramp. |
| `notes/` | Lecture notes from the source playlist (raw + deepened). |
| `network-qa/` | Deep-dive Q&A on networking puzzles. |
| `agents/backend-fp.system.md` | The tutor persona — single source of truth for how the AI teaches. |
| `.claude/agents/backend-fp.md` | Claude Code subagent (`@backend-fp`). Also exists as an opencode agent/skill under `.opencode/`. |

## How to help in this repo

- **Teaching/answering backend questions:** adopt the persona in
  `agents/backend-fp.system.md` (or invoke `@backend-fp`). Read the relevant
  `kb/`/`foundations/`/`notes/` file first; teach from first principles; use the
  beginner→intermediate→senior pitfalls ladder; expose what frameworks hide.
- **Adding a new KB topic:** match the `kb/01-what-is-a-backend.md` structure
  exactly, update `kb/README.md`'s status, and cross-link related files. A file
  without the pitfalls ladder and the "how frameworks hide this" section is not
  done.
- **Accuracy bar:** this is study material for a systems/HFT target. Verify
  networking/OS/architecture claims; state the precise version even when
  simplifying. Prefer correct-and-small over large-and-fuzzy.
- **Style:** language-agnostic concepts, not framework recipes. Mermaid diagrams
  for flows, tables for comparisons, concise prose.
