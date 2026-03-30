---
name: prd-spec
description: >
  Write a full, post-prototype Product Requirements Document (PRD) for a signed-off feature or
  product. Use this skill whenever a PM needs to produce a PRD, spec doc, or requirements document
  that will be handed off to engineering and/or shared with stakeholders. Trigger on phrases like
  "write a PRD", "spec this out", "I need a requirements doc", "write up the spec", "document
  this feature for engineering", "post-prototype PRD", or "we got sign-off, now I need to write
  it up". This skill produces a classic, full-length PRD with a TLDR at the top — not a one-liner
  brief or a lean canvas. Use it whenever the output needs to be comprehensive enough for engineers
  to estimate, plan, and build from.
---

# PRD Spec Skill — Post-Prototype

You are helping a product manager write a full Product Requirements Document (PRD) for a feature
that has passed prototype sign-off. The hard decisions have been made — this document captures
*what gets built, by whom, and to what standard*, precisely enough for engineering to act on and
stakeholders to align around.

## Context: why post-prototype matters

A post-prototype PRD is different from an early-stage one. The PM is no longer exploring the
problem space — they're closing it. That means:

- The core user need and solution direction are validated — don't re-litigate them
- The spec should distinguish clearly between what was validated in the prototype vs. what's
  new or assumed for the full build
- Edge cases, non-functional requirements, and out-of-scope decisions matter more now — these
  are the things that weren't in the prototype but will surface in production
- The audience is split: **stakeholders** need to understand scope and approve it;
  **engineers** need enough detail to estimate and build without constant back-and-forth

---

## How to run this skill

Work through these phases in order. Ask questions conversationally — don't dump everything at
once. Confirm your understanding at each phase before moving on.

---

### Phase 1: Orient around the prototype

Before writing anything, understand what's already been decided. Ask:

- What did the prototype cover, and what was the key insight or validation from sign-off?
- What's the core user problem this solves? (One sentence, from the user's perspective)
- Who are the primary users? Are there secondary users or admin personas?
- Are there any major decisions that changed between the prototype and the full build?

This shapes the entire document. If the PM is vague here, push gently — "what would you say
to a new engineer joining the team tomorrow to get them up to speed in 2 minutes?"

---

### Phase 2: Pin down goals and metrics

A PRD without measurable success criteria is a wish list. Ask:

- What does success look like in 30 / 90 days post-launch?
- What are the 1-2 north star metrics for this feature?
- Are there any guardrail metrics — things we must NOT make worse?
- How will we know if we've failed and should roll back or pivot?

Push for specificity: "adoption is high" is not a metric. "70% of active users have used the
feature at least once within 30 days of launch" is.

---

### Phase 3: Gather functional requirements

This is the core of the PRD for engineering. Work through requirements systematically:

**Happy path first:** Walk through the primary user flow step by step. What does the user do,
what does the system do, what's the output?

**Prioritisation:** For each requirement, assign a MoSCoW priority:
- **Must have** — launch is blocked without this
- **Should have** — important but a workaround exists
- **Could have** — nice to have if time permits
- **Won't have (v1)** — explicitly out of scope

**Edge cases:** What happens when things go wrong? Probe for:
- Empty states (first use, no data)
- Error states (network failure, invalid input)
- Permission/access edge cases
- Concurrency or race conditions if relevant
- High-volume or scale edge cases

**Non-functional requirements:** Don't skip these — they trip up engineering handoffs.
- Performance targets (e.g., page load < 2s at p95)
- Accessibility (WCAG level)
- Security and data privacy requirements
- Browser/device/platform support
- Internationalisation and localisation needs

---

### Phase 4: Clarify design and UX

- Are final designs available, or are they still in progress?
- Link to or describe the key screens and flows
- Call out any UX decisions that engineering needs to honour (e.g., animation behaviour,
  empty states, loading patterns)
- Are there design system components to use, or is this net new?

---

### Phase 5: Define what's out of scope

This section is as important as the requirements — it prevents scope creep and sets expectations.
Ask the PM to explicitly name:

- Features that were considered but deferred to v2
- Platforms or user segments not supported in v1
- Integrations that are not included
- Any known limitations that are accepted for launch

If the PM says "I haven't thought about that" — that's a sign an out-of-scope decision needs
to be made before the doc is final.

---

### Phase 6: Surface open questions

Every PRD has things that aren't fully resolved. Capture them explicitly with:
- The question
- Who owns the answer
- The deadline for resolving it (ideally before engineering kickoff)

---

### Phase 7: Launch and rollout

- Is this a full launch or a phased rollout (e.g., % of users, specific cohorts)?
- Are feature flags needed?
- What does the comms plan look like (internal, customers, support team)?
- Are there dependencies on other teams (data, infra, legal, support)?

---

## Output: the PRD document

Produce the document in this exact structure. Use markdown. Be specific and concrete — avoid
placeholder language like "[describe X here]". If you don't have enough information for a
section, note what's still needed rather than leaving it vague.

```
# PRD: [Feature Name]
**Status:** Draft | In Review | Approved
**Author:** [PM name]
**Last updated:** [date]
**Stakeholders:** [list]

---

## TLDR
- **What:** [One sentence on what this feature does]
- **Why:** [One sentence on the user problem it solves]
- **Who:** [Primary user(s)]
- **Launch target:** [Date or sprint]
- **Key metric:** [The single most important success measure]
- **Scope flag:** [One sentence on what's explicitly NOT in v1]

---

## 1. Background & context
[2-3 paragraphs: the problem, what was validated in the prototype, and why we're building
this now. Reference the prototype sign-off if relevant.]

## 2. Goals & success metrics
### Primary goals
[2-3 goals, written as outcomes not outputs]

### Success metrics
| Metric | Baseline | Target | Timeframe |
|--------|----------|--------|-----------|
| ...    | ...      | ...    | ...       |

### Guardrail metrics
[Metrics that must not degrade — e.g., page load time, error rate, NPS]

## 3. Users & use cases
### Primary persona
[Name, role, context — 3-4 sentences]

### Core use case
[The primary job-to-be-done, written as a user story:
"As a [user], I want to [action] so that [outcome]"]

### Secondary use cases
[If applicable]

## 4. Functional requirements
### Must have
- [Requirement 1]
- [Requirement 2]

### Should have
- [Requirement]

### Could have (v1 if time permits)
- [Requirement]

### Won't have (v1)
- [Explicitly deferred item]

## 5. User flows & edge cases
### Primary flow
[Step-by-step: User does X → System does Y → User sees Z]

### Edge cases
| Scenario | Expected behaviour |
|----------|--------------------|
| Empty state | ... |
| Error state | ... |
| [Other] | ... |

## 6. Non-functional requirements
| Requirement | Specification |
|-------------|---------------|
| Performance | e.g., p95 load time < 2s |
| Accessibility | e.g., WCAG 2.1 AA |
| Security | e.g., data encrypted at rest |
| Browser support | e.g., Chrome, Firefox, Safari — last 2 major versions |
| Mobile | e.g., responsive down to 375px |

## 7. Design & UX
[Link to designs. Call out key UX decisions engineering must honour.
Note any design system components to use.]

## 8. Out of scope (v1)
- [Item 1 — and why it's deferred]
- [Item 2]

## 9. Technical considerations
[Known constraints, dependencies, integrations, infra needs.
Written for engineers — include specifics where known.]

## 10. Dependencies & stakeholders
| Dependency | Team/person | What's needed | By when |
|------------|-------------|---------------|---------|
| ...        | ...         | ...           | ...     |

## 11. Launch & rollout plan
- **Rollout strategy:** [Full launch / % rollout / feature flag / cohort]
- **Internal comms:** [Who needs to know before launch]
- **Customer comms:** [If applicable]
- **Support readiness:** [What support needs to know]
- **Rollback plan:** [How to revert if something goes wrong]

## 12. Open questions
| Question | Owner | Due date | Status |
|----------|-------|----------|--------|
| ...      | ...   | ...      | Open   |
```

---

## Writing guidance

**Be an editor, not a transcriber.** If the PM gives you vague input, push back with a
specific question rather than writing vague output. A PRD with "the feature should be fast"
is worse than one with a gap flagged: "⚠️ Performance target not yet defined — needed before
engineering kickoff."

**The TLDR is for stakeholders, the body is for engineers.** Keep the TLDR crisp and
decision-focused. The functional requirements and edge cases sections should be precise
enough that an engineer can start building without a follow-up meeting.

**Flag missing information explicitly.** Use ⚠️ to mark sections where information is
incomplete or a decision is still pending. This is more honest and useful than padding with
assumptions.

**Out of scope is not an afterthought.** If the PM hasn't thought about what's NOT in v1,
help them — suggest common deferrals for the feature type and let them confirm. A PRD without
a clear out-of-scope section will be held responsible for everything that wasn't said.
