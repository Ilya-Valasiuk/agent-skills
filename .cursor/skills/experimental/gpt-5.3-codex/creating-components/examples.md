# Component creation examples

## Example 1: shared component with props

Path:
`src/components/common/button/Button.tsx`

```tsx
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

## Example 2: simple shared component without props

Path:
`src/components/common/logo/Logo.tsx`

```tsx
export const Logo: React.FC = () => (
  <div className="logo">
    <img src="/logo.svg" alt="Logo" />
  </div>
);
```

## Example 3: parent component with sub-component structure

Structure:

```text
src/components/home/hero/
├── Hero.tsx
└── components/
    └── hero-content/
        └── HeroContent.tsx
```

`Hero.tsx` should import and compose `HeroContent`, while each file keeps one component and named export.
