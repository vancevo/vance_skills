---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use when building web components, pages, or applications where visual direction matters.
---

# Frontend Design

> **AI INSTRUCTION: STEP 2 (AESTHETIC PLANNING)**
> Read this file **after** understanding the core mandate in `frontend-developer-skill.md`.
> Before you write any visual code, you must establish the design direction based on this file. 
> Once you understand the aesthetic requirements, proceed to `frontend-patterns-skill.md` for technical execution.

Sử dụng skill này khi yêu cầu không chỉ là "code cho chạy được" mà là "code cho đẹp và có chủ đích". Kỹ năng này dành cho việc xây dựng landing pages, dashboards, hoặc các UI components cần sự khác biệt, chứ không phải giao diện AI chung chung mang tính chất "trả bài".

## 1. Core Principle (Nguyên tắc Cốt lõi)

**Pick a direction and commit to it.** (Chọn một phong cách và kiên định với nó).
Một giao diện quá "an toàn" sẽ tệ hơn là một giao diện có cá tính với vài quyết định táo bạo. Hãy đưa ra quyết định thẩm mỹ thật mạnh mẽ.

## 2. Design Workflow

### Bước 1: Frame the interface first
Trước khi code, hãy chốt:
- Mục đích và đối tượng người dùng.
- Cảm xúc truyền tải (tone).
- Hướng thiết kế chính.
- Một điều duy nhất người dùng cần ghi nhớ.

**Các hướng thiết kế khả thi:**
- Brutally minimal (Tối giản cực độ).
- Editorial (Giống báo chí/tạp chí).
- Industrial (Công nghiệp, thô).
- Geometric (Hình khối).
- Soft and organic (Mềm mại, tự nhiên).
*Lưu ý: Đừng trộn lẫn các phong cách. Hãy chọn một và thực thi thật sắc nét.*

### Bước 2: Build the visual system
Định nghĩa hệ thống:
- Phân cấp Typography.
- Màu sắc (Color variables).
- Nhịp điệu khoảng cách (Spacing rhythm).
- Quy luật logic layout và Motion (hoạt ảnh).

### Bước 3: Compose with intention
Ưu tiên:
- **Asymmetry (Bất đối xứng):** dùng khi cần phân cấp mạnh hơn.
- **Overlap (Xếp chồng):** dùng khi cần tạo chiều sâu.
- **Whitespace (Khoảng trắng):** dùng để làm rõ sự tập trung.
- Mật độ thông tin dày đặc: chỉ dùng cho các dashboard chuyên môn sâu.
*Tuyệt đối tránh mặc định sắp xếp đối xứng kiểu thẻ (card grid) nếu không thực sự phù hợp.*

### Bước 4: Make motion meaningful
Chỉ sử dụng hoạt ảnh để:
- Trình bày sự phân cấp thông tin.
- Nhấn mạnh một hành động.
- Tạo ra 1-2 khoảnh khắc đáng nhớ nhất.
*Không rải rác các hover effects vô nghĩa khắp mọi nơi.*

## 3. Strong Defaults

### Typography
- Chọn font có cá tính. Tránh font mặc định. Pha trộn giữa font hiển thị (Display face) cá tính và font văn bản (Body face) dễ đọc.

### Color
- Cam kết với một bảng màu rõ ràng. Một dải màu chủ đạo với các điểm nhấn (accents) thường hoạt động tốt hơn bảng màu bảy sắc cầu vồng.
- Tránh xa các UI "tím-gradient-trên-nền-trắng" rẻ tiền trừ khi đó thực sự là yêu cầu.

### Background
Tạo khí chất (Atmosphere):
- Gradients, Meshes, Textures, Noise mờ, hoặc Pattern. Nền phẳng, trống không hiếm khi là lựa chọn tốt nhất.

## 4. Anti-Patterns (Tuyệt đối tránh)
X Không tạo giao diện SaaS Hero Sections đổi lẫn cho nhau.
X Không xếp đống các thẻ (card piles) mà không có hierarchy.
X Không dùng typography như để "giữ chỗ" (placeholder).
X Không tạo hoạt ảnh chỉ vì "làm nó dễ".

## Khúc Giao Mức Độ Tương Tác
Khi bạn đã thấu hiểu phong cách thiết kế, hãy dùng **[frontend-patterns-skill.md](./frontend-patterns-skill.md)** để triển khai bằng các React Component Patterns sạch sẽ và tối ưu.
