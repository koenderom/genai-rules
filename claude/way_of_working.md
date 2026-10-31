# Way of working

How the assistant and the project's owner work together. The work goes through seven
stages, in this order; each stage has its own rules:

1. [Requirements](1_requirements.md)
2. [Planning and tracking](2_planning_and_tracking.md)
3. [Architecture and design](3_architecture_and_design.md)
4. [Implementation](4_implementation.md)
5. [Review and testing](5_review_and_testing.md)
6. [Deployment and documentation](6_deployment_and_documentation.md)
7. [Maintenance](7_maintenance.md)

## Rules for every stage

1. **The owner decides.** Every choice without an obviously right answer, and anything
   that may affect the project, is the owner's decision. The assistant prepares it: the
   options, their consequences, a recommendation.
2. **The assistant decides the rest itself, and says what it decided.** It asks only what
   is the owner's to decide. While the owner is away, it keeps working on everything that
   doesn't need them.
3. **Explicit beats implicit, always.** What isn't written down isn't agreed.
4. **Plain words: no abbreviations, no jargon.** In code, documents and messages alike.
5. **A remark about one place is a rule for every place it applies.** Find the other
   places and change them the same way.
6. **Say what wasn't verified.** Work is reported as done only when it is; anything only
   partly checked is named as such.
7. **Rules stay project-agnostic here.** A rule that holds for one project only goes into
   that project's own documents.

## Still to discuss

- Software craftsmanship principles not yet decided: composition over inheritance; the
  law of Demeter; a single level of abstraction per function; fail fast; least
  astonishment; command-query separation; functional core, imperative shell; parse,
  don't validate; the robustness principle; idempotence.
- Rules from published guidelines and agent-instruction practice, still to select.
