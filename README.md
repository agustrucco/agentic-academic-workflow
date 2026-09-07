# udesa

Working repository for the **Master in Business & Technology** (Maestría en Gestión de Servicios Tecnológicos y de Telecomunicaciones) at Universidad de San Andrés (UdeSA), Buenos Aires.

This is not a code repository. It is a **research, design, and writing repo** — structured with the same agent/skill discipline normally applied to software: separating planning from execution, documenting how work is done, keeping each deliverable isolated.

---

## What's here

### MT10 — Innovación Tecnológica

**Deliverable: loyalty platform proposal for Argentina's leading supermarket chain**

A full business case proposing a unified data platform and digital wallet for the market leader in Argentine supermarket retail (22.3% market share, ~120 stores, ~20M monthly transactions). The chain is the uncontested leader in e-commerce for the sector yet loses traceability on 35–45% of its in-store transactions because customers don't identify themselves at checkout — and is the only top-2 player with no proprietary digital wallet, while its two main competitors (15% and 17% market share) already launched theirs.

The proposal includes:

- **Competitive analysis** — market share, digital wallet landscape, margin leakage to third-party payment processors
- **Agentic data platform design** — not six isolated AI projects, but a single orchestrator that connects POS, e-commerce, the in-house credit card core, warehouse management, and social media interaction for the first time
- **Omnichannel strategy** — CRM, campaign management, real-time segmentation, customer service consolidation
- **Financial model** — ROI case with sensitivity analysis across three adoption scenarios; NPV positive even in the worst-case scenario tested
- **Phase 0 experiments** — three low-cost probes to replace the biggest modeling assumptions with real evidence before committing full budget
- **10-minute board pitch** — slide deck scripted for a CFO/CEO/CMO audience in a role-play defense

Key documents:
- [`plan-de-negocios.md`](plan-de-negocios.md) — full business plan (60+ pages, Spanish)
- [`materias/mt10-innovacion-tecnologica/fidelizacion-coto/`](materias/mt10-innovacion-tecnologica/fidelizacion-coto/) — research, solution plans, and deliverables

---

## How work is structured

The interesting part of this repo is the **agentic AI workflow** used to produce the deliverables. Six specialized Claude agents coordinate across phases:

```
Research → Design → Review → Write → Slides
```

| Agent | Role | Never does |
|---|---|---|
| `tp-orchestrator` | Coordinates phases across any deliverable | Research, design, or write directly |
| `tp-research-analyst` | Market research, competitor analysis, theory frameworks | Design the solution or write the document |
| `tp-solution-architect` | Designs the solution and ROI case; reviews plans | Write the final document |
| `tp-plan-writer` | Writes the final document in `entregable/` | Research or design independently |
| `tp-presentation-designer` | Scripts and structures the spoken pitch | Generate new business content |
| `tp-ux-ui-designer` | Builds visual artifacts (HTML presentations, landing pages) using the design system | Invent business content |

**Core rule:** no section is written before its research and design are complete and reviewed. The separation between `tp-solution-architect` and `tp-plan-writer` exists to catch a poorly-founded claim or a weak component before it reaches the final document.

Agent definitions: [`.claude/agents/`](.claude/agents/)

---

## Skills (reusable across deliverables)

| Skill | Purpose |
|---|---|
| [`tp-workflow`](.claude/skills/tp-workflow/SKILL.md) | Phase skeleton and tool-selection table |
| [`how-to-research-competitor`](.claude/skills/how-to-research-competitor/SKILL.md) | Protocol for researching a competitor or benchmark |
| [`how-to-build-roi-case`](.claude/skills/how-to-build-roi-case/SKILL.md) | ROI case structure without inventing numbers |
| [`how-to-structure-pitch`](.claude/skills/how-to-structure-pitch/SKILL.md) | Pitch structure — timing and audience come from each deliverable's brief |

---

## Design system

A shared visual language for all presentations in the repo: color tokens, typography, grid, and reusable slide components. Defined once, applied consistently across any deliverable.

[`design-system/`](design-system/)

---

## Repo structure

```
consignas/            — assignment briefs, as-given by each course
materias/
  mt10-innovacion-tecnologica/
    fidelizacion-coto/
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

- **Rigor over creativity**: every market claim or number must trace back to a source.
- **No filler**: AI components are proposed because they solve a specific problem found in the research, not because the brief mentions them as desirable.
- **Audience clarity**: each deliverable is written for the real audience stated in its brief, not a generic academic report.
- **Each deliverable is independent**: format, audience, and checklist from one assignment do not carry over to another.
