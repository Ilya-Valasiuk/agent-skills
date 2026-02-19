# Component Examples

## Example 1: Component with Props

```typescript
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

## Example 2: Component without Props

```typescript
export const Logo: React.FC = () => (
  <div className="logo">
    <img src="/logo.svg" alt="Logo" />
  </div>
);
```

## Example 3: Props with Full Ordering

```typescript
type Props = {
  requiredName: string;
  requiredId: number;
  optionalDescription?: string;
  optionalClassName?: string;
  onClick: () => void;
  onSubmit?: (data: DataType) => void;
};

export const FormField: React.FC<Props> = ({
  requiredName,
  requiredId,
  optionalDescription,
  optionalClassName,
  onClick,
  onSubmit,
}) => (
  <div className={optionalClassName}>
    {/* implementation */}
  </div>
);
```

## Example 4: Folder Structure for Nested Component

```
src/components/common/contact-form/
├── ContactForm.tsx           # Main component
└── components/
    ├── contact-form-header/
    │   └── ContactFormHeader.tsx
    └── contact-form-body/
        └── ContactFormBody.tsx
```

## Example 5: Page Component Structure

```
src/components/home/
├── Home.tsx                  # Main page component
└── components/
    ├── hero-content/
    │   └── HeroContent.tsx
    └── feature-grid/
        └── FeatureGrid.tsx
```
