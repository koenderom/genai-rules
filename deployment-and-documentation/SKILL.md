---
name: deployment-and-documentation
description: Rules for publishing and documentation. Use when committing, merging or publishing, and when writing or changing documentation (README, guides, rules, notes).
---

# 6. Deployment and documentation

How changes are published, and how the project explains itself.

## Publishing

1. **The main branch always works.** A change that depends on another one is merged
   after it.
2. **Outside the pull-request flow, nothing is committed or pushed without the owner's
   approval each time.**
3. **Nothing user-specific is published:** user-specific configuration and notes live in
   a private repository.
4. **No repository goes public without a license chosen for it.** Without one, nobody
   may legally reuse it. The owner chooses the conditions (for example: free use, on the
   condition that the author is credited).

## Documentation

5. **Written for its reader:** public documents address any user of the project, not the
   owner; the owner's private notes don't speak of the owner in the third person.
6. **Each thing is said once,** where its reader looks; other places link to it.
7. **Bullets over prose, short lines.**
8. **No dates or names on rules.** The one exception: a measured number keeps the date it
   was measured on, next to it.
9. **Instructions that were never tried are marked as such** (an untested platform, an
   unused feature).
10. **A rule for one assistant's way of working stays out of the project's documents,**
   which every contributor reads.
