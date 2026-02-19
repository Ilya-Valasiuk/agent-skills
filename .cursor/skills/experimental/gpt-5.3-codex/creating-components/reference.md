# Component conventions reference

## Directory placement

- Shared component: `src/components/common/[component-name]/[ComponentName].tsx`
- Page-level component: `src/components/[page-name]/[component-name]/[ComponentName].tsx`
- Sub-component: `src/components/.../[parent]/components/[sub-component-name]/[SubComponentName].tsx`

## Naming rules

- Folder names: kebab-case
- File names: PascalCase
- Exported component name must match file name

## Export and typing rules

- No default export for regular components
- Define components as:
  - `export const ComponentName: React.FC<Props> = (...) => (...)`
  - or `export const ComponentName: React.FC = () => (...)` when no props
- Use `type Props` for props typing

## Props ordering

Order props in `Props` type as:
1. Required props
2. Optional props
3. Function props

## File composition rules

- One component per file
- Keep related smaller units under `components/` in the parent folder

## Page route note

When creating a page component in `src/app`:
- With locale segment: `src/app/[locale]/[route-name]/page.tsx`
- Without locale segment: `src/app/[route-name]/page.tsx`
