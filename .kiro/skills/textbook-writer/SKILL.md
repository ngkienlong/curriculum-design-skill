---
name: textbook-writer
description: >
  Viết giáo trình (textbook) chi tiết cho từng dự án trong syllabus STEM/AI.
  Dùng khi người dùng muốn viết giáo trình, tài liệu học, nội dung bài học,
  hoặc tài liệu tham khảo cho học sinh dựa trên syllabus đã có.
  Kể cả khi người dùng nói "viết nội dung cho dự án X" hoặc "soạn tài liệu học" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "1.0"
---

## Khả năng

Viết giáo trình chi tiết cho từng dự án trong syllabus STEM/AI. Mỗi dự án tạo ra 1 file giáo trình riêng.

## Khi nào dùng

- Người dùng muốn viết giáo trình / textbook cho các dự án trong syllabus
- Người dùng đã có syllabus và muốn tạo nội dung chi tiết
- Người dùng nói "viết giáo trình", "soạn tài liệu học", "viết textbook"

## Input

- **Bắt buộc:** File syllabus (ở root khoá: `[tên-khoá]/syllabus.md`)
- **Tuỳ chọn:** Dự án cụ thể muốn viết (nếu không chỉ định → viết tất cả)

## Quy trình thực hiện

### Bước 1: Đọc syllabus
Đọc file syllabus để hiểu tổng quan khoá học, danh sách dự án, mục tiêu từng dự án.

### Bước 2: Viết giáo trình cho từng dự án
Với mỗi dự án trong syllabus, viết 1 file giáo trình theo cấu trúc bên dưới. Viết lần lượt từng dự án, sau mỗi dự án **hỏi người dùng có muốn điều chỉnh gì không** trước khi sang dự án tiếp.

### Bước 3: Lưu file
Lưu từng file vào subfolder của dự án tương ứng: `[tên-khoá]/[du-an-X-tên]/textbook-[slug-dự-án].md`

**Quy tắc đặt tên:** Slug trong tên file phải trùng với slug trong tên folder.
- Folder `du-an-1-den-sos` → file `textbook-den-sos.md`
- Folder `du-an-3-cam-bien-lui-xe` → file `textbook-cam-bien-lui-xe.md`
- Ví dụ đầy đủ: `arduino-robot-thcs/du-an-1-den-sos/textbook-den-sos.md`

```markdown
# [Tên dự án]

**Số buổi:** [Số buổi] x [X phút/buổi]

---

## 1. Giới thiệu dự án

### Bối cảnh thực tế
Mô tả vấn đề thực tế mà dự án giải quyết. Viết sinh động, gần gũi với học sinh.

### Câu hỏi dẫn dắt
"[Câu hỏi từ syllabus]"

### Mục tiêu học tập
- [ ] Mục tiêu 1 (theo thang Bloom)
- [ ] Mục tiêu 2
- ...

### Sản phẩm đầu ra
Mô tả cụ thể sản phẩm học sinh sẽ hoàn thành.

---

## 2. Kiến thức nền tảng

### 2.1 [Chủ đề kiến thức 1]
Giải thích lý thuyết cần thiết. Dùng hình ảnh minh hoạ, ví dụ cụ thể.
Viết ở mức độ phù hợp lứa tuổi.

### 2.2 [Chủ đề kiến thức 2]
...

> 💡 **Mẹo:** [Tip hữu ích cho học sinh]

> ⚠️ **Lưu ý an toàn:** [Nếu có liên quan đến an toàn điện, hoá chất, v.v.]

---

## 3. Hướng dẫn thực hành

### 3.1 Vật tư và công cụ cần chuẩn bị
| STT | Vật tư / Công cụ | Số lượng | Ghi chú |
|-----|-------------------|----------|---------|
| 1 | ... | ... | ... |

### 3.2 Sơ đồ kết nối / Bản vẽ thiết kế
(Mô tả chi tiết cách kết nối mạch, lắp ráp, hoặc thiết kế phần mềm)

### 3.3 Hướng dẫn từng bước

**Bước 1: [Tên bước]**
- Mô tả chi tiết
- Code mẫu (nếu có):
```[ngôn ngữ]
// code ở đây
```
- Kết quả mong đợi: ...

**Bước 2: [Tên bước]**
...

---

## 4. Nâng cao

Mô tả mở rộng cho học sinh nhanh. Gợi ý cách thực hiện.

---

## 5. Câu hỏi ôn tập

1. [Câu hỏi kiểm tra hiểu biết]
2. [Câu hỏi áp dụng]
3. [Câu hỏi phân tích / sáng tạo]

---

## 6. Thuật ngữ

| Thuật ngữ | Giải thích |
|-----------|------------|
| ... | ... |
```