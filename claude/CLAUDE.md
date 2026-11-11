# Claude

Imported by a project's own `CLAUDE.md` (`@.claude/skills/claude/CLAUDE.md`). Claude Code
loads only `CLAUDE.md`, `AGENTS.md` and `.claude/rules/` files by itself; this file points
it at the rules for every stage, one folder up. The stage rules are skills, one folder
per stage next to it, loaded when needed.

@../ai_chat_rules.md
@../way_of_working.md

## Claude-specific rules

1. **The rules repository is a git submodule at `.claude/skills`** in every project that
   uses it:
   - add it once: `git submodule add <repository URL> .claude/skills`;
   - the project's own `CLAUDE.md` gets one line: `@.claude/skills/claude/CLAUDE.md`;
   - clone the project with `git clone --recurse-submodules`; take a newer version of the
     rules with `git submodule update --remote .claude/skills`.
   - Why there: Claude Code finds a skill only as a direct subfolder of `.claude/skills/`
     holding a `SKILL.md`. The submodule needs no symbolic links, so it works on Windows
     without Developer Mode.
   - The other ways, if the project's requirements choose them: a clone at
     `~/.claude/skills` (one copy for all projects), or a Claude Code plugin.
