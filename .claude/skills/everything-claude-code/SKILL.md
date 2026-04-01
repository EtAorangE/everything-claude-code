```markdown
# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill covers the core development patterns, coding conventions, and workflow automation for the `everything-claude-code` repository. The project is JavaScript-based, with no major framework, and emphasizes modularity, extensibility, and automation for adding install targets, skills/agents, commands, CI hooks, dependencies, and documentation. This guide will help you contribute effectively and consistently.

## Coding Conventions

- **File Naming:** Use `camelCase` for JavaScript files and directories.
  - Example: `installManifests.js`, `installTargetsRegistry.js`
- **Import Style:** Use relative imports.
  - Example:
    ```js
    const registry = require('./install-targets/registry');
    ```
- **Export Style:** Mixed (both CommonJS and ES module patterns may appear).
  - Example (CommonJS):
    ```js
    module.exports = function install() { /* ... */ };
    ```
  - Example (ESM):
    ```js
    export function install() { /* ... */ }
    ```
- **Commit Messages:** Use prefixes like `fix:`, `feat:`, `docs:`, `chore:`. Keep messages concise (~58 chars).
  - Example: `feat: add support for new gemini install target`

## Workflows

### Add New Install Target
**Trigger:** When you want to support installing to a new platform or project type.  
**Command:** `/add-install-target`

1. Create install scripts and documentation under a new directory (e.g., `.codebuddy/`, `.gemini/`).
2. Update `manifests/install-modules.json` to register the new target.
3. Update `schemas/ecc-install-config.schema.json` and/or `schemas/install-modules.schema.json` for validation.
4. Implement a new script: `scripts/lib/install-targets/{target}-project.js`.
5. Update `scripts/lib/install-manifests.js` and `scripts/lib/install-targets/registry.js` to recognize the new target.
6. Add or update tests in `tests/lib/install-targets.test.js`.
7. Update `README.md` as needed.

**Example:**
```js
// scripts/lib/install-targets/gemini-project.js
module.exports = function installGeminiProject(config) {
  // Implementation for Gemini platform
};
```

---

### Add New Skill or Agent
**Trigger:** When introducing a new AI skill or agent capability.  
**Command:** `/add-skill`

1. Create a new `SKILL.md` or agent `.md` file in `skills/` or `agents/`.
2. Add supporting files (references, scripts, rules, etc.) if needed.
3. Update `manifests/install-modules.json` to register the new skill/agent.
4. Update `AGENTS.md` and/or `README.md` to reflect the addition.
5. Add or update tests if the skill/agent has code or CLI integration.

**Example:**
```markdown
// skills/myNewSkill/SKILL.md
# My New Skill
Description, usage, and examples...
```

---

### Add or Extend Command Workflow
**Trigger:** When automating or documenting a new workflow command for agents or users.  
**Command:** `/add-command`

1. Create or update command markdown files in `commands/` (e.g., `prp-implement.md`).
2. Address review feedback by fixing parsing, quoting, or logic issues.
3. Update references in `README.md` or other docs if needed.

**Example:**
```markdown
// commands/santa-loop.md
# Santa Loop Command
Automates the Santa workflow for agents...
```

---

### CI Hook and Test Hardening
**Trigger:** When improving CI reliability, security, or cross-platform compatibility.  
**Command:** `/fix-ci-hook`

1. Update `hooks/hooks.json` and/or `scripts/hooks/*.js|sh` to fix, harden, or extend hook logic.
2. Update or add tests under `tests/hooks/` or `tests/scripts/`.
3. Update lockfiles (`package-lock.json`, `yarn.lock`) if dependencies or scripts are changed.
4. Update schema files if validation is involved.

**Example:**
```js
// scripts/hooks/pre-commit.js
module.exports = function() {
  // Lint and test before commit
};
```

---

### Dependency Bump (GitHub Actions)
**Trigger:** When a new version of a GitHub Action or npm package is released.  
**Command:** `/bump-action`

1. Update version numbers in `.github/workflows/*.yml` for actions like `checkout`, `setup-node`, etc.
2. Update lockfiles or `package.json`/`yarn.lock` if npm packages are involved.
3. Commit with a standardized message (often via dependabot).

**Example:**
```yaml
# .github/workflows/ci.yml
- uses: actions/checkout@v4
```

---

### Doc or README Update Workflow
**Trigger:** When clarifying, adding, or fixing documentation.  
**Command:** `/update-docs`

1. Edit markdown files under `README.md`, `README.zh-CN.md`, `docs/`, or `skills/*/SKILL.md`.
2. Optionally update `WORKING-CONTEXT.md` or `AGENTS.md`.
3. Update related files for cross-referencing or catalog updates.

**Example:**
```markdown
// docs/troubleshooting.md
# Troubleshooting
Common issues and solutions...
```

---

## Testing Patterns

- **Test File Pattern:** All test files are named `*.test.js`.
- **Framework:** Not explicitly specified; likely uses a standard JS test runner (e.g., Mocha, Jest).
- **Placement:** Tests are located under `tests/`, mirroring the structure of the code they cover.
- **Example:**
  ```js
  // tests/lib/install-targets.test.js
  const assert = require('assert');
  const installGeminiProject = require('../../scripts/lib/install-targets/gemini-project');

  describe('installGeminiProject', () => {
    it('should install Gemini project correctly', () => {
      // Test implementation
    });
  });
  ```

## Commands

| Command           | Purpose                                                      |
|-------------------|--------------------------------------------------------------|
| /add-install-target | Add support for a new install target (platform/project)     |
| /add-skill          | Add a new skill or agent                                    |
| /add-command        | Add or extend a workflow command                            |
| /fix-ci-hook        | Harden or fix CI hooks and their tests                      |
| /bump-action        | Update GitHub Actions dependencies                          |
| /update-docs        | Update documentation or README files                        |
```