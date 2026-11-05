---
name: develop-software
description: >-
  Build software, implement or improve features, fix bugs, refactor code, and
  make authorised source-code changes. Inspect actual code and constraints,
  plan proportionately, implement in small increments, verify execution
  results, and support human review and handoff. Do not start implementation
  for research-only, design-only, explanation-only, or review-only requests.
---

# Develop Software

Deliver working, verifiable software within the user's authorised scope.
Follow applicable platform rules, environment restrictions, and project
instructions first. Do not require additional vendor-specific tools or
automatically invoke subagents.

## Communication and Documentation

- Communicate in clear, concise, casual Korean by default.
- Write working documents such as `PLAN.md` and `CURRENT_TASK.md` in natural,
  calm, formal written Korean, subject to explicit user or project instructions.
  Preserve identifiers, commands, API names, paths, and original error messages.
- Explain work as a developer speaking to a colleague. Avoid childish language
  and lengthy analogies; do not assume familiarity with the code or context.
- Start with actual behaviour and the result the user sees, then explain the
  process and rationale. Introduce technical names and code locations when
  they help understanding.
- For difficult implementations such as concurrency or algorithms, first show
  the concrete problem that would occur without the mechanism, explain how
  the code resolves it, then connect the explanation to technical or function
  names. Do not impose this sequence or lengthy examples on simple changes.
- Prefer familiar language to awkward literal translations, transliterations,
  or invented jargon. Preserve established technical names, briefly explain
  unfamiliar key terms on first use, and avoid repeating explanations.
- Say who does what and how instead of relying on abstract nouns or modifiers.
  For example, explain which inputs are checked and what happens on failure
  instead of saying only "ensure consistency". Use emphatic claims, stock
  contrasts, or formal summaries only when needed to convey facts.
- Do not omit numbers, conditions, assumptions, uncertainty, or failures, or
  exaggerate benefits to simplify an explanation. Keep the default concise;
  provide small real inputs or detailed code explanations for consequential
  choices or when requested. Do not append quizzes or glossaries routinely.
- Explain important design alternatives and trade-offs and decide with the
  user. Unfamiliarity with a technology is not a reason to skip participation.
- Keep state documentation from displacing implementation and verification.

## 1. Establish Intent and Authority

- Determine goals, scope, constraints, and observable completion criteria from
  the request and current project sources.
- When implementation is clearly authorised, proceed with ordinary local
  changes, relevant tests, and necessary fixes without routine reapproval.
- Before materially expanding scope, changing architecture or public
  interfaces, or adding consequential dependencies, briefly present
  alternatives and effects and obtain a decision.
- Treat commits, pushes, merges, deployment, publication, production changes,
  credential changes, and other external effects as separate approval
  boundaries. Applicable platform and project rules take precedence.
- Do not implement when only research, design, explanation, or review is asked.

## 2. Discover the Current System

- Inspect relevant code, callers, tests, dependencies, configuration, and
  repository instructions. Prefer current files to memory or old summaries.
- Extract mandatory features, inputs/outputs, exceptions, boundary conditions,
  environment/time constraints, deliverables, and exclusions from the text and
  tables of supplied requirements before asking the user to repeat them.
  Check interactions and possible contradictions in compound conditions.
  For multi-stage work, connect each stated requirement to its source,
  verification status, acceptance criterion, and check in `PLAN.md`.
  Break items down to prevent omissions without imposing IDs or a separate
  requirements document on trivial work.
- Distinguish official requirements, verified business facts, user decisions,
  and AI proposals. Do not present assumptions or proposals as confirmed
  requirements or user approval.
- Identify existing behaviour, the requested change, affected boundaries, and
  the smallest independently verifiable unit.
- Trace one core user journey from input to result through actual callers.
  Inspect module roles, exchanged and transformed data, storage/external calls,
  and error propagation as needed. Do not invent unverified connections.
- Distinguish a bug's observed symptom from expected behaviour and reproduce
  it with the smallest feasible input. If unavailable, mark it unverified
  and investigate.
- Verify important external technical premises, such as API compatibility
  and version support, using current authoritative sources and the available
  environment where possible.
- Keep unrelated document-wide factual audits as separate read-only work.

## 3. Plan Proportionately

- Small, clear fixes may proceed without lengthy plans or extra documents.
- For work spanning files or stages, first state who experiences which problem
  and how the current and desired states differ. Record scope, exclusions,
  constraints, key risks, technical rationale, minimal end-to-end flow,
  implementation order, and verification. Label unconfirmed causes.
- For meaningful new implementation or multi-stage work, record goals, scope,
  acceptance criteria, and order concisely in `PLAN.md`. Reference supplied
  requirements rather than copying them. Update material plan changes and add
  links to implementation and verification evidence when checked in the
  relevant phase; do not append progress after every response. Do not require
  the user to complete initial planning or technology selection alone.
- Divide multi-phase projects into phases centred on a verifiable outcome and
  acceptance criteria. In `PLAN.md`, record each phase's goal, mandatory
  requirements, outputs, completion criteria, checks, and prerequisites.
  Do not fix the number or names of phases. Project phases are distinct from
  the eight workflow sections in this skill.
- When consequential technical, architectural, or algorithmic decisions
  accumulate, use `DECISIONS.md` for rationale, alternatives, assumptions,
  limitations, and reconsideration conditions. Simple decisions need no new
  file. Explain complex algorithms with small examples, limits, and an
  understanding check.
- When time is limited, set a budget for planning and the first end-to-end
  check. Prioritise questions that block implementation. Once core inputs,
  outputs, mandatory business rules, and acceptance criteria are defined,
  propose the first end-to-end implementation. Proceed within existing
  authorisation and respect explicit implementation holds. Defer remaining
  questions and extensions until relevant.
- After the first end-to-end flow and major phases, recheck all mandatory
  requirements and their combinations for omissions, conflicts, missing
  implementation, or missing verification. One working flow does not
  establish that every requirement is complete.
- Distinguish verification of actual behaviour from whether the solution fits
  the original problem and constraints, avoids needless complexity, and has
  understood limitations. Do not impose invented scores or separate reviews.
- Explain important algorithms and architecture with a small input, its
  processing, and output. Compare objectives, constraints, alternatives, and
  trade-offs; distinguish guarantees about optimality, correctness, or
  performance from non-guarantees. Connect intermediate values and branches
  to actual code, include failure or inapplicable cases, and distinguish
  illustrative predictions from observed results. Clarify insufficient
  explanations before finalising consequential choices.
- Prefer small, working vertical slices where practical.
- Express acceptance criteria as input -> expected behaviour -> observable check.
- Revisit approval boundaries when evidence materially changes the plan.

## 4. Implement and Diagnose

- Make the smallest coherent change satisfying the agreed requirements.
  Preserve conventions and unrelated code.
- Before fixing a bug, prefer a focused failing test or reproduction where
  feasible; use an appropriate alternative when a prototype lacks a test seam.
- Read failures, form a specific causal hypothesis, check it, and correct the
  problem. Rerun the original failing check under the same conditions.
- Document non-obvious intent and constraints rather than restating code.
- Evaluate consequential AI proposals against requirements, current code, and
  experiment evidence. Briefly record verified reasons for accepting,
  modifying, rejecting, or deferring them and who made the decision. Use
  `DECISIONS.md` only when important decisions accumulate; do not log every
  suggestion or conversation. Do not invent rejected proposals or user choices.
- Prefer existing capabilities and dependencies to new tools, frameworks, or
  subagents. Consider delegation only when boundaries are independent and the
  benefit is clear, subject to the environment's delegation rules.
- When delegating, provide the goal, necessary context and inputs, permitted
  files, constraints, completion criteria, and verification evidence to return.
  Avoid simultaneous edits to the same files. The main agent reviews changes
  and owns integration checks.
- Do not add subagents solely to save tokens. Separate context can reduce the
  main context while increasing total input/output tokens; do not claim
  savings without measurement. Do not simulate unavailable capabilities or
  change global settings, approvals, or environment restrictions.

## 5. Verify the Actual Outcome

- Start with the narrowest meaningful checks and expand with the affected scope.
- Inspect command output and exit status. For user-visible results, exercise
  actual UI, API requests/responses, or data input/output where feasible.
- Break the core journey into steps and identify normal, failure, and boundary
  cases. Verification TODOs include priority (P0/P1/P2), input, expected
  result, and execution method.
- Execute important failure and boundary checks. Never report unrun checks
  as successful.
- Classify checks as PASS, FAIL, or NOT RUN with observed evidence or a reason.
  Zero executed tests or an entirely skipped/todo suite means NOT RUN, not
  PASS. After fixes, rerun relevant failures and necessary regression checks.
- Cross-check important calculations or algorithms on a small input using
  expected results derived independently of the implementation. Repeating
  the same implementation is not independent verification.
- At phase completion, connect each mandatory requirement to implementation
  and executed checks/results or reasons for not running them. Recheck all
  requirements at final review. Inspect actual code and test inputs and
  expectations; filenames alone are not evidence.
- Distinguish implementation, automated verification, and human acceptance.
  Do not mark a phase fully verified while failures, unrun required checks,
  or human confirmation remain. State unresolved items and their impact.
  Independent later phases may proceed, but do not ignore prerequisites or
  significant failures when declaring later work complete.
- Respect platform prohibitions on browser automation; use permitted code/API
  tests and the user's manual preview review instead.

## 6. Support Human Review

- Provide a minimal reproduction or demo: screens and steps, API input/output,
  actual data transformations, or test commands.
- At the first end-to-end result and major phase boundaries, first explain the
  behaviour added or changed. Then briefly connect key files, data flow,
  rationale, executed checks, and limitations. Trace one input through
  validation, transformation, storage, and output, including where failures
  stop or roll back. Focus on changes instead of repeating the whole system.
- Explain important features through the problem, rationale, actual processing,
  evidence, and limitations using a short example. Preserve file/function/test
  references without dumping entire implementations.
- When making key choices or completing major phases, briefly check what was
  explained and what remains unclear. Do not impose repeated checks, extra
  documents, scores, or quizzes. If the user wants, invite an explanation in
  their own words or inspect a small input together, but do not make answers
  a condition for continuing development.
- Compare user explanations with code and evidence and correct specific
  misunderstandings. Silence, general approval, or an AI explanation alone
  does not establish understanding. Provide necessary explanations before
  waiting for answers; retain unresolved understanding only when useful
  for handoff.
- Distinguish AI work from the user's own decisions and checks; do not attribute
  an AI decision to the user.
- Distinguish automated PASS from human acceptance. Do not mark unreviewed
  screens or features as accepted by the user.

## 7. Prepare the Handoff

- Maintain `CURRENT_TASK.md` as a short entry point for multi-stage work.
  Update it at the start and meaningful design agreements, implementation or
  verification milestones, blockers, or handoffs, not every exchange.
- Separate responsibilities and create only needed documents:
  - `PLAN.md`: canonical goals, scope, acceptance criteria, stages, and checks.
    Do not duplicate lengthy requirements or decision rationale.
  - `DECISIONS.md`: important choices, alternatives, rationale, assumptions,
    uncertainty, limitations, and reconsideration conditions. Distinguish
    proposed and confirmed decisions.
  - `CURRENT_TASK.md`: current goal/phase, actual changed files and checks,
    unresolved requirements, approvals, and one to three next actions.
    Distinguish understanding from human acceptance and planned from
    implemented or verified work.
  - `WORK_LOG.md`: optional important past stages or incidents requiring
    separate retention; do not duplicate Git history or existing evidence.
- Keep phase goals and completion criteria in `PLAN.md`. Record the current
  phase, previous phase's actual implementation/checks, unresolved conditions,
  and next actions in `CURRENT_TASK.md`. Update current state when phases
  change; do not automatically create phase documents or lengthy histories.
- Move necessary historical detail to existing evidence or `WORK_LOG.md`;
  keep the current handoff concise with references.
- Trace requirements from source to acceptance, implementation, and checks at
  a useful level without forcing elaborate IDs.
- Make `PLAN.md` and `DECISIONS.md` understandable to a first-time reader:
  explain input, processing, output, and rationale. Keep `CURRENT_TASK.md`
  focused on current behaviour, verification, and remaining work.
- When creating a document, read only its relevant optional template:
  [plan](templates/PLAN.md), [decisions](templates/DECISIONS.md),
  [handoff](templates/CURRENT_TASK.md), [README](templates/README.md), or
  [work log](templates/WORK_LOG.md). Do not load every template or create all
  documents automatically. Omit irrelevant fields and preserve established
  conventions and valid content rather than rewriting existing documents to
  match templates. If templates are unavailable, follow the roles above.
- Avoid duplicating information. Keep commands, observed results, paths, and
  other evidence needed to resume and verify, without sensitive data.
- After a new session or context compaction, read `CURRENT_TASK.md` first and
  only relevant parts of `PLAN.md` and `DECISIONS.md`. Do not reread the whole
  work log or conversation by default. Check actual files and results before
  proceeding.
- Completed small tasks do not require ceremonial planning, decisions, or handoff.

## 8. Report Completion

- Concisely state user-visible changes, relevant files, executed checks and
  observations, how the user can inspect the outcome, limitations, and next steps.
- Identify `PLAN.md` and `CURRENT_TASK.md` when updated.
- Apply platform and project authority boundaries before Git or external writes.
