# Rules for building software with a generative AI assistant

Project-agnostic rules for how an AI assistant and a project's owner build software
together, from requirements to maintenance.

- **[`way_of_working.md`](way_of_working.md):** the rules for every stage, loaded in every
  conversation, and the list of stages.
- **One folder per stage, each a skill:** `requirements/`, `planning-and-tracking/`,
  `architecture-and-design/`, `implementation/`, `review-and-testing/`,
  `deployment-and-documentation/`, `maintenance/`. Each loads only when a task belongs to
  its stage. A skill stands on its own, or through a reference to a shared part; nothing
  is written twice. The folders sit at the top level, so the repository works as a
  project's `.claude/skills/`, as `~/.claude/skills/`, or as a plugin.
- **Third-party skills, one folder each,** copied in so they come along in every project:
  `clean-code/`, `python-best-practices/`. Each folder keeps its own license, and a `SOURCE.md` with
  where it comes from and how to update it.
- **[`SOURCES.md`](SOURCES.md):** where the named principles come from. For the reader;
  not loaded.
- **One folder per assistant** holds only what that assistant needs on top: for Claude,
  [`claude/CLAUDE.md`](claude/CLAUDE.md), which loads `way_of_working.md`, and
  [`claude/skills.md`](claude/skills.md), the library of review skills in regular use.
- **Use in a project:** as a git submodule at `.claude/skills`; the steps are in
  [`claude/CLAUDE.md`](claude/CLAUDE.md).
- **Size:** about 110 lines are loaded in every conversation (`way_of_working.md` and the
  Claude files); each stage skill adds 15 to 112 lines when it's needed. Claude Code's
  guidance is to keep instruction files under about 200 lines each.

## Related work

- **[Constructive Programming Manifesto (CPM)](https://github.com/cosmin-ionescu-caa/CPM)**
  by Cosmin Ionescu (CC BY 4.0): eleven principles for shaping software deliberately
  (disciplined flexibility, fixing problems at the source, preventing errors by design,
  simplifying after a feature works, ...), and four skills that apply them. A source of
  inspiration for these rules: where its principles meet them, [`SOURCES.md`](SOURCES.md)
  says so.

## License

[CC BY 4.0](LICENSE): free to use, share and adapt, also commercially, as long as you give
credit. For example: "Based on genai-rules by Koen Derom
(https://github.com/koenderom/genai-rules), CC BY 4.0", stating whether you changed it.
