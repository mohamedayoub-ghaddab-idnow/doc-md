# PR Review Guidelines

This document contains common feedback and best practices collected from code reviews. Use this as a checklist when preparing pull requests.

---

## CSS and Design

### Design System Tokens

- **Always use design system tokens** for font sizes and spacing
- Avoid hardcoded values; reference the design system instead

---

## Package Management

### Version Pinning

- **Use exact versions** (no caret `^` or tilde `~`)
- This ensures consistent builds across environments

**Examples:**

```json
// ❌ Avoid
"@pdfslick/react": "^1.5.0"

// ✅ Correct
"@pdfslick/react": "1.5.0"
```

---

## Import Statements

### Absolute Paths

- **Prefer absolute imports** over relative paths (`../..`)
- Use imports from `src` root for better maintainability
- Makes refactoring easier and improves code searchability

**Examples:**

```typescript
// ❌ Avoid
import { Component } from "../../../components/Component";

// ✅ Correct
import { Component } from "src/components/Component";
```

### Shared Components

- A component is **shared only if used by 2+ other components**
- If used by only one component, it should be in a subfolder of the parent component
- Don't prematurely move components to shared folders

---

## Naming Conventions

### Case Style

- **Use camelCase** for all naming (variables, functions, file names where applicable)

---

## Testing

### Vitest Imports

- **No need to explicitly import** `describe`, `it`, `expect` from `vitest`
- These are available globally in the test environment

**Examples:**

```typescript
// ❌ Avoid
import { describe, it, expect } from "vitest";

// ✅ Correct
// Just use describe, it, expect directly
```

- **No need to add**

```typescript
beforeEach(() => {
    vi.clearAllMocks();
```

- These are handled globally

---

## React Best Practices

### Component Definition

- **Components should be arrow functions**
- Maintains consistency across the codebase

**Examples:**

```typescript
// ❌ Avoid
function MyComponent() {
  return <div>Hello</div>;
}

// ✅ Correct
const MyComponent = () => {
  return <div>Hello</div>;
};
```

---

## Notes

This is a living document. Add new items as you encounter recurring feedback in code reviews.
