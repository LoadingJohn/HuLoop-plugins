---
name: Scaffold Project
description: Generate project structure and configuration files for new projects
version: 1.0.0
argument-hint: (project_name) (type) [--framework framework] [--language lang]
allowed-tools: [Write, Glob, Bash]
---

# Scaffold Project

This skill generates complete project scaffolding with all necessary configuration files, directory structure, and boilerplate code.

## Usage

Activate with:
```
/scaffold-project my-app react --language typescript
```

## Supported Project Types

### Frontend
- **React**: Create React App, Next.js, or custom setup
- **Vue**: Vue 3 or Vue 2
- **Angular**: Angular latest
- **Svelte**: Svelte kit
- **Vanilla**: Plain HTML/CSS/JS

### Backend
- **Node.js**: Express, Fastify, or bare
- **Python**: Flask, FastAPI, or Django
- **Go**: Standard or gin framework
- **Rust**: Actix or Rocket

### Full-Stack
- **MERN**: MongoDB, Express, React, Node
- **LAMP**: Linux, Apache, MySQL, PHP
- **Serverless**: AWS Lambda, Google Cloud Functions

### Utilities
- **CLI**: Command-line tool structure
- **Library**: Reusable library setup
- **Plugin**: Plugin architecture

## Capabilities

- **Directory Structure**: Complete folder hierarchy
- **Configuration Files**: Package.json, tsconfig, docker, etc.
- **Git Setup**: .gitignore, .github/workflows
- **Documentation**: README, contributing guide
- **Testing**: Test setup (Jest, pytest, etc.)
- **CI/CD**: GitHub Actions, GitLab CI configurations

## Example

```bash
/scaffold-project ecommerce mern
```

Creates:
```
ecommerce/
├── client/               # React frontend
│   ├── src/
│   ├── public/
│   └── package.json
├── server/               # Node.js backend
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   └── package.json
├── docker-compose.yml
├── README.md
└── .github/workflows/
```

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| name | string | ✅ | Project name |
| type | enum | ✅ | Project type |
| --framework | string | ❌ | Specific framework |
| --language | string | ❌ | Programming language |
| --git | boolean | ❌ | Initialize git repo (default: true) |

## Output Structure

- `.gitignore`: Configured for your stack
- `README.md`: Project documentation template
- `package.json` or equivalent: Dependencies
- `.github/workflows/`: CI/CD pipelines
- `docker/`: Docker configuration
- `tests/`: Test setup and examples
