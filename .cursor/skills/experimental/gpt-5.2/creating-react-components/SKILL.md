---
name: creating-react-components
description: Creates and scaffolds new React/Next.js UI components in src/components using the project's component structure rules (kebab-case folders, PascalCase files, named exports, React.FC + Props typing). Use when the user asks to create, scaffold, add, or generate a new component or sub-component.
---

# Creating React Components

Use this skill when you need to **create a new component** (or sub-component) in `src/components/` and keep it consistent with `.cursor/rules/component-structure.mdc`.

## Quick start (default workflow)

1. **Choose placement**
   - Shared/reusable → `src/components/common/<component-name>/`
   - Feature/page-specific → `src/components/<feature-or-page>/components/<component-name>/`
2. **Pick names**
   - Folder: `kebab-case` (example: `modal-header`)
   - File: `PascalCase` (example: `ModalHeader.tsx`)
   - Export: matches file name (example: `export const ModalHeader ...`)
3. **Create the component**
   - **Named export only** (no `export default`)
   - `export const ComponentName: React.FC<Props> = (...)`
   - If no props: `export const ComponentName: React.FC = (...)`
   - Prefer implicit return when only returning JSX: `() => ( ... )`
4. **If you need sub-components**
   - Create `components/` under the parent component folder
   - Each sub-component: its own `kebab-case` folder + `PascalCase` file
5. **Validate**
   - Run the checklist below, then run the repo’s standard scripts (lint/typecheck/tests).

## Implementation details

### 1) Placement rules

- **Components live in `src/components/`**.
- Use `src/components/common/` for components intended to be reused across multiple pages/features.
- For nested composition, put sub-components under the parent’s `components/` directory.

### 2) Naming rules (must be consistent)

- **Folder names**: `kebab-case`
- **File names**: `PascalCase`
- **Component export name**: must match the file name

If the user provides one of these, derive the other deterministically:

- Folder `card-content` → file/export `CardContent`
- File `CardContent.tsx` → folder `card-content`

### 3) Props rules

- Define props as `type Props = { ... }` in the same file.
- Order fields:
  1. required props
  2. optional props
  3. function props

## Post-create validation checklist (feedback loop)

Copy/paste and check items off while working:

```
Component creation checklist
- [ ] Location: under src/components/ (common/ or feature/page folder)
- [ ] Folder name is kebab-case
- [ ] Component file name is PascalCase and ends with .tsx
- [ ] Exactly one component per file
- [ ] Named export only (no default export)
- [ ] Exported component name matches file name
- [ ] Uses React.FC<Props> (or React.FC when no props)
- [ ] If component only returns JSX, uses implicit return: () => ( ... )
- [ ] Props are defined as type Props and ordered: required → optional → functions
- [ ] If sub-components exist, they live under parent/components/ and follow the same rules
- [ ] Imports are clean (no unused imports, no missing deps)
- [ ] The component is wired into its parent/usage site
- [ ] Run repo scripts (from package.json): lint, typecheck, test (whatever exists)
```

If any checklist item fails: fix it, then re-run the relevant script(s) until green.

## Templates and examples

- **Templates**: see [TEMPLATES.md](TEMPLATES.md)
- **Folder trees**: see [EXAMPLES.md](EXAMPLES.md)
