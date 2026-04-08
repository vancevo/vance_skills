# Frontend Development Resources & Skills

Chào mừng bạn đến với thư mục **Frontend**. Thư mục này tập hợp các tệp cấu hình, kỹ năng của agent (AI), và toàn bộ các bộ quy tắc chuẩn mực (rules) dành riêng cho quá trình phát triển Frontend (đặc biệt là Next.js và React) trong dự án.

## 🗂 Cấu trúc thư mục

### 🤖 Kỹ Năng / Role (Agent Skill)
* **[`frontend-developer-skill.md`](./frontend-developer-skill.md)**
  Định nghĩa vai trò và bộ kỹ năng (skill) của một **Senior Frontend Developer**. File này hướng dẫn chuẩn mực về Next.js/React, phân tách Server/Client Components, quản lý state (Zustand, React Query), và các checklist quan trọng về hiệu năng (Core Web Vitals), bảo mật cũng như trợ năng (A11Y). Giao file này cho AI Agent khi bạn cần Agent lập trình frontend.

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
