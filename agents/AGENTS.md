# Org-control (skills only)

This project uses **org-control** via org skills. No MCP server is required. Planning, review, docs, QA, and risk follow the org workflows below.

**Preferences:** Stored in `mcp/preferences.json` (strictness, ask_before). Get or set via the **org-preferences** skill (read/write the file).

**Vague or unclear request** → use **org-receptionist** to route to the right workflow.

**Feature, bugfix, refactor, or complex task** → use **org-orchestrator** to normalize the request and build a plan.

**Quick index:** Code/PR review → org-senior-dev. Tailwind/mobile UI → org-tailwind-reviewer. SEO (meta, headings, URLs, alt) → org-seo-reviewer. Stack/ADR → org-architecture-steward. Risk → org-risk-assessor. Docs → org-docs-team. QA/sign-off → org-qa-team. Feedback/cross-domain → org-feedback-loop. Content strategy/post → org-content-strategist / org-content-creator. Component structure → component-philosophy. Change preferences → org-preferences. Set up new project rules (.cursor from README/docs) → org-project-setup.
