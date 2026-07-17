<!--
  TEMPLATE for a knowledge-base topic.
  Copy to kb/NN-slug.md, fill every section, keep it language-agnostic.
  See CONTRIBUTING.md for the workflow and rules.
-->

# Topic: <Human-Readable Name>

> **Source:** playlist video <N> — "<title>" (<url>)  ·  roadmap module <X>
> **Level:** foundation | core | advanced
> **Prerequisites:** <other KB topics this builds on, or "none">
> **Status:** done

---

## 1. TL;DR (read this if you read nothing else)
One or two sentences stating the single most important idea.

## 2. The Problem This Solves
What real difficulty exists before this concept? Why did engineers need it?
Frame it as a problem statement, not a definition.

## 3. First-Principles Mental Model
The **smallest true model** a beginner can hold. No jargon, no framework names.
Use a mermaid diagram if a flow is involved.

```mermaid
flowchart LR
    A[...] --> B[...]
```

## 4. Core Concepts (language-agnostic)
Define the key ideas in plain English. Tables are good for terminology.

| Concept | Plain-English Meaning |
|---------|----------------------|
| ... | ... |

## 5. How It Fits the Request Lifecycle
Where does this sit between "client sends a request" and "client gets a
response"? How does it relate to neighboring topics? Link them.

## 6. Beginner Mistakes
The flaws juniors hit: misunderstandings of the model, obvious wrong turns,
"it works on my machine" traps.

- ...
- ...

## 7. Intermediate Mistakes
Working-but-fragile designs: missing failure modes, ignoring concurrency,
no observability, premature optimization, copy-paste without understanding.

- ...
- ...

## 8. Advanced / Senior-Level Pitfalls & Trade-offs
Trade-offs, scale limits, subtle distributed-systems failures, cost and
observability blind spots. This is where "senior" shows.

- ...
- ...

## 9. Advanced Industry Practice (Real-World, Beyond the Course)

Go past the source video. Document how this concept is actually engineered in
production systems at scale, with concrete, named examples where possible.

- **Production patterns:** how mature teams implement this in real infrastructure
  (e.g., exactly-once via idempotency keys + dedupe tables; cache hierarchies
  browser → CDN → app → DB; bulkheads/circuit breakers in service meshes).
  Reference real systems (Kafka, S3, DynamoDB, Envoy, Kubernetes…) only to
  illustrate the universal pattern, not as a tutorial.
- **Trade-offs at scale:** cost, latency, and operational burden; where the
  "textbook" model breaks with millions of users, multi-region, or partial
  failure as the default.
- **What engineers actually ship:** the pragmatic compromise between ideal design
  and reality (e.g., eventual consistency for a feed, strong consistency for
  money).
- **Failure modes seen in industry:** incidents, outages, or footguns specific to
  this concept at scale, and the guardrail that prevents them.

Source this from first principles + real-world knowledge; mark anything
uncertain rather than inventing specifics.

## 10. How Frameworks Hide This (the curtain)
What does Express / Spring / Rails / etc. abstract away for this concept?
Name the machinery so it's no longer a black box.

## 11. Self-Check / Interview Questions
3–6 questions that prove understanding at increasing depth.

1. ...
2. ...

## 12. Related Topics
- `NN-other.md` — <one line on the relationship>
