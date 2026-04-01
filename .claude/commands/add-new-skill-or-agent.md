---
name: add-new-skill-or-agent
description: Workflow command scaffold for add-new-skill-or-agent in everything-claude-code.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-skill-or-agent

Use this workflow when working on **add-new-skill-or-agent** in `everything-claude-code`.

## Goal

Adds a new skill or agent to the system, including documentation, registration, and sometimes supporting files.

## Common Files

- `skills/{skill-name}/SKILL.md`
- `skills/{skill-name}/**`
- `agents/{agent-name}.md`
- `manifests/install-modules.json`
- `AGENTS.md`
- `README.md`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create a new SKILL.md or agent .md file in the appropriate directory (skills/ or agents/).
- Add supporting files (e.g., references, scripts, rules, or agent subcomponents) if needed.
- Update manifests/install-modules.json to register the new skill/agent.
- Update AGENTS.md and/or README.md to reflect the new addition.
- Add or update tests if the skill/agent has code or CLI integration.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.