# Component Conventions Reference

## Naming conventions

| Element          | Convention  | Example                            |
|------------------|-------------|------------------------------------|
| Folder name      | kebab-case  | `card-content`, `button-group`     |
| File name        | PascalCase  | `CardContent.tsx`, `ButtonGroup.tsx`|
| Component export | PascalCase  | `export const CardContent`         |
| Props type       | `type Props`| `type Props = { ... }`             |

The file name and exported component name must always match.

## Export pattern

Always use named exports:

```tsx
export const Button: React.FC<Props> = ({ title, onClick }) => (
  <button onClick={onClick}>{title}</button>
);
```

Never use default exports in components.

Use `React.FC<Props>` when the component accepts props, or `React.FC` when it does not.

## Implicit vs explicit return

Use implicit return (arrow body) when the function body is only JSX:

```tsx
// Implicit — preferred when body is JSX-only
export const Logo: React.FC = () => (
  <div className="logo">
    <img src="/logo.svg" alt="Logo" />
  </div>
);
```

Use explicit return when the component contains logic before the JSX:

```tsx
export const Counter: React.FC<Props> = ({ initial }) => {
  const [count, setCount] = useState(initial);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
};
```

## Props ordering

Define props in this order inside `type Props`:

1. **Required** props (no `?`)
2. **Optional** props (`?`)
3. **Function** props (callbacks like `onClick`, `onSubmit`)

```tsx
type Props = {
  title: string;          // required
  id: number;             // required
  description?: string;   // optional
  className?: string;     // optional
  onClick: () => void;    // function (required)
  onSubmit?: (data: FormData) => void; // function (optional)
};
```

## Optional supporting files

Create these only when needed:

| File           | Purpose                          |
|----------------|----------------------------------|
| `types.ts`     | Shared types for this component  |
| `constants.ts` | Component-specific constants     |
| `helpers.ts`   | Component-specific helpers      |
| `index.ts`     | Re-exports for cleaner imports   |
