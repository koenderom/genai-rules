---
name: maintenance
description: Rules for maintaining code. Use when changing existing code: fixing bugs, extending features, refactoring.
---

# 7. Maintenance

How the code stays healthy as it changes.

1. **The boy-scout rule: leave the code a little cleaner than you found it,** limited to
   the lines a change already touches, so each change keeps one subject.
2. **Broken windows: don't leave small defects unfixed; they invite more.** A stale
   comment, a dead constant or a warning left in place makes the next one look normal.
3. **New features and bug fixes don't increase complexity.** When one would, go back to
   architecture and design first, and refactor where needed, after the owner's approval.
4. **Once published, stay backwards compatible:** interfaces, configuration files and
   stored data keep their format unless a change truly needs another. Extending is fine;
   a setting that's missing gets a sensible default, so an existing configuration keeps
   working. When compatibility must break, the release notes say so and give a migration
   guide that makes upgrading as easy as possible, preferably an automated migration.
