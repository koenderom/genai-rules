# 4. Implementation

How the code is written. The design rules ([3](3_architecture_and_design.md)) apply here
too, at the level of each function.

## Simplicity

1. **Don't reinvent the wheel:** use the standard library and mature packages; write
   project code only for what they don't cover, and keep that code to a minimum.
2. **Simplicity beats cleverness:** the version a reader follows at first sight wins, even
   if it's longer. A clever construction needs a reason the reader can check, stated next
   to it.
3. **No code that isn't needed now:** no options, parameters or abstractions nobody asked
   for.

## Names

4. **Plain words of the domain; no jargon, no abbreviations, no catch-all words** such as
   manager, data, info, helper, process, registry.
5. **One concept, one name, everywhere:** code, configuration keys, documents, tests,
   messages. One word per concept, one concept per word.
6. **A name says what the value is, including its criterion:** "highest score first",
   not "best first".
7. **Names follow the language's usual hints** (for example, in Python: `is_` for a
   yes/no answer, `iter_` for an iterator, `to_` for a conversion).
8. **A name never disagrees with what it holds, and doesn't encode the type:** no
   `_list` on something that may become a set.
9. **A file is named after what it holds; a name carries no history** (no `_new`,
   `_clean`, `_v2`).

## Comments

10. **Comment only where it adds something: the intent and the algorithm, not the
    mechanics.** Never rephrase what the code says clearly.
11. **Every file starts with its purpose.** No workflow, phase or history information in
    source files.
12. **Written for a human reader who doesn't know the code yet:** define a term before
    using it; explain every non-obvious construct where it appears (a regular expression
    with an example of what it matches, an operator with a special meaning, a formula's
    closed form).
13. **A comment never suggests behaviour the code doesn't have.**
14. **Each explanation lives once, where its reader looks** (a setting is explained in
    the configuration file, not again in the code).
15. **Bullets over prose:** one idea per bullet.

## Functions and data

16. **No functions that work only through side effects:** a function returns its result;
    when changing something is its purpose, its name says so.
17. **Functions with the same role have the same signature:** same parameters, same
    order.
18. **Normalize once, at the edge, and keep only the normalized form** (clean or
    lowercase the input where it's read, not at every use).
19. **No unexplained numbers:** a number that shapes a result is a named constant at the
    top of the file, with where its value comes from; values that depend on each other
    are derived, not set separately.

## Errors

20. **Catch specific errors, never all of them;** when bad input is tolerated, log a
    warning, so nothing disappears silently.

## What doesn't stay in the code

21. **Untested code doesn't exist:** it gets tested (code that talks to an outside
    system: at least one real run) or removed.
22. **One-off work isn't kept:** a data migration or repair runs once, as a script outside
    the repository; its code and tests don't stay.
23. **No personal data in published code:** examples and tests use invented people and
    companies.
