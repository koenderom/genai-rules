# Claude

Imported by the project's `CLAUDE.local.md` (`@.claude/skills/claude/CLAUDE.md`). Claude
Code loads only `CLAUDE.md`, `CLAUDE.local.md`, `AGENTS.md` and `.claude/rules/` files by
itself; this file points it at the rules for every stage, one folder up. The stage skills are one folder per
stage next to it, loaded when needed.

@../ai_chat_rules.md
@../way_of_working.md

## Claude-specific rules

1. **The rules repository is checked out under each project, at `.claude/skills`,**
   as a plain clone, invisible to the project's own git:
   - clone it once, from the project's folder:
     `git clone <repository URL> .claude/skills`;
   - a `CLAUDE.local.md` in the project's folder gets one line:
     `@.claude/skills/claude/CLAUDE.md`;
   - both go in the project's `.git/info/exclude`, git's own exclude list, which is
     never committed: `.claude/` and `CLAUDE.local.md`. Not in `.gitignore`, which
     the project's repository shows;
   - take a newer version of the rules with `git -C .claude/skills pull`.
   - Why there: Claude Code finds a skill as a direct subfolder of the project's
     `.claude/skills/` holding a `SKILL.md`, and reads `CLAUDE.local.md` as the
     user's own instructions for that project. No submodule, no symbolic links: it
     works on Windows without Developer Mode.
