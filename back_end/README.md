# Backend Development Resources & Skills

Chào mừng bạn đến với thư mục **Backend**. Đây là nơi quản lý hệ sinh thái kĩ năng, nguyên tắc và chuẩn mực cốt lõi dành cho máy chủ (Server-side) của dự án. Hệ thống được tập trung xoay quanh hệ sinh thái **Node.js, NestJS / Express.js**, TypeScript, cùng với PostgreSQL và Redis.

## 🗂 Cấu trúc thư mục

### 🤖 Kỹ Năng / Role (Agent Skill)
* **[`backend-developer-skill.md`](./backend-developer-skill.md)**
  Định nghĩa vai trò của một **Senior Backend Developer**. File này hướng dẫn cực kì nghiêm ngặt về cách tư duy và viết code cho API, Middleware, background jobs (BullMQ), kết nối DB (Prisma), và cách tổ chức thư mục theo chuẩn Layered Architecture (Controller → Service → Repository). Cung cấp file này cho AI Agent khi bạn giao cho nó thiết kế cấu trúc API hoặc sửa đổi code ở máy chủ.

### 📚 Bộ Quy Tắc (Project Rules)
Đây là các bộ luật cốt lõi (core mandate) của riêng phân hệ backend. Tất cả đoạn mã logic ở Server do con người hay AI viết ra đều phải thoả mãn các file này:

* **[`database.md`](./database.md)**
  Nguyên tắc liên quan đến việc định nghĩa lược đồ (Schema Design), ràng buộc, khoá ngoại, và tối ưu truy vấn bằng ORM.
  
* **[`api-conventions.md`](./api-conventions.md)**
  Quy chuẩn định dạng API trả về (API Envelope), mã trạng thái HTTP chuẩn mực và phong cách thiết kế định tuyến RESTful.
  
* **[`error-handling.md`](./error-handling.md)**
  Hướng xử lý ngoại lệ (Exception Handling), bắt lỗi toàn cục trong một ứng dụng Node.js để tránh trường hợp crash server đột ngột.

* **[`security.md`](./security.md)**
  Các phương pháp phòng chống XSS, SQL Injection, sử dụng JWT/auth token hợp lệ, quy định Validate (Zod), và cách kiểm soát biến môi trường bảo mật.

## 💡 Cách Sử Dụng
1. **Dành cho Developer Backend:** Đảm bảo toàn bộ kiến trúc đang viết tuân thủ luồng Layered. Hãy nắm rõ bộ `security.md` và `api-conventions.md` trước khi review code.
2. **Khởi tạo AI Agent:** Để Agent làm việc hiệu quả, hãy gắn bối cảnh bắt buộc của nó hướng thẳng vào file `backend-developer-skill.md`, và đồng thời truyền theo các quy tắc `database`, `api`, hoặc `security` tương ứng để nó tạo ra mã nguồn chính xác.
