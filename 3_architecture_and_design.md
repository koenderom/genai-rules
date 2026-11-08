# 3. Architecture and design

How the solution is structured, decided before it's built.

## Goals, in order of priority

When two goals pull in different directions, the higher one wins.

1. **Correct and safe:** the software reliably and consistently does what it's meant to
   do, proven by passing tests rather than assumed, and fails visibly when it can't.
2. **Maintainable and extensible:** a change touches one place and can't quietly break
   another.
3. **Readable and reviewable** by a human who doesn't know it yet.

## Rules

1. **Don't reinvent the wheel.** Before designing a component, look for the mature,
   existing solution: the standard library, a well-established package, a standard tool
   or practice. Minimize the code written for the project itself.
2. **Use established design patterns where they fit:** while designing, review the known
   patterns (factory, strategy, observer, ...) before inventing a structure.
3. **Simplicity:** the simplest design that does the job.
   - Build only what is needed now, not for an imagined future need.
   - Abstract a recurring structure once it has appeared three times, not at the first
     repetition. A verbatim copy of code is removed at once (implementation rule on
     duplicated code).
   - Make it right and clear first; make it fast only where measurements show the need.
   - The fewest elements: once the code passes its tests, says what it's for and has no
     duplication, every other class, function, parameter or layer goes.
4. **Consistency:** one design approach throughout the project; a variation needs a
   stated reason. The same kind of part has the same structure.
5. **General mechanisms over special cases:** a configurable scale rather than a switch
   for one situation. Prefer the general solution whenever it is as clear as the specific
   one.
6. **Make usage easy:** the most straightforward reading of an interface is the correct
   one. No interface that only works as intended for someone who knows its
   implementation or its history; a wrong use is hard to write, or fails visibly.
7. **The SOLID principles:**
   - **Single responsibility:** each part (module, class, function, file, configuration
     section) has one reason to change; its name says which.
   - **Open-closed:** adding a variant adds code; it doesn't change existing code.
   - **Liskov substitution:** an implementation can stand in wherever its interface is
     expected, in behaviour, not only in signature: it asks no more of its caller than
     the interface does, and promises no less (e.g. a subclass doesn't refuse an input
     its base class accepts, nor return `None` where the base class always returns a
     value).
   - **Interface segregation:** no part depends on methods or parameters it doesn't use.
     It outweighs uniform signatures: several small interfaces rather than one signature
     with parameters some implementations ignore.
   - **Dependency inversion:** a part that talks to the outside world receives its
     client; it doesn't create a global one.
8. **High cohesion, low coupling, locality of change:** what belongs together sits
   together; parts depend on each other as little as possible, and only through what
   they're given; one change in behaviour means a change in one place.
9. **Organize by subject, not by processing stage:** everything about one subject (its
   checks, its calculation) sits together.
10. **Keep structure; don't flatten it:** pass the whole object, not a string glued
   together from its parts. A decision that may grow smarter later is a function of its
   own, taking the whole object.
11. **Specifics live in configuration, not in the code:** personal values, preferences
   and thresholds are configured; the code stays general.
12. **Configuration is checked when it's loaded:**
    - a mistake stops the program at the start, with a message saying what to fix;
    - where the intent is obvious, the program fixes it and warns, instead of making the
      user do the work;
    - settings are grouped by their effect, with the effect stated at the top of each
      group.
13. **Store each fact once (database normalization):** no copy of the same data in a second
    place, such as table columns next to a JSON copy of the same record, or a full copy of
    a record for each result computed from it.
    - Point to the original instead: e.g. a score row holding the posting's key, the
      scenario and the score.
    - Copies drift apart: a repair fixes one and not the other.
    - A copy only for a measured reason (speed), stated where it's made.
14. **Composition over inheritance:** build behaviour by combining small objects, not by
    deep class hierarchies. Inherit only for a true "is a" relation; a shared helper is
    a function or an object passed in, not a base class.
15. **Law of Demeter ("talk to friends, not strangers"):** a part uses what it was given,
    not the inside of what that holds. `order.total()`, not
    `order.customer.account.balance`: a chain of dots ties the caller to a structure it
    shouldn't know.
16. **Functional core, imperative shell:** decisions and calculations are pure functions
    (same input, same output, nothing changed elsewhere); the few parts that read, write
    or call the outside world sit at the edge and stay thin. The core is then testable
    without mocks.
17. **Make illegal states unrepresentable ("parse, don't validate"):** turn outside data
    into precise types once, where it enters; inside, a value that exists is valid: a
    status as one of its few allowed values (an enumeration), not any text; an email
    address as its own type, not a string checked again at every use.
18. **Robustness principle (Postel's law), for input from outside:** be liberal in what you
    accept from websites, feeds, files and users, conservative in what you produce.
    Tolerated bad input is logged, never silently fixed or dropped.
19. **Idempotence:** running the same operation twice gives the same result as once. A
    repeated run updates instead of duplicating, sends a notification once, and can be
    restarted safely after a failure partway.

## Sources

Where the named principles in these rules come from, for the full reasoning.

- **Simplicity (KISS):** first noted by the U.S. Navy in 1960; associated with Kelly
  Johnson, engineer at Lockheed's Skunk Works.
- **Passes the tests, reveals intention, no duplication, fewest elements (Beck's four
  rules of simple design, in that order):** Kent Beck, *Extreme Programming Explained*
  (1999), in the practice of simple design; Martin Fowler,
  ["Beck Design Rules"](https://martinfowler.com/bliki/BeckDesignRules.html).
- **Build only what is needed now (YAGNI):** Extreme Programming; Ron Jeffries, one of its
  founders; Martin Fowler, ["Yagni"](https://martinfowler.com/bliki/Yagni.html).
- **Make it fast only where measurements show the need:** Donald Knuth, "Structured
  Programming with go to Statements", *Computing Surveys* (1974): "premature optimization
  is the root of all evil".
- **Abstract a recurring structure from its third appearance (rule of three):** Martin
  Fowler, *Refactoring* (1999), who credits Don Roberts.
- **SOLID:** Robert C. Martin, "Design Principles and Design Patterns" (2000), and *Agile
  Software Development: Principles, Patterns, and Practices* (2002); the acronym is
  Michael Feathers', around 2004.
  - Open-closed: Bertrand Meyer, *Object-Oriented Software Construction* (1988).
  - Liskov substitution: Barbara Liskov, "Data Abstraction and Hierarchy", OOPSLA (1987);
    Barbara Liskov and Jeannette Wing, "A Behavioral Notion of Subtyping", *ACM TOPLAS*
    (1994).
- **Design patterns, and composition over inheritance:** Gamma, Helm, Johnson and
  Vlissides, *Design Patterns* (1994): "favor object composition over class inheritance".
- **Law of Demeter:** proposed by Ian Holland at Northeastern University in 1987; Karl
  Lieberherr, Ian Holland and Arthur Riel, "Object-Oriented Programming: An Objective
  Sense of Style", OOPSLA (1988).
- **Functional core, imperative shell:** Gary Bernhardt,
  ["Functional Core, Imperative Shell"](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell)
  (screencast) and ["Boundaries"](https://www.destroyallsoftware.com/talks/boundaries)
  (talk, SCNA 2012).
- **Make illegal states unrepresentable:** Yaron Minsky, "Effective ML" (lecture at
  Harvard, 2010; see his
  ["Effective ML Revisited"](https://blog.janestreet.com/effective-ml-revisited/));
  **parse, don't validate:** Alexis King,
  ["Parse, don't validate"](https://lexi-lambda.github.io/blog/2019/11/05/parse-don-t-validate/)
  (2019).
- **Robustness principle:** Jon Postel, in the TCP specification,
  [RFC 761](https://www.rfc-editor.org/rfc/rfc761) (1980).
- **Idempotence:** a term from mathematics; for operations that may be repeated, see the
  HTTP specification, [RFC 9110](https://www.rfc-editor.org/rfc/rfc9110), "Idempotent
  Methods".
- **Store each fact once (normalization):** Edgar F. Codd, "A Relational Model of Data for
  Large Shared Data Banks", *Communications of the ACM* (1970).
