# claude-skills

Divakar's personal Claude Agent Skills — reusable `SKILL.md` instructions Claude loads
automatically when a task matches, instead of being re-explained from scratch every time.

## Skills

- **[`divakar-learning-roadmap/`](./divakar-learning-roadmap/)** — Builds a Socratic learning
  roadmap for any technical topic (DSA, LLD, Java, Spring Boot, system design, etc.): problem
  before solution, one concept at a time, three-question ritual, review + mock exam. Also fixes,
  upfront, the repo topic folder name, the content shape per tier, and the Concept name each
  session will be referenced by — the identifiers the other two skills below build on.
- **[`divakar-notion-skill/`](./divakar-notion-skill/)** — Pushes session notes to Notion in a
  standard page hierarchy (topic page → session subpages, titled by Concept, never "Session N")
  and a standard note template, with a metadata header carrying the Topic/Concept/repo-shape/
  repo-target decided by the roadmap.
- **[`divakar-documentation-skill/`](./divakar-documentation-skill/)** — Organizes Divakar's
  `software-engineering` notes repo: topic folder layout, the three content shapes (book,
  topic-notes, design case-study), the PDF-to-book synthesis workflow, syncing matured Notion
  notes into the repo using the metadata above, and the "update repo" standing command.

## How they fit together

```
divakar-learning-roadmap  →  divakar-notion-skill  →  divakar-documentation-skill
     (decides topic,            (captures per-session        (consolidates into
      shape, concepts)           working notes)                software-engineering repo,
                                                                 which feeds the portfolio site)
```

The roadmap decides the repo topic folder name, content shape, and each session's Concept name
once, upfront. Notion notes carry those same identifiers in a metadata header instead of
re-deriving them. The documentation skill reads that metadata to place content directly — no
guessing, and no reference ever depends on a session number, since the `software-engineering`
repo has no concept of one.
