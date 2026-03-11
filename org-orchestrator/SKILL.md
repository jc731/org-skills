---
name: org-orchestrator
description: Acts as the project manager. Normalizes requests, enforces organizational policies (ask_before triggers like breaking changes), and builds structured plans. Use when a user asks for a task that requires organizational policy enforcement or when they start a new complex request.
---

# Org Orchestrator

## Quick Start

The orchestrator normalizes incoming requests, checks against organizational preferences, and builds structured plans.

1. **Understand the Request**: Determine if it's a feature, bugfix, refactor, or question.
2. **Check Preferences**: Run the `manage_preferences.py` script to get current organizational policies.
3. **Enforce Policies**: If the request triggers an `ask_before` policy (e.g., breaking change, security sensitive, schema migration), ask the user for explicit approval before proceeding.
4. **Build Plan**: Formulate a structured plan with acceptance criteria based on the request and policies. For frontend or UI work that involves new or refactored components, the plan should call out that component boundaries and structure follow the **component-philosophy** skill (e.g., "when implementing, apply component-philosophy to decide what should be its own component").

## When to Involve Other Skills

Route work and call out these skills in the plan so the right expertise is applied:

- **Code or PR review** → **org-senior-dev** (strictness-based diff review). For Tailwind/React/Next/Nuxt UI changes, also **org-tailwind-reviewer** for mobile-first checks.
- **Stack choice, technology decision, or formal ADR** → **org-architecture-steward**.
- **Documentation** after a feature/PR or doc audit → **org-docs-team** (finalization or audit).
- **Blog ideas, content calendar, what to write next** → **org-content-strategist**; **org-content-creator** to write a specific post.
- **Cross-domain issues** (e.g. code fixed but docs not updated, or implementation violates an ADR) → **org-feedback-loop** to create an artifact and hand off to the right skill.

## Workflow

1. Execute `python scripts/manage_preferences.py get` to read `mcp/preferences.json` (or `.cursor/org-preferences.json`).
2. Compare the user's request against the `ask_before` list and the `strictness` level.
3. If an approval is required, halt and ask the user.
4. If approved or no approval is required, return a structured plan to the user.

## Updating Preferences

If the user asks to update preferences, use the script:
`python scripts/manage_preferences.py set --strictness [low|medium|high] --ask_before [item1,item2]`
