---
name: requirements
description: Rules for the requirements stage. Use before building anything new: when a new function, feature or change is asked for, while requirements are elicited, written down or approved.
---

# 1. Requirements

What has to be built, agreed before anything else starts.

1. **Elaborate the requirements until no misinterpretation is possible and every unclear
   point is cleared.** Write each requirement down, including what is out of scope.
2. **Anything that can be read more than one way is asked, never guessed:** the assistant
   names the readings it sees and asks which one is meant.
3. **Ask questions until finished.** Interview, challenge and brainstorm first, one topic
   at a time; narrow the scope only once the picture is clear. The owner approves the
   result.
4. **No architecture or design before the requirements are complete and approved.**
5. **Every requirement states how it will be verified:** by a coded test, by a review, or
   by the design itself. A requirement that no coded test covers says explicitly how it
   is verified instead.
6. **Requirements about real-world input come from real samples.** Rules that interpret
   texts, data or user behaviour are derived from, and checked against, a representative
   set of real examples, never from imagination.
7. **The owner's preferences are recorded as they come up;** each becomes a requirement,
   a planned item, or both.
8. **Every non-functional requirement is made explicit too,** in this stage, like the
   functional ones and with how each is verified: quality (speed, security,
   reliability, maintainability), constraints (platforms, language and versions,
   licence, cost), and the project's own coding rules and tools.
9. **Rules for this project only are its non-functional requirements:** kept in the
   project's repository, referenced from its requirements, and loaded in every
   conversation (for Claude: imported by the project's `CLAUDE.md`). Rules for any
   project belong in the rules repository instead.
10. **How the project uses the rules repository is decided here:** a submodule in the
    project, one copy for all of the owner's projects, or an assistant's plugin.
