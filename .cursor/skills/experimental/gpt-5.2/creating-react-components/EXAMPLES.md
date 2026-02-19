# Examples

## Example: shared component

```text
src/components/common/modal-header/
└── ModalHeader.tsx
```

In `ModalHeader.tsx`, export `ModalHeader` as a named export.

## Example: feature/page-specific component

```text
src/components/pricing/
├── Pricing.tsx
└── components/
    └── plan-card/
        └── PlanCard.tsx
```

## Example: component with sub-components

```text
src/components/common/hero/
├── Hero.tsx
└── components/
    ├── hero-content/
    │   └── HeroContent.tsx
    └── hero-cta/
        └── HeroCta.tsx
```
