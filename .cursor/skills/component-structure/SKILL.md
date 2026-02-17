---
name: component-structure
description: Defines how to structure and organize React/Next.js components. Use when creating, refactoring, or organizing components in the src/ directory.
---
# Component Structure and Organization

## When to Use
- Use this skill whenever you are creating a new React component or modifying an existing one.
- This skill applies to all `.tsx` files in the project.
- It is particularly helpful when refactoring existing components to match project standards.

## Instructions

### 1. Export Pattern
- **No default exports** in components - always use named exports.
- Define components using `export const [ComponentName]: React.FC<Props>` (or `React.FC` if no props).
- Use **arrow function body style** (implicit return) for simple JSX returns: `() => ( ... )`.

### 2. File and Folder Organization
- **Folder names:** `kebab-case` (e.g., `card-content`).
- **File names:** `PascalCase` (e.g., `CardContent.tsx`).
- **Component exports:** Must match the file name.
- **Rules:**
  - Each component must have its own folder.
  - Each file should contain exactly one component.
  - For sub-components, create a `components/` sub-folder within the parent component's folder.

### 3. Directory Structure
- `src/components/common`: Shared components used across multiple pages.
- `src/components/[component-name]`: Main component directory.
  - `[ComponentName].tsx`: Main file.
  - `components/`: Sub-components directory.
- **Page Directories:**
  - `src/app/([locale])/([route-name])/page.tsx`: Exports `[RouteNamePage]`.

### 4. Props Definition
- Use `type Props` for component props.
- Order: Required props → Optional props → Function props.

### 5. Examples

#### Props Definition
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

#### Component with Props
```typescript
type Props = {
  title: string;
  className?: string;
  onClick: () => void;
};

export const Button: React.FC<Props> = ({ title, className, onClick }) => (
  <button className={className} onClick={onClick}>
    {title}
  </button>
);
```

#### Component without Props
```typescript
export const Logo: React.FC = () => (
  <div className="logo">
    <img src="/logo.svg" alt="Logo" />
  </div>
);
```
