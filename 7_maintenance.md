# 7. Maintenance

How the code stays healthy as it changes.

1. **The boy-scout rule: leave the code a little cleaner than you found it,** limited to
   the lines a change already touches, so each change keeps one subject.
2. **Don't leave small defects unfixed:** a stale comment, a dead constant or a warning
   left in place invites more of them.
3. **Least privilege:** every part gets only the access it needs; credentials come from
   the environment and are read only by the part that uses them.
4. **New features and bug fixes don't increase complexity.** When one would, go back to
   architecture and design first, and refactor where needed, after the owner's approval.
