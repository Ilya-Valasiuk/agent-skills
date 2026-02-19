# Component Creation Checklist

## Validation

1.  **Named Export Only**: No `default export`.
2.  **Naming Convention**:
    -   File: `PascalCase` (e.g., `Header.tsx`).
    -   Folder: `kebab-case` (e.g., `src/components/common/header`).
3.  **Component Type**:
    -   Uses `React.FC<Props>` or `React.FC`.
    -   Uses implicit return `() => (...)` for pure JSX components.
4.  **Props**:
    -   `type Props` defined (not `interface`).
    -   Ordered: Required -> Optional -> Functions.
5.  **Structure**:
    -   One component per file.
    -   Sub-components in `components/` subfolder.
