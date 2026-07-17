# Network Q&A — My Questions, Answered From First Principles

> A personal folder for the networking questions **I actually asked**, each
> answered simply, then extended into **how real large-scale systems** (Netflix,
> YouTube, Zoom, WhatsApp, Google) solve the same problem. Diagrams included so
> the mental model sticks.

Read order doesn't matter — each file is standalone. But they build on each
other, so top-to-bottom is smoothest.

| # | Question I asked | Core concepts | File |
|---|------------------|---------------|------|
| 1 | Why doesn't my laptop keep one permanent IP address everywhere? | IP vs MAC, DHCP, private vs public IP, NAT, sessions | [`01-why-ip-address-changes.md`](./01-why-ip-address-changes.md) |
| 2 | If messages are split into packets, can't they get lost or arrive out of order? | Packets, TCP vs UDP, sequence numbers, retransmission, real-time media | [`02-packets-loss-and-ordering.md`](./02-packets-loss-and-ordering.md) |

---

## How to use this folder

1. Read the **Short answer** first — that's the 30-second version.
2. Read the **First-principles build-up** — the *why*, from the ground up.
3. Study the **diagram** until you can redraw it from memory.
4. Read **"How real systems do it at scale"** — this is where the concept meets
   production reality (millions of users).
5. Skim the **pitfalls ladder** (beginner → intermediate → senior) to see the
   mistakes people make at each level.
6. Answer the **Quick check** questions out loud.

---

## The one-line summary of both questions

> **An IP address describes *where you are on the network right now*, not *who
> your device is*. And the network makes *no promises* about delivering your data
> in order, or at all — reliability is something software (TCP) chooses to build
> on top, or deliberately skips (UDP) when speed matters more.**

Everything else in these files is a consequence of those two truths.
