---
name: divakar-documentation-skill
description: Organize and write technical notes/documentation the way Divakar structures his notes repos (modeled on the `software-engineering` repo). Use whenever Divakar is adding a new topic/book/notes folder to a personal knowledge repo, asking "update repo" to bring recent changes into line with conventions, synthesizing a book from source PDFs, or asking how to structure/split/name a new set of technical notes. Captures his exact rules: one top-level folder per topic (kebab-cased title as the folder name, stable once created), three content shapes (book style, topic-notes style, design case-study style) picked by source material, the PDF-to-book synthesis workflow, and the "update repo" standing command.
---

# Divakar's Documentation Skill

## Who This Is For
Divakar Velagacherla. Keeps personal software-engineering notes in a repo that acts as the
content source for the "Learning" section of his portfolio site — closer to a CMS relationship
than a one-off copy-paste. That's why structure and naming matter more here than in a typical
notes repo: whatever ingests the content needs the shape to stay predictable across topics.

---

## Repo Layout Rules (Non-Negotiable)

1. **One top-level folder per topic/book.** New topics get a new top-level folder when work on
   them starts — never nest a new topic inside an existing one.
2. **Folder name = that book/topic's actual title, kebab-cased.** E.g. a book titled "Internals
   of Core Java" lives in `internals-of-core-java/`, not `java/` or any other shorthand. The
   portfolio derives its display name and routing directly from the folder name — name it right
   the first time.
3. **Folders are stable once created — never rename or restructure existing ones** on your own
   judgment. Adding a new topic should always just mean adding a new folder; reorganizing old
   ones is exactly the churn that setup avoids. If an existing folder's structure looks wrong,
   ask before changing it.
4. **Every topic folder has its own `README.md`** acting as that topic's table of contents/index.
5. **The root `README.md` stays a short, high-level index** pointing at each topic folder — it
   never accumulates topic-specific detail (that belongs in the topic's own README).

---

## Three Content Shapes — Pick Based on the Source Material

Never force one shape onto content that doesn't match it. If it's genuinely unclear which shape
fits, ask once rather than guessing.

### 1. Book style
Use when the source material is a single flowing narrative (Part → Chapter → Section).
- Split into **one file per major Part/Section** — never one file per chapter or subtopic. Keep
  the split coarse: "one giant topic per page," not maximum granularity.
- Each part file keeps its original heading levels.
- The folder's `README.md` holds the book's intro/how-to-read-this plus a table of contents
  linking to each part file in order.
- Default to **flowing narrative prose over Q&A formatting** — read like a technical book (e.g.
  Alex Xu's *System Design Interview*), not an interview crib sheet. This carries forward to
  every new book unless told otherwise.

### 2. Topic-notes style
Use when the source material is a set of discrete, mostly-independent topics.
- Keep it as many small flat files grouped into subfolders by theme.
- The folder's `README.md` is a roadmap/checklist linking to each file.

### 3. Design case-study style
Use for one concrete, practiced example applying the other two shapes (e.g. a real system design
worked through for interviews).
- One markdown file per case study, flat — no subfolder per case.
- Any diagrams live alongside the file, filename matching the case's markdown file (e.g.
  `url-shortener.md` + `url-shortener.png`), referenced from the markdown as a normal image link.
- The folder's `README.md` lists each case as a checklist item.

---

## Book-Synthesis Workflow — Producing a Book from Source PDFs

Follow this sequence whenever source material is a pile of near-duplicate PDFs, so the cost
doesn't balloon the way a naive "read every PDF in full" pass does:

1. **Hash every PDF before reading any of them**: `md5 *.pdf` (or `shasum`), for the whole folder
   up front, not file-by-file. Files with identical hashes are byte-identical — read exactly one
   copy, skip the rest outright.
2. **Run every PDF through `pdftotext -layout` into scratchpad `.txt` files, then hash those
   `.txt` files too.** This catches near-duplicates that share a filename pattern (`Foo.pdf` /
   `Foo-1.pdf`) but aren't byte-identical because of embedded metadata or one extra page.
   Comparing extracted *text* costs nothing in model tokens — it's a shell command — and groups
   files by actual prose content instead of guessing from filenames. Only read (via the file-read
   tool) one `.txt` file per content-hash group, and never the original PDF once its text has
   been extracted this way.
3. **Extract straight to scratchpad notes per source file, in condensed form** — short bullets
   capturing substance, not verbatim transcription. These scratchpad notes are what actually get
   used to write the book; raw PDF reads earlier in the conversation shouldn't need revisiting.
   Write one scratchpad file per source PDF as you finish it rather than holding everything in
   context until the end.
4. **Write the book in a single pass** from the scratchpad notes once every source is extracted —
   don't re-read the original PDFs or scroll back through conversation history. Organize by
   topic, not by source document or original question order. Merge the same question asked at
   multiple difficulty levels into one deepest treatment instead of repeating it per level.

---

## "Update Repo" — Standing Command

When Divakar says **"update repo,"** treat it as a request to bring whatever was just added into
line with these conventions, without re-explaining what's wrong each time:

1. Run `git status` to find new/untracked and modified files since the last commit.
2. For each new file, check it against the relevant convention above — topic folder naming
   (kebab-case, matches the actual title), the correct content shape for that folder, filename
   casing/spelling, and image colocation/naming for design case studies (`<name>.md` +
   `<name>.png`, flat, no `images/` subfolder).
3. Fix naming/placement issues directly (rename, move, fix stray headers duplicating the title,
   etc.) rather than just flagging them.
4. Update the relevant index files so new content is actually linked, not just present on disk —
   the topic's own `README.md`, and any parent-level README that also lists that content (e.g. a
   design added under a case-study folder may need linking from that topic's top `README.md` as
   well as the case-study folder's own one).
5. Only ask before acting if something is genuinely ambiguous (new content doesn't obviously fit
   any existing shape) — don't ask for confirmation on mechanical renames/relinks that directly
   follow the rules already written down here.

---

## Known Preferences (Apply Without Re-Asking)

- Consolidated notes should read like a book, not a Q&A list.
- Book-style content gets split coarsely (by Part/Section) if split at all — never one file per
  chapter or subtopic.
- If a new book's source material doesn't obviously fit one of the shapes above, ask once via a
  clarifying question rather than assuming an existing approach transfers unchanged.
- Repo structure exists to serve an automated downstream consumer (the portfolio site) — treat
  predictability and stability of existing structure as higher priority than local tidiness.
