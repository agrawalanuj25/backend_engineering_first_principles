# Backend Engineering — From First Principles

A language-agnostic knowledge base + reusable AI agent for **backend engineering
from first principles**: building reliable, scalable, fault-tolerant, maintainable,
and efficient systems — without being locked to any framework or language.

> **Why this exists.** Most people learn backend *through* a framework (Express,
> Spring, Rails). That creates blind spots: you solve problems in the framework's
> vocabulary and never see the machinery it hides. This project teaches the
> **concepts underneath** — HTTP, routing, serialization, auth, middleware,
> databases, caching, queues, observability, scaling — independent of any tool,
> so the knowledge transfers across languages and survives framework churn.

This repository is the foundation of an open-source agent you can use for years:
as you watch the source playlist, one knowledge file is added per video, and the
agent "trains" by reading those files.

---

## What's inside

```
backend_engineering_first_principles/
├── README.md                 # This file
├── LICENSE                   # MIT
├── CONTRIBUTING.md           # How to extend the KB video-by-video
│
├── agents/
│   └── backend-fp.system.md # Portable system prompt (paste into any LLM)
│
├── .opencode/
│   ├── agents/
│   │   └── backend-fp.md    # opencode subagent (invoke with @backend-fp)
│   └── skills/
│       └── backend-fp/       # opencode skill (auto-loads when relevant)
│           └── SKILL.md
│
├── kb/                       # THE KNOWLEDGE BASE (grows video-by-video)
│   ├── README.md            # Index: video → KB file → status
│   ├── _TEMPLATE.md        # Topic template (the "training" format)
│   └── 01-what-is-a-backend.md
│
└── notes/                   # Raw study notes from the playlist (source material)
```

## How the "agent" is delivered (3 forms, one brain)

The **same first-principles knowledge** is exposed three ways so you can use it
anywhere:

| Form | File | How to use |
|------|------|------------|
| **Portable system prompt** | `agents/backend-fp.system.md` | Copy into ChatGPT, Claude, or any LLM chat to get the persona + KB instructions. |
| **opencode subagent** | `.opencode/agents/backend-fp.md` | In opencode, type `@backend-fp <question>`. It reads `kb/` on demand. |
| **opencode skill** | `.opencode/skills/backend-fp/SKILL.md` | Auto-loads when you ask backend questions from first principles. |

All three point at `kb/` as the single source of truth. Add a file to `kb/`
and **every** form of the agent gets smarter — that is the "self-training."

## Design principles (non-negotiable)

1. **Language-agnostic.** Concepts, not `app.get('/users')`. Code appears only
   as abstract mechanisms, not framework recipes. (Per the source course, the
   eventual Node/Go code tracks live elsewhere; this repo stays conceptual.)
2. **First principles first.** Every topic starts from *what problem are we
   solving* and the *smallest true model*, then layers complexity.
3. **The pitfalls ladder.** Each topic documents mistakes at **beginner →
   intermediate → advanced/senior** level, because knowing *what breaks* is half
   of engineering.
4. **Pull back the curtain.** Explicitly state what frameworks hide for each
   concept, so the black box becomes visible.
5. **Grows forever.** One file per source video; never "finished."

## The learning order (from the source roadmap)

Foundations (HTTP, routing, serialization, auth, validation) → request pipeline
(middleware, context, handlers) → data & async (databases, caching, queues,
search) → resilience/ops (errors, logging, security, scaling) → ecosystem
(testing, OpenAPI, webhooks, DevOps). See `kb/README.md` for the live index.

## Source

Primary source: the *Backend from First Principles* playlist by **Sriniously**
(YouTube). `notes/` contains raw lecture notes; `kb/` contains the curated,
agent-trained knowledge derived from them.

## License

MIT — see [LICENSE](./LICENSE). Free to use, fork, and ship.
