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
4. **Write the language's idioms:** code reads the way experienced users of the language
   write it (in Python: "pythonic" code).

## Names

5. **Plain words of the domain; no jargon, no abbreviations, no catch-all words** such as
   manager, data, info, helper, process, registry.
6. **One concept, one name, everywhere:** code, configuration keys, documents, tests,
   messages. One word per concept, one concept per word.
7. **A name says what the value is, including its criterion:** "highest score first",
   not "best first".
8. **Names follow the language's usual hints,** part of its idioms (in Python: `is_` for
   a yes/no answer, `iter_` for an iterator, `to_` for a conversion).
9. **A name never disagrees with what it holds, and doesn't encode the type** (no `_list`
   on something that may become a set), unless that is common practice in the language.
10. **A file is named after what it holds; a name carries no history** (no `_new`,
    `_clean`, `_v2`).

## Comments

11. **Comment only where it adds something: the intent and the algorithm, not the
    mechanics.** Never rephrase what the code says clearly.
12. **Every file starts with its purpose.** No workflow, phase or history information in
    source files.
13. **Written for a human reader who doesn't know the code yet:** define a term before
    using it; explain every non-obvious construct where it appears (a regular expression
    with an example of what it matches, an operator with a special meaning, a formula's
    closed form).
14. **A comment never suggests behaviour the code doesn't have.**
15. **Each explanation lives once, where its reader looks** (a setting is explained in
    the configuration file, not again in the code).
16. **Structured for readability:** concise, to the point and precise; bullets over
    prose, one idea per bullet.

## Functions and data

17. **A function is used correctly at first sight:** its name, parameters and return
    value say what it does, so the obvious call is the right one. No call that only
    works when the caller knows how the function is built inside, or in which order
    hidden steps must happen.
18. **No functions that work only through side effects:** a function returns its result;
    when changing something is its purpose, its name says so.
19. **Functions with a similar role have the same signature:** same parameters, same
    order.
20. **A helper used in one place sits next to that place,** or as close to it as the
    language allows.
21. **Normalize once, at the edge, and keep only the normalized form** (clean or
    lowercase the input where it's read, not at every use).
22. **No unexplained numbers:** a number that shapes a result is a named constant at the
    top of the file, with where its value comes from; values that depend on each other
    are derived, not set separately.
23. **General functionality is kept apart from user-specific settings:** the code never
    hard-codes anything specific to one user; that goes in configuration files, which
    may be kept private. Examples and tests use invented data.

## Errors

24. **Catch specific errors, never all of them;** when bad input is tolerated, log a
    warning, so nothing disappears silently.
25. **For compiled code, warnings are errors:** the build treats every compiler warning as
    an error, so none is left standing.

## Changes and tests

26. **One subject per change, in small steps.** A change that needs another one merged
    first says so in its title ("merge after ...").
27. **Code and its tests are written together.** Untested code doesn't exist: it gets
    tested (code that talks to an outside system: at least one real run) or removed.
28. **One-off work isn't kept:** a data migration or repair runs once, as a script outside
    the repository; its code and tests don't stay.
