---
name: creating-components
description: Scaffolds React components following project conventions for naming, folder structure, exports, and props. Use when the user asks to create, add, scaffold, or generate a new React component.
---

# Creating React Components

## Quick Start

When creating a new component, follow this workflow and validate against the checklist before finishing.

## Creation Workflow

Copy this checklist and track progress:

```
Task Progress:
- [ ] Step 1: Determine component type and location
- [ ] Step 2: Create folder and file structure
- [ ] Step 3: Implement component with correct exports and props
- [ ] Step 4: Add sub-components if needed (create components/ subfolder)
- [ ] Step 5: Run validation checklist
```

**Step 1: Determine component type and location**

- **Common component** (shared across pages) → `src/components/common/[component-name]/`
- **Page-specific component** → `src/components/[page-name]/components/[component-name]/`
- **Sub-component** → `src/components/[parent]/components/[sub-component-name]/`

**Step 2: Create folder and file structure**

- Folder: `kebab-case` (e.g., `contact-form`, `hero-content`)
- File: `[ComponentName].tsx` in PascalCase matching the export name
- One component per file

**Step 3: Implement component**

- Use named export: `export const ComponentName: React.FC<Props>`
- Use implicit return for simple JSX: `() => ( ... )`
- Define `type Props` with required first, optional next, handlers last

**Step 4: Add sub-components (if needed)**

- Create `components/` folder inside parent component folder
- Each sub-component gets its own `[sub-name]/[SubName].tsx` structure

**Step 5: Validate**

Run through the Validation Checklist below before completing.

## Validation Checklist

After creating or modifying a component, verify:

```
Validation Checklist:
- [ ] Named export (no default export)
- [ ] React.FC<Props> or React.FC definition
- [ ] Folder name is kebab-case
- [ ] File name is PascalCase matching component name
- [ ] Props type defined with correct order (required → optional → handlers)
- [ ] Implicit return used when component only returns JSX
- [ ] One component per file
- [ ] Sub-components in components/ subfolder with same structure
```

If any item fails, fix it before proceeding.

## Naming Reference

| Element | Convention | Example |
|--------|------------|---------|
| Folder | kebab-case | `card-content`, `modal-header` |
| File | PascalCase | `CardContent.tsx`, `ModalHeader.tsx` |
| Export | PascalCase | `CardContent`, `ModalHeader` |
| Props type | Props | `type Props = { ... }` |

## Additional Resources

- **Structure reference**: See [reference.md](reference.md) for full directory structure and rules
- **Code examples**: See [examples.md](examples.md) for Button, Logo, and nested component examples
