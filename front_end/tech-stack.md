# Technology Stack — Selection & Standards

> This rule defines the **approved tech stack** for Frontend projects. When starting a new project or proposing a new dependency, follow the decision criteria below.

---

## 🗂️ Quick Reference — Approved Stack

| Layer | Primary Choice | Alternative | Avoid |
|-------|---------------|-------------|-------|
| **Frontend — Landing/SEO** | Next.js 14+ (App Router) | — | CRA (deprecated) |
| **Frontend — Admin/Dashboard** | React + Vite (SPA) | — | Next.js (overkill for admin) |
| **UI Components** | shadcn/ui + Radix UI | Chakra UI | MUI (too heavy) |
| **Styling** | Tailwind CSS | CSS Modules | Styled-components (runtime cost) |
| **State Management** | Zustand | Redux Toolkit | MobX, Recoil |
| **Data Fetching** | TanStack Query (React Query) | SWR | Axios alone |
| **Language** | TypeScript (always) | — | Plain JavaScript |
| **Auth (Client)** | NextAuth.js (Next) / JWT stored locally | Lucia Auth | Firebase Auth |
| **Monitoring/Analytics** | Vercel Analytics / PostHog | Google Analytics | — |
| **Testing** | Vitest + Testing Library | Jest | Mocha |
| **E2E Testing** | Playwright | Cypress | Selenium |
| **CI/CD** | GitHub Actions | — | Jenkins (legacy) |
| **Deployment** | Vercel / Cloudflare Pages | AWS S3/CloudFront | — |

---

## 🖥️ Frontend — Chọn đúng framework

### Decision Table

| Tiêu chí | Next.js 14 (App Router) | React + Vite (SPA) |
|----------|------------------------|--------------------|
| **Mục đích** | Landing page, marketing, blog | Admin panel, dashboard, internal tool |
| **SEO** | ✅ SSR/SSG — Google index tốt | ❌ SPA — khó SEO |
| **Lưu trữ** | Vercel (tối ưu nhất) | Cloudflare Pages, Netlify, S3 |
| **Performance** | Server Components — ít JS gửi về client | Client-side rendering |
| **Auth** | NextAuth.js | JWT stored in cookie/localStorage |
| **API** | API Routes hoặc Server Actions | Gọi backend REST riêng biệt |
| **Build complexity** | Cao hơn | Đơn giản hơn |

> **Rule**: Một project thường có **cả hai** — Next.js cho public site + React cho admin.

---

### Next.js — Landing Page / SEO Project

```bash
npx create-next-app@latest my-landing \
  --typescript --tailwind --eslint --app --src-dir --import-alias "@/*"
```

**Tại sao Next.js cho landing page:**
- Server-Side Rendering (SSR) → Google crawl được nội dung
- Static Site Generation (SSG) → build thành HTML tĩnh, lưu CDN, siêu nhanh
- Image optimization tự động (`next/image`)
- `<head>` metadata API tích hợp sẵn
- Incremental Static Regeneration (ISR) → cập nhật nội dung không rebuild toàn bộ

```tsx
// app/layout.tsx — SEO metadata
export const metadata: Metadata = {
  title: { default: 'My App', template: '%s | My App' },
  description: 'Mô tả trang chính',
  openGraph: { type: 'website', locale: 'vi_VN', url: 'https://myapp.com' },
};
```

**Folder structure (App Router)**
```text
src/app/
├── (marketing)/          # Public pages (SSG/SSR)
│   ├── page.tsx          # Homepage
│   ├── about/page.tsx
│   ├── blog/
│   │   ├── page.tsx      # Blog list (SSG)
│   │   └── [slug]/page.tsx  # Blog post (ISR)
│   └── pricing/page.tsx
├── (auth)/               # Auth pages
│   ├── login/page.tsx
│   └── register/page.tsx
├── api/v1/               # API Routes
└── layout.tsx
```

---

### React + Vite — Admin / Dashboard Project

```bash
npx create-vite@latest my-admin -- --template react-ts
cd my-admin && npm install
```

**Tại sao React SPA cho admin:**
- Admin panel không cần SEO (đăng nhập mới vào được)
- SPA build đơn giản, deploy lên S3/Cloudflare Pages/Nginx
- Trạng thái phức tạp (table, filter, form) dễ quản lý hơn
- Hot reload nhanh hơn trong development

**Folder structure (Vite SPA)**
```text
src/
├── pages/               # Các trang (react-router)
│   ├── Dashboard.tsx
│   ├── Users/
│   │   ├── UserList.tsx
│   │   └── UserDetail.tsx
│   └── Settings.tsx
├── components/
│   ├── layout/          # Sidebar, Header, Layout
│   └── ui/              # Shared UI components
├── features/            # Feature-based modules
│   └── users/
│       ├── api.ts       # TanStack Query hooks
│       ├── store.ts     # Zustand slice
│       └── types.ts
├── lib/                 # axios instance, utils
└── main.tsx
```

**Key Rules cho Admin:**
- Protected routes với `<AuthGuard>` component
- Role-based UI: `usePermission()` hook ẩn/hiện features
- Token refresh tự động trong axios interceptor

---

## ✅ Technology Decision Process

When **proposing a new library or technology** for the frontend, evaluate against these criteria:

| Criterion | Questions to ask |
|-----------|-----------------|
| **Necessity** | Does an approved alternative already solve this? |
| **Maintenance** | Stars > 1k? Last commit < 6 months? |
| **Bundle size** | Check bundlephobia.com — is it worth the KB? |
| **TypeScript** | Does it have native TS types? |
| **License** | Is it MIT/Apache? (No GPL in commercial products) |
| **Security** | `npm audit` — zero high/critical vulnerabilities |
| **Community** | Active issues/discussions? Stack Overflow answers? |

### Decision Template
```markdown
## Technology Decision: [Library Name]

**Problem**: What problem does this solve?
**Alternative evaluated**: What from the approved stack was considered?
**Why chosen**: Specific reason this is better for the use case
**Risk**: Known downsides or migration cost
**Decision**: ✅ Adopt / ❌ Reject
```
