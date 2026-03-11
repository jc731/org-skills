---
name: org-feedback-loop
description: Formats and routes structured feedback loops between implicit "teams" (e.g., QA to Docs, Architecture to Dev). Use when cross-domain communication or issue escalation is required.
---

# Org Feedback Loop

## Quick Start

The Feedback Loop skill creates standardized artifacts when one domain (e.g., QA) finds an issue that belongs to another domain (e.g., Documentation or Development).

1. **Identify the Gap**: Recognize when an issue spans domains (e.g., a bug was fixed, but the docs weren't updated).
2. **Determine Direction**: E.g., `qa_to_documentation`, `architecture_risk_to_development`.
3. **Build Artifact**: Use the utility script to generate a structured artifact file.

## Artifact Generation

To create a feedback artifact, run:

```bash
python scripts/build_artifact.py \
  --direction "qa_to_documentation" \
  --type "documentation_gap" \
  --reason "Error handling for invalid credentials returns 401 but documentation states 400" \
  --content "Update the API.md file to reflect the 401 status code for invalid login." \
  --requires-escalation false \
  --requires-adr false
```

## Workflows
- **QA to Documentation**: Used when a feature works but lacks instructions or API specs.
- **Architecture to Development**: Used when a PR implementation violates a previously decided ADR.
- **Docs to Architecture/Risk**: Used when documenting a feature reveals an undocumented edge case or security risk.

## Actioning Artifacts
Once generated, the artifact is saved in `.cursor/feedback/`. Present the contents of the artifact to the user and ask if they would like you to switch to the target persona to resolve it.

**Target skills by direction:** So the right skill is invoked when acting on feedback, use this mapping:
- `qa_to_documentation` → **org-docs-team** (update or add docs).
- `architecture_risk_to_development` → **org-senior-dev** (review/align code with ADR or architecture) or **org-architecture-steward** (create or update ADR).
- `architecture_risk_to_documentation` → **org-docs-team** (document the decision or risk).
- `docs_to_architecture_risk` → **org-architecture-steward** or risk assessment; **org-feedback-loop** again if a new artifact to development is needed.