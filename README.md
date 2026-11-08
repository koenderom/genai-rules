# Rules for building software with a generative AI assistant

Project-agnostic rules for how an AI assistant and a project's owner build software
together, from requirements to maintenance.

- **[`way_of_working.md`](way_of_working.md):** the rules for every stage, loaded in every
  conversation, and the list of stages.
- **[`skills/`](skills/):** one skill per stage (requirements, planning and tracking,
  architecture and design, implementation, review and testing, deployment and
  documentation, maintenance). Each loads only when a task belongs to its stage. Every
  skill stands on its own, so a rule may repeat in another skill, never within one.
- **[`SOURCES.md`](SOURCES.md):** where the named principles come from. For the reader;
  not loaded.
- **One folder per assistant** holds only what that assistant needs on top: for Claude,
  [`claude/CLAUDE.md`](claude/CLAUDE.md), which loads `way_of_working.md`, and
  [`claude/skills.md`](claude/skills.md), the library of review skills in regular use.
- **Use in a project:** add this repository as a git submodule (e.g. at `.ai-rules/`).
  For Claude, the project's own `CLAUDE.md` gets one line: `@.ai-rules/claude/CLAUDE.md`.
  The stage skills must also be where the assistant looks for skills (for Claude Code:
  the project's `.claude/skills/`, the user's `~/.claude/skills/`, or a plugin); which
  of these is still open.
- **Size:** about 100 lines are loaded in every conversation (`way_of_working.md` and the
  Claude files); each stage skill adds 15 to 120 lines when it's needed. Claude Code's
  guidance is to keep instruction files under about 200 lines each.
