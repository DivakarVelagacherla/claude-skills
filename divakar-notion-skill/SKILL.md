---
name: divakar-notion-skill
description: Push structured notes to Divakar's Notion workspace using his standard page hierarchy and session note template. Use whenever Divakar asks to push/save notes to Notion, at Stage 7 ("Push to Notion") of a divakar-learning-roadmap session, or when deciding how to lay out a new Notion page for a topic. Also use when preparing to consolidate mature Notion notes into the software-engineering repo — this skill defines the source format before that hand-off to divakar-documentation-skill.
---

# Divakar's Notion Skill

## Who This Is For
Divakar Velagacherla. Uses Notion as the working/raw capture layer for learning sessions —
notes land here first, in a consistent template, before any of them are mature enough to become
part of his consolidated `software-engineering` notes repo.

---

## Page Hierarchy

- **Each topic gets its own Notion page**, titled with the same repo topic folder name decided
  in `divakar-learning-roadmap` Step 1 (display case is fine in Notion, e.g. "Internals of Core
  Java" — but it must kebab-case to exactly the repo folder name, `internals-of-core-java`, with
  no second spelling). One page per topic, not one page per concept.
- **Each session on that topic is a subpage inside it, titled with the Concept name — never
  "Session N."** The session number is stored as a page property (for ordering/scheduling) but
  is never the title and never how the subpage gets referenced.
- Push after a session's three-question ritual passes, not during — notes should reflect
  understanding already reached, not function as a crutch while still figuring it out.

---

## Naming Rule — Concept, Never Session Number

This is the rule that keeps Notion and the `software-engineering` repo from drifting apart: the
repo has no idea what "session 12" means, so that reference becomes dead the moment it leaves
Notion. To prevent that:

- **Never write "see session N" anywhere** — not in a note body, not in a cross-link, not when
  talking about the material out loud. Always name (and link to) the concept itself.
- The session number is metadata about *when* something was studied, not *what* it is. It can
  appear in the metadata header below for scheduling context, but it is never a lookup key.
- If Divakar refers to "session 12" when asking for something, resolve it to the concept name
  via the roadmap's session list before doing anything with it — don't carry "session 12" forward
  into a note, a repo file, or any other artifact.

---

## Standard Session Note Template

Every note starts with a metadata header carrying the identifiers decided in
`divakar-learning-roadmap` — this is what lets `divakar-documentation-skill` consolidate later
without re-deriving or guessing anything:

```
**Topic:** <Topic title> (repo folder: `<kebab-case-topic-folder>`)
**Concept:** <Concept name — matches the roadmap's session list exactly>
**Session #:** <N>  — scheduling only, never used as a reference
**Repo content shape:** book-style | topic-notes-style | design-case-study
**Repo target:** <topic-folder>/<expected file or part>.md

## The One-Line Summary
> [one sentence that captures the concept and its tradeoff]

## The Problem
[scenario without jargon]

## What [Concept] Is
[explanation with analogy]

## Key Tradeoffs
[comparison table or bullet list]

## Three-Question Ritual
| Question | Answer |
|---|---|
| What problem does it solve? | ... |
| What breaks without it? | ... |
| When NOT to use it? | ... |

## Tool/AWS Equivalents
[mapping table]
```

Every section is required unless genuinely not applicable (e.g. no tool/AWS equivalent exists for
a purely theoretical concept) — don't silently drop a section because it's harder to fill in.

---

## Book/Reference Integration

When a session has a parallel reference book or resource (e.g. Alex Xu for system design):
- Read the reference **after** the session, not before, and **section by section** as each topic
  is covered — not the full chapter upfront.
- Compare: "what was different or new from what we covered?"
- Only fold that comparison into the Notion note after it's been made explicitly — never
  transcribe the reference straight into the note.

---

## Alignment with `divakar-documentation-skill`

Notion and the `software-engineering` repo are two stages of the same pipeline, not two copies
of the same thing — keep their shapes distinct on purpose:

- **Notion = per-session working notes.** Structured as Q&A/ritual (one-line summary → problem →
  concept → tradeoffs → three-question table → tool equivalents). Intentionally granular: one
  subpage per session. This is closest in spirit to the repo's **topic-notes style** — discrete,
  mostly-independent units — not to its book style.
- **The repo = consolidated, synthesized knowledge.** Once enough sessions on a topic exist in
  Notion, consolidating them into `software-engineering/` is a separate, deliberate step — never
  an automatic mirror of whatever is in Notion at a given moment.

The content shape and repo target in each note's metadata header are decided once, upfront, in
`divakar-learning-roadmap` — never re-derived or guessed at consolidation time. That's what
makes the hand-off mechanical instead of interpretive:
- **Building toward a single flowing narrative** (e.g. a book like *Internals of Core Java*) —
  **convert** the Q&A/ritual structure into flowing prose. Don't carry the three-question tables
  or "One-Line Summary" headers into the book; the ritual is a learning tool, not target prose.
- **A set of discrete, mostly-independent topics** (e.g. `system-design/basics/`) — the
  per-session structure can survive largely as-is, reshaped into the repo's topic-notes file
  format.
- Either way, once content lands in the repo, the repo's own conventions apply (kebab-case topic
  folder matching the real title, topic `README.md` as index, stable folder names) — Notion's
  internal structure doesn't need to satisfy those naming rules, since it's the pre-repo working
  layer, not the ingested content itself.
