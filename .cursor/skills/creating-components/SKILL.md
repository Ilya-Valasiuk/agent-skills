---
name: creating-components
description: Scaffolds React components following project conventions for naming, folder structure, exports, and props. Use when the user asks to create, add, scaffold, or generate a new React component.
---

# Creating Components

## Workflow

Copy this checklist and track progress:

```
Component Progress:
- [ ] Step 1: Determine placement
- [ ] Step 2: Create folder structure
- [ ] Step 3: Create component file
- [ ] Step 4: Add sub-components (if needed)
- [ ] Step 5: Validate against checklist
```

**Step 1: Determine placement**

Infer from context if possible, otherwise ask the user. 
See [placement.md](placement.md) for paths and conventions for each type:

- Shared (common) component
- Page-specific component
- Sub-component of existing component
- Page component

**Step 2: Create folder structure**

Create a kebab-case folder in the appropriate location. 
See [folder-structures.md](folder-structures.md) for diagrams of each scenario.

**Step 3: Create component file**

Create a PascalCase `.tsx` file inside the folder. Follow these rules:

- Named export only (no default exports)
- Use `React.FC<Props>` or `React.FC` signature
- Use implicit return `() => (...)` when the body is JSX-only
- Define `type Props` with required props first, optional second, function props last

For templates, see [examples.md](examples.md).

**Step 4: Add sub-components (if needed)**

If the component needs sub-components, create a `components/` folder inside:

```
[component-name]/
├── [ComponentName].tsx
└── components/
    └── [sub-component-name]/
        └── [SubComponentName].tsx
```

Each sub-component follows the same rules. Nesting can go 5-6 levels deep.

**Step 5: Validate against checklist**

Run through the validation checklist below before considering the component complete.

---

## Validation checklist

After creating a component, verify every item:

### Naming
- [ ] Folder name is kebab-case (e.g., `card-content`)
- [ ] File name is PascalCase and matches the exported component (e.g., `CardContent.tsx` exports `CardContent`)
- [ ] File is inside its own folder (not loose in a parent directory)

### Exports
- [ ] Uses named export: `export const ComponentName: React.FC<Props>`
- [ ] No default exports
- [ ] One component per file

### Props
- [ ] Props defined as `type Props` (not `interface`)
- [ ] Required props listed first
- [ ] Optional props listed second
- [ ] Function props (`onClick`, `onSubmit`, etc.) listed last
- [ ] `React.FC<Props>` used (or `React.FC` if no props)

### Structure
- [ ] Component placed in the correct directory (common vs page-specific)
- [ ] Sub-components live in a `components/` subfolder, not alongside the parent
- [ ] Implicit return used when the body is JSX-only

### Files
- [ ] Optional helper files (`types.ts`, `constants.ts`, `helpers.ts`, `index.ts`) created only if needed

---

## Additional resources

- For placement paths and conventions, see [placement.md](placement.md)
- For folder structure diagrams, see [folder-structures.md](folder-structures.md)
- For naming, export, and props conventions, see [reference.md](reference.md)
- For code templates, see [examples.md](examples.md)
