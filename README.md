# agentic-academic-workflow

Working repository for the **Master in Business & Technology** (Maestría en Gestión de Servicios Tecnológicos y de Telecomunicaciones) at Universidad de San Andrés (UdeSA), Buenos Aires.

This is not a code repository. It is a **research, design, and writing repo** — structured with the same agent/skill discipline normally applied to software: separating planning from execution, documenting how work is done, keeping each deliverable isolated.

---

## MT10 — Innovación Tecnológica

**Deliverable: loyalty platform proposal for Argentina's leading supermarket chain**

A full business case proposing a unified agentic data platform and a proprietary digital wallet for the #1 player in Argentine supermarket retail. The company holds **22.3% market share**, operates **120+ stores**, and processes **~12 million in-store transactions per month** — yet loses traceability on **35–45% of those transactions** because customers don't identify themselves at checkout. It is also the only top-2 player with no proprietary digital wallet, while both its closest competitors (21% and 17% market share) already launched theirs.

### The problem, in numbers

| Metric | Value |
|---|---|
| Market share | 22.3% — Argentina's #1 supermarket |
| Monthly in-store transactions | ~12 million |
| Transactions with no customer traceability | 35–45% |
| Sales captured by third-party payment processors | 45% (at 1.2–1.8% + VAT per transaction) |
| Additional sales on debit (no loyalty data) | 23.9% |
| Top competitors with proprietary digital wallet | 2 of 5 — already live and scaling |

Every month without action is another month of customer data generated and permanently lost across 12 million transactions.

### What the proposal covers

- **Competitive analysis** — full market-share breakdown, digital wallet landscape across all five major competitors, quantified margin leakage to third-party payment processors
- **Agentic data platform** — a single orchestrator connecting five siloed systems (POS, e-commerce, in-house credit card core, warehouse management, and social channels) for the first time — not six isolated AI projects bolted on top of each other
- **Omnichannel strategy** — CRM architecture, campaign management, real-time segmentation, customer service channel consolidation
- **Financial model** — full ROI case with sensitivity analysis across three adoption scenarios; **NPV positive in all three**, including the adversarial scenario
- **Phase 0** — three low-cost experiments specifically designed to replace the largest modeling assumptions with real evidence before committing the full budget
- **10-minute board pitch** — scripted for a CFO/CEO/CMO audience in a role-play defense format

Key documents:
- [`plan-de-negocios.md`](plan-de-negocios.md) — full business plan (60+ pages, Spanish)
- [`materias/mt10-innovacion-tecnologica/fidelizacion-retailco/`](materias/mt10-innovacion-tecnologica/fidelizacion-retailco/) — research, solution plans, and deliverables

---

## How work is structured

The interesting part of this repo is the **multi-agent AI workflow** used to produce the deliverables. Six specialized Claude agents coordinate across strict phases:

```
Research → Design → Review → Write → Slides
```

No section is written before its research and design are complete and reviewed. The separation between the solution architect agent and the plan writer agent exists to catch a poorly-founded claim or a weak component before it reaches the final document.

| Agent | Role | Never does |
|---|---|---|
| `tp-orchestrator` | Coordinates phases across any deliverable | Research, design, or write directly |
| `tp-research-analyst` | Market research, competitor analysis, theory frameworks | Design the solution or write the document |
| `tp-solution-architect` | Designs the solution and ROI case; reviews plans | Write the final document |
| `tp-plan-writer` | Writes the final document in `entregable/` | Research or design independently |
| `tp-presentation-designer` | Scripts and structures the spoken pitch | Generate new business content |
| `tp-ux-ui-designer` | Builds visual artifacts (HTML presentations, landing pages) applying the design system | Invent business content |

Agent definitions: [`.claude/agents/`](.claude/agents/)

---

## Reusable skills

| Skill | Purpose |
|---|---|
| [`tp-workflow`](.claude/skills/tp-workflow/SKILL.md) | Phase skeleton and tool-selection table — loaded at the start of every section |
| [`how-to-research-competitor`](.claude/skills/how-to-research-competitor/SKILL.md) | Protocol for researching a competitor or benchmark without inventing data |
| [`how-to-build-roi-case`](.claude/skills/how-to-build-roi-case/SKILL.md) | ROI case structure that surfaces assumptions explicitly instead of hiding them |
| [`how-to-structure-pitch`](.claude/skills/how-to-structure-pitch/SKILL.md) | Pitch structure — timing and audience always come from the deliverable's brief, not a fixed template |

---

## Design system

A shared visual language for all presentations: color tokens, typography, grid, and reusable slide components. Defined once, applied consistently across any deliverable.

[`design-system/`](design-system/)

---

## Repo structure

```
consignas/            — assignment briefs, as-given by each course
materias/
  mt10-innovacion-tecnologica/
    fidelizacion-retailco/
      research/       — cited research (market, theory, competitors)
      plans/          — solution design, reviewed before writing
      entregable/     — final document + presentation/
design-system/
  tokens/             — palette, typography, spacing, grid
  components/         — reusable slide patterns
.claude/
  agents/             — six specialized agents
  skills/             — four reusable skills
  agent-memory/       — per-agent persistent memory across sessions
```

---

## Working principles

- **Rigor over creativity** — every market claim or number must trace back to a source; if there is no reliable source, it is marked explicitly as a team assumption, never stated as fact
- **No filler** — AI components are proposed because they solve a specific problem found in the research, not because the brief mentions them as desirable
- **Audience clarity** — each deliverable is written for the real audience stated in its brief, not a generic academic report that works for anyone
- **Each deliverable is independent** — format, audience, and checklist from one assignment do not carry over to another
