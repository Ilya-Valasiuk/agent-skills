# Component Templates

## With Props

```typescript
type Props = {
  requiredName: string;
  requiredId: number;
  optionalDescription?: string;
  optionalClassName?: string;
  onClick: () => void;
  onSubmit?: (data: DataType) => void;
};

export const ComponentName: React.FC<Props> = ({ requiredName, requiredId, optionalDescription, optionalClassName, onClick, onSubmit }) => (
  <div className={optionalClassName} onClick={onClick}>
    <h1>{requiredName}</h1>
    <p>{requiredId}</p>
    {optionalDescription && <p>{optionalDescription}</p>}
  </div>
);
```

## Without Props

```typescript
export const ComponentName: React.FC = () => (
  <div className="component-name">
    <p>Component content</p>
  </div>
);
```

## Sub-Component Structure

```typescript
// src/components/[parent]/components/[sub-component]/[SubComponentName].tsx

type Props = {
  // ...
};

export const SubComponentName: React.FC<Props> = ({ ... }) => (
  // ...
);
```
