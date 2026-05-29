# Next.js App Router Structure Reference

Use this reference when deciding where code should live in a Next.js App Router repo.

## `src/api`

Purpose: API client modules grouped by domain.

### Common

- `src/api/common/types.ts`: generic API response and pagination types
- `src/api/common/module.ts`: shared API utilities

### Domain module

Use one folder per domain, for example `blog`, `projects`, or `services`.

- `module.ts`: request functions and fetchers
- `queries.ts`: React Query hooks or query option builders
- `types.ts`: domain-specific types
- `constants.ts`: optional domain constants
- `helpers.ts`: optional transformations and parsing helpers

Use `src/api` for client-side or shared fetching concerns, not server actions.

## `src/actions`

Purpose: Next.js server actions grouped by mutation domain.

Per-domain structure:

- `index.ts`: main action exports
- `types.ts`: optional action payload and result types
- `helpers.ts`: optional helper functions used only by actions

Use `src/actions` for server-side mutations and side effects such as submit, send, create, update, delete, or trigger workflows.

## `src/app`

Purpose: file-system routing and route-local framework files.

### General rule

Keep route files slim. Prefer loading data and rendering components from `src/components/<page-name>/<PageName>.tsx`.

### Typical files

- `page.tsx`
- `layout.tsx`
- `template.tsx`
- `error.tsx`
- `not-found.tsx`
- `loading.tsx`
- `robots.ts`
- `sitemap.ts`

### Routing patterns

- `[[locale]]`: optional locale segment
- `(group-name)`: route group without URL impact
- static segments such as `blog`
- dynamic segments such as `[slug]`
- catch-all segments such as `[...rest]`

### API routes

Route handlers belong under `src/app/api/**/route.ts`.

Examples:

- `src/app/api/route.ts`
- `src/app/api/users/route.ts`
- `src/app/api/users/[id]/route.ts`

Do not move API route handlers into `src/api`; that folder is for client modules and query logic.

## `src/components`

Purpose: presentational and page-composition UI.

### Shared components

Place reusable components in:

- `src/components/common/<component-name>/<ComponentName>.tsx`

Optional companions:

- `components/`
- `types.ts`
- `constants.ts`
- `helpers.ts`
- `index.ts`

### Page components

Place page-level UI in:

- `src/components/<page-name>/<PageName>.tsx`

Optional companions:

- `components/`
- `types.ts`
- `constants.ts`
- `helpers.ts`
- `index.ts`

### Nesting

Complex compositions may nest several levels deep. Each level should keep the same pattern:

- kebab-case folder
- PascalCase component file
- optional `components/` subfolder for children

## `src/constants`

Purpose: app-wide constants separated by domain or concern.

Common examples:

- `api.ts`
- `pages.ts`
- `public-variables.ts`

## `src/context`

Purpose: React context definitions without provider business logic.

Per-context structure:

- `src/context/<context-name>/<ContextName>Context.tsx`
- `src/context/<context-name>/index.ts`
- optional `types.ts`, `constants.ts`, `helpers.ts`

## `src/providers`

Purpose: provider components that implement state and business logic around a context.

Per-provider structure:

- `src/providers/<provider-name>/<ProviderName>Provider.tsx`
- `src/providers/<provider-name>/index.ts`
- optional `types.ts`, `constants.ts`, `helpers.ts`

## `src/helpers`

Purpose: project-specific helper functions with business context.

Examples:

- `cms.ts`
- `i18n.ts`
- `ui.ts`

If the logic is highly generic and reusable outside the app domain, prefer `src/utils` instead.

## `src/hooks`

Purpose: reusable React hooks.

### Simple hook

- `src/hooks/useClickOutside.ts`
- `src/hooks/useDebounce.ts`

### Complex hook

- `src/hooks/useAuth/useAuth.ts`
- `src/hooks/useAuth/index.ts`
- optional `types.ts`, `constants.ts`, `helpers.ts`

Use the folder form when the hook has several support files.

## `src/layouts`

Purpose: reusable layout wrapper components.

Per-layout structure:

- `src/layouts/<layout-name>/<LayoutName>.tsx`
- optional `src/layouts/<layout-name>/index.ts`

## `src/styles`

Purpose: global CSS and style layers.

Common files:

- `globals.css`
- `reset.css`
- `overrides.css`

## `src/types`

Purpose: global TypeScript definitions shared across domains.

Common files:

- `locale.ts`
- `recaptcha.ts`

## `src/utils`

Purpose: generic utilities without business logic.

Common files:

- `array.ts`
- `date.ts`
- `storage.ts`

If the same function could be reused in other projects without knowing anything about this app, it is a strong candidate for `src/utils`.

If the logic knows about CMS models, page slugs, locale config, or app-specific workflows, it probably belongs in `src/helpers` instead.

## `src/http`

Purpose: optional shared HTTP client setup and error handling.

Typical structure:

- `src/http/index.ts`
- `src/http/constants.ts`
- `src/http/http-error/HttpError.ts`
- `src/http/http-error/helpers.ts`
- `src/http/http-error/types.ts`

Use this folder only when the project centralizes HTTP transport concerns.
