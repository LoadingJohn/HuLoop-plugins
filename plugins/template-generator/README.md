# Template Generator Plugin

Generate boilerplate code and project templates for rapid development.

## Features

- 🏗️ **Scaffold Projects**: Create complete project structures
- 🧩 **Generate Components**: Frontend and backend component templates
- ⚙️ **Configuration**: Auto-generated config files
- 📦 **Framework Support**: Multiple framework templates
- 🧪 **Testing Ready**: Pre-configured with testing setup

## Installation

```bash
/plugin install template-generator@huloop-plugins
```

## Quick Start

### Create a New Project

```bash
/scaffold-project my-app react --typescript
```

Generates:
- Complete React project structure
- TypeScript configuration
- Testing setup (Jest)
- CI/CD workflows
- Git initialization

### Generate a Component

```bash
/generate-component Button react --typescript --with-tests
```

Creates:
- Button.tsx - Component code
- Button.module.css - Styles
- Button.test.tsx - Test file
- index.ts - Export file

## Available Skills

### 1. Scaffold Project
- **Command**: `/scaffold-project`
- **Purpose**: Generate complete project structure
- **Input**: Project name, type, and options
- **Output**: Full project directory

### 2. Generate Component
- **Command**: `/generate-component`
- **Purpose**: Create component templates
- **Input**: Component name and type
- **Output**: Component files and structure

## Supported Technologies

### Frontend Frameworks
- React (with CRA, Next.js, or Vite)
- Vue (3 or 2)
- Angular
- Svelte
- Plain HTML/CSS/JS

### Backend Frameworks
- Node.js (Express, Fastify)
- Python (Flask, FastAPI, Django)
- Go (standard, gin)
- Rust (Actix, Rocket)
- Java (Spring Boot)

### Full-Stack Stacks
- MERN (MongoDB, Express, React, Node)
- LAMP (Linux, Apache, MySQL, PHP)
- Serverless (AWS Lambda, Google Cloud)
- JAMstack (Static + APIs)

### Utilities
- CLI applications
- Reusable libraries
- Plugin systems
- Design systems

## Project Templates

### React + TypeScript

```bash
/scaffold-project my-react-app react --typescript
```

Structure:
```
src/
├── components/
├── pages/
├── hooks/
├── utils/
├── types/
└── App.tsx
```

### Full-Stack MERN

```bash
/scaffold-project ecommerce mern
```

Structure:
```
client/                    # React frontend
├── src/
└── package.json

server/                    # Node.js backend
├── src/
├── models/
└── package.json

docker-compose.yml
MongoDB setup
```

### Python FastAPI

```bash
/scaffold-project api python --framework fastapi
```

Structure:
```
app/
├── main.py
├── routes/
├── models/
└── dependencies.py
```

### CLI Tool

```bash
/scaffold-project my-cli cli
```

Structure:
```
src/
├── cli.js
├── commands/
└── utils/

bin/
└── my-cli
```

## Component Templates

### React Functional Component

```bash
/generate-component Card react --typescript
```

Generates:
```typescript
interface CardProps {
  title: string;
  children: React.ReactNode;
}

export const Card: React.FC<CardProps> = ({ title, children }) => {
  return (
    <div className="card">
      <h2>{title}</h2>
      {children}
    </div>
  );
};
```

### React Hook

```bash
/generate-component useAuth react --type hook --typescript
```

Generates:
```typescript
export const useAuth = () => {
  const [user, setUser] = React.useState(null);
  const [loading, setLoading] = React.useState(false);

  // Hook implementation
};
```

### Express Controller

```bash
/generate-component UserController backend --framework express
```

Generates:
```javascript
class UserController {
  async getUser(req, res) {
    // Implementation
  }

  async createUser(req, res) {
    // Implementation
  }
}
```

### API Model

```bash
/generate-component User backend --type model --framework fastapi
```

Generates:
```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    email: str
```

## Configuration Files Included

### Always Generated
- `.gitignore` - Version control ignore patterns
- `README.md` - Project documentation template
- `LICENSE` - Open source license

### Framework-Specific
- `package.json` / `requirements.txt` - Dependencies
- `tsconfig.json` / `go.mod` - Configuration
- `docker-compose.yml` - Container setup
- `.github/workflows/` - CI/CD pipelines
- `jest.config.js` / `pytest.ini` - Testing

## Options

### Common Options

```bash
--typescript          # Use TypeScript (when available)
--git                # Initialize git repo (default: true)
--install            # Install dependencies (default: false)
--strict             # Use strict mode/linting (default: true)
```

### Framework-Specific

```bash
--framework          # Specific framework (express, fastapi, etc.)
--styling            # CSS solution (css, scss, tailwind)
--testing            # Testing library (jest, vitest, pytest)
```

## Examples

### Example 1: React App with All Features

```bash
/scaffold-project my-app react --typescript --with-tailwind
cd my-app
npm install
npm start
```

### Example 2: Full-Stack Application

```bash
/scaffold-project blog mern --typescript
cd blog
docker-compose up
# Start development
```

### Example 3: Generate Multiple Components

```bash
/generate-component Header react --typescript
/generate-component Footer react --typescript
/generate-component Layout react --typescript
```

## Customization

After scaffolding, customize:

1. **Dependencies**: Edit `package.json` / `requirements.txt`
2. **Configuration**: Modify config files as needed
3. **Styling**: Update CSS/styling solution
4. **Environment**: Create `.env` files
5. **Scripts**: Add build/dev scripts

## Best Practices

1. Use TypeScript for larger projects
2. Include tests from the start
3. Set up CI/CD workflows
4. Follow framework conventions
5. Document your project structure

## Troubleshooting

### Port Already in Use
```bash
# Check what's running
lsof -i :3000

# Use different port
npm start -- --port 3001
```

### Dependencies Installation Failed
```bash
# Clear cache
npm cache clean --force

# Reinstall
npm install
```

### TypeScript Errors
- Run type check: `npm run type-check`
- Update TypeScript: `npm install -D typescript@latest`
- Check tsconfig.json settings

## Contributing

Have ideas for new templates? [Open an issue](https://github.com/LoadingJohn/HuLoop-plugins/issues)

## License

MIT License - See LICENSE file for details
