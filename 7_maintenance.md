# 7. Maintenance

How the code stays healthy as it changes.

1. **The boy-scout rule: leave the code a little cleaner than you found it,** limited to
   the lines a change already touches, so each change keeps one subject.
2. **Broken windows: don't leave small defects unfixed; they invite more.** A stale
   comment, a dead constant or a warning left in place makes the next one look normal.
3. **Least privilege:** every part gets only the access it needs; credentials come from
   the environment and are read only by the part that uses them.
4. **New features and bug fixes don't increase complexity.** When one would, go back to
   architecture and design first, and refactor where needed, after the owner's approval.

## Sources

- **The boy-scout rule:** Robert C. Martin, *Clean Code* (2008), chapter 1.
- **Broken windows:** Andrew Hunt and David Thomas, *The Pragmatic Programmer* (1999),
  after James Q. Wilson and George Kelling's "broken windows" theory (1982).
- **Least privilege:** Jerome Saltzer and Michael Schroeder, "The Protection of
  Information in Computer Systems", *Proceedings of the IEEE* (1975).
