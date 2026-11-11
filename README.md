# Rules for working with a generative AI assistant

Generic rules for interacting with an AI assistant, in any conversation, and for
building software with one, from requirements to maintenance.

- **[`ai_chat_rules.md`](ai_chat_rules.md):** rules for AI chat assistants: how the
  assistant answers, in any conversation. Not tied to software: usable on its own as the
  instructions or memory of any chat assistant.
- **[`way_of_working.md`](way_of_working.md):** the rules for every stage of building
  software, and the list of stages. Both files are loaded in every conversation.
- **One folder per stage, each a skill:** `requirements/`, `planning-and-tracking/`,
  `architecture-and-design/`, `implementation/`, `review-and-testing/`,
  `deployment-and-documentation/`, `maintenance/`. Each loads only when a task belongs to
  its stage. A skill stands on its own, or through a reference to a shared part; nothing
  is written twice. The folders sit at the top level, so the repository works as a
  project's `.claude/skills/`, as `~/.claude/skills/`, or as a plugin.
- **Third-party skills, one folder each,** copied in so they come along in every project:
  `clean-code/`, `python-best-practices/`. Each folder keeps its own license, and a `SOURCE.md` with
  where it comes from and how to update it.
- **[`SOURCES.md`](SOURCES.md):** where the named principles come from, and related work.
  For the reader; not loaded.
- **One folder per assistant** holds only what that assistant needs on top: for Claude,
  [`claude/CLAUDE.md`](claude/CLAUDE.md), which loads `ai_chat_rules.md` and
  `way_of_working.md`, and [`claude/skills.md`](claude/skills.md), the library of review
  skills in regular use, read when the review skill links to it, not loaded in every
  conversation.
- **Use in a project:** as a git submodule at `.claude/skills`; the steps are in
  [`claude/CLAUDE.md`](claude/CLAUDE.md).

## License

[CC BY 4.0](LICENSE): free to use, share and adapt, also commercially, as long as you give
credit. For example: "Based on genai-rules by Koen Derom
(https://github.com/koenderom/genai-rules), CC BY 4.0", stating whether you changed it.
