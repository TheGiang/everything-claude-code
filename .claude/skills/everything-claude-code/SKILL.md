# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches development patterns for the everything-claude-code repository, a JavaScript-based Claude plugin system. The codebase focuses on plugin configuration management, hook system development, and extensible skill/command architecture. Development follows conventional commit patterns with emphasis on plugin reliability and documentation quality.

## Coding Conventions

### File Naming
- Use **camelCase** for JavaScript files: `setupPackageManager.js`, `docUpdater.js`
- Use **kebab-case** for configuration files: `plugin.json`, `marketplace.json`
- Use **UPPERCASE** for documentation: `SKILL.md`, `README.md`

### Import/Export Style
```javascript
// Mixed import patterns - adapt to context
const utils = require('./lib/utils.js');
import { setupPackageManager } from './setup-package-manager.js';

// Mixed export patterns
module.exports = { functionName };
export default skillDefinition;
```

### Commit Conventions
- Use conventional commit prefixes: `fix:`, `feat:`, `docs:`, `style:`
- Keep messages under 52 characters
- Examples: `fix: resolve plugin hook loading error`, `feat: add new skill command`

## Workflows

### Plugin Configuration Fix
**Trigger:** When plugin installation or hook loading fails
**Command:** `/fix-plugin-config`

1. Identify the configuration error in console logs or error messages
2. Locate the problematic configuration file (`.claude-plugin/plugin.json` or `.claude-plugin/marketplace.json`)
3. Update the JSON structure, fixing syntax errors or missing required fields
4. Test plugin loading by restarting Claude or triggering plugin reload
5. Commit with format: `fix: resolve plugin configuration loading issue`

```json
// Example plugin.json fix
{
  "name": "everything-claude-code",
  "version": "1.0.0",
  "hooks": "./hooks/hooks.json",
  "skills": "./skills/"
}
```

### Hooks Configuration Update
**Trigger:** When hooks fail to execute or run at wrong times
**Command:** `/fix-hooks`

1. Identify hook execution issue through error logs or unexpected behavior
2. Open `hooks/hooks.json` and review hook definitions
3. Update hook paths, triggers, or execution conditions
4. Verify hook file paths exist and are executable
5. Test hook execution manually or through trigger events
6. Commit with format: `fix: update hook definitions for proper execution`

```json
// Example hooks.json structure
{
  "pre-commit": {
    "path": "./scripts/pre-commit.js",
    "trigger": "before-commit"
  },
  "post-install": {
    "path": "./scripts/setup-package-manager.js",
    "trigger": "after-plugin-install"
  }
}
```

### Documentation Update
**Trigger:** When adding new features or improving user experience
**Command:** `/update-docs`

1. Identify documentation gaps or outdated information in README.md
2. Add new feature documentation, installation instructions, or usage examples
3. Update formatting and structure for better readability
4. Review for consistency with current codebase state
5. Commit with format: `docs: update README with new feature documentation`

### Security and Bug Fixes
**Trigger:** When security issues or bugs are identified
**Command:** `/security-fix`

1. Identify security vulnerabilities or bugs in utility files
2. Focus on high-risk files like `scripts/lib/utils.js` and setup scripts
3. Implement fixes addressing the root cause
4. Update related documentation with security considerations
5. Test fixes thoroughly across different scenarios
6. Commit with format: `fix: resolve security vulnerability in utils`

### Skill and Command Addition
**Trigger:** When adding new capabilities to the plugin
**Command:** `/add-skill`

1. Create skill definition file in `skills/` directory following SKILL.md format
2. Add corresponding command file in `commands/` directory
3. Update `.claude-plugin/plugin.json` to register new skill
4. Document the skill's purpose, usage, and examples
5. Test skill loading and command execution
6. Commit with format: `feat: add new skill for [capability description]`

```markdown
// Example skill structure
# New Skill Name

## Overview
Brief description of what this skill does

## Commands
| Command | Purpose |
|---------|---------|
| /new-command | Description of functionality |
```

## Testing Patterns

### Test File Organization
- Test files follow pattern: `*.test.js`
- Place tests adjacent to source files or in dedicated test directories
- Framework appears to be custom or minimal - adapt to existing patterns

### Testing Approach
```javascript
// Example test structure (adapt to project's testing framework)
describe('Plugin Configuration', () => {
  test('should load valid plugin.json', () => {
    // Test plugin loading logic
  });
  
  test('should handle malformed configuration', () => {
    // Test error handling
  });
});
```

## Commands

| Command | Purpose |
|---------|---------|
| `/fix-plugin-config` | Resolve plugin installation and loading errors |
| `/fix-hooks` | Update hook definitions and execution paths |
| `/update-docs` | Improve README and documentation |
| `/security-fix` | Address security vulnerabilities and bugs |
| `/add-skill` | Create new skills and commands |