---
alwaysApply: true
---
# NextJS App Router Application Folder Structure

This rule defines the organization and structure of the `/src` directory.

---
### src/api

API client modules organized by domain with data fetching logic.

- **common**
  - `types.ts` - Generic types based on API (e.g., `ResponseData<T>`, `Pagination`)
  - `module.ts` - Shared API utilities
- **[domain-name]** *example: blog, projects, services*
  - `module.ts` - API request functions (fetchers)
  - `queries.ts` - React Query hooks
  - `types.ts` - Domain-specific types
  - `constants.ts` - Domain constants (optional)
  - `helpers.ts` - Data transformation helpers (optional)

### src/actions

Server actions for Next.js server-side operations, organized by domain.

- **[domain-name]** *example: contact, sendgrid*
  - `index.ts` - Main action exports
  - `types.ts` - Action types (optional)
  - `helpers.ts` - Helper functions (optional)

### src/app

Next.js App Router with file-system based routing. Keep pages free of logic and focus on loading data and rendering components from `/components/[page-name]/[PageName].tsx`.

**Structure:**
- **[[locale]]** - Optional dynamic segment for internationalization (matches `/` and `/en`, `/fr`, etc.)
  - **([group-name])** - Route groups. Organize routes without affecting URL structure.
    - Can contain: `page.tsx`, `layout.tsx`, `error.tsx`, `loading.tsx`, `not-found.tsx`, nested routes (static, dynamic, catch-all), other route groups.
  - **blog** - Static route segment
    - **[slug]** - Dynamic segment (e.g., `/blog/first-post`)
      - `page.tsx` - Blog post page
  - **[...rest]** - Catch-all segment for all unmatched routes
    - `page.tsx` - Catch-all page (typically redirects to 404)
  - `page.tsx` - Page component
  - `layout.tsx` - Shared UI for route segments
  - `template.tsx` - Re-rendered layout on navigation
  - `error.tsx` - Error boundary
  - `not-found.tsx` - 404 page
  - `loading.tsx` - Loading UI
- **api** - API routes (Route Handlers)
  - `route.ts` - Root API endpoint (e.g., `/api`)
  - **users** - Static route segment
    - `route.ts` - Handles `/api/users` endpoint
    - **[id]** - Dynamic segment
      - `route.ts` - Handles `/api/users/[id]` endpoint (e.g., `/api/users/123`)
- `robots.ts` - Dynamic robots.txt generation
- `sitemap.ts` - Dynamic sitemap generation

### src/components

- **common** - Shared components used across multiple pages (e.g., Header, Footer, Button)
  - **[component-name]** *(example: header, footer, button)*
    - `[ComponentName].tsx`
    - **components** - Sub-components specific to this component
    - Optional files (types.ts, constants.ts, helpers.ts, index.ts)
- **[page-name]** *(example: home, about-us, services)*
  - `[PageName].tsx` - Main page component, utilizes components from `./components` or `common`
  - **components** - Specific components for `[PageName].tsx`
    - **[component-name]**
      - `[ComponentName].tsx`
      - **components** - Can be nested deeper for complex compositions
        - Optional files (types.ts, constants.ts, helpers.ts)
  - Optional files (types.ts, constants.ts, helpers.ts, index.ts)

**Nesting:**
- Components can be deeply nested (5-6 levels common) for proper composition
- Each level follows the same pattern: folder → component file + optional `components/` subfolder

**Naming:**
- Component files: PascalCase (e.g., `Button.tsx` exports `Button`)
- Folders: kebab-case (e.g., `contact-form/`, `hero-content/`)

### src/constants

Application-wide constants organized by domain in individual files.

**Common files:** `api.ts`, `pages.ts`, `public-variables.ts`

### src/context

React Context definitions for global state management. Each context in its own folder.

**Structure:**
- **[context-name]** *(example: contact-us-modal)*
  - `[ContextName]Context.tsx` - Context definition
  - `index.ts` - Re-exports the context
  - Optional files (types.ts, constants.ts, helpers.ts)

### src/providers

Provider components that implement context providers with business logic and state management. Each provider in its own folder.

**Structure:**
- **[provider-name]** *(example: contact-us-modal)*
  - `[ProviderName]Provider.tsx` - Provider component that wraps Context.Provider with logic and state
  - `index.ts` - Re-exports the provider
  - Optional files (types.ts, constants.ts, helpers.ts)

### src/helpers

Project-specific helper functions organized by domain (e.g., `cms.ts`, `i18n.ts`, `ui.ts`).

### src/hooks

Custom React hooks for reusable component logic.

- **Simple hooks**: Single file (e.g., `useClickOutside.ts`, `useDebounce.ts`)
- **Complex hooks**: Folder structure
  - **[hook-name]** *(example: useAuth)*
    - `[hookName].ts` - Main hook file
    - `index.ts` - Re-exports
    - Optional files (types.ts, constants.ts, helpers.ts)

### src/layouts

Layout wrapper components. Each layout in its own folder.

**Structure:**
- **[layout-name]** *(example: common-layout)*
  - `[LayoutName].tsx` - Layout component
  - `index.ts` - Re-exports (optional)

### src/styles

Global CSS and style files.

**Common files:** `globals.css` (Tailwind imports), `reset.css`, `overrides.css`

### src/types

Global TypeScript type definitions organized by domain.

**Common files:** `locale.ts`, `recaptcha.ts`

### src/utils

Reusable utility functions for common operations. Keep utils free of business logic.

**Common files:** `array.ts`, `date.ts`, `storage.ts`

### src/http (Optional folder. May not be present in all projects)

HTTP client configuration and error handling.

- `index.ts` - Main HTTP client exports
- `constants.ts` - HTTP configuration
- **http-error** - Error handling utilities
  - `HttpError.ts`, `helpers.ts`, `types.ts`
