---
name: lesson-plan-compiler
description: >
  Tổng hợp nhiều file giáo án (lesson plan) thành 1 file duy nhất.
  Dùng khi người dùng muốn gộp tất cả giáo án của các dự án thành 1 tài liệu hoàn chỉnh cho giáo viên.
  Kể cả khi người dùng nói "gộp giáo án", "tổng hợp lesson plan", "merge kế hoạch dạy" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "2.0"
---

## Khả năng

Đọc tất cả file giáo án riêng lẻ trong các subfolder dự án và tổng hợp thành 1 file markdown duy nhất, theo đúng cấu trúc template giáo án EDP chuẩn.

## Khi nào dùng

- Người dùng muốn gộp / tổng hợp các file giáo án thành 1 file
- Người dùng nói "gộp giáo án", "tổng hợp lesson plan", "merge kế hoạch dạy"
- Sau khi đã viết xong giáo án cho tất cả dự án

## Input

- **Bắt buộc:** Các file giáo án `lesson-plan-*.md` trong các subfolder dự án (ví dụ: `arduino-robot-thcs/du-an-1-*/lesson-plan-*.md`)
- **Khuyến khích:** File syllabus (ở root khoá: `[tên-khoá]/syllabus.md`)

## Template giáo án chuẩn

Mỗi giáo án trong file tổng hợp PHẢI tuân theo cấu trúc template EDP THCS/THPT tại file:
`[Template] Giáo án EDP THCS THPT.md`

### Cấu trúc template cho 1 dự án (BUỔI 1)

```markdown
# TÊN BÀI

Môn: …
Khối/Module: …
Thời lượng: … tiết

## Mô tả bài học

Trong bài học này, học sinh sẽ tìm hiểu kiến thức về …(các kiến thức trọng tâm) và vận dụng để … *(tên sản phẩm)*.

## I. Yêu cầu cần đạt

### **1\. Kiến thức**
Thực hiện bài học này học sinh sẽ khám phá các kiến thức:
- (danh từ) …

### **2\. Năng lực**
Thực hiện bài học này học sinh sẽ rèn luyện và phát triển các năng lực với các biểu hiện:
- Năng lực đặc thù
  * (động từ) …
- Năng lực chung
  * …

### **3\. Phẩm chất**
Bài học này tạo điều kiện để học sinh phát triển những phẩm chất với các biểu hiện:
- …

## II. Sản phẩm
(Mô hình/Game/Video/Bản thiết kế/…) + tên sản phẩm:
- …

## III. Thiết bị dạy học và học liệu

Các nguyên vật liệu cần chuẩn bị cho một sản phẩm:

| Nguyên vật liệu | Đơn vị | Số lượng |
| :---- | :---: | :---: |
| … | … | … |

Các công cụ và thiết bị cần chuẩn bị cho một nhóm:

| Công cụ và thiết bị | Đơn vị | Số lượng |
| :---- | :---: | :---: |
| … | … | … |

Các tài liệu, phiếu học tập:

| Đường dẫn tài liệu, phiếu học tập, video,... |
| :---- |
| … |

## IV. Tiến trình dạy học

### **1\. Xác định vấn đề (...')**
#### **1.1. Mục tiêu**
- Xác định được vấn đề/nhiệm vụ học tập và yêu cầu sản phẩm.
- Đặt được các câu hỏi để làm rõ vấn đề (nếu có).

#### **1.2. Tổ chức thực hiện**
**1.2.1. Khởi động**
- Giáo viên (GV): …
- Học sinh (HS): …

**1.2.2. Giao nhiệm vụ**
…

### **2\. Nghiên cứu kiến thức nền (...')**
#### **2.1. Mục tiêu**
…
#### **2.2. Tổ chức thực hiện**
**2.2.1. Tìm hiểu + kiến thức 1**
…
**2.2.2. Tìm hiểu + kiến thức 2**
…

### **3\. Đề xuất, lựa chọn giải pháp và lên kế hoạch (...')**
#### **3.1. Mục tiêu**
- Đề xuất và phác thảo được các ý tưởng/giải pháp về…
- Lên được kế hoạch để chế tạo…

#### **3.2. Tổ chức thực hiện**
…

### **4\. Chế tạo mẫu, thử nghiệm và đánh giá (...')**
#### **4.1. Mục tiêu**
- Chế tạo/lập trình/thiết kế được…

#### **4.2. Tổ chức thực hiện**
…

### **5\. Chia sẻ, thảo luận và điều chỉnh (...')**
#### **5.1. Mục tiêu**
- Thuyết trình được về mô hình/dự án…
- Nhận xét, góp ý được về mô hình/dự án… của nhóm bạn.
- Đề xuất được các định hướng cải tiến mô hình/dự án…

#### **5.2. Tổ chức thực hiện**
…

### **6\. Tổng kết (...')**
…
```

### Cấu trúc template cho dự án 2 buổi (BUỔI 2)

Nếu dự án kéo dài 2 buổi, sau phần Buổi 1 sẽ có thêm:

```markdown
## HẾT BUỔI 1

## BUỔI 2

### **1\. Ôn tập (...')**
…

### **2\. Chế tạo mẫu, thử nghiệm và đánh giá (...')**
#### **2.1. Mục tiêu**
…
#### **2.2. Tổ chức thực hiện**
…

### **3\. Chia sẻ, thảo luận và điều chỉnh (...')**
#### **3.1. Mục tiêu**
- Thuyết trình được về mô hình/dự án…
- Nhận xét, góp ý được về mô hình/dự án… của nhóm bạn
- Đề xuất được các định hướng cải tiến mô hình/dự án…

#### **3.2. Tổ chức thực hiện**
…

### **4\. Tổng kết (...')**
…
```

### Phần cuối mỗi giáo án

Mỗi giáo án kết thúc với 2 bảng:

```markdown
## Thông tin tài liệu

| Được soạn ngày: |  | Bởi: |  |
| :---- | :---- | :---- | :---- |
| Được review ngày: |  | Bởi: |  |
| Được hiệu chỉnh ngày: |  | Bởi: |  |

## Phân bổ các hoạt động

| Nội dung | Chương trình 2T |  | Chương trình 1T |  |
| :---: | :---: | :---: | :---: | :---: |
|  | **Buổi** | **Thời lượng (phút)** | **Buổi** | **Thời lượng (phút)** |
|  |  |  |  |  |
```

## Quy trình thực hiện

### Bước 1: Đọc syllabus
Lấy thông tin tổng quan: tên khoá, đối tượng, số buổi, danh sách dự án.

### Bước 2: Đọc tất cả file giáo án
Đọc lần lượt các file `lesson-plan-*.md` trong các subfolder dự án, sắp xếp theo thứ tự dự án.

### Bước 3: Tổng hợp

Cấu trúc file tổng hợp:

```markdown
# Giáo án tổng hợp: [Tên khoá học]

**Đối tượng:** ...
**Số buổi:** ...
**Mục tiêu cuối khoá:** ...

---

## Mục lục

| Buổi | Dự án | Trang |
|------|-------|-------|
| 1 | [Tên dự án 1] | ... |
| 2 | [Tên dự án 2] | ... |
| ... | ... | ... |

---

## Hướng dẫn sử dụng giáo án

Giới thiệu ngắn cho giáo viên:
- Phương pháp EDP là gì, tại sao dùng
- Cách đọc giáo án (cấu trúc theo template chuẩn EDP THCS/THPT)
- Nguyên tắc linh hoạt: điều chỉnh thời gian theo tình hình thực tế
- Cách sử dụng phần "Thông tin tài liệu" và "Phân bổ các hoạt động"

---

## Tổng quan vật tư toàn khoá

| Vật tư / Công cụ | Dự án sử dụng | Số lượng/nhóm |
|-------------------|----------------|---------------|
| ... | DA 1, DA 2, ... | ... |

---

# Buổi 1 — Dự án 1: [Tên]

(Nội dung giáo án dự án 1 — giữ nguyên theo template EDP)

---

# Buổi 2 — Dự án 2: [Tên]

(Nội dung giáo án dự án 2 — giữ nguyên theo template EDP)

---

(Tiếp tục cho các buổi còn lại)

---

## Phụ lục

### Mẫu phiếu EDP
(Tổng hợp các template phiếu cho từng bước EDP)

### Rubric đánh giá tổng hợp
(Gộp rubric từ các dự án)

### Checklist chuẩn bị trước khoá học
(Danh sách tất cả những gì GV cần chuẩn bị)
```

### Bước 4: Lưu file

## Nguyên tắc tổng hợp

- **Giữ nguyên cấu trúc template EDP** cho từng giáo án. Không thay đổi heading, thứ tự mục, hay format bảng.
- Mỗi giáo án phải có đầy đủ các phần theo template:
  - Mô tả bài học
  - I. Yêu cầu cần đạt (Kiến thức, Năng lực, Phẩm chất)
  - II. Sản phẩm
  - III. Thiết bị dạy học và học liệu (3 bảng: nguyên vật liệu, công cụ, tài liệu)
  - IV. Tiến trình dạy học (6 bước EDP)
  - Thông tin tài liệu
  - Phân bổ các hoạt động
- Giữ nguyên nội dung từng giáo án, không cắt bớt.
- Thêm phần hướng dẫn sử dụng ở đầu cho GV mới.
- Tổng hợp vật tư toàn khoá để GV chuẩn bị 1 lần.
- Đánh số buổi rõ ràng (dự án 2 buổi thì ghi Buổi 5a, 5b).
- Thêm phụ lục với các mẫu phiếu và rubric.
- Nếu giáo án gốc chưa đúng template, **chuyển đổi** cho khớp template khi tổng hợp.

## Lưu file

- Lưu ở root của khoá: `[tên-khoá]/lesson-plan-tong-hop.md`
- Ví dụ: `arduino-robot-thcs/lesson-plan-tong-hop.md`
