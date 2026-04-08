# Rule Catalog — Performance

## Next.js Image Optimization

IsUrgent: True
Category: Performance

### Description

Avoid using raw HTML `<img src="..."/>` tags for static assets. Always use Next.js' native `<Image />` component (`next/image`) to enforce automatic WebP optimization, lazy loading, and Core Web Vitals (CLS/LCP) protection. Must assign `width` and `height` (or `fill` with `sizes`).

## Complex prop memoization

IsUrgent: True
Category: Performance

### Description

Wrap complex prop values (objects, arrays, maps, inline functions) in `useMemo` or `useCallback` prior to passing them into expensive child components. This guarantees stable references across renders and prevents unnecessary reconciliation flows.

Wrong:
```tsx
<ExpensiveComponent
    config={{
        provider: 'stripe',
        detail: user.paymentInfo
    }}
/>
```

Right:
```tsx
const config = useMemo(() => ({
    provider: 'stripe',
    detail: user.paymentInfo
}), [user.paymentInfo]);

<ExpensiveComponent config={config} />
```

## Heavy External Libraries Load (Dynamic import)

IsUrgent: False
Category: Performance

### Description

Large payload components (like Charts, Maps, rich text editors, 3D Canvas) must be decoupled from the primary bundle using Next.js `dynamic()` or React `lazy()` wrapped in Suspense so they do not block the First Contentful Paint (FCP).
