# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

HuLoop Plugins is a **Claude Code plugin marketplace** - a structured collection of plugins that extend Claude's capabilities. This repo serves as the marketplace itself and contains both the marketplace definition and example plugins.

## Architecture Overview

### Marketplace Structure

The marketplace uses a **registry pattern** defined in `.claude-plugin/marketplace.json`:

```
.claude-plugin/
└── marketplace.json          # Entry point - defines all available plugins
```

This single JSON file is what Claude Code reads when users add the marketplace. It contains:
- Marketplace metadata (name, owner, description)
- Array of plugin entries with name, description, source path, and category
- Each plugin entry points to a local path: `./plugins/{plugin-name}`

### Plugin Structure

Each plugin is a **self-contained package** at `plugins/{plugin-name}/`:

```
plugins/{plugin-name}/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata (required)
├── skills/
│   ├── {skill-1}/SKILL.md   # Individual skill definition
│   └── {skill-2}/SKILL.md   # Each skill is one slash command
├── README.md                 # Plugin documentation
└── LICENSE                   # MIT recommended
```

### Skills vs Plugins

**Plugins** = packages that bundle related functionality + documentation
**Skills** = individual, invokable capabilities within a plugin (what users actually use with `/skill-name`)

A plugin can contain multiple skills. For example, `analytics-dashboard` plugin contains:
- `/generate-metrics` skill
- `/create-report` skill

## Key Files & Their Roles

### `.claude-plugin/marketplace.json`
- **Purpose**: Entry point for the entire marketplace
- **Schema**: Follows `https://anthropic.com/claude-code/marketplace.schema.json`
- **Required fields**: `$schema`, `name`, `description`, `owner`, `plugins` array
- **Plugin source**: Uses relative paths `./plugins/{name}` for local plugins
- **Update this when**: Adding/removing plugins or changing marketplace metadata

### `plugins/{name}/.claude-plugin/plugin.json`
- **Purpose**: Declares a single plugin's metadata
- **Required fields**: `name`, `description`, `author` (with name/email)
- **Optional fields**: `version`, `license`, `keywords`
- **Must match**: The plugin name in marketplace.json

### `plugins/{name}/skills/{skill-name}/SKILL.md`
- **Purpose**: Defines a single skill (slash command)
- **YAML frontmatter** (required):
  ```yaml
  ---
  name: Display Name
  description: What this skill does
  version: 1.0.0
  argument-hint: (parameters)
  allowed-tools: [Read, Glob, Grep, Bash, Write, Edit]
  ---
  ```
- **Content**: Markdown documentation + implementation details
- **allowed-tools**: Declares which Claude Code tools this skill uses

### `plugins/{name}/README.md`
- **Purpose**: User-facing documentation for the plugin
- **Should include**: Skills provided, features, usage examples, parameters

## Workflow: Adding a New Plugin

When adding a new plugin to the marketplace:

1. **Create plugin directory structure**:
   ```
   plugins/new-plugin/
   ├── .claude-plugin/plugin.json
   ├── skills/skill-1/SKILL.md
   ├── skills/skill-2/SKILL.md
   └── README.md
   ```

2. **Create `.claude-plugin/plugin.json`** with plugin metadata

3. **Create skill files** in `skills/{name}/SKILL.md` format with YAML frontmatter

4. **Add plugin entry to `.claude-plugin/marketplace.json`**:
   ```json
   {
     "name": "new-plugin",
     "description": "Clear description",
     "category": "development|productivity|...",
     "source": "./plugins/new-plugin",
     "author": {"name": "...", "email": "..."},
     "homepage": "GitHub URL"
   }
   ```

5. **Validate JSON** - Both marketplace.json and plugin.json must be valid JSON

## Current Plugins

The marketplace includes 3 example plugins:

- **analytics-dashboard** (`./plugins/analytics-dashboard/`)
  - `/generate-metrics` - Calculate statistics
  - `/create-report` - Generate reports

- **data-processor** (`./plugins/data-processor/`)
  - `/validate-data` - Validate/sanitize data
  - `/transform-data` - Convert formats (JSON, CSV, XML, YAML, TSV, JSONL)

- **template-generator** (`./plugins/template-generator/`)
  - `/scaffold-project` - Generate project structures
  - `/generate-component` - Generate component templates

Each follows the standard structure and can be used as a template for new plugins.

## Important Constraints

### marketplace.json Validation
- Must be valid JSON (use `python3 -m json.tool` to validate)
- `$schema` field is required
- Plugin `source` paths should use relative paths starting with `./`
- All plugins listed must have corresponding directories in `./plugins/`

### Plugin Metadata Requirements
- Plugin name must be lowercase with hyphens (no spaces)
- plugin.json must exist at `plugins/{name}/.claude-plugin/plugin.json`
- Each skill must have a unique, descriptive name
- No hardcoded credentials or API keys in any files

### Skill Definition Requirements
- YAML frontmatter is mandatory
- `allowed-tools` must specify which tools the skill uses (security/transparency)
- Descriptions should be clear about what the skill does
- `argument-hint` helps users understand parameters

## Contributing & External Plugins

Contributors submit plugins to `external_plugins/{plugin-name}/` via pull requests. The submission process is documented in `CONTRIBUTING.md`. Key requirements:
- Standard plugin structure
- Comprehensive README with examples
- No hardcoded secrets
- Clear error handling
- Valid JSON files

## Testing Plugins Locally

To test if plugins are properly discovered:
1. Validate marketplace.json: `python3 -m json.tool .claude-plugin/marketplace.json`
2. Verify each plugin directory exists and has required files
3. In Claude Code: `/plugin > Add marketplace > https://github.com/LoadingJohn/HuLoop-plugins`
4. Use `/plugin install {plugin-name}` to verify installation
5. Invoke skills with `/skill-name` to test functionality

## Common Tasks

**Validate marketplace.json syntax:**
```bash
python3 -m json.tool .claude-plugin/marketplace.json > /dev/null && echo "Valid"
```

**Check plugin structure:**
```bash
ls -la plugins/analytics-dashboard/.claude-plugin/plugin.json
ls -la plugins/analytics-dashboard/skills/*/SKILL.md
```

**Add a new plugin to marketplace:**
- Add directory under `plugins/`
- Create plugin.json
- Create skills in `skills/*/SKILL.md`
- Add entry to `.claude-plugin/marketplace.json`
- Verify JSON is valid
