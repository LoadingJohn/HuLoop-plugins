# Plugin Development Template

This is a template guide for creating new HuLoop plugins. Use this as a reference when building your own plugins.

## Directory Structure

```
your-plugin/
├── .claude-plugin/
│   └── plugin.json                 # Required: Plugin metadata
├── .mcp.json                       # Optional: MCP server configuration
├── skills/                         # Recommended: Skill definitions
│   ├── skill-one/
│   │   └── SKILL.md               # Skill implementation
│   └── skill-two/
│       └── SKILL.md               # Skill implementation
├── commands/                       # Legacy: Slash commands (not recommended)
├── README.md                       # Required: Plugin documentation
└── LICENSE                         # Recommended: License file
```

## 1. Create plugin.json

**File**: `.claude-plugin/plugin.json`

```json
{
  "name": "your-plugin-name",
  "description": "Brief description of what your plugin does",
  "author": {
    "name": "Your Name",
    "email": "your@email.com"
  },
  "version": "1.0.0",
  "license": "MIT",
  "keywords": ["keyword1", "keyword2", "keyword3"]
}
```

### Fields

- **name** (required): Plugin identifier in lowercase with hyphens
- **description** (required): One-line description (appears in discovery)
- **author** (required): Object with `name` and `email`
- **version** (optional): Semantic versioning (1.0.0)
- **license** (optional): License identifier (MIT, Apache-2.0, etc.)
- **keywords** (optional): Array for discovery

## 2. Create Skills

**Directory**: `skills/{skill-name}/SKILL.md`

### Skill Metadata (YAML Frontmatter)

```yaml
---
name: Skill Display Name
description: What this skill does (visible as trigger description)
version: 1.0.0
argument-hint: (example parameters)
allowed-tools: [Read, Glob, Grep, Bash, Edit, Write]
---
```

### Skill.md Template

```markdown
---
name: My Awesome Skill
description: Does something really useful
version: 1.0.0
argument-hint: (input_file) [--option value]
allowed-tools: [Read, Bash]
---

# My Awesome Skill

One-paragraph description of what this skill does and its primary use cases.

## Usage

Basic invocation:
```
/my-awesome-skill input.txt
```

With options:
```
/my-awesome-skill input.txt --option value
```

## Capabilities

Bullet list of what this skill can do:
- First capability
- Second capability
- Third capability

## Examples

### Example 1: Basic usage

Description of example with code:

```bash
/my-awesome-skill data.json
```

Output and what to expect.

### Example 2: With options

Description:

```bash
/my-awesome-skill data.json --format html
```

Results and next steps.

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| input | string | ✅ | Description of input |
| option | string | ❌ | Description of option |

## Supported Formats/Types

List formats, types, or options your skill supports:
- Format/Type 1: Description
- Format/Type 2: Description

## Output

Description of output:
- What gets returned
- Where files are saved
- Format of output

## Troubleshooting

### Issue 1
Problem and solution.

### Issue 2
Problem and solution.

## Performance Notes

If applicable:
- Large file handling
- Typical execution time
- Optimization tips
```

## 3. Create README.md

**File**: `README.md` (in plugin root)

```markdown
# Plugin Name

One-line description of your plugin.

## Features

- 🎯 Feature 1: Description
- 🎯 Feature 2: Description
- 🎯 Feature 3: Description

## Installation

```bash
/plugin install plugin-name@huloop-plugins
```

## Quick Start

Brief section showing typical usage:

```bash
/skill-name input.txt
```

Expected output.

## Available Skills

List each skill with:
- Command
- Purpose
- Usage example

## Examples

Show 2-3 practical examples users can copy.

## Configuration

Any environment variables or config needed.

## Troubleshooting

Common issues and solutions.

## Contributing

Link to CONTRIBUTING.md

## License

License type.
```

## 4. Naming Conventions

### Plugin Names
- Use lowercase with hyphens
- Be descriptive: `code-formatter`, `data-processor`
- Avoid generic names: `plugin`, `tool`

### Skill Names
- Use verb-noun pattern: `generate-report`, `validate-data`
- Descriptive and action-oriented
- Examples:
  - `create-project`
  - `transform-data`
  - `generate-documentation`
  - `analyze-code`

### File Organization
- One skill per directory
- Skill names match directory names
- SKILL.md is the required file

## 5. Best Practices

### Documentation
- ✅ Clear descriptions of what your skill does
- ✅ Real-world usage examples
- ✅ Parameter descriptions
- ✅ Troubleshooting section
- ✅ Output format documentation

### Code Quality
- ✅ Error handling for invalid input
- ✅ Input validation
- ✅ Helpful error messages
- ✅ Comments for complex logic
- ✅ Test your skills thoroughly

### Security
- ✅ No hardcoded credentials
- ✅ Validate user input
- ✅ Safe shell command usage
- ✅ No unsafe file operations
- ✅ Clear warnings about destructive operations

### User Experience
- ✅ Intuitive parameter names
- ✅ Sensible defaults
- ✅ Clear feedback on progress
- ✅ Helpful error messages
- ✅ Quick execution (< 30 seconds ideal)

## 6. Tools Available to Skills

Your skills can use these Claude Code tools:

| Tool | Purpose |
|------|---------|
| Read | Read file contents |
| Write | Create new files |
| Edit | Modify existing files |
| Glob | Find files by pattern |
| Grep | Search file contents |
| Bash | Execute shell commands |
| Agent | Delegate to specialized agents |

Declare which tools your skill uses in the `allowed-tools` frontmatter field.

## 7. Version Numbering

Use Semantic Versioning (MAJOR.MINOR.PATCH):
- **1.0.0** - First stable release
- **1.0.1** - Bug fix
- **1.1.0** - New feature, backward compatible
- **2.0.0** - Breaking changes

## 8. Publishing Checklist

Before submitting your plugin:

- [ ] plugin.json is valid JSON
- [ ] All skills have SKILL.md with metadata
- [ ] README.md is comprehensive
- [ ] No hardcoded secrets
- [ ] All examples tested and working
- [ ] Parameter documentation complete
- [ ] Error handling implemented
- [ ] Tool usage documented
- [ ] License file included
- [ ] Proper naming conventions followed

## 9. Example Plugin Structure

See example implementations:
- `analytics-dashboard` - Multi-skill plugin with reporting
- `data-processor` - Data transformation and validation
- `template-generator` - Code scaffolding and generation

## 10. Getting Help

- Check existing plugins for examples
- Read the [official Claude plugins docs](https://code.claude.com/docs/en/plugins)
- Open an issue with questions

## Template Repository

Copy this structure to start:

```bash
mkdir my-plugin
cd my-plugin
mkdir -p .claude-plugin
mkdir -p skills/{skill-name}

# Create files
touch .claude-plugin/plugin.json
touch skills/{skill-name}/SKILL.md
touch README.md
touch LICENSE
```

Fill in with your content following this template guide.

---

Ready to build? Start with a single skill and expand from there!
