# Way of working

How the assistant and the project's owner build software together. How the assistant
answers, in any conversation, is in [`ai_chat_rules.md`](ai_chat_rules.md). The work
goes through seven stages, in this order; each stage has its own skill:

1. [Requirements](requirements/SKILL.md)
2. [Planning and tracking](planning-and-tracking/SKILL.md)
3. [Architecture and design](architecture-and-design/SKILL.md)
4. [Implementation](implementation/SKILL.md)
5. [Review and testing](review-and-testing/SKILL.md)
6. [Deployment and documentation](deployment-and-documentation/SKILL.md)
7. [Maintenance](maintenance/SKILL.md)

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
   - **A change matches the style of the file it changes,** so the project stays
     consistent.
   - **Minimal diff:** a change touches only what it needs to, unless another rule asks
     for more: this one, or the boy-scout rule (maintenance rules).
6. **Say what wasn't verified.** Work is reported as done only when it is; anything only
   partly checked is named as such.
   - **No guess presented as a fact:** a claim ("works for every site") is checked on
     real data before it's written down; a value that is only a guess (a rating, a
     threshold) says so, or is left out.
7. **Rules stay project-agnostic here.** A rule that holds for one project only is one of
   that project's non-functional requirements, kept in the project (requirements rules).
   The same goes for skills: one that carries over to other projects by its nature lives
   here, even while only one project uses it; one tied to a single project lives in that
   project.
8. **One language per project, used consistently in every stage:** requirements, code,
   documents, commit messages and pull requests.
9. **Keep the working context small, to save tokens:** compress it regularly, or start a
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

## The stage skills

- The assistant loads a stage skill when a task belongs to that stage (each skill's
  description says when), or when the owner calls the skill by name.
- This file and `ai_chat_rules.md` are the only ones loaded in every conversation; the
  stage skills load only when they're needed, which keeps the working context small
  (rule 9).

## The rules in a project

- The rules repository is added to the project as a git submodule, at the place where
  the assistant looks for skills, so every stage skill is found without copies or links.
  The assistant's own folder says how (for Claude: [`claude/CLAUDE.md`](claude/CLAUDE.md)).
- Which way a project uses (this submodule, one copy for all of the owner's projects, or
  an assistant's plugin) is decided with its requirements.

## Still to discuss

- Rules from published guidelines and agent-instruction practice, still to select.
