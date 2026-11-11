---
name: implementation
description: Rules for writing code. Use whenever code, tests or code comments are written or changed.
---

# 4. Implementation

How the code is written. The architecture and design rules apply here too, at the level of
each function.

## Simplicity

1. **Simplicity beats cleverness:** the version a reader follows at first sight wins, even
   if it's longer. A clever construction needs a reason the reader can check, stated next
   to it.
2. **Explicit is better than implicit** (the Zen of Python): what code depends on and
   what it does shows where it's used: behaviour is stated, not left to a default the
   reader must know. This rule
   itself is an example: written out, rather than assumed from "keep it clear".
3. **Write the language's idioms:** code reads the way experienced users of the language
   write it (in Python: "pythonic" code).

## Names

4. **Words of the domain, no catch-all words** such as manager, data, info, helper,
   process, registry.
5. **One concept, one name, everywhere:** code, configuration keys, documents, tests,
   messages. One word per concept, one concept per word.
6. **A name says what the value is, including its criterion:** "highest score first",
   not "best first".
7. **Names follow the language's usual hints,** part of its idioms (in Python: `is_` for
   a yes/no answer, `iter_` for an iterator, `to_` for a conversion).
8. **A name never disagrees with what it holds, and doesn't encode the type** (no `_list`
   on something that may become a set), unless that is common practice in the language.
9. **A file is named after what it holds; a name carries no history** (no `_new`,
    `_clean`, `_v2`).

## Comments

10. **Comment only where it adds something: the intent and the algorithm, not the
    mechanics.** Never rephrase what the code says clearly. What a caller needs to know
    is stated: preconditions, the result when it fails, side effects. An assumption is
    an unwritten precondition: write it down as one.
11. **Every file starts with its purpose.** No workflow, phase or history information in
    source files.
12. **Written for a human reader who doesn't know the code yet:** define a term before
    using it; explain every non-obvious construct where it appears (a regular expression
    with an example of what it matches, an operator with a special meaning, a formula's
    closed form).
    - Code that reads an outside format (a web page, another system's records) describes
      that format where it's read: how it's built and which parts are used, with a real
      example.
13. **A comment never suggests behaviour the code doesn't have.**
14. **Each explanation lives once, where its reader looks** (a setting is explained in
    the configuration file, not again in the code).
15. **Concise, to the point and precise.**

## Functions and data

16. **A function is used correctly at first sight (the principle of least astonishment:
    code does what its name and shape suggest):** its name, parameters and return value
    say what it does, so the obvious call is the right one. No call that only works when
    the caller knows how the function is built inside, or in which order hidden steps
    must happen.
17. **No functions that work only through side effects; a function either answers or acts
    (command-query separation):** a question returns its answer and changes nothing; a
    command changes something and its name says so. An exception (e.g. "pop": remove and
    return) is named so the effect is visible at the call site.
18. **Every function declares its types,** where the language supports it: the type of
    each input and of the output, "nothing" included. The signature then says what goes in
    and what comes out, and a checker verifies every call against it. A value that can be
    anything is declared as such, so the checker makes the code check it before use;
    never as "no checking". Tests may be the exception.
19. **Functions with a similar role have the same signature:** same parameters, same
    order; but never parameters a function doesn't use (interface segregation wins,
    see the design rules).
20. **One level of abstraction per function:** its lines are all at the same level, so a
    top-level function reads like a summary, and the details sit in the functions it
    calls.
    - **No line count:** a function's length follows from doing one thing at one level,
      not from a target. It's split where it does a second thing or a reader loses the
      thread, not to reach a number of lines. This overrides the clean-code skill's
      "ideally 4-6 lines": splitting further scatters one idea over many small functions.
21. **No duplicated code: each operation is written once, and reused wherever it's
    needed,** so a fix lands everywhere and a reader recognises the operation by its name.
    No duplication takes priority over other rules.
    - **A copy** becomes one function at its first copy (e.g. splitting a comma-separated
      text into its parts, even in two lines). Only a short one-liner that reads clearly
      on its own stays inline.
22. **A helper used in one place sits next to that place,** or as close to it as the
    language allows.
23. **Normalize once, at the edge, and keep only the normalized form** (clean or
    lowercase the input where it's read, not at every use).
24. **No unexplained numbers:** a number that shapes a result is a named constant at the
    top of the file, with where its value comes from; values that depend on each other
    are derived, not set separately.

25. **No global or shared mutable state:** a function gets what it needs as parameters and
    returns what it produces; values at module level are constants. State that really has
    to be shared (a cache, a connection) sits behind one small interface, never changed
    directly from several places.

## Errors

26. **Fail fast:** report a problem where it happens, as early as possible, instead of
    continuing with bad data: a broken configuration stops the program before it starts
    working; an impossible value raises where it's found, not three calls later.
27. **Catch specific errors, never all of them.**
28. **For compiled code, warnings are errors:** the build treats every compiler warning as
    an error, so none is left standing.

## Changes and tests

29. **One subject per change, in small steps.** A change that needs another one merged
    first says so in its title ("merge after ...").
30. **Code and its tests are written together.** Untested code doesn't exist: it gets
    tested (code that talks to an outside system: at least one real run) or removed.
31. **One-off work isn't kept:** a data migration or repair runs once, as a script outside
    the repository; its code and tests don't stay.
32. **A commit message says only what the code doesn't:** why the change was made, the
    problem it solves or the function it improves, and how it relates to other changes.
    As short as it can be while still understood, and never longer than the change
    itself.
