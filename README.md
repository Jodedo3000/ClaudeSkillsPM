# Claude Skills for Product Managers

A suite of Claude Code skills built for product managers — structured prompts that guide Claude to produce better, more consistent PM deliverables than it would from a bare request.

Built by [Johannes Dommnich](https://portfolio-jd.replit.app/) as a proof of concept for AI-augmented product management workflows.

---

## What is a Claude Skill?

A Claude Skill is a packaged set of instructions (a `SKILL.md` file) that Claude Code loads before tackling a task. Think of it as a specialist briefing — instead of Claude giving a generic answer, it follows a structured framework tailored to the specific task.

The difference in practice:

| Without a skill | With a skill |
|----------------|--------------|
| Claude gives a reasonable general answer | Claude follows a defined process and produces a structured deliverable |
| Output quality varies with how you phrase the prompt | Output is consistent and complete regardless of how the request is worded |
| PM has to know what to ask for | The skill knows what a good output looks like |

---

## Skills in this suite

| Skill | What it does | Status |
|-------|-------------|--------|
| [ai-evals](./ai-evals/) | Design evaluation frameworks for AI-powered features | ✅ v1 |
| prd-spec | Write a post-prototype PRD | 🔜 Coming soon |
| user-interview-script | Generate structured research interview guides | 🔜 Coming soon |
| feature-prioritization | Apply RICE/MoSCoW scoring to a feature list | 🔜 Coming soon |
| competitive-teardown | Structure a competitive analysis | 🔜 Coming soon |
| retro-facilitator | Generate a structured retrospective | 🔜 Coming soon |

---

## How to install a skill

1. Download the `.skill` file from the [`dist/`](./dist/) folder
2. Open Claude Code
3. Drag the `.skill` file into the Claude Code window, or run:
   ```
   /install-skill path/to/ai-evals.skill
   ```
4. Claude will confirm the skill is installed — you can now use it in any conversation

---

## How to use a skill

Just describe your task naturally. For example, for the AI Evals skill:

> *"I'm a PM launching an AI-powered email draft assistant for our support team. I need an eval plan before we ship."*

Claude will recognise the context, load the skill, and guide you through a structured process to produce a complete AI Eval Plan document.

---

## Skill: AI Evals

**The problem it solves:** Most PMs don't have a background in ML and don't know how to systematically evaluate whether an AI feature is working well. This skill guides them through the right questions and produces a structured, actionable eval plan.

**What it produces:** An AI Eval Plan document covering:
- Quality rubric (what "good" and "bad" look like across key dimensions)
- Failure modes and their severity
- Eval approach (human, automated, and/or model-graded)
- Test set design with edge cases and golden examples
- Monitoring plan with thresholds and ownership

**Benchmark:** Tested across 3 realistic PM scenarios. With skill: **100% pass rate** vs without skill: **67%** on structured completeness criteria. The biggest gains were in failure mode specificity, edge case coverage, and monitoring thresholds.

→ [View SKILL.md](./ai-evals/SKILL.md) · [Download .skill file](./dist/ai-evals.skill)

---

## How these were built

Each skill was built using the `skill-creator` workflow in Claude Code:
1. Draft a `SKILL.md` based on PM best practices for the domain
2. Write realistic test cases (what a real PM would actually ask)
3. Run the skill against each test case using a fresh Claude agent
4. Run the same prompts *without* the skill as a baseline
5. Grade both sets of outputs against assertions
6. Iterate until the skill meaningfully outperforms the baseline

