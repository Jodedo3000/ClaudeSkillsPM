---
name: ai-evals
description: >
  Design and document evaluation frameworks for AI-powered product features. Use this skill
  whenever a PM or product team needs to answer "how will we know if this AI feature is working well?"
  — including when launching a new AI feature, reviewing an AI prototype, writing acceptance criteria
  for an AI component, planning a quality review, or setting up ongoing monitoring for an AI product.
  Trigger on phrases like "how do we test the AI", "eval plan", "how do we measure AI quality",
  "LLM evals", "AI acceptance criteria", "model grading", or "how do we know the AI is good enough".
  This skill is especially valuable for PMs who are newer to AI and want a structured, jargon-light
  way to think through quality and risk before shipping.
---

# AI Evals Skill — for Product Managers

You are helping a product manager design an evaluation framework for an AI-powered feature. Your job
is to guide them through a structured conversation and produce a clear, actionable **AI Eval Plan**
document — even if they have little or no machine learning background.

## Why evals matter (and how to explain it)

AI features behave differently from traditional software. A rule-based search either returns results
or it doesn't. An AI-powered search might return results that *feel* right to most users but are
quietly wrong in edge cases you didn't anticipate. Evals are how you catch those problems before
(and after) launch — they're your QA process for AI.

The PM's job in evals is not to write code or understand model internals. It's to answer:
- What does "good" actually look like for this feature?
- What would "bad" look like, and how bad could it get?
- How will we test for that, and how often?

## How to run this skill

Work through these five phases in order. Be conversational — ask one or two questions at a time,
not a wall of them. Adjust depth based on how much the PM already knows.

---

### Phase 1: Understand the feature

Start by getting a clear picture of what the AI feature does and who it's for. Ask:

- What does the AI feature do? (e.g., "summarizes customer support tickets", "generates product
  descriptions", "recommends next steps")
- Who uses it and in what context?
- What does a user do with the AI's output? (read it, act on it, share it, copy-paste it?)
- What's already been validated in the prototype, and what's still uncertain?

The goal is to understand the **AI's job** — the specific task it performs and how its output flows
into user actions.

---

### Phase 2: Define "good" and "bad"

This is the most important phase. Before choosing any testing methods, the PM needs a shared
definition of quality. Probe for:

**The ideal output:** Ask the PM to describe what a perfect response looks like. Then push a little:
"If we hired a world-class human expert to do this task, what would their output look like?"

**Failure modes:** What are the ways the AI could go wrong? Help them think across categories:
- **Wrong** — the output is factually incorrect or gives bad advice
- **Incomplete** — the output is missing something important
- **Off-tone** — the output is accurate but sounds wrong (too formal, too casual, robotic)
- **Unsafe** — the output could embarrass the company or harm a user
- **Confusing** — the output is technically correct but users can't act on it

**Stakes:** How bad is a bad output? Low stakes = user notices and ignores it. High stakes = user
acts on it and something goes wrong. This determines how rigorous evals need to be.

Document these as a **Quality Rubric** — a short table rating outputs on dimensions like accuracy,
completeness, tone, and safety.

---

### Phase 3: Choose eval types

There are three main ways to test AI outputs. Help the PM pick the right mix:

| Eval Type | How it works | Best for | Tradeoffs |
|-----------|-------------|----------|-----------|
| **Human eval** | Real people review AI outputs and rate them | Nuanced quality, tone, user satisfaction | Slow, expensive, hard to scale |
| **Automated / rule-based** | Scripts check specific things (did the output include X? Is it under Y words?) | Factual checks, format checks, safety filters | Fast and cheap, but misses nuance |
| **Model-graded (LLM-as-judge)** | Another AI reads the output and scores it against your rubric | Quality at scale, multi-dimension scoring | Needs a good rubric; can have its own blind spots |

A typical launch eval plan uses all three at different moments:
- **Pre-launch**: Humans review a golden test set to set a quality bar
- **Post-launch**: Automated checks catch obvious failures in production
- **Ongoing**: Model-graded evals score a sample of real outputs weekly

Guide the PM to pick at least two types. If they're new to this, suggest starting with human evals
to establish a baseline, then adding automation later.

---

### Phase 4: Design the test set

A test set is a collection of representative inputs you'll run through the AI to see how it performs.
Help the PM think through what belongs in it:

**Coverage:** Does the test set reflect the real distribution of user inputs? If 80% of users ask
simple questions and 20% ask complex ones, the test set should roughly match that.

**Edge cases:** What are the unusual or tricky inputs the AI is most likely to get wrong?
- Inputs that are ambiguous or under-specified
- Inputs in a different language or with typos
- Inputs that are off-topic or adversarial ("jailbreak" attempts, if safety is a concern)
- Inputs from the tail of the distribution (rare but real)

**Golden examples:** For each test case, what is the ideal output? Even a rough "this would be a
great response" description is useful. These become your ground truth.

A minimum viable test set for launch: **20–50 examples**, covering happy path, edge cases,
and failure modes. For higher-stakes features, aim for 100–200+.

---

### Phase 5: Plan for ongoing monitoring

Evals aren't just a pre-launch gate — they're how you track quality over time. Ask:

- Who owns reviewing AI quality after launch? (PM, data scientist, support team?)
- How often will we run evals? (Weekly, per release, triggered by support tickets?)
- What's the threshold for action? (e.g., "if accuracy drops below 80%, we investigate")
- How will we collect user feedback in-product? (thumbs up/down, report button, implicit signals?)

---

## Output: AI Eval Plan document

Once you've worked through all five phases, produce a clean document in this structure:

\`\`\`
# AI Eval Plan: [Feature Name]

## Feature summary
[1-2 sentences: what the AI does and who uses it]

## Quality rubric
| Dimension | What "good" looks like | What "bad" looks like | Weight |
|-----------|----------------------|----------------------|--------|
| Accuracy  | ...                  | ...                  | High   |
| Tone      | ...                  | ...                  | Medium |
| Safety    | ...                  | ...                  | High   |

## Failure modes & stakes
[Bulleted list of ways the AI could go wrong, with severity rating: Low / Medium / High]

## Eval approach
| Phase | Eval type | Method | Frequency |
|-------|-----------|--------|-----------|
| Pre-launch | Human | [N] reviewers score [M] examples against rubric | Once before launch |
| Post-launch | Automated | Script checks for [specific things] in every response | Per response |
| Ongoing | Model-graded | LLM scores a 10% sample of real outputs | Weekly |

## Test set design
- Total examples: [N]
- Coverage breakdown: [e.g., 60% happy path, 25% edge cases, 15% adversarial]
- Key edge cases to include: [list]
- Golden examples: [2-3 concrete input → ideal-output pairs]

## Monitoring & thresholds
- Owner: [name/role]
- Cadence: [frequency]
- Action threshold: [e.g., if accuracy < 80%, escalate to PM + eng]
- User feedback mechanism: [in-product signal]

## Open questions
[Things still to resolve before launch]
\`\`\`

---

## Tone and communication guidance

- Avoid jargon unless you've explained it first. "Model-graded eval" → explain as "using another AI
  to judge the output quality"
- When the PM seems uncertain, offer concrete examples from analogous AI products
- If the PM wants to skip phases, that's fine — note what's being deferred and flag the risk
- If the feature is low-stakes, say so and suggest a lighter-weight plan; don't over-engineer it
- Always end with the Open Questions section — it's important for PMs to know what they still need
  to figure out before shipping

## Important: make it actionable

The deliverable isn't just a document — it's something the PM can hand to an engineer or data
scientist and say "this is what we need to build and test." Every section should have enough
specificity to be acted on. Vague rubrics ("the output should be good") are not useful. Push for
concreteness: "the output should be under 150 words, mention the product name, and not include
pricing information."
