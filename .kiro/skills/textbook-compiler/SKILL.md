---
name: textbook-compiler
description: >
  Tổng hợp nhiều file giáo trình (textbook) thành 1 file duy nhất.
  Dùng khi người dùng muốn gộp tất cả giáo trình của các dự án thành 1 tài liệu hoàn chỉnh.
  Kể cả khi người dùng nói "gộp giáo trình", "tổng hợp textbook", "merge tài liệu học" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "2.0"
---

## Khả năng

Tạo 1 file textbook tổng hợp cho toàn khoá học, rồi lần lượt copy nội dung textbook của từng dự án vào file đó. Không tự ý thay đổi nội dung giáo trình từng dự án.

## Khi nào dùng

- Người dùng muốn gộp / tổng hợp các file giáo trình thành 1 file.
- Người dùng nói "gộp giáo trình", "tổng hợp textbook", "merge tài liệu".
- Sau khi đã viết xong giáo trình cho tất cả dự án.

## Input

- Bắt buộc: Đường dẫn folder gốc của khoá học (chứa các subfolder dự án có file textbook).
- Khuyến khích: File syllabus (ở root khoá) để lấy thông tin tổng quan cho phần header.

## Quy trình thực hiện

### Bước 1: Tạo file textbook tổng hợp

Tạo file mới tại root khoá học với tên `textbook-[tên-khoá-kebab-case].md`. Lấy tên khoá từ tên folder gốc.

Ví dụ:
- Folder `arduino-robot-thcs/` → file `textbook-arduino-robot-thcs.md`.
- Folder `train-the-trainer-nguyen-ly-ai/` → file `textbook-train-the-trainer-nguyen-ly-ai.md`.

Ghi vào file phần header gồm:
- Tiêu đề khoá học.
- Đối tượng, số buổi, mục tiêu cuối khoá (lấy từ syllabus).
- Mục lục liệt kê tên các dự án.
- Phần giới thiệu khoá học ngắn gọn.

### Bước 2: Liệt kê các file textbook của từng dự án

Liệt kê các subfolder dự án theo thứ tự (du-an-1, du-an-2, ...).

Với mỗi subfolder, xác định file textbook chính (ví dụ: `du-an-1-*/textbook-*.md`).

### Bước 3: Copy nội dung từng dự án vào file tổng hợp

Lặp qua danh sách dự án theo thứ tự. Với mỗi dự án:

3.1. Append vào file tổng hợp dấu phân cách `---` và heading dự án (ví dụ: `# Phần 1: [Tên dự án]`) bằng tool ghi file thông thường.

3.2. Tạo file tạm với path ảnh đã được sửa sẵn cho dự án đó:

```bash
sed 's|assets/|du-an-X-tên-dự-án/assets/|g' du-an-X-tên-dự-án/textbook-*.md > /tmp/du-an-X-fixed.md
```

Lệnh `sed` này đọc file textbook gốc, thay tất cả `assets/` thành `du-an-X-tên-dự-án/assets/`, ghi ra file tạm `/tmp/du-an-X-fixed.md`. File gốc không bị sửa.

3.3. Append file tạm vào file tổng hợp, rồi xoá file tạm:

```bash
cat /tmp/du-an-X-fixed.md >> [tên-khoá]/textbook-[tên-khoá-kebab-case].md
rm /tmp/du-an-X-fixed.md
```

Cách này an toàn vì sed chỉ chạy trên file tạm chứa duy nhất 1 dự án, không ảnh hưởng các dự án khác đã được append.

3.4. Quy tắc: KHÔNG sửa heading level — copy nguyên xi. Người dùng sẽ tự xem nếu có chỗ heading bị trùng.

### Bước 4: Thêm phụ lục (tuỳ chọn)

Sau khi copy xong tất cả dự án, append phần phụ lục:
- Danh sách vật tư tổng hợp (gộp từ tất cả dự án).
- Bảng thuật ngữ tổng hợp (gộp từ tất cả dự án, sắp xếp A-Z, loại bỏ trùng lặp).

### Bước 5: Báo cáo cho user

Thông báo:
- Đường dẫn file đã tạo.
- Số dự án đã gộp.
- Tổng số dòng.

## Cấu trúc file textbook tổng hợp

```markdown
# Giáo trình: [Tên khoá học]

Đối tượng: ...
Số buổi: ...
Mục tiêu cuối khoá: ...

---

## Mục lục

1. Phần 1: [Tên dự án 1]
2. Phần 2: [Tên dự án 2]
...

---

## Giới thiệu khoá học

Tổng quan ngắn gọn về khoá học, mục tiêu, phương pháp học tập, cách sử dụng giáo trình.

---

# Phần 1: [Tên dự án 1]

(Nội dung textbook dự án 1 — copy nguyên xi, chỉ sửa path ảnh và heading level)

---

# Phần 2: [Tên dự án 2]

(Nội dung textbook dự án 2 — copy nguyên xi)

---

(Tiếp tục cho các dự án còn lại)

---

## Phụ lục

### Vật tư tổng hợp
(Gộp từ các dự án)

### Bảng thuật ngữ tổng hợp
(Gộp từ các dự án, A-Z, không trùng)
```

## Nguyên tắc bắt buộc

- KHÔNG sửa nội dung giáo trình từng dự án — chỉ copy nguyên xi.
- Chỉ sửa: heading level (để nhất quán) và path ảnh (để link không vỡ).
- Giữ nguyên thứ tự dự án theo thứ tự đánh số subfolder.
- Nếu textbook một dự án quá dài (>500 dòng), vẫn copy đầy đủ — không cắt bớt.

## Lưu file

- Lưu ở root khoá học: `[tên-khoá]/textbook-[tên-khoá-kebab-case].md`.
- Ví dụ: `train-the-trainer-nguyen-ly-ai/textbook-train-the-trainer-nguyen-ly-ai.md`.
- Nếu file đã tồn tại, hỏi user trước khi ghi đè.
