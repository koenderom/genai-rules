# 5. Review and testing

How every change is checked before it counts as done.

## Review

1. **Every change goes through a pull request that the owner reviews line by line.** The
   assistant never approves or merges; the owner's merge is the approval.
   - Exception, if the owner agrees: planning and status notes in a private repository
     go straight to the main branch. Anything that changes the software's behaviour,
     configuration included, still goes through a pull request.
2. **One subject per pull request, always against the main branch:** no pull request
   built on top of another, no pair that undoes and redoes the same change.
3. **Every removal is listed in the pull request's description, with its reason.**
4. **Every review comment gets an answer,** in its thread for open pull requests, in the
   conversation for merged ones. Comments are fetched again right before answering, and
   all pull requests (merged ones too) are checked for unanswered comments after every
   round of merges.
5. **No rewriting of history under review:** no force-push to a pull request being
   reviewed; bring it up to date by merging the main branch into it.
6. **After every round of merges, check the main branch:** all tests, and a real run.
7. **Pull requests are referred to by clickable links,** never by bare numbers.

## Testing

8. **Tests are code:** every implementation rule applies to them, with the same rigour.
9. **Tests check the required behaviour, not the implementation,** so a refactoring
   doesn't break them.
10. **Only the project's own code is tested:** any function taken from a mature library
    is trusted.
11. **Tests read like documentation:** named after the behaviour they check, with named
    placeholder values, visible steps, and the standard mocking tools instead of
    home-made fakes.
12. **Test data looks like the real thing,** with invented names, so every decision rule
    gets exercised.
13. **Changes that affect results are measured:** run before and after on a
    representative real data set, and report the difference.
14. **Done means implemented, tested, reviewed and documented.**
