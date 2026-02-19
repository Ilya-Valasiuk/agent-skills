---
name: creating-components
description: Creates and scaffolds new React/Next.js UI components in src/components using the project's component structure rules (kebab-case folders, PascalCase files, named exports, React.FC + Props typing). Use when the user asks to create, scaffold, add, or generate a new component or sub-component.
---

# Creating React Components

## Workflow

1.  **Determine Location**:
    -   Shared? → `src/components/common`
    -   Page-specific? → `src/components/[page-name]`
    -   Sub-component? → `src/components/[parent]/components/[sub-component]`

2.  **Verify**: Check if component already exists using `ls` or `glob`.

3.  **Scaffold**:
    -   Create folder: `kebab-case` (e.g., `user-profile`)
    -   Create file: `PascalCase.tsx` inside folder (e.g., `UserProfile.tsx`)
    -   **Strictly follow** templates in [TEMPLATES.md](TEMPLATES.md).

4.  **Validate**:
    -   Run through the checklist in [CHECKLIST.md](CHECKLIST.md) to ensure compliance.

## Naming Conventions

-   **Folders**: `kebab-case` (e.g., `nav-bar`, `submit-button`)
-   **Files**: `PascalCase` matching component name (e.g., `NavBar.tsx`, `SubmitButton.tsx`)
-   **Exports**: Named exports only (e.g., `export const NavBar ...`)

## Quick Reference

-   **Props**: define `type Props`, order: required -> optional -> functions.
-   **Function Component**: `React.FC<Props>` or `React.FC`.
-   **Return**: Implicit return `() => (...)` for JSX-only components.
