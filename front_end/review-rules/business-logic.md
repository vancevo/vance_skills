# Rule Catalog — Business Logic

## Zod Schema Validation Integrity

IsUrgent: True
Category: Business Logic

### Description

Any endpoint mutation or form submission must pass through a strict `Zod` validation schema. Avoid trusting raw Object types or manual string/length boundary checks directly inside React handlers. Component-level state should rely on `react-hook-form` coupled with the `zodResolver`.

### Suggested Fix

Extract form validation logic immediately:
```tsx
const loginSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8, "Mật khẩu quá ngắn")
});
```

## Async Error Handling via TanStack

IsUrgent: True
Category: Business Logic

### Description

When fetching or mutating data on the client side, backend error states must be explicitly caught. Use TanStack Query's `onError` callback or intercept Axios responses to throw readable feedback to the User Interface (via Toasts or Error Boundaries). Silent failures are strictly prohibited.

## Context API Misuse

IsUrgent: False
Category: Business Logic

### Description

Do not use Context API to store rapidly changing global variables, as it causes massive unnecessary re-renders in large component trees. For fast-changing state that bridges multiple remote components, mandate the use of `Zustand` atoms instead. Context is exclusively reserved for static/low-velocity data like Theme, Auth Tokens, or compound-component shared state.
