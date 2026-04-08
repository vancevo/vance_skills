# Frontend Development Resources & Skills

Chào mừng bạn đến với thư mục **Frontend**. Thư mục này tập hợp các tệp cấu hình, kỹ năng của agent (AI), và toàn bộ các bộ quy tắc chuẩn mực (rules) dành riêng cho quá trình phát triển Frontend (đặc biệt là Next.js và React) trong dự án.

## 🗂 Cấu trúc thư mục

### 🤖 Kỹ Năng / Role (Agent Skill)
Bộ kĩ năng Frontend được cấu trúc theo dạng chu kỳ (Pipeline) gồm 3 bước tuần tự. AI Agent buộc phải theo trình tự này để kết xuất mã nguồn đạt chuẩn:

1. **[`frontend-developer-skill.md`](./frontend-developer-skill.md)** (Bước 1: Core Mandate)
   Định nghĩa vai trò của một **Senior Frontend Developer**. Hướng dẫn chuẩn mực gốc về kiến trúc Next.js/React, phân tách Component, quản lý state và các checklist quy chuẩn.
2. **[`frontend-design-skill.md`](./frontend-design-skill.md)** (Bước 2: Aesthetic Planning)
   Hệ tư tưởng thẩm mỹ. Ngăn chặn giao diện "AI đại trà" thông qua các quyết định thiết kế Layout, Typography, và Motion có chủ đích.
3. **[`frontend-patterns-skill.md`](./frontend-patterns-skill.md)** (Bước 3: Technical Execution)
   Toolkit kỹ thuật (Implementation). Chứa các React Patterns nâng cao (Compound Components, Custom Hooks, Lazy Loading, Reducer) dùng để code sạch và tối ưu hiệu năng.
4. **[`frontend-review-skill.md`](./frontend-review-skill.md)** (Bước 4: Quality Gate)
   Kĩ năng Review Code. Áp dụng khi AI cần kiểm duyệt lỗi (Review Changes). Sử dụng bộ template định dạng xuất file cực kì nghiêm ngặt và đối chiếu các tiêu chí chất lượng qua thư mục con `review-rules/`.

### 📚 Bộ Quy Tắc (Project Rules)
Đây là các bộ luật cốt lõi (core mandate) đóng vai trò định hướng mọi hoạt động lập trình trong thư mục/dự án này. Mọi mã nguồn được tạo ra dù là con người hay AI đều phải tuân thủ nghiêm ngặt:

* **[`tech-stack.md`](./tech-stack.md)**
  Quy định rõ ràng về công nghệ được phép sử dụng (Frontend: Next.js, React, Tailwind, TypeScript...). 

* **[`clean-code.md`](./clean-code.md)**
  Bộ quy tắc Clean Code. Lưu ý về cách phân tách UI và Logic, xây dựng cấu trúc thư mục linh hoạt, nguyên tắc DRY (Don't Repeat Yourself), và SOLID.

* **[`code-style.md`](./code-style.md)**
  Quy chuẩn trình bày, đặt tên biến/hàm/component, và cấu trúc định dạng file giúp mã nguồn đồng nhất, sạch sẽ và chuyên nghiệp.

## 💡 Cách Sử Dụng
1. **Dành cho Developer:** Hãy đọc lướt qua hoặc đọc kĩ các file rules (`clean-code.md`, `code-style.md`) trước khi bắt đầu code tính năng mới để mã nguồn dự án luôn đồng bộ.
2. **Dành cho AI Agent:** Khi giao việc cho AI (ví dụ: Claude, Gemini), hãy tham chiếu Agent tới file [`frontend-developer-skill.md`](./frontend-developer-skill.md) cùng với các file quy tắc liên quan. Agent sẽ hiểu bối cảnh công nghệ (Next.js/React) và cách viết code mà dự án đang đòi hỏi.
