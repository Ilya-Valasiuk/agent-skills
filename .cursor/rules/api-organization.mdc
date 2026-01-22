---
description: "Standards for API organization, including folder structure, fetcher naming conventions, and domain types."
alwaysApply: false
---
# API Organization

This rule defines how to structure and organize API modules, including directory structure, shared types, and naming conventions for fetchers and types.

## 1. Directory Structure

```
src/api/
├── common/
│   ├── types.ts           # Shared types across all API modules
│   └── module.ts          # Shared API request functions (optional)
├── [domain-name]/
│   ├── module.ts          # API request functions (fetchers)
│   ├── types.ts           # Domain type definitions
│   ├── constants.ts       # Domain constants (optional)
│   └── helpers.ts         # Domain helpers (optional)
└── index.ts               # Optional re-exports
```

## 2. Common Types (src/api/common/types.ts)

Shared types that can be reused across all API modules.

```typescript
export type ResponseData<T, U = object> = {
  data: T;
  meta: U;
};

export type Pagination = {
  page: number;
  pageCount: number;
  pageSize: number;
  total: number;
};
```

## 3. Domain File Structure (src/api/[domain-name])

Each domain has its own folder, containing only the API logic, types, and helpers relevant to that domain.

### module.ts

HTTP request functions that interact with API endpoints.

**Naming conventions by HTTP method:**
- **GET**: `fetch*` prefix (e.g., `fetchProductById`, `fetchProductList`)
- **POST**: `create*` prefix (e.g., `createProduct`, `createUser`)
- **PUT/PATCH**: `update*` prefix (e.g., `updateProduct`, `updateUserProfile`)
- **DELETE**: `delete*` or `remove*` prefix (e.g., `deleteProduct`, `removeUser`)

**Pattern:**

```typescript
const BASE_URL = 'https://api.example.com';

export const fetchProductById = async (productId: string) => {
  const response = await fetch(`${BASE_URL}/products/${productId}`);

  if (response.ok) {
    const data: ProductResponse = await response.json();
    return data;
  }

  throw new Error("Failed to fetch product.");
};

export const createProduct = async (productPayload: CreateProductPayload) => {
  const response = await fetch(`${BASE_URL}/products`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(productPayload),
  });

  if (response.ok) {
    const data: ProductResponse = await response.json();
    return data;
  }

  throw new Error("Failed to create product.");
};
```

### types.ts

TypeScript type definitions for the domain.

**Naming:**
- Response types: `*Response` (e.g., `ProductResponse`)
- Request payloads: `*Payload` (e.g., `CreateProductPayload`, `UpdateProductPayload`)
- Entities: Singular noun (e.g., `Product`, `User`)

**Pattern:**

```typescript
import type { ResponseData, PaginatedMeta } from '@/api/common/types';

export type Product = {
  id: string;
  name: string;
  description: string;
  price: number;
};

export type ProductResponse = ResponseData<Product>;

export type ProductListResponse = ResponseData<Product[], PaginatedMeta>;

export type CreateProductPayload = {
  name: string;
  description: string;
  price: number;
};
```

## 4. Parameter Validation

Always validate required parameters before making an API call.

```typescript
export const fetchProductById = async (productId: string | null) => {
  if (!productId) {
    throw new Error('Product ID is required');
  }

  const response = await fetch(`${BASE_URL}/products/${productId}`);
  // ...
};
```
