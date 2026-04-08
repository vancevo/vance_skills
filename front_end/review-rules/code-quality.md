# Rule Catalog — Code Quality

## Conditional class names must use utility function (`cn`)

IsUrgent: True
Category: Code Quality

### Description

Ensure conditional CSS is handled via the shared `cn` wrapper (shadcn/Tailwind utility) instead of custom ternaries, string concatenation, or template strings directly inside JSX. Centralizing class logic keeps components consistent and easier to maintain.

### Suggested Fix

```ts
import { cn } from '@/lib/utils' // or '@/utils/classnames'
const classNames = cn('base-class', isActive ? 'text-primary-600' : 'text-gray-500')
```

## Tailwind-first styling

IsUrgent: True
Category: Code Quality

### Description

Favor Tailwind CSS utility classes instead of adding new `.module.css` files or inline `style={{}}` attributes. Styles must be kept in Tailwind to reduce maintenance overhead and adhere to the project's atomic CSS paradigm.

## Classname ordering for easy overrides

### Description

When writing reusable components, always place the incoming `className` prop *after* the component’s own hardcoded class values so that downstream consumers can override or extend the styling effectively. 

Wrong:
```tsx
const Button = ({ className }) => {
  return <div className={cn(className, 'bg-primary-600')}></div>
}
```

Right:
```tsx
const Button = ({ className }) => {
  return <div className={cn('bg-primary-600', className)}></div>
}
```
