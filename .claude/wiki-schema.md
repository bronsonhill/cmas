---
title: Content Schema
version: 0.1
domain: CMAS (Computational Modelling and Simulation) wiki
---

# Content Schema

Defines structure, conventions, and workflows for the `wiki/` wiki in this repo
(the Karpathy agentic-wiki pattern, adapted for a single-subject, multi-contributor,
public repo). All content-editing skills must follow this.

## Directory structure

```
wiki/
├── index.md          # top-level catalog — links to each section
├── log.md            # append-only chronological history of ingests/lints/queries
├── sources/           # one page per external resource (Canvas link, paper, video) — NO copyrighted text or files, links only
├── entities/          # people, models, tools, papers, software (e.g. `netlogo.md`)
├── concepts/           # ideas, mechanisms, algorithms (e.g. `cellular-automaton.md`)
└── materials/         # worked examples, derived notes, cross-source syntheses, revision material
```

There is no `raw/` directory. University of Melbourne course materials are copyright —
never copy the original PDF/slide/video into this repo. Source pages hold a link plus
an original summary written in your own words.

## Page conventions

- **Naming:** kebab-case.md (e.g. `agent-based-model.md`).
- **Frontmatter (YAML)**, required on every content page:
  ```yaml
  ---
  title: Agent-Based Model
  type: concept | entity | source | material
  tags: [abm, netlogo]
  date: 2026-07-20
  ---
  ```
  `source` pages also carry `link: <url>` (the Canvas/paper/video URL) instead of a
  copy of the material.
- **Wikilinks:** use `[[page-name]]` for all cross-references, bidirectional where
  possible.
- **Citations:** claims on concept/entity/material pages should link back to the
  `[[sources/xxx]]` page(s) they came from.
- **Images:** only original diagrams you create, or images you have rights to use —
  never scrape copyrighted course slides. Store under `wiki/materials/assets/`.

No `domain` field — this wiki covers one subject (CMAS), so section (`sources` /
`entities` / `concepts` / `materials`) is enough to scope content. (The upstream
personal-wiki version of this schema used a multi-subject `domain` field; it's
deliberately dropped here.)

## Workflows (via `.claude/skills/`)

- **wiki_ingest** — add a new source: write the source stub (link + original
  summary), create/update concept and entity pages, refresh `wiki/*/index.md`
  and `wiki/log.md`.
- **wiki_query** — answer a question by reading `wiki/index.md` first, then
  synthesizing across pages with citations; file valuable outputs back to
  `wiki/materials/`.
- **wiki_lint** — check dangling links, orphans, index drift, frontmatter issues;
  update `wiki/log.md` and write a report to `wiki/lint-reports/`.
- **cue-cards** — generate spaced-repetition cards from any content page, output in
  Obsidian Spaced Repetition format with an Anki-importable export alongside it.
- **practice-exam** — generate a typeset practice exam (LaTeX/PDF) drawing questions
  from `wiki/`, optionally mimicking a real past-exam's structure.
- **Schema evolution** — update this file when conventions change; contributors and
  the agent co-maintain it. A schema change should land in the same PR as any script
  update it implies (e.g. `wiki_lint/lint.py`).

## Obsidian / Quartz integration

- The repo is a plain Obsidian vault at `wiki/` and is also built as a public
  static site with [Quartz](https://quartz.jzhao.xyz/) (`npx quartz build --serve`).
  Both consume the same `[[wikilinks]]` syntax — don't use Obsidian-only syntax that
  Quartz can't render (check `quartz/plugins/` if unsure).
- `wiki/` is versioned as part of this same git repo (not a separate wiki repo) —
  see `CONTRIBUTING.md` for the PR workflow.

## Tips

- Ingest one source at a time; give a human (you, or a PR reviewer) a chance to
  sanity-check before scaling up.
- Run `wiki_lint` after every ingest and periodically (e.g. weekly, or as part of
  PR review) as the wiki grows.
- Start small — a couple of concept pages fleshed out well beat a dozen stubs.

This schema is co-evolved by contributors and the agent. Extend it as conventions
solidify.
