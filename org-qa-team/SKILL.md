---
name: org-qa-team
description: Defines acceptance criteria, test plans, and when to run tests; ensures QA findings are routed correctly. Use when planning or reviewing tests, acceptance criteria, coverage, or when a handoff from QA to docs/dev is needed.
---

# Org QA Team

## Quick Start

The QA Team focuses on testability, acceptance criteria, and routing QA-related feedback. It does not replace running tests—it ensures plans and reviews consider tests and that gaps are handed off correctly.

1. **Clarify scope**: Is this acceptance criteria for a feature, a test plan, coverage review, or a QA→docs/dev handoff?
2. **Define or review**: Write or critique acceptance criteria; suggest when to run tests (e.g. pre-merge); call out missing tests or coverage gaps.
3. **Hand off when needed**: Use **org-feedback-loop** when QA findings need to reach docs or development (e.g. qa_to_documentation).

## Acceptance Criteria

- Criteria should be testable and clear (no vague "works well").
- Tie to user-visible or contract outcomes (API behavior, UI state).
- When reviewing a plan or PR, ask: "What would we run to confirm this is done?"

## When to Involve Other Skills

- **Test code or PR under review** → Recommend **org-senior-dev** for review of test code and coverage.
- **Docs for tests or QA process** (e.g. how to run tests, test env) → **org-docs-team** to add or update.
- **QA finding that another team must act on** (e.g. tests pass but docs are wrong) → **org-feedback-loop** (e.g. qa_to_documentation) so the right skill is invoked.
- **Plan lacks testing steps** → In plans, call out that **org-qa-team** can help define acceptance criteria and test steps; **org-orchestrator** may already reference this when the plan includes QA.

## Output

- For acceptance criteria: short, numbered, testable list.
- For test plans: when to run what (e.g. unit before push, E2E before release).
- For handoffs: use feedback-loop artifact and name the target skill (docs-team, senior-dev, etc.).
