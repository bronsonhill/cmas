# CLAUDE.md

Orientation for working in this repo. Don't duplicate detail that lives elsewhere —
follow the pointers.

## What this is

A public, agent-assisted wiki for the CMAS (Computational Modelling and Simulation)
subject, built as a [Quartz](https://quartz.jzhao.xyz/) site over a plain Obsidian
vault. Two parts:

- `wiki/` — the content (Obsidian vault, also the Quartz build source). Structure,
  frontmatter, and page conventions: `.claude/wiki-schema.md`. Day-to-day formatting
  rules: `RULES.md`.
- `quartz/` — the site generator itself (vendored framework code). Rarely needs
  touching for wiki work; `quartz/cli/args.js` sets the default content directory
  to `wiki`.

## Before editing `wiki/`

Read `.claude/wiki-schema.md` first if you haven't already this session. The one
rule that's easy to violate by accident: **never copy University of Melbourne
course material into the repo** (slides, PDFs, recordings, transcripts) — it's
copyright and this repo is public. Source pages hold a link plus an original
summary, never the material itself.

## Skills

`.claude/skills/` has the workflows for growing and maintaining the wiki — use
them rather than hand-rolling the equivalent:

- `wiki_ingest` — add a source (lecture/paper/video) as a page + linked concepts/entities
- `wiki_lint` — health check (`python3 .claude/skills/wiki_lint/lint.py`); run before any PR touching `wiki/`
- `wiki_query` — answer a question by synthesizing across the wiki with citations
- `cue-cards` — generate spaced-repetition decks (Obsidian SR + Anki export)
- `practice-exam` — generate a typeset LaTeX practice exam from wiki content

## Commands

```bash
npm install
npx quartz build --serve       # local preview, reads from wiki/
python3 .claude/skills/wiki_lint/lint.py   # wiki health check
```

## Contributing / git

Normal branch + PR workflow, never push straight to `main` — see
`CONTRIBUTING.md` for the full flow.
