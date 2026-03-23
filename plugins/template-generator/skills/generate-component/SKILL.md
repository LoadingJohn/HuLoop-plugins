---
name: Generate Component
description: Generate component code templates for frontend and backend frameworks
version: 1.0.0
argument-hint: (component_name) (type) [--framework framework] [--typescript]
allowed-tools: [Write, Bash]
---

# Generate Component

This skill generates reusable component templates for various frameworks including React, Vue, Angular, and backend component patterns.

## Usage

Activate with:
```
/generate-component UserCard react --typescript
/generate-component APIController express
```

## Component Types

### Frontend Components
- **Functional**: React functional component
- **Class**: React class component
- **Hook**: Custom React hook
- **Vue**: Vue 3 composition API
- **Angular**: Angular component class
- **Web Component**: Custom HTML element

### Backend Components
- **Middleware**: Express/Fastify middleware
- **Controller**: API endpoint controller
- **Service**: Business logic service
- **Model**: Data model/entity
- **Repository**: Data access layer
- **Utility**: Helper functions

## Capabilities

- **TypeScript Support**: Optional type annotations
- **PropTypes/Validation**: Input validation
- **Styling**: CSS, SCSS, Tailwind, or Styled Components
- **Testing**: Jest/Vitest test file
- **Documentation**: JSDoc comments
- **Examples**: Usage examples included

## Example

```bash
/generate-component UserProfile react --typescript --with-tests
```

Creates:
```
UserProfile/
├── UserProfile.tsx          # Component
├── UserProfile.module.css   # Styles
├── UserProfile.test.tsx     # Tests
├── index.ts                 # Export
└── UserProfile.stories.tsx  # Storybook (optional)
```

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| name | string | ✅ | Component name |
| type | enum | ✅ | Component type |
| --framework | string | ❌ | Framework (react, vue, angular) |
| --typescript | boolean | ❌ | Generate TS files (default: false) |
| --with-tests | boolean | ❌ | Include test file (default: true) |
| --with-styles | boolean | ❌ | Include CSS file (default: true) |

## Generated Files

- **Component file**: Main component code
- **Styles**: CSS/SCSS file (optional)
- **Tests**: Jest/Vitest test file (optional)
- **Index**: Export file
- **Story**: Storybook story file (optional)
- **Doc**: Component documentation

## Code Quality

All generated components include:
- Proper error handling
- Input validation
- Accessibility features
- Clean code practices
- TypeScript types (when applicable)
