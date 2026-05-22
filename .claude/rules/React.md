# React

## Rules
- Use **functional components** only; no class components.
- Prefer **named exports** for components used elsewhere; default export for page/route components is fine.
- Define **props with TypeScript interfaces** (e.g. `interface ButtonProps { label: string }`).
- Extract **custom hooks** for reusable state and side-effect logic; keep components focused on rendering.
- Use **meaningful component and file names** in PascalCase; one main component per file when possible.
- Prefer **composition** over prop drilling; use React context sparingly and only for cross-cutting concerns.
- Keep **side effects in `useEffect`** with clear dependencies; avoid unnecessary effects and stale closures.
- Keep it **DRY**, Don't Repeat Yourself. Do not duplicate components that are 60-99% similar, for example `<Card />` vs `<FeaturedCard />` unless there are complex logic reasons to do so.
- Prefer creating **reusable** primitive components like `<Modal />` or `<Button />` and place them inside `components/UI` subdirectory path (see folder structure details)

## CSS
- import css module as a constant named `styles`
  - example: `import styles from "./Button.module.css";` 

## Folder Structure

- follow known conventions for **NextJS** apps using App Router
- under `/src/app` create a folder called components if it doesn't exist
- under `/components` create a folder called `ui`. this will be the location for reusable components
- unit test files and css module files should live in the same folder as the component

### React Examples

```tsx
// ✅ GOOD – typed props, functional component
interface CardProps {
  title: string
  children: React.ReactNode
}

function Card({ title, children }: CardProps) {
  return (
    <article>
      <h2>{title}</h2>
      {children}
    </article>
  )
}
```

```tsx
// ✅ GOOD – custom hook for reusable logic
function useToggle(initial = false) {
  const [on, setOn] = useState(initial)
  const toggle = useCallback(() => setOn((v) => !v), [])
  return [on, toggle] as const
}
```

```tsx
// ❌ BAD – untyped props, inline object creation in JSX
function Card(props) {
  return <div style={{ padding: 10 }}>{props.title}</div>
}
```
