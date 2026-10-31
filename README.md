# Rules for building software with a generative AI assistant

Project-agnostic rules for how an AI assistant and a project's owner build software
together, from requirements to maintenance.

- **The rules** are in this folder: [`way_of_working.md`](way_of_working.md) connects
  the seven stage files and loads them.
- **One folder per assistant** holds only what that assistant needs on top: for Claude,
  [`claude/CLAUDE.md`](claude/CLAUDE.md), which loads the general rules, and
  [`claude/skills.md`](claude/skills.md), the library of skills in regular use.
- **Use in a project:** add this repository as a git submodule (e.g. at `.ai-rules/`).
  For Claude, the project's own `CLAUDE.md` gets one line: `@.ai-rules/claude/CLAUDE.md`.
- **Size:** everything is loaded into every session (about 300 lines). Claude Code's
  guidance is to keep instructions under about 200 lines per file; if adherence drops,
  rules that matter for some files only can move to path-scoped rules.
