# Skills library

Skills and review agents in regular use with Claude Code, and when to use them. Skills
are installed per project in `.claude/skills/<name>/SKILL.md`, or for all projects in
`~/.claude/skills/`.

- The files themselves aren't copied here: their sources state no license, so they may
  not be republished. Each line links to where the skill comes from.

| Skill or agent | What it does | When | Source |
|---|---|---|---|
| clean-code | Reviews for readability: names, small functions, clear structure, error handling (after Robert C. Martin's *Clean Code*) | own review of every change | [ClawForge](https://github.com/jackjin1997/ClawForge) |
| python-best-practices | Reviews Python for current idioms: type hints, data classes, packaging, testing | own review of Python changes | origin not recorded: to trace |
| code-reviewer | Checks a change against the project's guidelines and for bugs | own review of every change | Anthropic's pr-review-toolkit ([claude-code plugins](https://github.com/anthropics/claude-code)) |
| silent-failure-hunter | Finds errors that are caught and dropped without a trace | changes with error handling | Anthropic's pr-review-toolkit |
| comment-analyzer | Checks comments for accuracy and lasting value | changes with comments or docstrings | Anthropic's pr-review-toolkit |
| type-design-analyzer | Reviews new types for clear invariants | changes that add types | Anthropic's pr-review-toolkit |
| pr-test-analyzer | Checks whether the tests cover the required behaviour | changes with tests | Anthropic's pr-review-toolkit |
| code-simplifier | Proposes simpler versions of changed code | after a change works | Anthropic's pr-review-toolkit |
| constructive-practice | Applies the Constructive Programming Manifesto to code, documents and designs: finds speculative abstractions, over-layering, scattered safeguards, duplicated paths and accumulated workarounds | own review of a design or a larger change | [CPM](https://github.com/cosmin-ionescu-caa/CPM) (CC BY 4.0) |
| constructive-debugging | A root-cause protocol for debugging, in CPM's spirit: observations, hypotheses and verified conclusions kept apart | a bug whose cause isn't obvious | [CPM](https://github.com/cosmin-ionescu-caa/CPM) (CC BY 4.0) |
| compact-task-language, compact-task-execution | A compact notation for task briefs and designs (TASK, DO, KEEP, TEST, DEPENDS ON, ...), and executing a plan written in it | writing or carrying out an implementation brief | [CPM](https://github.com/cosmin-ionescu-caa/CPM) (CC BY 4.0) |
| /code-review, /simplify, /security-review | Built-in reviews: bugs, simplification, security | own review; security for code that handles input from outside | built into Claude Code |
