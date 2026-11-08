# 4. Implementation

How the code is written. The design rules ([3](3_architecture_and_design.md)) apply here
too, at the level of each function.

## Simplicity

1. **Don't reinvent the wheel:** use the standard library and mature packages; write
   project code only for what they don't cover, and keep that code to a minimum.
2. **Simplicity beats cleverness:** the version a reader follows at first sight wins, even
   if it's longer. A clever construction needs a reason the reader can check, stated next
   to it.
3. **Explicit is better than implicit** (the Zen of Python): what code depends on and
   what it does shows where it's used: values are passed, not picked up from global
   state; behaviour is stated, not left to a default the reader must know. This rule
   itself is an example: written out, rather than assumed from "keep it clear".
4. **No code that isn't needed now:** no options, parameters or abstractions nobody asked
   for.
5. **Write the language's idioms:** code reads the way experienced users of the language
   write it (in Python: "pythonic" code).

## Names

6. **Plain words of the domain; no jargon, no abbreviations, no catch-all words** such as
   manager, data, info, helper, process, registry.
7. **One concept, one name, everywhere:** code, configuration keys, documents, tests,
   messages. One word per concept, one concept per word.
8. **A name says what the value is, including its criterion:** "highest score first",
   not "best first".
9. **Names follow the language's usual hints,** part of its idioms (in Python: `is_` for
   a yes/no answer, `iter_` for an iterator, `to_` for a conversion).
10. **A name never disagrees with what it holds, and doesn't encode the type** (no `_list`
   on something that may become a set), unless that is common practice in the language.
11. **A file is named after what it holds; a name carries no history** (no `_new`,
    `_clean`, `_v2`).

## Comments

12. **Comment only where it adds something: the intent and the algorithm, not the
    mechanics.** Never rephrase what the code says clearly. What a caller needs to know
    is stated: preconditions, the result when it fails, side effects. An assumption is
    an unwritten precondition: write it down as one.
13. **Every file starts with its purpose.** No workflow, phase or history information in
    source files.
14. **Written for a human reader who doesn't know the code yet:** define a term before
    using it; explain every non-obvious construct where it appears (a regular expression
    with an example of what it matches, an operator with a special meaning, a formula's
    closed form).
15. **A comment never suggests behaviour the code doesn't have.**
16. **Each explanation lives once, where its reader looks** (a setting is explained in
    the configuration file, not again in the code).
17. **Structured for readability:** concise, to the point and precise; bullets over
    prose, one idea per bullet.

## Functions and data

18. **A function is used correctly at first sight (the principle of least astonishment:
    code does what its name and shape suggest):** its name, parameters and return value
    say what it does, so the obvious call is the right one. No call that only works when
    the caller knows how the function is built inside, or in which order hidden steps
    must happen.
19. **No functions that work only through side effects; a function either answers or acts
    (command-query separation):** a question returns its answer and changes nothing; a
    command changes something and its name says so. An exception (e.g. "pop": remove and
    return) is named so the effect is visible at the call site.
20. **Every function declares its types,** where the language supports it: the type of
    each input and of the output, "nothing" included. The signature then says what goes in
    and what comes out, and a checker verifies every call against it. A value that can be
    anything is declared as such, so the checker makes the code check it before use;
    never as "no checking". Tests may be the exception.
21. **Functions with a similar role have the same signature:** same parameters, same
    order; but never parameters a function doesn't use (interface segregation wins,
    design rule 7).
22. **One level of abstraction per function:** its lines are all at the same level, so a
    top-level function reads like a summary, and the details sit in the functions it
    calls.
23. **No duplicated code: each operation is written once, and reused wherever it's
    needed,** so a fix lands everywhere and a reader recognises the operation by its name.
    No duplication takes priority over other rules.
    - **A copy** becomes one function at its first copy (e.g. splitting a comma-separated
      text into its parts, even in two lines). Only a short one-liner that reads clearly
      on its own stays inline.
    - **A recurring structure** that isn't a verbatim copy (the same shape of code, with
      different details) gets a generic implementation from its third appearance on.
24. **A helper used in one place sits next to that place,** or as close to it as the
    language allows.
25. **Normalize once, at the edge, and keep only the normalized form** (clean or
    lowercase the input where it's read, not at every use).
26. **No unexplained numbers:** a number that shapes a result is a named constant at the
    top of the file, with where its value comes from; values that depend on each other
    are derived, not set separately.
27. **General functionality is kept apart from user-specific settings:** the code never
    hard-codes anything specific to one user; that goes in configuration files, which
    may be kept private. Examples and tests use invented data.

## Errors

28. **Fail fast:** report a problem where it happens, as early as possible, instead of
    continuing with bad data: a broken configuration stops the program before it starts
    working; an impossible value raises where it's found, not three calls later.
29. **Catch specific errors, never all of them;** when bad input is tolerated, log a
    warning, so nothing disappears silently.
30. **For compiled code, warnings are errors:** the build treats every compiler warning as
    an error, so none is left standing.

## Changes and tests

31. **One subject per change, in small steps.** A change that needs another one merged
    first says so in its title ("merge after ...").
32. **Code and its tests are written together.** Untested code doesn't exist: it gets
    tested (code that talks to an outside system: at least one real run) or removed.
33. **One-off work isn't kept:** a data migration or repair runs once, as a script outside
    the repository; its code and tests don't stay.

## Sources

Where the named principles in these rules come from, for the full reasoning. Each is
checked against its Wikipedia article, the publisher, or the original text.

- **Explicit is better than implicit:** Tim Peters, *The Zen of Python*,
  [PEP 20](https://peps.python.org/pep-0020/).
- **No code that isn't needed now (YAGNI):** see the design rules' sources.
- **No duplicated code (DRY):** Andrew Hunt and David Thomas, *The Pragmatic Programmer*
  (1999).
- **Command-query separation:** Bertrand Meyer, *Object-Oriented Software Construction*
  (1988).
- **One level of abstraction per function:** Kent Beck, *Smalltalk Best Practice
  Patterns* (1997), "Composed Method"; Robert C. Martin, *Clean Code* (2008), chapter 3.
- **Fail fast:** Jim Gray, "Why Do Computers Stop and What Can Be Done About It?" (1985),
  for systems; Jim Shore, ["Fail Fast"](https://martinfowler.com/ieeeSoftware/failFast.pdf),
  *IEEE Software* (2004), for code.
