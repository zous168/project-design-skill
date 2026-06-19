# project-design-skill

A Claude Code **skill** that turns a brief or detailed project requirement into a
complete set of **production-grade analysis & design documents** — plus an
optional **interactive prototype** — through an automatic, step-by-step pipeline
where every artifact goes **create → review → optimize**. No application code is
produced (the prototype is the one intentional exception).

Adapted from Devika's agent pipeline (Planner → Researcher → Coder → Decision →
Patcher → Reporter): the "Coder" becomes a document **Writer**, the "Patcher"
becomes an explicit **Reviewer**, and a **Prototype phase** (frontend-design +
a visual-style "taste" review) is added.

## What it produces

A versioned design set (each doc carries `doc_version` / `updated` / `status`):

| # | Document |
|---|----------|
| 01 | Requirements Spec (PRD) + roles × permission matrix |
| 02 | Business & Domain Analysis |
| 03 | System Architecture (+ sub-system decomposition, ADRs) |
| 04 | Feature Tree (sub-system → module → page → operation) |
| 05 | Data Design (cfg / data / logs / stats) |
| 06 | Interface / API Design (REST + OpenAPI/Swagger) |
| 07 | Async / Background Processing (jobs, async tasks, scheduled) |
| 08 | Non-Functional Requirements (incl. i18n / theming / responsive) |
| 09 | Technology Selection |
| 10 | Project Structure & Directory Design (module-first) |
| 11 | Risk Assessment · 12 Test Strategy · 13 Roadmap · 14 Task Plan (slices + DoD) |

Plus (conditional): UX/Interaction Brief, Security, Privacy/Compliance,
Integration/Migration, Ops/Deployment, Cost/Capacity, **Caching Design**;
an interactive **prototype** in the chosen front-end stack (real components,
pages + components, mock data, working interactions, a compiled `dist/` preview);
and `README` / `CHANGELOG` / `consistency-report` on assembly.

## Pipeline

```
Phase 0 Intake & Clarify  → baseline + tech direction (FE/UI, BE, DB, architecture)
                            + sub-systems + roles + defaults (theme/i18n/responsive)
Phase 1 Plan              → which docs + whether to prototype (per sub-system)
Phase 2 Research          → focused, keyword-driven (conditional)
Phase 3 Draft→Review→Optimize, per document
Phase 4 Prototype         → generate (frontend-design) → taste review → optimize
Phase 5 Consistency review→ cross-document + prototype coherence + traceability
Phase 6 Assemble          → index, CHANGELOG, set version
```

## Layout

```
project-design-docs/
├── SKILL.md                      # the skill: pipeline, principles, templates
├── REQUIREMENTS.md               # requirement→coverage matrix + iteration log
└── references/
    ├── document-catalog.md       # the document library (01–14 + conditionals)
    └── review-rubrics.md         # content / logic / consistency / taste rubrics
```

## Install / use

Copy the `project-design-docs/` folder into your Claude Code skills directory
(e.g. `~/.claude/skills/`), or reference it from your project. Then ask Claude to
"创建项目 / design a system / write a spec / 出一套设计方案" and the skill triggers.

Optional companions used in the Prototype phase:
- `frontend-design` (Anthropic plugin) — UI visual direction.
- `taste` = `design-taste-frontend` — anti-slop visual-style review:
  `npx skills add Leonxlnx/taste-skill`.

## License

See [LICENSE](LICENSE).
