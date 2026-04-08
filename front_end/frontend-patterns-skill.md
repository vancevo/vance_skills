---
name: frontend-patterns
description: Frontend development patterns for React, Next.js, state management, performance optimization, and UI best practices.
---

# Frontend Patterns

> **AI INSTRUCTION: STEP 3 (TECHNICAL EXECUTION)**
> Read this file **after** you have absorbed the aesthetics from `frontend-design-skill.md`. 
> This is your technical toolbox. Use these advanced architectural patterns to implement the frontend cleanly and efficiently.

Sử dụng bộ kĩ năng này khi xây dựng Components, quản lý State, fetch dữ liệu, tối ưu hiệu năng hay quản lý Forms phức tạp. Nó sẽ giúp nâng cấp code từ cấu trúc cơ bản lên chuẩn mức Senior.

## 1. Component Patterns

### Composition Over Inheritance
Luôn ưu tiên cấu thành component linh hoạt thông qua ngõ nhận `children` thay vì nhồi nhét quá nhiều props cứng ngắc.

```tsx
export function Card({ children, variant = 'default' }: CardProps) {
  return <div className={`card card-${variant}`}>{children}</div>
}
export function CardHeader({ children }) {
  return <div className="card-header">{children}</div>
}
// Usage: <Card><CardHeader>Title</CardHeader></Card>
```

### Compound Components (Components Hợp Chất)
Sử dụng Context nội bộ để các child components giao tiếp ngầm với nhau mà không cần truyền props qua lại.
(Ví dụ: `<Tabs>`, `<TabList>`, `<Tab>`).

```tsx
const TabsContext = createContext<TabsContextValue | undefined>(undefined)

export function Tabs({ children, defaultTab }) {
  const [activeTab, setActiveTab] = useState(defaultTab)
  return <TabsContext.Provider value={{ activeTab, setActiveTab }}>{children}</TabsContext.Provider>
}

export function Tab({ id, children }) {
  const context = useContext(TabsContext)
  if (!context) throw new Error('Tab must be used within Tabs')
  return <button onClick={() => context.setActiveTab(id)}>{children}</button>
}
```

### Render Props
Dùng để đóng gói mảng logic nặng (vd: fetch logic, state) và nhường quyền kiểm soát giao diện lại cho Consumer.

```tsx
<DataLoader url="/api/markets">
  {(markets, loading, error) => {
    if (loading) return <Spinner />
    if (error) return <Error error={error} />
    return <MarketList markets={markets} />
  }}
</DataLoader>
```

## 2. Custom Hooks Patterns

Luôn bóc tách logic rời khỏi UI component bằng cách tạo Custom Hooks.

### Async Data Fetching Hook
Đóng gói quy trình Loading / Error / Data / Refetch thông qua Custom Hook chuẩn. Hoặc ưu tiên dùng TanStack React Query.
### Debounce Hook
```tsx
export function useDebounce<T>(value: T, delay: number): T {
  const [debouncedValue, setDebouncedValue] = useState<T>(value)
  useEffect(() => {
    const handler = setTimeout(() => setDebouncedValue(value), delay)
    return () => clearTimeout(handler)
  }, [value, delay])
  return debouncedValue
}
```

## 3. State Management Patterns

### Context + Reducer Pattern
Đối với các Object State phức tạp trong cùng một Feature nhưng không muốn dùng thư viện ngoài (Zustand), hãy phối hợp `useReducer` và `ContextAPI`.

```tsx
const MarketContext = createContext<{ state: State; dispatch: Dispatch<Action> } | undefined>(undefined)

export function MarketProvider({ children }) {
  const [state, dispatch] = useReducer(reducer, { markets: [], loading: false })
  return <MarketContext.Provider value={{ state, dispatch }}>{children}</MarketContext.Provider>
}

export function useMarkets() {
  const ctx = useContext(MarketContext)
  if (!ctx) throw new Error('useMarkets must be inside MarketProvider')
  return ctx
}
```

## 4. Tối Ưu Hiệu Năng (Performance Optimization)

- **Memoization:** Cẩn trọng dùng `useMemo` cho thuật toán xử lý dữ liệu nặng và `useCallback` khi pass method xuống child component. Dùng `React.memo` cho pure components.
- **Lazy Loading:** `lazy(() => import('./HeavyChart'))` bọc trong ranh giới `<Suspense>`.
- **Virtualization:** Dùng `@tanstack/react-virtual` để cuộn danh sách hàng ngàn items mà không bị lag (chỉ render mảng DOM đang xuất hiện trên viewport).

## 5. Animation Patterns

**Framer Motion** là lựa chọn số 1:
```tsx
import { motion, AnimatePresence } from 'framer-motion'
// ...
<AnimatePresence>
  {markets.map(market => (
    <motion.div
       key={market.id}
       initial={{ opacity: 0, y: 20 }}
       animate={{ opacity: 1, y: 0 }}
       exit={{ opacity: 0, y: -20 }}
       transition={{ duration: 0.3 }}
    >
      <MarketCard />
    </motion.div>
  ))}
</AnimatePresence>
```

## 6. Lớp Bảo Vệ & Form (Safety)
- **Error Boundaries:** Cần bọc Root Layout hoặc Feature Section bằng Class Component `<ErrorBoundary>` để khi 1 component dính lỗi, ứng dụng sẽ không sụp màn hình trắng toàn trang.
- **Focus Management:** Giao diện Dialog / Modal / Dropdown luôn phải "khoá" tiêu điểm Focus (keyboard escape, arrow navigation, trap focus). Mọi UI bắt buộc hỗ trợ Accesibility.
