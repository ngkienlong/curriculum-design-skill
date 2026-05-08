---
name: textbook-writer
description: >
  Viết giáo trình (textbook) chi tiết cho từng dự án trong syllabus STEM/AI.
  Dùng khi người dùng muốn viết giáo trình, tài liệu học, nội dung bài học,
  hoặc tài liệu tham khảo cho học sinh dựa trên syllabus đã có.
  Kể cả khi người dùng nói "viết nội dung cho dự án X" hoặc "soạn tài liệu học" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "2.1"
---

## Khả năng

Viết giáo trình chi tiết cho từng dự án trong syllabus STEM/AI theo quy trình human-in-the-loop: AI đề xuất khung sườn → user duyệt → AI viết từng phần → user duyệt từng phần. Mỗi dự án tạo ra 1 file giáo trình riêng.

## Khi nào dùng

- Người dùng muốn viết giáo trình / textbook cho các dự án trong syllabus.
- Người dùng đã có syllabus và muốn tạo nội dung chi tiết.
- Người dùng nói "viết giáo trình", "soạn tài liệu học", "viết textbook".

## Input

- Bắt buộc: File syllabus (ở root khoá: `[tên-khoá]/syllabus-[tên-khoá].md`).
- Tuỳ chọn: Dự án cụ thể muốn viết (nếu không chỉ định → hỏi user chọn dự án nào trước).

## Nguyên tắc xuyên suốt

- AI không được tự động viết hết toàn bộ textbook trong một lần. Phải đi qua các điểm kiểm soát (human in the loop).
- Mỗi dự án xử lý độc lập. Không xử lý song song nhiều dự án.
- Sau mỗi điểm kiểm soát, chỉ tiếp tục khi user đã duyệt rõ ràng.

## Quy trình thực hiện

### Bước 1: Đọc syllabus và xác nhận dự án cần viết

Đọc file syllabus để hiểu:
- Tổng quan khoá học, đối tượng, số buổi.
- Danh sách dự án, thứ tự, sản phẩm đầu ra của từng dự án.
- Kiến thức cốt lõi và mục tiêu Bloom của dự án sẽ viết.

Nếu user chưa chỉ định dự án nào → liệt kê các dự án trong syllabus và hỏi user muốn bắt đầu từ dự án nào.

### Bước 2: Đề xuất khung sườn textbook (đợi user duyệt)

Trước khi viết bất cứ nội dung nào, AI đề xuất khung sườn của textbook cho dự án đã chọn. Khung sườn gồm:

- Các header có đánh số (1, 2, 3... và các header con 1.1, 1.2...).
- Mỗi header có một dòng mô tả ngắn về nội dung sẽ viết trong phần đó.
- Hình ảnh dự kiến: ở những phần cần hình ảnh minh hoạ, ghi rõ "[Hình dự kiến: mô tả ngắn gọn về hình]".

Trình bày khung sườn dưới dạng outline (chưa tạo file). Ví dụ:

```
# [Tên dự án]

## 1. Giới thiệu dự án
### 1.1 Bối cảnh thực tế
  → Mô tả vấn đề thực tế mà dự án giải quyết.
  [Hình dự kiến: ảnh minh hoạ bối cảnh thực tế của vấn đề]
### 1.2 Câu hỏi dẫn dắt
  → Câu hỏi từ syllabus.
### 1.3 Mục tiêu học tập
  → Liệt kê mục tiêu theo thang Bloom, lấy từ syllabus
### 1.4 Sản phẩm đầu ra
  → Mô tả cụ thể sản phẩm học sinh sẽ hoàn thành, lấy từ syllabus
  [Hình dự kiến: ảnh phác hoạ sản phẩm cuối]

## 2. Kiến thức nền tảng
### 2.1 [Chủ đề 1]
  → ...
  [Hình dự kiến: sơ đồ giải thích nguyên lý của ...]
### 2.2 [Chủ đề 2]
  → ...

## 3. Hướng dẫn thực hành
### 3.1 Vật tư và công cụ
  → Bảng liệt kê vật tư.
### 3.2 Sơ đồ kết nối
  [Hình dự kiến: sơ đồ kết nối mạch / wiring diagram]
### 3.3 Hướng dẫn từng bước
  → ...

## 4. Nâng cao
  → Phân hoá cho học sinh nhanh.

## 5. Câu hỏi ôn tập
  → 3-5 câu hỏi kiểm tra hiểu biết.

## 6. Thuật ngữ
  → Bảng thuật ngữ kèm giải thích.
```

Đợi user duyệt. User có thể:
- Duyệt nguyên trạng → chuyển sang Bước 3.
- Yêu cầu thêm/bớt/sắp xếp lại header.
- Yêu cầu thay đổi hình ảnh dự kiến (thêm hình, bỏ hình, đổi mô tả hình).

Chỉ khi user duyệt khung sườn → AI tạo file textbook (theo quy tắc lưu file ở cuối) và ghi khung sườn này vào file dưới dạng các header rỗng (chưa có nội dung), kèm placeholder `[Hình dự kiến: ...]` ở những vị trí đã thống nhất.

### Bước 3: Viết từng phần theo khung sườn (đợi user duyệt sau mỗi phần)

Sau khi file đã có khung sườn, AI viết nội dung text từng phần một, theo thứ tự từ trên xuống. Ở bước này chỉ tập trung viết text, chưa tạo ảnh — các placeholder `[Hình dự kiến: ...]` giữ nguyên.

Quy trình cho mỗi phần:

3.1. Lấy phần tiếp theo chưa có nội dung (ví dụ: bắt đầu từ "1.1 Bối cảnh thực tế").

3.2. Viết nội dung chi tiết cho phần đó:
- Ngôn ngữ phù hợp với độ tuổi đối tượng (đã ghi trong syllabus).
- Sinh động, gần gũi, có ví dụ thực tế.
- Code mẫu (nếu có) phải chạy được, đúng cú pháp ngôn ngữ đang dạy.
- Bảng/checklist khi cần.
- Giữ nguyên placeholder `[Hình dự kiến: ...]` — chưa tạo ảnh ở bước này.

3.3. Ghi nội dung vào đúng vị trí trong file textbook (giữ nguyên các phần khác chưa viết, giữ nguyên placeholder ảnh).

3.4. Trình bày phần vừa viết cho user và đợi duyệt:
- User duyệt → chuyển sang phần tiếp theo (quay lại 3.1).
- User yêu cầu chỉnh → sửa lại phần đó rồi đợi duyệt lại.

3.5. Lặp lại cho đến khi tất cả các phần trong khung sườn đều có nội dung text.

### Bước 4: Tạo ảnh đồng loạt

Sau khi toàn bộ nội dung text đã được viết và duyệt xong, AI quét lại file textbook để tìm tất cả placeholder `[Hình dự kiến: ...]` còn lại và tạo ảnh đồng loạt.

Quy trình:

4.1. Liệt kê tất cả placeholder ảnh còn trong file, trình bày cho user xác nhận danh sách ảnh cần tạo.

4.2. Tạo ảnh lần lượt:
- Với sơ đồ mạch điện, sơ đồ kết nối → dùng skill `technical-diagram`.
- Với hình minh hoạ khái niệm, infographic → dùng skill `create-svg` hoặc `create-image`.
- Lưu ảnh vào subfolder: `[tên-khoá]/[du-an-X-tên]/assets/`.

4.3. Thay từng placeholder trong file textbook bằng `![alt text](assets/tên-file.svg)` hoặc `.png`.

4.4. Trình bày kết quả cho user duyệt. User có thể yêu cầu tạo lại ảnh nào chưa đạt.

### Bước 5: Tổng kết

Sau khi user duyệt toàn bộ ảnh:
- Đọc lại toàn bộ file textbook để kiểm tra tính nhất quán (giọng văn, đánh số, format).
- Trình bày tóm tắt cho user: số phần đã viết, số ảnh đã tạo, đường dẫn file.
- Hỏi user: muốn viết textbook cho dự án tiếp theo không, hay dừng ở đây.

Nếu user muốn viết tiếp dự án khác → quay lại Bước 1 với dự án mới.

## Lưu file

- Thư mục: subfolder của dự án trong khoá học.
- Tên file: `textbook-[slug-dự-án].md`.
- Quy tắc đặt tên: slug trong tên file phải trùng với slug trong tên folder.
  - Folder `du-an-1-den-sos` → file `textbook-den-sos.md`.
  - Folder `du-an-3-cam-bien-lui-xe` → file `textbook-cam-bien-lui-xe.md`.
- Ví dụ đầy đủ: `arduino-robot-thcs/du-an-1-den-sos/textbook-den-sos.md`.
- Ảnh đi kèm: `arduino-robot-thcs/du-an-1-den-sos/assets/[tên-ảnh].svg` hoặc `.png`.

## Cấu trúc textbook hoàn chỉnh

```markdown
# [Tên dự án]

Số buổi: [Số buổi] x [X phút/buổi]

---

## 1. Giới thiệu dự án

### 1.1 Bối cảnh thực tế
Mô tả vấn đề thực tế mà dự án giải quyết. Viết sinh động, gần gũi với học sinh.

![Bối cảnh thực tế](assets/boi-canh.svg)

### 1.2 Câu hỏi dẫn dắt
"[Câu hỏi từ syllabus]"

### 1.3 Mục tiêu học tập
- [ ] Mục tiêu 1 (theo thang Bloom).
- [ ] Mục tiêu 2.

### 1.4 Sản phẩm đầu ra
Mô tả cụ thể sản phẩm học sinh sẽ hoàn thành.

---

## 2. Kiến thức nền tảng

### 2.1 [Chủ đề 1]
Giải thích lý thuyết cần thiết. Dùng hình ảnh minh hoạ, ví dụ cụ thể.

![Sơ đồ nguyên lý](assets/nguyen-ly.svg)

### 2.2 [Chủ đề 2]
...

> Mẹo: [Tip hữu ích cho học sinh].

> Lưu ý an toàn: [Nếu có liên quan đến an toàn điện, hoá chất, v.v.].

---

## 3. Hướng dẫn thực hành

### 3.1 Vật tư và công cụ cần chuẩn bị

| STT | Vật tư / Công cụ | Số lượng | Ghi chú |
|-----|-------------------|----------|---------|
| 1 | ... | ... | ... |

### 3.2 Sơ đồ kết nối

![Sơ đồ kết nối](assets/wiring.svg)

### 3.3 Hướng dẫn từng bước

Bước 1: [Tên bước]
- Mô tả chi tiết.
- Code mẫu (nếu có):
  ```[ngôn ngữ]
  // code ở đây
  ```
- Kết quả mong đợi: ...

Bước 2: [Tên bước]
...

---

## 4. Nâng cao

Mô tả mở rộng cho học sinh nhanh. Gợi ý cách thực hiện.

---

## 5. Câu hỏi ôn tập

1. [Câu hỏi kiểm tra hiểu biết].
2. [Câu hỏi áp dụng].
3. [Câu hỏi phân tích / sáng tạo].

---

## 6. Thuật ngữ

| Thuật ngữ | Giải thích |
|-----------|------------|
| ... | ... |
```

## Tóm tắt vòng human-in-the-loop

```
Đọc syllabus + chọn dự án
        ↓
AI đề xuất khung sườn (header + hình dự kiến)  →  [User duyệt]
        ↓
AI tạo file textbook và ghi khung sườn rỗng vào file
        ↓
  Lặp cho từng phần trong khung sườn:
  AI viết nội dung text (giữ placeholder ảnh)  →  AI cập nhật file  →  [User duyệt]
        ↓
AI tạo ảnh đồng loạt cho tất cả placeholder  →  [User duyệt]
        ↓
AI tổng kết, hỏi dự án tiếp theo
```
