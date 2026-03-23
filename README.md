# HuLoop Plugins

A curated collection of Claude Code plugins for the HuLoop ecosystem. This marketplace extends Claude's capabilities with specialized tools, skills, and integrations.

## 📚 Overview

HuLoop Plugins provides a standardized plugin architecture that integrates seamlessly with Claude Code. Plugins can add custom skills, slash commands, MCP server integrations, and agent capabilities.

## 🚀 Getting Started

### Installing Plugins

To install a plugin from this repository:

```bash
/plugin install plugin-name@huloop-plugins
```

Or discover plugins in Claude Code:
```
/plugin > Discover > HuLoop Plugins
```

### Plugin Structure

Each plugin follows this standard structure:

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json           # Plugin metadata (required)
├── .mcp.json                 # MCP server config (optional)
├── skills/                   # Skill definitions (recommended)
│   └── feature-name/
│       └── SKILL.md          # Skill implementation
├── commands/                 # Legacy slash commands (optional)
└── README.md                 # Plugin documentation
```

## 📦 Available Plugins

### Core Plugins

#### 1. **Analytics Dashboard** (`analytics-dashboard`)
Real-time analytics and insights generation for data analysis projects.

**Features:**
- Data visualization helpers
- Performance metrics calculation
- Trend analysis
- Report generation

**Installation:**
```bash
/plugin install analytics-dashboard@huloop-plugins
```

---

#### 2. **Data Processor** (`data-processor`)
Advanced data transformation and processing capabilities for ETL workflows.

**Features:**
- Data validation and sanitization
- Format conversion (JSON, CSV, XML)
- Batch processing
- Schema detection

**Installation:**
```bash
/plugin install data-processor@huloop-plugins
```

---

#### 3. **Template Generator** (`template-generator`)
Generate boilerplate code and project templates for rapid development.

**Features:**
- Project scaffolding
- Component templates
- Configuration generators
- Code snippet library

**Installation:**
```bash
/plugin install template-generator@huloop-plugins
```

---

## 🔧 Plugin Development

### Creating a New Plugin

1. **Create directory structure:**
   ```bash
   mkdir -p plugins/my-plugin/.claude-plugin
   mkdir -p plugins/my-plugin/skills/my-skill
   ```

2. **Create `plugin.json`:**
   ```json
   {
     "name": "my-plugin",
     "description": "What your plugin does",
     "author": {
       "name": "Your Name",
       "email": "your@email.com"
     }
   }
   ```

3. **Create skills in `skills/my-skill/SKILL.md`:**
   ```markdown
   ---
   name: My Skill
   description: What this skill does
   version: 1.0.0
   argument-hint: (optional arguments)
   allowed-tools: [Read, Glob, Grep, Bash]
   ---

   # Implementation

   Your skill implementation here...
   ```

4. **Add documentation in `README.md`**

### Plugin.json Specification

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | ✅ | Plugin identifier (lowercase, hyphens) |
| `description` | string | ✅ | Required description of plugin purpose |
| `author` | object | ✅ | `{ name: string, email: string }` |
| `version` | string | ❌ | Semantic versioning |
| `license` | string | ❌ | License identifier |
| `keywords` | array | ❌ | Search keywords |

### Skill.md Specification

**YAML Frontmatter:**
```yaml
---
name: Skill Name
description: What the skill does (triggers AI invocation)
version: 1.0.0
argument-hint: (optional parameter hints)
allowed-tools: [List, Of, Tools]
---
```

**Supported Tools:**
- `Read` - Read files
- `Glob` - Find files by pattern
- `Grep` - Search file contents
- `Bash` - Execute shell commands
- `Edit` - Edit files
- `Write` - Create files
- Plus all other Claude Code tools

## 📋 Submission Guidelines

### Community Plugin Submission

To submit your plugin to HuLoop Plugins:

1. **Quality Standards:**
   - Clear, comprehensive README
   - Error handling and validation
   - Security best practices
   - No external API keys in code

2. **Documentation:**
   - Usage examples
   - Parameter descriptions
   - Troubleshooting guide
   - License specification

3. **Submission Process:**
   - Fork this repository
   - Add your plugin to `/external_plugins/{plugin-name}`
   - Create a pull request with description
   - Wait for review and approval

4. **Security Review:**
   - No hardcoded credentials
   - Proper input validation
   - Safe shell command usage
   - No unauthorized external calls

## 📂 Directory Structure

```
HuLoop-plugins/
├── plugins/                          # Official HuLoop plugins
│   ├── analytics-dashboard/
│   ├── data-processor/
│   └── template-generator/
├── external_plugins/                 # Community-contributed plugins
├── PLUGIN_TEMPLATE.md               # Plugin development template
└── README.md                         # This file
```

## 🔗 Integration Methods

### Skills (Recommended)
Modern approach for both AI-triggered and user-invoked capabilities.
- Located in `skills/<name>/SKILL.md`
- YAML frontmatter for metadata
- Markdown for implementation

### Commands (Legacy)
Older approach using `commands/*.md` directory structure.
- Still functional but not recommended for new plugins
- Use skills format for new development

### MCP Servers (Advanced)
Model Context Protocol server integration via `.mcp.json`
- External tool integration
- HTTP server configuration
- Context-aware activation

## 🤝 Contributing

We welcome contributions! Please ensure your plugin:

- ✅ Follows the standard directory structure
- ✅ Includes comprehensive documentation
- ✅ Has clear error handling
- ✅ Adheres to security best practices
- ✅ Works with Claude Code

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

## 📄 License

HuLoop Plugins are available under the MIT License. Individual plugins may have their own licenses—see each plugin's README for details.

## 🆘 Support

- **Documentation:** See individual plugin README files
- **Issues:** [GitHub Issues](https://github.com/LoadingJohn/HuLoop-plugins/issues)
- **Discussions:** [GitHub Discussions](https://github.com/LoadingJohn/HuLoop-plugins/discussions)

## 📚 Resources

- [Claude Code Documentation](https://code.claude.com/docs/en/plugins)
- [Official Claude Plugins](https://github.com/anthropics/claude-plugins-official)
- [Model Context Protocol (MCP)](https://modelcontextprotocol.io)

---

**Made with ❤️ for the HuLoop community**