# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This repository contains a Claude plugin system with hooks, configuration management, and documentation. The codebase follows conventional commit patterns and focuses on plugin configuration fixes, hook system updates, documentation improvements, and security enhancements. The project uses JavaScript without a specific framework and emphasizes proper plugin loading, event handling, and comprehensive documentation.

## Coding Conventions

### File Naming
- Use **camelCase** for file names
- Test files follow `*.test.js` pattern
- Configuration files use kebab-case (e.g., `plugin.json`, `marketplace.json`)

### Import/Export Patterns
```javascript
// Mixed import styles - adapt to existing patterns in each file
const utils = require('./lib/utils');
import { hookHandler } from './hooks/handler';

// Mixed export styles
module.exports = { setupPackageManager };
export default pluginConfig;
```

### Commit Messages
- Use conventional commit format
- Keep messages around 52 characters
- Common prefixes: `fix:`, `feat:`, `revert:`, `style:`, `docs:`
- Include issue references where applicable

## Workflows

### Plugin Configuration Fix
**Trigger:** When plugin loading, hook registration, or marketplace installation fails
**Command:** `/fix-plugin-config`

1. **Identify configuration issue** - Check plugin loading errors, missing fields, or installation failures
2. **Update plugin.json or marketplace.json** - Fix configuration paths, metadata, or dependency issues
3. **Test plugin loading** - Verify the plugin loads correctly in Claude environment
4. **Commit fix with issue reference** - Use format: `fix: resolve plugin configuration for proper loading (#issue)`

```json
// Example plugin.json fix
{
  "name": "everything-claude-code",
  "version": "1.0.0",
  "main": "./index.js",
  "hooks": "./hooks/hooks.json"
}
```

### Hook System Update
**Trigger:** When hooks fire at wrong times, fail to load, or need path fixes
**Command:** `/fix-hooks`

1. **Identify hook timing/loading issue** - Debug hook execution order, missing events, or path problems
2. **Update hooks.json with correct paths/events** - Fix hook configurations and event bindings
3. **Test hook execution** - Verify hooks fire at correct times with proper data
4. **Commit with specific issue description** - Use format: `fix: update hook paths for proper event handling`

```json
// Example hooks.json structure
{
  "pre-command": {
    "script": "./scripts/hooks/preCommand.js",
    "events": ["command:before"]
  },
  "post-install": {
    "script": "./scripts/hooks/postInstall.js",
    "events": ["plugin:installed"]
  }
}
```

### README Documentation Update
**Trigger:** When documentation needs enhancement, restructuring, or visual improvements
**Command:** `/update-readme`

1. **Identify documentation gap or improvement** - Find missing sections, outdated info, or unclear explanations
2. **Update README.md structure/content** - Improve organization, add examples, clarify instructions
3. **Add images, badges, or links if needed** - Enhance visual appeal and external references
4. **Commit with descriptive message** - Use format: `docs: improve README structure and content`

```markdown
<!-- Example README improvements -->
## Installation
[![npm version](https://badge.fury.io/js/package-name.svg)](https://badge.fury.io/js/package-name)

### Quick Start
1. Install the plugin
2. Configure your settings
3. Run the setup command
```

### Security and Bug Fixes
**Trigger:** When security issues, command injection risks, or multiple bugs are identified
**Command:** `/security-audit-fix`

1. **Audit code for security issues** - Check for command injection, unsafe file operations, input validation
2. **Fix vulnerabilities and bugs** - Implement proper sanitization, validation, and error handling
3. **Update documentation with security warnings** - Add security considerations to relevant docs
4. **Commit with issue references** - Use format: `fix: address security vulnerabilities and command injection risks (#issue)`

```javascript
// Example security fix
// Before (vulnerable)
exec(`npm install ${packageName}`);

// After (secure)
const { spawn } = require('child_process');
const sanitizedPackage = packageName.replace(/[^a-zA-Z0-9-_]/g, '');
spawn('npm', ['install', sanitizedPackage]);
```

## Testing Patterns

### Test File Structure
- Test files use `*.test.js` naming convention
- Framework: Unknown (adapt to existing patterns)
- Focus areas: Plugin loading, hook execution, configuration validation

```javascript
// Example test structure
describe('Plugin Configuration', () => {
  test('should load plugin with valid config', () => {
    // Test implementation
  });
  
  test('should handle invalid hook paths', () => {
    // Test implementation
  });
});
```

## Commands

| Command | Purpose |
|---------|---------|
| `/fix-plugin-config` | Fix plugin configuration issues for proper loading and installation |
| `/fix-hooks` | Update hook configurations and implementations for proper event handling |
| `/update-readme` | Iteratively improve README structure, content, and visual elements |
| `/security-audit-fix` | Address multiple security vulnerabilities and bugs comprehensively |