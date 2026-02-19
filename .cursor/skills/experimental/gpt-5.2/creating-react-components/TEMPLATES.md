# Templates

These are copy/paste starting points. Adjust as needed, but keep:
- **named exports only**
- **`React.FC` typing**
- **`type Props`**

## Component without props

```tsx
import type React from 'react';

export const Logo: React.FC = () => (
  <div className="logo">
    <img src="/logo.svg" alt="Logo" />
  </div>
);
```

## Component with props (props ordered: required → optional → functions)

```tsx
import type React from 'react';

type Props = {
  title: string;
  className?: string;
  onClick: () => void;
};

export const Button: React.FC<Props> = ({ title, className, onClick }) => (
  <button className={className} onClick={onClick} type="button">
    {title}
  </button>
);
```

## Parent component with sub-components folder

```text
src/components/common/feature-card/
├── FeatureCard.tsx
└── components/
    ├── feature-card-header/
    │   └── FeatureCardHeader.tsx
    └── feature-card-body/
        └── FeatureCardBody.tsx
```
