# Contributing to HuLoop Plugins

Thank you for your interest in contributing to HuLoop Plugins! This document provides guidelines and instructions for submitting your own plugins to the ecosystem.

## Ways to Contribute

### 1. Create New Plugins
Build plugins that extend Claude's capabilities for the HuLoop community.

### 2. Improve Existing Plugins
- Fix bugs
- Enhance documentation
- Add features
- Improve performance

### 3. Report Issues
Found a bug? Have a feature idea? Open an issue to let us know.

### 4. Suggest Improvements
Help improve our templates, documentation, or guidelines.

## Plugin Submission Process

### Step 1: Develop Your Plugin

Follow the [PLUGIN_TEMPLATE.md](PLUGIN_TEMPLATE.md) guide:

```bash
mkdir your-plugin-name
cd your-plugin-name
mkdir -p .claude-plugin
mkdir -p skills/your-skill
```

Create required files:
- `.claude-plugin/plugin.json`
- `skills/*/SKILL.md`
- `README.md`
- `LICENSE` (MIT recommended)

### Step 2: Test Your Plugin

Before submission:

- ✅ Test all skills thoroughly
- ✅ Verify error handling
- ✅ Check documentation is clear
- ✅ Validate JSON files
- ✅ Ensure no hardcoded secrets
- ✅ Run through the [submission checklist](#submission-checklist)

### Step 3: Fork and Branch

```bash
# Fork the repository on GitHub
git clone https://github.com/YOUR-USERNAME/HuLoop-plugins.git
cd HuLoop-plugins
git checkout -b add/your-plugin-name
```

### Step 4: Add Your Plugin

```bash
# Copy your plugin to external_plugins
cp -r /path/to/your-plugin-name external_plugins/
cd external_plugins/your-plugin-name

# Verify structure
ls -la
```

Expected structure:
```
external_plugins/your-plugin-name/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── skill-name/
│       └── SKILL.md
├── README.md
└── LICENSE
```

### Step 5: Commit and Push

```bash
git add external_plugins/your-plugin-name
git commit -m "Add your-plugin-name plugin

Description of what your plugin does.

Features:
- Feature 1
- Feature 2

Closes #XXX (if applicable)"

git push origin add/your-plugin-name
```

### Step 6: Create Pull Request

On GitHub, create a PR with:

**Title**: `Add {plugin-name} plugin`

**Description**:
```markdown
## Summary
Brief description of what your plugin does.

## Features
- Feature 1
- Feature 2
- Feature 3

## Skills Included
- `/skill-1`: What it does
- `/skill-2`: What it does

## Documentation
- Complete README with examples
- Clear parameter documentation
- Troubleshooting guide

## Testing
- [x] Tested all skills
- [x] Verified error handling
- [x] No hardcoded secrets
- [x] Documentation complete

## Related Issues
Closes #XXX
```

### Step 7: Review and Merge

The maintainers will:
- Review code quality
- Verify security
- Check documentation
- Request changes if needed
- Merge when approved ✅

## Submission Checklist

### Plugin Metadata
- [ ] `plugin.json` is valid JSON
- [ ] Plugin has unique name
- [ ] Author information is complete
- [ ] Description is clear and concise

### Skills
- [ ] At least one SKILL.md file
- [ ] YAML frontmatter is valid
- [ ] `allowed-tools` is specified
- [ ] Skills are tested and working
- [ ] Argument hints are helpful
- [ ] Descriptions are clear

### Documentation
- [ ] README.md is comprehensive
- [ ] Installation instructions clear
- [ ] Usage examples are present
- [ ] Parameters documented in tables
- [ ] Output format explained
- [ ] Troubleshooting section included

### Security
- [ ] No hardcoded API keys
- [ ] No hardcoded credentials
- [ ] Input validation present
- [ ] Safe shell command usage
- [ ] No unsafe file operations
- [ ] Dependencies are necessary

### Code Quality
- [ ] Error messages are helpful
- [ ] Code is readable
- [ ] Comments explain complex logic
- [ ] No unnecessary dependencies
- [ ] Performance is acceptable

### Testing
- [ ] All skills tested manually
- [ ] Error cases handled
- [ ] Edge cases considered
- [ ] Examples in README work

## Quality Standards

Your plugin should meet these standards for approval:

### Functionality
- Works as documented
- Handles errors gracefully
- Provides helpful error messages
- Completes in reasonable time

### Documentation
- Clear purpose and use cases
- Working examples provided
- All parameters documented
- Troubleshooting included

### Security
- No exposed credentials
- Input validation present
- Safe file operations
- No external calls without disclosure

### Maintainability
- Clear code structure
- Proper naming conventions
- Comments for complex logic
- Version numbering

## Guidelines

### Naming Conventions

**Plugin Names**
- Lowercase with hyphens
- Descriptive: `code-formatter`, `api-client`
- Avoid generic names: `plugin`, `tool`

**Skill Names**
- Verb-noun format: `generate-report`, `validate-data`
- Clear and descriptive
- Match directory names

### Documentation Style

- Use clear, concise language
- Include real-world examples
- Format tables and lists properly
- Use code blocks for commands
- Add emojis sparingly

### Version Numbers

Follow [Semantic Versioning](https://semver.org/):
- **1.0.0**: Initial release
- **1.0.1**: Bug fix
- **1.1.0**: Feature (backward compatible)
- **2.0.0**: Breaking changes

## Common Issues and Solutions

### Issue: "plugin.json is invalid"
**Solution**: Validate with `jsonlint` or `python -m json.tool`

### Issue: "Hardcoded credentials found"
**Solution**: Remove all secrets. Use environment variables or documentation instead.

### Issue: "Missing error handling"
**Solution**: Wrap operations in try-catch, provide helpful error messages.

### Issue: "Insufficient documentation"
**Solution**: Add examples, parameter descriptions, and troubleshooting.

### Issue: "Skills don't work"
**Solution**: Test manually, verify allowed-tools, check YAML syntax.

## Getting Help

- **Questions?** Open a [GitHub Discussion](https://github.com/LoadingJohn/HuLoop-plugins/discussions)
- **Found a bug?** Open an [Issue](https://github.com/LoadingJohn/HuLoop-plugins/issues)
- **Need guidance?** Check [PLUGIN_TEMPLATE.md](PLUGIN_TEMPLATE.md)
- **Want examples?** Review existing plugins in `/plugins`

## Code of Conduct

- Be respectful to maintainers and other contributors
- Provide constructive feedback
- Help others with questions
- Report security issues privately
- No spam or self-promotion

## License

By contributing, you agree that your plugin will be under the same license as the main repository (MIT). Individual plugins can use other licenses (Apache-2.0, GPL, etc.) specified in their own LICENSE file.

## Questions?

- Check existing issues and discussions
- Review the [official Claude plugins docs](https://code.claude.com/docs/en/plugins)
- Ask in discussions before creating complex plugins

---

Thank you for contributing to HuLoop Plugins! 🎉
