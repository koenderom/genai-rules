# Sources

Where the named principles in the rules come from, for the full reasoning. For the
reader, not the assistant: this file isn't loaded with the rules.

## Architecture and design

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

## Implementation

- **Explicit is better than implicit:** Tim Peters, *The Zen of Python*,
  [PEP 20](https://peps.python.org/pep-0020/).
- **No code that isn't needed now (YAGNI):** see "Architecture and design" above.
- **No duplicated code (DRY):** Andrew Hunt and David Thomas, *The Pragmatic Programmer*
  (1999).
- **Command-query separation:** Bertrand Meyer, *Object-Oriented Software Construction*
  (1988).
- **One level of abstraction per function:** Kent Beck, *Smalltalk Best Practice
  Patterns* (1997), "Composed Method"; Robert C. Martin, *Clean Code* (2008), chapter 3.
- **No global or shared mutable state:** Andrew Hunt and David Thomas, *The Pragmatic
  Programmer*, 20th anniversary edition (2019), tips 47 ("Avoid Global Data"), 48, 50
  ("Don't Hoard State; Pass It Around") and 57 ("Shared State Is Incorrect State").
- **Fail fast:** Jim Gray, "Why Do Computers Stop and What Can Be Done About It?" (1985),
  for systems; Jim Shore, ["Fail Fast"](https://martinfowler.com/ieeeSoftware/failFast.pdf),
  *IEEE Software* (2004), for code.

## Review and testing

- **Fast, independent, repeatable, self-validating tests:** the F.I.R.S.T. rules, Robert C.
  Martin, *Clean Code* (2008), chapter 9, "Unit Tests" (the T, timely, is in the
  implementation rules: tests are written with the code).
- **A failing test first; find bugs once:** Andrew Hunt and David Thomas, *The Pragmatic
  Programmer*, 20th anniversary edition (2019), tips 31 and 94.
- **Automatic, reproducible checks:** *The Pragmatic Programmer*, tips 89 ("Use Version
  Control to Drive Builds, Tests, and Releases"), 90 ("Test Early, Test Often, Test
  Automatically") and 95 ("Don't Use Manual Procedures").

## Maintenance

- **The boy-scout rule:** Robert C. Martin, *Clean Code* (2008), chapter 1.
- **Broken windows:** Andrew Hunt and David Thomas, *The Pragmatic Programmer* (1999),
  after James Q. Wilson and George Kelling's "broken windows" theory (1982).
