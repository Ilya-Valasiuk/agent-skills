---
name: creating-components
description: Creates React/Next.js components using this project's folder, naming, export, and props conventions. Use when asked to create, scaffold, add, or generate a new component or sub-component in src/components.
---

# Creating Components

## When to use

Use this skill when the user asks to create a new React/Next.js component or sub-component.

## Workflow

Copy this checklist and mark progress while implementing:

```text
Component Creation Progress:
- [ ] Step 1: Classify component scope and target location
- [ ] Step 2: Create folder/file structure
- [ ] Step 3: Implement component with required export/typing pattern
- [ ] Step 4: Run validation checklist
- [ ] Step 5: Fix issues and re-validate
```

### Step 1: Classify scope and target location

1. Decide if the component is shared or page-specific:
   - Shared: place under `src/components/common`
   - Page-specific: place under `src/components/[page-name]`
2. For sub-components, place under parent `components/` folder.
3. If requirements are ambiguous, ask one clarifying question before creating files.

### Step 2: Create structure

Follow `reference.md` for naming and placement rules.

### Step 3: Implement component

Follow this default implementation pattern:

- Use named exports only
- Use `export const ComponentName: React.FC<Props>` (or `React.FC` if no props)
- Use `type Props`
- Keep one component per file
- Prefer implicit return for simple JSX components

### Step 4: Validate

Run the full checklist in `validation-checklist.md`.

### Step 5: Feedback loop

If any validation item fails:
1. Fix the issue
2. Re-run the checklist
3. Repeat until all required checks pass

## Output format

When reporting back, include:

1. Created paths
2. Any assumptions made
3. Validation result (pass/fail and what was fixed)

## Additional resources

- Conventions: [reference.md](reference.md)
- Validation: [validation-checklist.md](validation-checklist.md)
- Copyable examples: [examples.md](examples.md)
