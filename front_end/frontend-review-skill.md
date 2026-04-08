---
name: frontend-code-review
description: "Trigger when the user requests a review of frontend files (e.g., `.tsx`, `.ts`, `.js`). Support both pending-change reviews and focused file reviews while applying the Vancevo checklist rules."
---

# Frontend Code Review

> **AI INSTRUCTION: STEP 4 (QUALITY GATE)**
> Use this skill whenever the user asks to review frontend code. This acts as the final gatekeeper against poor quality code and architecture drifts.

## Intent
Support two review modes:
1. **Pending-change review** – inspect working-tree files slated for commit (Git diffs) and flag checklist violations before submission.
2. **File-targeted review** – review the specific file(s) the user names and report findings.

Stick to the localized Vancevo checklist for every applicable file review.

## Code Audit Checklists
Mọi Agent thực thi quá trình soi code bắt buộc phải tham chiếu 3 files sau trong thư mục `review-rules/` để tìm ra quy chuẩn bắt lỗi:
- `review-rules/code-quality.md`: Đảm bảo quy chuẩn CSS (Tailwindcn) và nguyên tắc viết mã.
- `review-rules/performance.md`: Đảm bảo không dính các lỗi hiệu năng như thiếu Memoization, Async Load component hay lạm dụng rerender.
- `review-rules/business-logic.md`: Đảm bảo tính nhất quán của Zod, React Hook Form, Zustand và Tanstack.

Đánh dấu mức độ `Urgent` (Khẩn cấp) cho mỗi file theo định nghĩa trong file tham chiếu tương ứng.

## Review Process
1. Open the relevant component/module. Gather lines that relate to business logic, async hooks, prop memoization, Tailwind strings, and Zod checks.
2. For each rule violation, note where the code deviates and capture a representative snippet.
3. Compose the review section per the strict template below. Group violations first by **Urgent** flag, then by category order.

## Required Output (AI MUST FOLLOW)
When invoked, your response **MUST EXACTLY** follow one of the two templates:

### Template A (If bugs/violations are found)
```text
# Code review
Found <N> urgent issues need to be fixed:

## 1 <Mô tả ngắn gọn về lỗi / bug>
FilePath: <đường_dẫn_file> line <dòng>
<Đoạn code liên quan đang bị lỗi>

### Suggested fix
<Giải pháp / Code mẫu khắc phục>

---
... (tương tự cho các lỗi Urgent khác) ...

Found <M> suggestions for improvement:

## 1 <Mô tả đề xuất cải thiện>
FilePath: <đường_dẫn_file> line <dòng>
<Đoạn code có thể cải thiện>

### Suggested fix
<Đề xuất code nên viết lại>

---
... (tương tự cho các suggestions khác) ...
```

*Note:* 
- If there are no urgent issues, omit that section. If there are no suggestions, omit that section.
- If the issue number is >10, summarize as "10+ urgent issues" and output only the top 10.
- Append a brief follow-up: *"Bạn có muốn tôi tự động áp dụng các bản sửa lỗi (Suggested fix) này vào mã nguồn không?"*

### Template B (If the code is flawless)
```text
## Code review
No issues found. Bậc thầy Code Frontend gởi lời chào! Khởi tạo Pull Request thôi nào!
```
