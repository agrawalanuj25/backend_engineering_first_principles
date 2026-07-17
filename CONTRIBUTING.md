# Contributing — growing the knowledge base

The agent gets smarter every time a `kb/` file is added. This repo is designed
to grow **video-by-video** alongside the source playlist. You do not need to be
an expert to contribute — you need to have watched the video and understood the
concept at a first-principles level.

## The workflow (one video → one KB file)

1. **Watch** a playlist video and read any matching raw notes in `notes/`.
2. **Create** a new topic file in `kb/` named `NN-slug.md`
   (e.g. `02-http.md`, `03-routing.md`). Use the next number and a short slug.
3. **Fill it** using the template `kb/_TEMPLATE.md`. Do **not** skip the
   beginner → intermediate → advanced pitfalls sections — those are the point.
4. **Keep it language-agnostic.** Describe *mechanisms and trade-offs*, not
   framework code. A phrase like "the router maps a URL pattern to a handler"
   is fine; `app.get('/users', ...)` is not (unless contrasting what a
   framework hides).
5. **Update the index** `kb/README.md`: add the row and mark status `done`.
6. **Optionally** add the raw lecture notes to `notes/` if they aren't there.

That's it. The opencode subagent, the skill, and the portable prompt all read
`kb/` automatically — no other wiring needed.

## Rules of the road

- **First principles over recipes.** Explain *why* a thing exists before *how*.
- **Define the problem the concept solves.** If you can't state the problem,
  you don't understand the concept yet.
- **The pitfalls ladder is mandatory.** For every topic, list what goes wrong at
  beginner, intermediate, and senior level. Senior pitfalls are about
  trade-offs, edge cases at scale, and subtle failure modes — not syntax.
- **Name the hidden machinery.** For each concept, state what frameworks
  abstract away. That is the whole reason this project exists.
- **No duplication of framework docs.** We are not rewriting Express/docs.
  We teach the concept underneath.
- **Link related topics** at the bottom so the KB reads like a web, not islands.

## Good vs bad topics

| Good | Bad |
|------|-----|
| "Caching: the problem of repeated expensive work, and the strategies to avoid it" | "How to use Redis in Node" |
| "Auth: proving identity and proving permission, and why stateless is hard" | "JWT tutorial with jsonwebtoken" |
| "Serialization: crossing the wire, and why binary beats text at scale" | "JSON.parse examples" |

## What "done" means

A topic is done when a smart beginner could read it and (a) understand the
concept from scratch, (b) know the mistakes people make at their level, and
(c) understand what their framework is hiding from them.
