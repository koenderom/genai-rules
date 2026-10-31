# Rules for building software with a generative AI assistant

Project-agnostic rules for how an AI assistant and a project's owner build software
together, from requirements to maintenance.

- One folder per assistant: [`claude/`](claude/) for Claude. Other assistants can get
  their own folder next to it.
- **Use in a project:** add this repository as a git submodule (e.g. at `.ai-rules/`), and
  point the project's own assistant instructions at it. For Claude, the project's
  `CLAUDE.md` imports the entry file with a line `@.ai-rules/claude/way_of_working.md`.
