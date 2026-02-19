# Component Structure Reference

## Contents

- Directory structure
- Export and definition rules
- Props ordering
- Sub-component nesting

## Directory Structure

```
src/components/
├── common/                          # Shared across pages
│   └── [component-name]/            # kebab-case
│       ├── [ComponentName].tsx      # PascalCase
│       └── components/              # Optional sub-components
│           └── [sub-name]/
│               └── [SubName].tsx
└── [page-name]/                     # Page-specific (e.g., home, about-us)
    ├── [PageName].tsx
    └── components/
        └── [component-name]/
            ├── [ComponentName].tsx
            └── components/          # Can nest 5–6 levels for complex compositions
                └── ...
```

## Export Rules

- No default exports; always use named exports
- Definition: `export const ComponentName: React.FC<Props>` or `export const ComponentName: React.FC`
- Component name matches file name: `Button.tsx` exports `Button`
- One component per file

## Return Style

- Implicit return when component only returns JSX: `() => ( ... )`
- Explicit return when logic is needed: `() => { ... return ... }`

## Props Definition

Use `type Props` with this order:

1. Required props
2. Optional props
3. Function/handler props last

```typescript
type Props = {
  requiredName: string;
  requiredId: number;
  optionalDescription?: string;
  optionalClassName?: string;
  onClick: () => void;
  onSubmit?: (data: DataType) => void;
};
```

## Sub-component Structure

- Create `components/` inside the parent component folder
- Each sub-component: `[sub-name]/[SubComponentName].tsx`
- Same naming conventions apply at every level
- Nest up to 5–6 levels for complex compositions
