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
| /code-review, /simplify, /security-review | Built-in reviews: bugs, simplification, security | own review; security for code that handles input from outside | built into Claude Code |
