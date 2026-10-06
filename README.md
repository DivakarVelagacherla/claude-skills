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

## Installing

This repo is a [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugins/create-marketplace):
each skill above (`divakar-learning-roadmap`, `divakar-notion-skill`, `divakar-documentation-skill`)
is also its own standalone plugin, so you can install just the one(s) you want — you don't have to
take all three.

### Claude Code (terminal, VS Code, JetBrains, or the Code tab in the desktop/web app)

1. Add this repo as a marketplace, once:
   ```
   /plugin marketplace add DivakarVelagacherla/claude-skills
   ```
2. Install whichever plugin(s) you want:
   ```
   /plugin install divakar-learning-roadmap@claude-skills
   /plugin install divakar-notion-skill@claude-skills
   /plugin install divakar-documentation-skill@claude-skills
   ```
   Each prompts you to pick an install scope (user / project / local), then installs on its own.

   From a plain shell (no session running), use `claude plugin marketplace add` /
   `claude plugin install` instead of the `/plugin` form — same arguments.

### Claude app (claude.ai web/mobile) and the Claude desktop app's chat

These share one account-level plugin list — add a plugin once and it's also available in Cowork,
and syncs automatically into any Claude Code session signed in to the same account.

1. Go to **[Customize → Plugins](https://claude.ai/customize/plugins)** (in claude.ai or the
   desktop app).
2. **Add → Add marketplace**, and enter `DivakarVelagacherla/claude-skills` (or the full GitHub
   URL).
3. The three plugins appear individually in the list — select **Add** on whichever one(s) you
   want.
4. In chat or Cowork, either describe the task and let Claude pick the matching skill, or type
   `/` and search for the plugin/skill by name to invoke it directly.

If you already added it in Claude Code via `/plugin marketplace add` instead, that install is
local to that machine and won't show up in claude.ai/Cowork automatically — use the
**Customize → Plugins** route separately if you want it on your account too.

> Not yet pushed: these plugin manifests currently live on the `learning-skill` branch of
> `DivakarVelagacherla/claude-skills`, not `main`. Merge/push before giving this link to anyone
> else, or they'll need to pin the branch with `DivakarVelagacherla/claude-skills#learning-skill`.
