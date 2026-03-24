# Org Skills: Concept and Plan

## Concept (from this thread)

- **Skills act as a team of roles.** Each skill has one clear job; they invoke each other at the right time so the right expertise is applied.
- **Orchestrator** routes work and calls out which skills to use in plans. **Feedback-loop** creates handoff artifacts and maps directions to target skills. **Specialist skills** (senior-dev, tailwind, docs, content, architecture, component-philosophy) do their job and defer when out of scope.
- **Goal:** No single skill does everything. Cross-invoke so that e.g. a PR review can trigger component-philosophy, tailwind-reviewer, or a doc handoff as needed.

## Current Skills and Roles

| Skill | Role |
|-------|------|
| org-orchestrator | Plan, policies, route to other skills |
| org-senior-dev | Code/PR review; uses component-philosophy, defers to tailwind/docs/feedback/arch |
| org-tailwind-reviewer | Mobile-first Tailwind; uses component-philosophy; defers to senior-dev/docs/feedback |
| org-architecture-steward | Stack, ADRs; involves docs, feedback, component-philosophy |
| org-docs-team | Doc finalization and audit; involves feedback, senior-dev, content |
| org-content-strategist | Content strategy; involves content-creator, docs |
| org-content-creator | Blog/content writing; involves strategist, docs |
| org-feedback-loop | Cross-domain handoffs; maps directions to docs, senior-dev, architecture |
| component-philosophy | Component structure; used by senior-dev and tailwind; defers to them for full review |

## Proposed New Skills

### 1. org-qa-team

- **Job:** Acceptance criteria, test plans, when to run tests, coverage expectations. Ensures "done" includes testability and that QA findings get routed correctly.
- **Invokes:** **org-senior-dev** (review test code), **org-docs-team** (test/QA docs), **org-feedback-loop** (e.g. qa_to_documentation when tests exist but docs don’t).
- **Invoked by:** **org-orchestrator** (when plan includes testing/QA), **org-senior-dev** (when review finds test gaps or acceptance criteria missing), **org-docs-team** (when finalizing and test docs are in scope).

### 2. org-accessibility

- **Job:** UI accessibility review—semantics, ARIA, keyboard, contrast, focus. Complements layout (tailwind) and structure (component-philosophy).
- **Invokes:** **component-philosophy** (when structure affects a11y), **org-tailwind-reviewer** (layout/visibility), **org-docs-team** (a11y docs or statements).
- **Invoked by:** **org-orchestrator** (frontend/UI plans that should consider a11y), **org-senior-dev** (frontend review), **org-tailwind-reviewer** (when a11y surfaces in UI review).

## Invocation Review (after adding new skills)

- **Orchestrator:** Add QA (testing/acceptance criteria in plan), Accessibility (UI/frontend plan). Already has senior-dev, tailwind, arch, docs, content, feedback, component-philosophy.
- **Senior-dev:** Add org-qa-team (test gaps, acceptance criteria), org-accessibility (frontend a11y). Already has tailwind, feedback, docs, arch, component-philosophy.
- **Tailwind-reviewer:** Add org-accessibility when a11y comes up. Already has senior-dev, feedback, docs, component-philosophy.
- **Architecture, docs, content-creator, content-strategist:** No change except docs may invoke org-qa-team when test/QA docs are in scope.
- **Feedback-loop:** Add mapping for QA-related directions (e.g. qa_to_documentation → org-docs-team; development needs test plan → org-qa-team). Already maps docs, senior-dev, architecture.
- **Component-philosophy:** No change.
- **New skills (qa, accessibility):** Each has a "When to involve other skills" section that points to the above.

## Status

- [x] Add org-qa-team and org-accessibility SKILL.md files.
- [x] Update orchestrator, feedback-loop, senior-dev, tailwind, docs with new invocation lines.
- [x] Final pass: confirm every skill’s "When to involve" and feedback-loop target list are consistent.

## Invocation matrix (who invokes whom)

| Skill | Invokes |
|-------|--------|
| **org-orchestrator** | senior-dev, tailwind-reviewer, architecture-steward, docs-team, content-strategist, content-creator, **qa-team**, **accessibility**, feedback-loop, component-philosophy (for frontend) |
| **org-senior-dev** | orchestrator (strictness), component-philosophy, tailwind-reviewer, **accessibility**, **qa-team**, feedback-loop, docs-team, architecture-steward |
| **org-tailwind-reviewer** | component-philosophy, senior-dev, **accessibility**, feedback-loop, docs-team |
| **org-architecture-steward** | component-philosophy, docs-team, feedback-loop |
| **org-docs-team** | feedback-loop, senior-dev, **qa-team**, content-strategist, content-creator |
| **org-content-strategist** | content-creator, docs-team |
| **org-content-creator** | content-strategist, docs-team |
| **org-feedback-loop** | docs-team, **qa-team**, senior-dev, architecture-steward (by direction) |
| **org-qa-team** | senior-dev, docs-team, feedback-loop, (orchestrator references in plans) |
| **org-accessibility** | component-philosophy, tailwind-reviewer, docs-team, senior-dev |
| **component-philosophy** | senior-dev, tailwind-reviewer (for full review / Tailwind-specific) |
