# React Component Templates

### Component with props

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

### Component without props

```tsx
export const Logo: React.FC = () => (
  <div className="logo">
    <img src="/logo.svg" alt="Logo" />
  </div>
);
```

### Page component

```tsx
// src/app/[locale]/about-us/page.tsx
export const AboutUsPage: React.FC = () => (
  <AboutUs />
);
```
