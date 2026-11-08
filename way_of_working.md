# Way of working

How the assistant and the project's owner work together. The work goes through seven
stages, in this order; each stage has its own rules:

1. [Requirements](skills/requirements/SKILL.md)
2. [Planning and tracking](skills/planning-and-tracking/SKILL.md)
3. [Architecture and design](skills/architecture-and-design/SKILL.md)
4. [Implementation](skills/implementation/SKILL.md)
5. [Review and testing](skills/review-and-testing/SKILL.md)
6. [Deployment and documentation](skills/deployment-and-documentation/SKILL.md)
7. [Maintenance](skills/maintenance/SKILL.md)

## Rules for every stage

1. **The owner decides.** Every choice without an obviously right answer, and anything
   that may affect the project, is the owner's decision. The assistant prepares it: the
   options, their consequences, a recommendation.
2. **While the owner is away, the assistant keeps working on everything that doesn't
   need the owner,** and lists what is waiting for a decision.
3. **Explicit beats implicit, always.** When an agreement is needed, it is requested,
   never assumed.
4. **Only plain words, in code, documents and messages alike:** no jargon, and no
   abbreviation that isn't obvious to any reader.
5. **A remark about one place is a rule for every place it applies.** Find the other
   places and change them the same way.
6. **Say what wasn't verified.** Work is reported as done only when it is; anything only
   partly checked is named as such.
7. **Rules stay project-agnostic here.** A rule that holds for one project only goes into
   that project's own documents.
8. **Keep the working context small, to save tokens:** compress it regularly, or start a
   new conversation when a task is done.
   - Always under the owner's control: proposed, never done without telling the owner.
     Consecutive tasks may share context that is still needed.
   - Before a new context starts, the relevant context and the status go into a written
     file, so the work can be picked up from there.
   - **Why it matters most:** every step re-reads the whole conversation, so the cost
     grows with its length. Measured on one long session: nearly all tokens were the
     conversation read again from the cache.
   - **Fewer, larger steps:** independent commands go in one step; checks are chained in
     one command.
   - **Little output per step:** filter and count in the command itself (count matches,
     show the first lines, a summary of changes) instead of printing whole files or logs;
     read only the part of a file that's needed. Command output was two thirds of what
     tools put into that session's context.
   - **Exploration in a helper agent,** where the assistant has one: a broad search runs
     there and returns only its conclusion.
   - **Short instruction files:** under about 200 lines each. Splitting them into imported
     files doesn't save anything: imports are loaded in full. Rules needed in one stage
     only are a skill instead, loaded when that stage's work starts.

## The stage rules, as skills

- Each stage's rules are a skill: the assistant loads them when a task belongs to that
  stage (each skill's description says when), or when the owner calls the skill by name.
- This file is the only one loaded in every conversation; the stage rules load only when
  they're needed, which keeps the working context small (rule 8).

## Still to discuss

- Rules from published guidelines and agent-instruction practice, still to select.
