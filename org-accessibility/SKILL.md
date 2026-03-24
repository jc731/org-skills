---
name: org-accessibility
description: Reviews UI for accessibility—semantics, ARIA, keyboard, focus, contrast. Use when reviewing frontend/UI for a11y or when the user asks about accessibility.
---

# Org Accessibility

## Quick Start

The Accessibility skill reviews UI (markup, components, styles) for accessibility. It complements layout (tailwind) and structure (component-philosophy) by focusing on how users with assistive tech and keyboard navigate and understand the interface.

1. **Identify scope**: Which pages or components are in scope? (e.g. form, modal, nav.)
2. **Check semantics and behavior**: Landmarks, headings, labels, focus order, keyboard traps, ARIA where needed (and not redundant).
3. **Call out contrast and visibility**: Sufficient contrast, focus indicators, visible focus.

## Core Checks

- **Semantics**: Correct elements (e.g. `<button>` not `<div onclick>`, `<label>` for inputs, heading hierarchy).
- **Keyboard**: All interactive elements reachable and operable by keyboard; no focus traps (e.g. modals).
- **ARIA**: Use when semantics aren’t enough (e.g. live regions, expanded/collapsed); avoid ARIA when native semantics suffice.
- **Focus**: Visible focus style; focus order follows visual order where possible.

## When to Involve Other Skills

- **Component structure affects a11y** (e.g. repeated pattern that should be a component with proper semantics) → Apply or reference **component-philosophy** so structure and semantics align.
- **Layout or responsive behavior affects a11y** (e.g. focus order on mobile, touch targets) → **org-tailwind-reviewer** for layout; work together on touch target size and order.
- **Documentation** (a11y statement, how to test a11y) → **org-docs-team** to add or update.
- **Full PR or broader code review** → **org-senior-dev**; stay focused on a11y and defer logic/security/tests to senior-dev.

## Output

- List issues with location (file/component) and severity (blocking vs. suggestion).
- Concrete fix (e.g. add `aria-label`, use `<button>`, ensure `:focus-visible`).
- When handing off, name the skill (docs-team, tailwind-reviewer, component-philosophy, senior-dev) so the agent invokes the right one.
