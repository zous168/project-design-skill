---
doc_version: 11
updated: 2026-06-19
status: reviewed
---

# project-design-docs — Requirements Baseline

What this skill must satisfy, as a checklist for review and future iteration.
(This file practices the skill's own *Iteration & version management* convention:
version frontmatter above, iteration log at the bottom.)

## Coverage matrix (requirement → where it lives)

| # | Requirement | Status | Location in skill |
|---|-------------|:--:|---|
| R1 | Brief **or** detailed input → step-by-step production-grade docs | ✅ | Intro, Phase 0–6 |
| R2 | **No code** (prototype is the only exception); Markdown; language follows input | ✅ | Intro, Scope guardrails, principle "Match the user's language" |
| R3 | Per-doc **create → review → optimize** | ✅ | Phase 3 |
| R4 | AI **content + logic** review | ✅ | Rubric A, Rubric B |
| R5 | Cross-document **consistency** review | ✅ | Rubric C, Phase 5 |
| R6 | Up-front **clarify / 提示选择** when ambiguous | ✅ | Phase 0, AskUserQuestion |
| R7 | **Tech-selection gate** (FE/UI lib, BE, **database(s)**, architecture) drives prototype + data design + structure | ✅ | Phase 0 step 4 |
| R8 | **Sub-system confirmation** + decompose complex systems | ✅ | Phase 0 step 5, Phase 1, file layout |
| R9 | **Responsive breakpoints** as a design consideration | ✅ | Phase 0 step 5, UX brief, NFR, Rubric D |
| R10 | **System roles** + role × capability matrix | ✅ | Doc 01, Feature Tree, Rubric C |
| R11 | **Feature Tree** (sub-system → module → page → operation, +roles/FR/API/screen) | ✅ | Doc 04, Rubric C |
| R12 | **Data** organized as **cfg / data / logs / stats** (cross-DB id-only) | ✅ | Doc 05, Rubric C |
| R13 | **API inventory outline** + per-endpoint defs + **OpenAPI/Swagger** | ✅ | Doc 06, Rubric C |
| R14 | **Project/directory structure** as a (framework-driven) design doc | ✅ | Doc 10 |
| R15 | **Prototype phase**: generate → **taste** review → optimize | ✅ | Phase 4, Rubric D |
| R16 | Generate via `frontend-design` (direction); review via **taste** (`design-taste-frontend`) | ✅ | Phase 4a/4b, Reference files |
| R17 | **Multi-screen** prototype (screen inventory first) | ✅ | Phase 4a #1 |
| R18 | Prototype in the **real chosen framework** (real components) | ✅ | Phase 4a #2 |
| R19 | **Pages + components** structure (no giant file) | ✅ | Phase 4a #3 |
| R20 | **Mock data + real interaction** (dialogs/toasts/drawers; create/new wired) | ✅ | Phase 4a #4 |
| R21 | **Drill-down linkage** (list row → detail, card → screen) | ✅ | Phase 4a #4 |
| R22 | **Empty / loading / error** states | ✅ | Phase 4a #4, UX brief, Rubric D |
| R23 | **Theme**: light / dark / follow-system (default) | ✅ | Principle, NFR, UX, Phase 4a #5, Rubric D |
| R24 | **i18n**: zh+en default on an extensible foundation (default) | ✅ | Principle, NFR, UX, Phase 4a #5, Rubric D |
| R25 | **Iteration & version management** (doc versions, CHANGELOG, revision mode) | ✅ | Principle, "Iteration & version management", Phase 3a/6, templates |
| R26 | **Async / background processing** design — job workers, async tasks, scheduled/cron (triggers, idempotency, retries, HA-safe, observability) | ✅ | Doc 07, Doc 10 (worker layout), Rubric C |
| R27 | **Task slicing + closed-loop / DoD** spec — independently-verifiable slices, task cards, serial gating, ①–⑨ loop, failure triage | ✅ | Doc 14, principle "Work in independently-verifiable slices", derived from Feature Tree (04) |
| R28 | **API unified as REST** — resource URLs, standard verbs/status, `/api/v1`, deviation needs a reason | ✅ | Doc 06 item 1 + bar, Rubric C "API style uniform" |
| R29 | **Database selection asked in Phase 0** — primary datastore (+ analytics/cache); cfg/data/logs/stats maps onto it | ✅ | Phase 0 step 4, Doc 05 item 2, Doc 09 "headline stack early" |
| R30 | **Caching design** — cache key-points + **passive (cache-aside, with 击穿/穿透/雪崩 guards)** + **active (write-through / warming / refresh-ahead)** + invalidation/consistency | ✅ | Conditional doc "Caching Design", Doc 03 cross-cutting, Doc 07 (warm tasks), Rubric C "Cache consistency" |
| R31 | **Compiled preview HTML** — framework prototype also ships a built `dist/` (npm run build, `base:'./'`+hash) that opens statically without a dev server | ✅ | Phase 4a item 2, "Verify by clicking through", file layout (`dist/`), Prototype catalog entry |
| R32 | **Prototype covers every in-scope sub-system** (admin/website/app/…) or records an explicit, reasoned deferral — no silent omission | ✅ | Phase 4a item 1, Rubric D "Sub-system coverage", Rubric C feature-tree coverage |
| R33 | **Interaction acceptance by click-through** — each interactive element actually clicked & its effect confirmed (checklist in prototype-notes), via preview/browser tools | ✅ | Phase 4 "Verify by clicking through", Rubric D "Interaction is click-verified" |
| R34 | **Module layer on both stacks for large sub-systems** — front-end & back-end organized module-first (self-contained `modules/<module>/`), small may stay type-first | ✅ | Doc 10 items 1–3 + bar, Rubric C "Module alignment" |
| R35 | **Per-surface usage-scenario type + UI-aesthetic bar** asked in Phase 0 (tool / admin console / marketing site / dashboard / mobile) — drives the **visual direction** (which generator leads) **and the functional layout** (density, nav, chrome-vs-content) | ✅ | Phase 0 step 5, 00-PROGRESS template, UX brief, Rubric D "Calibrated to the surface's aesthetic bar" |
| R36 | **Ask the user for visual references / 效果图** in Phase 0 (mockups, competitor screenshots, brand/style guide) — recorded in the baseline, fed into prototype generation + UX brief visual direction | ✅ | Phase 0 step 6, Phase 4a generate, UX brief, Rubric D |
| R37 | **Requirement-change workflow** — capture & log → classify → impact-analysis (via Feature Tree) → update affected docs only (bump version) → re-run Phase 5 consistency → version & record | ✅ | Principle "living artifacts", "Iteration & version management" → Requirement-change workflow, Revision mode |

## Working agreement
- New requirements **improve this skill**, not the `crm-design-demo` example
  (the demo only validates the skill).

## Skill iteration log
- **2026-06-19 · v1.10 — usage scenario, visual references & change workflow.**
  Three user-driven additions. (1) **Per-surface usage scenario + UI-aesthetic
  bar** asked in Phase 0 step 5: each in-scope surface declares what kind of
  product it is (utility tool / admin console / marketing site / dashboard /
  mobile) and how much polish it needs — this drives both the **visual direction**
  (which prototype generator leads) and the **functional layout** (information
  density, nav pattern, chrome-vs-content); recorded in the baseline, carried into
  the UX brief, and made a calibration criterion in Rubric D so a deliberately
  utilitarian console isn't judged by marketing-site polish. (2) **Visual
  references / 效果图** requested from the user in a new Phase 0 step 6 (mockups,
  competitor screenshots, brand/style guide), recorded in the baseline and fed into
  Phase 4a generation + the UX brief — the strongest anchor against a templated
  default. (3) **Requirement-change workflow** added to *Iteration & version
  management*: capture & log → classify → impact-analysis (via the Feature Tree) →
  update affected docs only (bump version) → re-run Phase 5 consistency → version &
  record; the "living artifacts" principle now points at it. READMEs (EN + 中文)
  Phase-0 summary updated. (R35/R36/R37)
- **2026-06-19 · v1.9 — dependency sources documented.** Added a **Dependencies
  (external skills)** section to SKILL.md with git URLs + install + fallback for
  the two optional Phase-4 skills — `frontend-design`
  (github.com/anthropics/claude-plugins-public) and `taste` =
  `design-taste-frontend` (github.com/Leonxlnx/taste-skill); mirrored in the repo
  README (EN + 中文).
- **2026-06-19 · v1.8 — module layer on both stacks.** 工程结构文档(10):大型子系统
  的**前端与后端都要 module-first**(`modules/<module>/` 自包含,对齐功能树/架构模块
  边界);小型可类型优先,需说明。Rubric C 增「Module alignment」跨文档校验。(R34)
- **2026-06-19 · v1.7 — sub-system coverage + click-through acceptance.**
  (1) Phase 4a 强制原型**按子系统列屏清单、覆盖每个在范围子系统**,未做须**显式记录延后**(非静默遗漏)——回应"原型缺后台/APP 是否 skill 问题":是,生成期未强制(只审核期发现),已修。(2) 验收升级为**点选验收**:用 preview/browser 工具逐个交互元素点击确认效果 + `prototype-notes.md` 验收清单;"能渲染"不算验收。Rubric D 增"子系统覆盖"+"交互点选验收"。(R32/R33)
- **2026-06-19 · v1.6 — compiled preview HTML.** Framework prototype must also
  ship a **built `dist/`**(`npm run build`,Vite `base:'./'` + hash 路由),可不依赖
  dev server 直接静态打开;"Verify it runs" 增加"编译预览能打开"校验;文件布局加
  `prototype/dist/`。(R31)
- **2026-06-19 · v1.5 — caching design.** Added conditional doc **Caching Design**
  (缓存关键点 + 被动 cache-aside 含击穿/穿透/雪崩对策 + 主动 write-through/预热/
  refresh-ahead + 失效与一致性 + 缓存点清单表);挂接架构 03 横切、异步 07(预热/刷新
  调度)、Rubric C(缓存一致性校验)。(R30)
- **2026-06-19 · v1.4 — database selection gate.** Phase 0 step 4 now also asks
  the **database(s)** (primary datastore + analytics/cache); doc 05 maps the
  cfg/data/logs/stats split onto the chosen store; doc 09 lists database among the
  headline-stack choices settled early. (R29)
- **2026-06-19 · v1.3 — REST API unification.** Doc 06 now defaults the API
  surface to **REST** (resource URLs, standard verbs/status, `/api/v1`, deviation
  needs a reason; events/queues stay in doc 07); added a REST-uniformity check to
  Rubric C. (R28)
- **2026-06-19 · v1.2 — task slicing & closed-loop.** Added core doc **14 — Task
  Plan & Delivery Workflow** (independently-verifiable slices derived from the
  feature tree, task cards, serial gating, ①–⑨ closed-loop/DoD, failure triage,
  agent defaults) + an operating principle applying the same slicing discipline to
  the design work itself. Adapted from the user's reference dev workflow. (R27)
- **2026-06-19 · v1.1 — async/background processing.** Added core doc **07 —
  Async / Background Processing Design** (job workers, async tasks, scheduled/cron;
  triggers, idempotency, retries, DLQ, HA-safe scheduling, observability);
  renumbered NFR→08…roadmap→13; worker/queue/scheduler layout added to the
  project-structure doc; async-coverage check added to Rubric C. (R26)
- **2026-06-19 · v1.0 — consolidated baseline.** Built up over these rounds:
  doc-only pipeline (clarify → plan → research → draft/review/optimize →
  consistency → assemble) → added Prototype phase + taste review → integrated the
  real `taste` skill → tech-selection gate + project-structure doc + prototype
  interactions → multi-screen + remaining states + drill-down linkage + wired all
  actions → responsive breakpoints + sub-system decomposition + Feature Tree +
  roles + cfg/data/logs/stats + OpenAPI/Swagger → real-framework prototype
  (pages+components, mock data) → theme + i18n defaults → audit pass (reconciled
  prototype description) → iteration & version management.
