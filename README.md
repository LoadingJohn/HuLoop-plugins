# HuLoop Plugins Marketplace

A curated collection of Claude Code plugins for the HuLoop ecosystem. Easy-to-use tools for analytics, data processing, and code generation.

## 🚀 Quick Start

### Add the Marketplace to Claude Code

1. Open Claude Code
2. Type `/plugin` and select "Add marketplace"
3. Enter this URL: `https://github.com/LoadingJohn/HuLoop-plugins`
4. Click "Sync"

### Install Plugins

Once added, install any plugin with:
```
/plugin install plugin-name
```

Or browse all available plugins:
```
/plugin > Discover > HuLoop Plugins
```

## 📦 Available Plugins

### 1. Analytics Dashboard
Real-time analytics and insights generation for data analysis projects.

**Skills:**
- `/generate-metrics` - Calculate statistics from JSON/CSV data
- `/create-report` - Generate professional analytics reports

**Features:**
- Statistical analysis (mean, median, standard deviation)
- Distribution analysis and trends
- Multi-format report generation (HTML, Markdown, JSON)

**Example:**
```
/generate-metrics sales_data.csv
/create-report q1-performance html
```

---

### 2. Data Processor
Advanced data transformation and ETL workflows with format conversion and validation.

**Skills:**
- `/validate-data` - Validate and sanitize data files
- `/transform-data` - Convert between formats (JSON, CSV, XML, YAML, TSV, JSONL)

**Features:**
- Type and format validation
- Schema enforcement
- Field mapping and transformations
- Multi-format support

**Example:**
```
/validate-data users.csv user_schema.json
/transform-data orders.csv --to json --map field_mapping.json
```

---

### 3. Template Generator
Generate boilerplate code and project templates for rapid development.

**Skills:**
- `/scaffold-project` - Generate complete project structures
- `/generate-component` - Create component templates for frameworks

**Features:**
- Multi-framework support (React, Vue, Angular, etc.)
- Full-stack templates (MERN, LAMP, etc.)
- Component templates with tests
- Auto-generated configuration

**Example:**
```
/scaffold-project my-app react --typescript
/generate-component Button react --typescript --with-tests
```

---

## 📚 Documentation

Each plugin includes comprehensive documentation:
- Detailed feature lists
- Parameter descriptions
- Real-world usage examples
- Troubleshooting guides

View plugin READMEs:
- [Analytics Dashboard](./plugins/analytics-dashboard/README.md)
- [Data Processor](./plugins/data-processor/README.md)
- [Template Generator](./plugins/template-generator/README.md)

## 🤝 Contributing

Submit your own plugins! Read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

MIT License - See [LICENSE](LICENSE) file

## 🆘 Support

- **Issues:** [GitHub Issues](https://github.com/LoadingJohn/HuLoop-plugins/issues)
- **Questions:** [GitHub Discussions](https://github.com/LoadingJohn/HuLoop-plugins/discussions)

---

**Made with ❤️ for the HuLoop community**