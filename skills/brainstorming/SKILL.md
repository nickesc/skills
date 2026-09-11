---
name: brainstorming
description: "Use when a coding request still needs product, UX, scope, or architecture decisions before implementation. Skip when the user gives a clear build instruction and the request plus repository context already settle the design."
---

# Brainstorming Ideas Into Designs

Turn requests with material open questions into enough shared design
to proceed. Scale the process to the choices that remain.

## Decide Whether Brainstorming Is Needed

Proceed through the normal development workflow when all of these are
true:

- The user clearly asked you to build, implement, or change something.
- The request and repository context settle the intended behavior,
  important constraints, interfaces, and success criteria well enough
  to act.
- Any choices left are local implementation details that will not
  change the user's requested outcome or an interface others depend on.

The size of a change affects how much evidence you need, but size alone
does not require a design phase. When a request is execution-ready,
state the approach briefly if that helps the user follow the work, then
implement. Do not ask the user to approve an implementation plan they
did not request.

If the user asked only to brainstorm, design, or plan, stop after that
deliverable. A clear design request does not authorize implementation.

Use the paths below when material design questions remain.

## Choose A Path

Choose the lightest path supported by what you know:

- **Spike:** test feasibility and report what you learn. Any code stays
  disposable.
- **Bounded:** resolve choices within a limited design surface, then
  give a short design preface and implement when requested.
- **Architectural:** design a complete system, subsystem, shared
  interface, or broadly coupled change and record it in a spec.

Tell the user which path you chose only when it changes the expected
deliverable or introduces an approval step. Inspect relevant code and
documentation before designing. Inspect Git history only when it can
answer a real question about intent or established patterns.

Reclassify when evidence changes. Explain the new evidence before
adding a spec, an approval point, or another user-visible step.
Uncertainty by itself does not justify a heavier path.

## Work With The User

- Ask independent questions together. Hold questions that depend on
  unsettled answers for a later round.
- Prefer multiple-choice questions. Use an open question when you do not
  yet know the credible options.
- Use your judgment about which design choices need user input. Ask when
  the answer would meaningfully change the proposed design; otherwise
  choose a reasonable default and proceed.
- Compare approaches only when more than one credible approach exists.
  Lead with your recommendation and explain the trade-offs.
- Apply YAGNI: exclude features and abstractions that the requested
  outcome does not require.
- Follow relevant repository patterns. Surface an existing structural
  problem only when it affects the proposed design. Do not include
  unrelated refactoring.

## Use HTML For Visual Thinking

Strongly favor the html skill when layouts, flows, architecture, states,
or side-by-side options would be easier to inspect visually. Invoke it
without asking first. Keep plain requirements and simple text choices in
chat.

Follow the repository's documentation pattern for durable HTML. If none
exists, use `docs/YYYY-MM-DD-<topic>-visual.html`. Link durable HTML from
the relevant spec. Put exploratory HTML in a unique
`.disposable/YYYY-MM-DD-<topic>/` folder. Ensure `.disposable/` appears
in `.gitignore`, report the exact path, and never delete the artifact.

## Spike

Use a spike for a feasibility question whose output is an answer rather
than production code. Present the question and probe in 2-3 sentences.
An explicit request to run the probe counts as authorization; otherwise
get a nod before proceeding.

Find out as cheaply as correctness allows. Put all new or changed probe
code in a unique `.disposable/YYYY-MM-DD-<topic>/` folder and ensure
`.disposable/` appears in `.gitignore`. Do not modify tracked project
files. If the probe cannot run under that constraint, explain why and
ask before expanding its scope.

Never delete disposable artifacts. Report the conclusion, supporting
evidence, what the probe did not establish, your recommendation, and the
exact artifact path. Productionizing the probe requires a new
implementation request.

## Bounded

Use the bounded path when the request has a limited design surface and
local impact. It may add something new or change an existing flow.

Resolve only choices that could change the implementation. Then give a
brief, natural preface that covers the approach, affected files, and
testing. Do not use a canned announcement or ask for approval. Implement
when the user requested a build; stop after the design when they did not.
Do not write a spec or implementation plan by default.

## Architectural

Use the architectural path for a new project or subsystem, a change to
system boundaries or shared interfaces, or work with broad coupling.
Design the complete requested system before implementation. Decompose it
into subprojects where that clarifies ownership, interfaces, or build
order, but do not design only the first part and leave the rest open.

The system design must cover the full goal, major capabilities,
subproject boundaries, interfaces, data flow, shared constraints, build
order, risks, testing strategy, and success criteria where relevant. It
must be complete enough that implementation planning does not reopen
settled design decisions. Present the design in sections scaled to their
complexity.

Write the system spec using the repository's existing documentation
pattern. If none exists, use `docs/YYYY-MM-DD-<topic>-design.md`. Never
commit the spec.

When a subproject later develops substantial design questions, write a
focused spec using the same repository pattern or
`docs/YYYY-MM-DD-<subproject>-design.md`. Link it from the system spec.
Update the system spec when a subproject changes a system-level decision.

After drafting any spec, invoke the stop-slop skill to tighten the prose
without changing exact requirements, identifiers, constraints, or
decisions. Then review the spec:

1. **Placeholders:** Replace every TBD, TODO, incomplete section, or
   vague requirement.
2. **Consistency:** Resolve contradictions and ensure the described
   components support the chosen behavior.
3. **Scope:** Confirm the spec covers the complete system and gives each
   subproject a coherent boundary and sequence.
4. **Ambiguity:** Make any requirement with more than one reasonable
   interpretation explicit.

Fix problems inline. Run the prose and technical reviews again after
material revisions.

Link the finished spec, summarize the settled design, and ask for final
approval in natural language before implementation. If the user requests
changes, revise and review it, then ask again.
After approval, continue through the normal development workflow when
the user requested a build. A design-only request ends with the spec.

Keep the approved spec current during implementation. Record small
implementation discoveries and continue. When a discovery meaningfully
changes the agreed design, update the spec and ask for user input before
continuing.
