---
name: textbook-compiler
description: >
  Tổng hợp nhiều file giáo trình (textbook) thành 1 file duy nhất.
  Dùng khi người dùng muốn gộp tất cả giáo trình của các dự án thành 1 tài liệu hoàn chỉnh.
  Kể cả khi người dùng nói "gộp giáo trình", "tổng hợp textbook", "merge tài liệu học" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "1.0"
---

## Khả năng

Đọc tất cả file giáo trình riêng lẻ trong thư mục `textbook/` và tổng hợp thành 1 file markdown duy nhất, có mục lục và cấu trúc rõ ràng.

## Khi nào dùng

- Người dùng muốn gộp / tổng hợp các file giáo trình thành 1 file
- Người dùng nói "gộp giáo trình", "tổng hợp textbook", "merge tài liệu"
- Sau khi đã viết xong giáo trình cho tất cả dự án

## Input

- **Bắt buộc:** Các file giáo trình `textbook.md` trong các subfolder dự án (ví dụ: `arduino-robot-thcs/du-an-1-*/textbook.md`)
- **Khuyến khích:** File syllabus (ở root khoá: `[tên-khoá]/syllabus.md`)

## Quy trình thực hiện

### Bước 1: Đọc syllabus
Lấy thông tin tổng quan: tên khoá, đối tượng, mục tiêu cuối khoá.

### Bước 2: Đọc tất cả file giáo trình
Đọc lần lượt các file trong `textbook/`, sắp xếp theo thứ tự dự án.

### Bước 3: Tổng hợp
Gộp thành 1 file với cấu trúc:

```markdown
# Giáo trình: [Tên khoá học]

**Đối tượng:** ...
**Số buổi:** ...
**Mục tiêu cuối khoá:** ...

---

## Mục lục

1. [Dự án 1: Tên] .............. trang X
2. [Dự án 2: Tên] .............. trang X
...

---

## Giới thiệu khoá học

Tổng quan ngắn gọn về khoá học, mục tiêu, phương pháp học tập (EDP), và cách sử dụng giáo trình này.

---

# Phần 1: [Tên dự án 1]

(Nội dung giáo trình dự án 1 — giữ nguyên, chỉ điều chỉnh heading level)

---

# Phần 2: [Tên dự án 2]

(Nội dung giáo trình dự án 2)

---

(Tiếp tục cho các dự án còn lại)

---

## Phụ lục

### Bảng thuật ngữ tổng hợp
(Gộp tất cả thuật ngữ từ các dự án, sắp xếp A-Z, loại bỏ trùng lặp)

### Danh sách vật tư tổng hợp
(Gộp tất cả vật tư từ các dự án, ghi rõ dự án nào cần gì)
```

### Bước 4: Lưu file

## Nguyên tắc tổng hợp

- Giữ nguyên nội dung từng dự án, không cắt bớt.
- Điều chỉnh heading level cho nhất quán (mỗi dự án là heading 1, các section bên trong giảm 1 level).
- Thêm phần giới thiệu khoá học ở đầu.
- Tổng hợp thuật ngữ và vật tư vào phụ lục.
- Thêm ghi chú kết nối giữa các dự án (ví dụ: "Kiến thức về LED ở Dự án 1 sẽ được sử dụng lại ở Dự án 3").

## Lưu file

- Lưu ở root của khoá: `[tên-khoá]/textbook-tong-hop.md`
- Ví dụ: `arduino-robot-thcs/textbook-tong-hop.md`
