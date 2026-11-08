---
name: review-and-testing
description: Rules for review and testing. Use when preparing or reviewing a pull request, answering review comments, writing or checking tests, and before calling a change done.
---

# 5. Review and testing

How every change is checked before it counts as done.

## Review

### Who reviews

1. **Every change goes through a pull request that the owner reviews line by line.** The
   assistant never approves or merges; the owner's merge is the approval.
   - Exception, if the owner agrees: planning and status notes in a private repository
     go straight to the main branch. Anything that changes the software's behaviour,
     configuration included, still goes through a pull request.

### Before asking for a review: the assistant's own review

2. **Read the whole change as the reviewer will see it,** line by line, in the pull
   request's view.
3. **Check it against what it is for:** the requirement it implements, and how that
   requirement is verified.
4. **Check it against every implementation rule:** names,
   comments, simplicity, consistency with the rest of the code.
5. **Run all automatic checks** (formatting, linting, type checking, dead-code search,
   tests): every one passes, with no warnings left.
   - **Coding style is checked by tools, not by eye:** the language's standard formatter
     and linters (in Python, e.g. ruff), configured in the project and run on every
     change. The reviewer's attention goes to what tools can't judge.
6. **Run the review skills on the changed files** ([skills](../../claude/skills.md));
   fix each finding, or say in the description why it stays.
7. **Look for the same problem elsewhere** and fix it in the same way.
8. **Measure what the change does to the results,** when it affects them: run before
   and after on a representative real data set, and report the difference.

### The pull request

9. **Always against the main branch:** no pull request built on top of another, no
   pair that undoes and redoes the same change.
10. **Small enough to review in one sitting;** a larger change is split into pull
    requests that each stand on their own.
11. **The title says in plain words what changes,** and "merge after ..." when it depends
    on another pull request.
12. **The description gives the reviewer what the code can't:** why the change is made;
    what changed; every removal, with its reason; the measured effect; how each
    requirement is verified; and what wasn't verified.

### During the review

13. **Every review comment gets an answer in its thread,** saying what changed or why
    nothing did. Comments are fetched again right before answering. When replies in the
    threads aren't possible, the answers go in one comment on the pull request, each
    quoting the remark it answers.
14. **A comment about one place is applied everywhere it applies** (way of working, rule 5).
15. **No rewriting of history under review:** no force-push to a pull request being
    reviewed; bring it up to date by merging the main branch into it.
16. **Pull requests are referred to by clickable links,** never by bare numbers.

### After the merge

17. **Check the main branch after every round of merges:** all tests, and a real run.
18. **Check every pull request, merged ones too, for unanswered comments;** answers about
    merged pull requests go in the conversation with the owner.

## Testing

19. **Tests are code:** every implementation rule applies to them, with the same rigour.
20. **Tests check the required behaviour, not the implementation,** so a refactoring
    doesn't break them. Only the project's own code is tested: any function taken from a
    mature library is trusted.
21. **Tests read like documentation:** named after the behaviour they check, with named
    placeholder values, visible steps, and the standard mocking tools instead of
    home-made fakes. Test data looks like the real thing, with invented names, so every
    decision rule gets exercised.
22. **Tests are fast, independent, repeatable and self-validating:**
    - **fast:** the whole suite runs in seconds, so it runs on every change;
    - **independent:** no test relies on another one's result or order;
    - **repeatable:** the same result every time, anywhere: no network, no real clock, no
      random input without a fixed seed;
    - **self-validating:** each test passes or fails, with nothing to inspect by hand;
23. **A bug gets a failing test first:** reproduce it in a test that fails, then fix the
    code until the test passes. The test stays, so the same bug is found only once.
24. **Every check runs automatically on every change, and gives the same result every
    time:** tests, linters and type checks run on every push (continuous integration), on
    each supported version of the language. Dependencies are pinned, so any run can be
    reproduced; no step depends on a manual procedure.
25. **Done means implemented, tested, reviewed and documented.**
