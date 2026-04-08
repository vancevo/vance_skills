# Vancevo Project Skills & Rules

Chào mừng bạn đến với kho lưu trữ **Vancevo Skills**. Đây là trung tâm quản lý toàn bộ các kỹ năng dành cho AI Agents (Agent Skills) cũng như các bộ tiêu chuẩn, nguyên tắc lập trình (Project Rules) của toàn bộ dự án.

Khác với một kho code thông thường, repo này đóng vai trò như "bộ não" hướng dẫn chuẩn mực cho cả các thành viên trong đội ngũ phát triển và cho các trợ lý AI (ví dụ: Claude, Gemini) tham gia vào việc viết hay phân tích mã nguồn.

---

## 🗂 Cấu Trúc Tổng Thể

Dự án được chia theo các phân hệ rõ ràng để tiện cho việc nạp kiến thức (context) mảng nào ra mảng đó. Điều này giúp tránh bị loãng thông tin và AI Agent có thể làm việc tập trung hơn.

### Hiện tại:
* **[`/front_end`](./front_end)**: Chứa toàn bộ Agent Skill và Rules (Tech Stack, Clean Code, Code Style) dành riêng cho mảng giao diện (hiện đang dùng Next.js / React). Khi có tác vụ ở Frontend, hãy điều phối AI Agent tham chiếu thư mục này.

### Mở rộng trong tương lai:
* **`/back_end`**: Sẽ chứa kỹ năng, kiến trúc API, Database schemas, nguyên tắc bảo mật và tech-stack dành cho mảng Backend (Node.js/Python/Go/Java...).
* **`/devops`**: Sẽ chứa hướng dẫn thiết lập CI/CD, kịch bản triển khai (Deployment scripts), quản trị Docker & Cloud và giám sát (Monitoring).
* **`/qa_testing`**: Sẽ chứa kỹ năng viết Automation Test, End-to-End Test, Integration Test và quy chuẩn nghiệm thu chất lượng phần mềm.

---

## 💡 Hướng Dẫn Sử Dụng (Dành cho Người Dùng / Kỹ Sư)

1. **Phân Rã Context**: Khi giao nhiệm vụ cho AI, ***đừng gửi toàn bộ thư mục***. Tác vụ thuộc phân hệ nào (thực thi ở Frontend hay Backend?), xin hãy chỉ đọc và truyền cho AI đúng các file rules nằm trong thư mục tương ứng. Sự tập trung sẽ đem lại kết quả code chính xác hơn.
2. **Khởi Tạo Phân Hệ Mới**: Tương tự như `/front_end`, khi muốn xây dựng quy chuẩn cho team BE hay DevOps, hãy tạo thư mục mới. Ở bên trong thư mục đó, luôn nhớ sinh tối thiểu 2 file cốt lõi:
   * `[role]-skill.md`: Định hình tư duy của AI khi đóng vai trò đó.
   * `tech-stack.md` (hoặc `rules.md`): Bộ luật bắt buộc tuân theo bằng code.

---
*Mọi thay đổi trên repo này sẽ ảnh hưởng trực tiếp đến chất lượng code chung của dự án do cả team kĩ sư lẫn team AI tham gia sản xuất. Vui lòng thảo luận kỹ trước khi chỉnh sửa bộ rules.*
