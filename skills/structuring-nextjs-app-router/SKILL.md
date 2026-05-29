---
name: structuring-nextjs-app-router
description: Standardize and preserve Next.js App Router project structure across `src/`, including route files, page composition, API modules, server actions, hooks, providers, helpers, and shared utilities. Use this skill whenever the user asks to add, move, rename, refactor, or review files in a Next.js App Router codebase, especially if the task affects file placement, page architecture, or folder naming.
---

# Next.js App Router Structure

Use this skill to place new code in the correct part of a Next.js App Router repo and to keep architecture consistent during refactors.

## Goals

- Keep `src/app` focused on routing concerns and thin route files
- Keep page UI in `src/components/<page-name>/<PageName>.tsx`
- Group domain logic by responsibility instead of mixing fetchers, actions, hooks, and view code
- Preserve consistent naming: kebab-case folders, PascalCase component files

## Workflow

### 1. Check whether the repo already follows this convention

Inspect nearby files before creating or moving anything.

- If the repo already follows this structure, continue with it.
- If the repo differs in a small accidental way, prefer nudging the new work toward this structure.
- If the repo uses a clearly different deliberate architecture, preserve the existing pattern unless the user asked to migrate or standardize it.

### 2. Classify the requested work

Decide what kind of artifact the user needs:

- route file or route metadata
- page-level UI
- shared component
- API client logic
- server action
- hook
- context or provider
- helper, utility, constant, type, or layout

Then place it using [references/REFERENCE.md](references/REFERENCE.md).

### 3. Keep `app/` thin

When editing `src/app`, prefer route files that do orchestration rather than UI implementation.

- `page.tsx` should load data, read params, call helpers/actions as needed, and render page components from `src/components/...`
- `layout.tsx`, `template.tsx`, `error.tsx`, `loading.tsx`, and `not-found.tsx` should stay focused on route behavior
- do not bury large presentational sections directly inside route files unless the repo already intentionally does that

### 4. Place view code in `components/`

- shared UI goes under `src/components/common/<component-name>/`
- page-specific UI goes under `src/components/<page-name>/`
- nested component composition goes inside `components/` subfolders

If the task is mainly about building or restructuring React components, also follow the `building-components` skill if it is available.

### 5. Keep domain logic separated by concern

- API client fetchers and query hooks belong in `src/api`
- server mutations belong in `src/actions`
- project-specific helper logic belongs in `src/helpers`
- generic reusable utilities belong in `src/utils`
- app-wide constants and types belong in `src/constants` and `src/types`

Do not mix these concerns just because a file is convenient to reach from a page.

## Placement Rules

Follow the full placement matrix in [references/REFERENCE.md](references/REFERENCE.md).

High-value defaults:

- Put route handlers in `src/app/api/**/route.ts`
- Put page UI in `src/components/<page-name>/<PageName>.tsx`
- Put domain API code in `src/api/<domain>/module.ts`, `queries.ts`, and `types.ts`
- Put server actions in `src/actions/<domain>/index.ts`
- Put contexts in `src/context/<context-name>/`
- Put providers in `src/providers/<provider-name>/`

## Naming Rules

- Folders: kebab-case
- React component files: PascalCase
- Context files: `<ContextName>Context.tsx`
- Provider files: `<ProviderName>Provider.tsx`
- Hook files: `useX.ts`

Match exported names to filenames whenever practical.

## Refactor Behavior

When the user asks to reorganize or standardize a Next.js repo:

- move files toward this structure gradually
- keep imports consistent after moves
- avoid broad churn outside the requested area
- do not invent new top-level `src/` categories unless the repo already has them or the user asked for them

## Validation Checklist

Before finishing, verify:

- route files stay in `src/app`
- page UI is not trapped inside `page.tsx` without a good reason
- domain logic is stored under the right top-level `src/` folder
- folder and file names follow the convention
- new files match nearby import/export patterns

## Examples

**Example 1**

Input: "Add a new Services page in a Next.js App Router app."

Expected structure:

- `src/app/[[locale]]/services/page.tsx`
- `src/components/services/Services.tsx`
- optional nested UI in `src/components/services/components/...`

**Example 2**

Input: "Create blog query hooks and fetchers."

Expected structure:

- `src/api/blog/module.ts`
- `src/api/blog/queries.ts`
- `src/api/blog/types.ts`
- optional `src/api/blog/constants.ts`
- optional `src/api/blog/helpers.ts`

Add optional domain files when the logic clearly belongs to that domain rather than to shared API utilities.

**Example 3**

Input: "Add a contact form server action."

Expected structure:

- `src/actions/contact/index.ts`
- optional `src/actions/contact/types.ts`
- optional `src/actions/contact/constants.ts`
- optional `src/actions/contact/helpers.ts`
