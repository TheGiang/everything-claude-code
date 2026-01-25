# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview
This codebase represents the everything-claude-code project, a JavaScript-based toolkit for Claude Code plugin development and automation. The project focuses on plugin configuration management, cross-platform scripting, and development workflow automation with an emphasis on security and proper documentation.

## Coding Conventions

### File Naming
- Use **camelCase** for all file names
- Test files follow the pattern `*.test.js`
- Configuration files use kebab-case (e.g., `plugin.json`, `hooks.json`)

### Import/Export Style
```javascript
// Mixed import styles - adapt to context
const utils = require('./lib/utils');
import { someFunction } from './module';

// Mixed export styles
module.exports = { function1, function2 };
export default myFunction;
```

### Commit Conventions
- Use conventional commit format with prefixes: `fix`, `feat`, `revert`, `style`, `docs`
- Keep commit messages around 52 characters
- Reference issue numbers when fixing security issues

## Workflows

### Plugin Configuration Fixes
**Trigger:** When plugin installation/loading fails or needs configuration updates
**Command:** `/fix-plugin-config`

1. Identify the specific plugin configuration issue (loading errors, metadata problems)
2. Update `.claude-plugin/plugin.json` or `.claude-plugin/marketplace.json` with correct values
3. Test plugin loading/installation to verify the fix works
4. Document the fix rationale in the commit message with clear explanation

**Example configuration fix:**
```json
{
  "name": "claude-code-plugin",
  "version": "1.0.0",
  "main": "index.js",
  "claudeCode": {
    "enabled": true,
    "autoLoad": true
  }
}
```

### Hooks Configuration Updates
**Trigger:** When hooks fail to execute or trigger at wrong times
**Command:** `/fix-hooks`

1. Identify the specific hook execution issue (wrong paths, missing triggers)
2. Update `hooks/hooks.json` configuration with correct script paths and events
3. Fix script paths or trigger events to match actual file structure
4. Test hook execution in development environment

**Example hooks configuration:**
```json
{
  "pre-commit": {
    "script": "scripts/hooks/preCommit.js",
    "enabled": true
  },
  "pre-push": {
    "script": "scripts/hooks/prePush.js",
    "enabled": false
  }
}
```

### Security Documentation Fixes
**Trigger:** When security issues are discovered or documentation needs security updates
**Command:** `/security-fix`

1. Identify the security vulnerability or documentation gap through analysis
2. Fix the actual code security issue (e.g., preventing command injection in utils.js)
3. Update relevant documentation files with security warnings and best practices
4. Reference specific issue numbers in commit messages for traceability

**Example security fix:**
```javascript
// Before - vulnerable to command injection
const executeCommand = (cmd) => exec(cmd);

// After - sanitized input
const executeCommand = (cmd) => {
  const sanitized = cmd.replace(/[;&|`$()]/g, '');
  return exec(sanitized);
};
```

### README Content Updates
**Trigger:** When adding new features, improving documentation layout, or adding resources
**Command:** `/update-readme`

1. Identify the specific README improvement needed (new features, better formatting, resource links)
2. Update content, formatting, or links following markdown best practices
3. Verify markdown rendering displays correctly in different viewers
4. Commit with descriptive message explaining the documentation improvement

### Cross-Platform Script Migration
**Trigger:** When adding cross-platform support or replacing bash scripts
**Command:** `/convert-to-nodejs`

1. Identify platform-specific scripts that need cross-platform compatibility
2. Rewrite scripts in Node.js using cross-platform APIs and libraries
3. Add utility libraries in `scripts/lib/` directory for shared functionality
4. Add comprehensive tests covering different platforms and edge cases
5. Update hook configurations to reference new Node.js scripts

**Example migration:**
```javascript
// Cross-platform file operations
const fs = require('fs').promises;
const path = require('path');

async function ensureDirectory(dirPath) {
  try {
    await fs.access(dirPath);
  } catch {
    await fs.mkdir(dirPath, { recursive: true });
  }
}
```

## Testing Patterns
- Test files use the `*.test.js` pattern
- Testing framework is project-specific (not standardized)
- Tests should cover cross-platform compatibility for utility functions
- Security-related code requires comprehensive test coverage

## Commands
| Command | Purpose |
|---------|---------|
| `/fix-plugin-config` | Fix Claude Code plugin configuration and metadata issues |
| `/fix-hooks` | Update hook paths, triggers, and configuration |
| `/security-fix` | Address security vulnerabilities and update documentation |
| `/update-readme` | Update README with new features and improved formatting |
| `/convert-to-nodejs` | Convert platform-specific scripts to cross-platform Node.js |