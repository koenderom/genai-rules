# Claude

Imported by the user's own `~/.claude/CLAUDE.md` (`@~/.claude/skills/claude/CLAUDE.md`).
Claude Code loads only `CLAUDE.md`, `AGENTS.md` and `.claude/rules/` files by itself; this
file points it at the rules for every stage, one folder up. The stage skills are one folder per
stage next to it, loaded when needed.

@../ai_chat_rules.md
@../way_of_working.md

## Claude-specific rules

1. **The rules repository is a clone at `~/.claude/skills`,** one copy for all
   projects:
   - clone it once: `git clone <repository URL> ~/.claude/skills`;
   - the user's own `~/.claude/CLAUDE.md` gets one line:
     `@~/.claude/skills/claude/CLAUDE.md`;
   - take a newer version of the rules with `git -C ~/.claude/skills pull`.
   - Why there: Claude Code finds a personal skill as a direct subfolder of
     `~/.claude/skills/` holding a `SKILL.md`, in every project, and nothing in a
     project shows it. No symbolic links, so it works on Windows without Developer
     Mode.
   - A project that chooses to carry the rules (way of working, "The rules in a
     project"): a git submodule at the project's `.claude/skills`, and the line
     `@.claude/skills/claude/CLAUDE.md` in the project's `CLAUDE.md`.
