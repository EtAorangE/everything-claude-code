---
name: add-new-install-target
description: Workflow command scaffold for add-new-install-target in everything-claude-code.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-install-target

Use this workflow when working on **add-new-install-target** in `everything-claude-code`.

## Goal

Adds support for a new install target (platform or project) to the system, including scripts, schema updates, registry, and tests.

## Common Files

- `manifests/install-modules.json`
- `schemas/ecc-install-config.schema.json`
- `schemas/install-modules.schema.json`
- `scripts/lib/install-manifests.js`
- `scripts/lib/install-targets/registry.js`
- `scripts/lib/install-targets/{target}-project.js`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create install scripts and documentation under a new directory (e.g., .codebuddy/, .gemini/).
- Update manifests/install-modules.json to register the new target.
- Update schemas/ecc-install-config.schema.json and/or schemas/install-modules.schema.json for validation.
- Implement a new scripts/lib/install-targets/{target}-project.js.
- Update scripts/lib/install-manifests.js and scripts/lib/install-targets/registry.js to recognize the new target.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.