---
name: syllabus-design
description: >
  Thiết kế syllabus (khung chương trình) STEM/AI theo phương pháp Project-Based Learning.
  Dùng khi người dùng muốn thiết kế syllabus, xây dựng chương trình học, lên khung khoá học, hoặc brainstorm dự án cho khoá STEM/AI. Kể cả khi người dùng chỉ nói "tôi muốn dạy X" hoặc "lên chương trình cho Y buổi" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "2.1"
---

## Khả năng

Thiết kế syllabus STEM/AI đáp ứng mục tiêu cuối khoá, theo phương pháp backward design + EDP.

## Khi nào dùng

- Người dùng muốn thiết kế syllabus / khung chương trình
- Người dùng cung cấp mục tiêu cuối khoá và muốn chia thành các dự án
- Người dùng muốn brainstorm dự án cho khoá học STEM/AI

## Input từ người dùng

- **Bắt buộc:** Mục tiêu cuối khoá
- **Tuỳ chọn:** Độ tuổi (TH / THCS / THPT), số buổi học, chủ đề cụ thể

## Quy trình thực hiện

### Bước 1: Thu thập tài liệu kiến thức nền (tuỳ chọn)
Trước khi làm bất cứ điều gì, agent hỏi người dùng:

> "Bạn có muốn cung cấp tài liệu kiến thức nền cho khoá học này không? Ví dụ: file PDF, file markdown, hoặc link trang web. Agent sẽ đọc kỹ các tài liệu này trước khi thiết kế chương trình."

Người dùng có thể:
- Cung cấp một hoặc nhiều file (kéo thả vào chat hoặc dùng #File)
- Cung cấp một hoặc nhiều link URL
- Bỏ qua bước này (trả lời "không" hoặc "bỏ qua")

Nếu người dùng cung cấp tài liệu:
- Đọc toàn bộ nội dung từng file và từng link được cung cấp.
- Tóm tắt ngắn gọn những gì đã đọc được: các chủ đề chính, công cụ/nền tảng được đề cập, mức độ phức tạp, đối tượng hướng đến.
- Xác nhận với người dùng: "Mình đã đọc xong tài liệu. Đây là những điểm chính mình ghi nhận: [tóm tắt]. Mình sẽ dùng những thông tin này để thiết kế chương trình phù hợp."
- Chỉ khi người dùng xác nhận tóm tắt đúng → mới chuyển sang Bước 2.

Nếu người dùng bỏ qua → chuyển thẳng sang Bước 2 mà không cần tóm tắt.

Lưu ý: Toàn bộ nội dung tài liệu đã đọc phải được dùng làm nền tảng cho tất cả các bước tiếp theo — đặc biệt khi đề xuất dự án, xác định kiến thức cốt lõi và viết mục tiêu theo thang Bloom.

### Bước 2: Làm rõ sản phẩm cuối khoá kỳ vọng
Người dùng có thể đưa mục tiêu cuối khoá ở dạng ý tưởng sơ khai (ví dụ: "dạy Arduino cho THCS", "học sinh làm được robot"). Trước khi chia nhỏ mục tiêu, cần làm rõ **sản phẩm cuối khoá kỳ vọng** — tức học sinh có thể tự tay làm được gì sau khi hoàn thành khoá học.

Từ input của người dùng, viết một đoạn mô tả ngắn gọn nhưng cụ thể về sản phẩm cuối khoá kỳ vọng. Ví dụ:
- Input sơ khai: "dạy Arduino cho THCS"
- Mô tả sản phẩm cuối khoá: "Học sinh tự lắp ráp và lập trình một xe robot 2 bánh có thể di chuyển theo lộ trình định sẵn và tránh vật cản bằng cảm biến siêu âm."

Trình bày cho người dùng và **đợi người dùng duyệt**. Người dùng có thể:
- Duyệt nguyên trạng
- Yêu cầu điều chỉnh mức độ kỳ vọng (đơn giản hơn / phức tạp hơn)

Sau khi người dùng duyệt → **tạo file** `final-project-[tên-dự-án-kebab-case].md` trong folder gốc của khoá học, ghi lại mô tả sản phẩm cuối khoá đã được duyệt. Ví dụ: `arduino-robot-thcs/final-project-xe-robot-tham-hiem.md`.

Chỉ khi đã lưu file xong → mới chuyển sang Bước 3.

### Bước 3: Chia nhỏ mục tiêu
Từ mục tiêu cuối khoá đã được duyệt ở Bước 2 → chia thành các nhóm mục tiêu nhỏ, sắp xếp theo trình tự logic (kiến thức nền trước, nâng cao sau).

Trình bày bảng nhóm mục tiêu với đúng 5 cột sau:

| # | Nhóm mục tiêu | Kiến thức cốt lõi | Mục tiêu theo thang Bloom | Số buổi dự kiến |

- **Kiến thức cốt lõi:** Liệt kê các khái niệm, kỹ thuật, công cụ chính mà nhóm mục tiêu này bao gồm (ví dụ: board, breadboard, LED, `digitalWrite()`, `delay()`).
- **Mục tiêu theo thang Bloom:** Dùng **động từ hành động đo lường được**, không viết chung chung. Ví dụ:
  - ✅ "Nhận biết và gọi tên các thành phần của Arduino (board, breadboard, LED, điện trở)"
  - ✅ "Kết nối mạch LED trên breadboard theo sơ đồ cho trước"
  - ✅ "Viết chương trình Arduino sử dụng `digitalWrite()` và `delay()` để điều khiển LED"
  - ❌ Không dùng động từ "Nhớ" vì không đo lường được
  - ❌ Không dùng động từ "Hiểu" vì không đo lường được

Trình bày danh sách cho người dùng và **đợi người dùng duyệt**. Người dùng có thể:
- Duyệt nguyên trạng
- Yêu cầu thêm/bớt/sắp xếp lại nhóm mục tiêu
- Điều chỉnh nội dung từng nhóm

Sau khi được duyệt → **tạo file `syllabus-[tên-khoá-kebab-case].md`** với phần header (tên khoá, đối tượng, số buổi, mục tiêu cuối khoá) và bảng nhóm mục tiêu đã duyệt (5 cột). File này sẽ được bổ sung dần ở các bước sau.

### Bước 4: Brainstorm dự án — lần lượt từng nhóm mục tiêu
Thực hiện **tuần tự** cho từng nhóm mục tiêu, không brainstorm tất cả cùng lúc:

4.1. Lấy nhóm mục tiêu tiếp theo chưa có dự án
4.2. Đề xuất 2-3 dự án thú vị, gần gũi thực tế cho nhóm mục tiêu đó. Trình bày theo format : Cấu trúc "tổng quan dự án" như định nghĩa bên dưới
4.3. **Đợi người dùng chọn 1 dự án** (hoặc yêu cầu đề xuất thay thế)
4.4. Dự án được chọn → tạo **rubric đánh giá riêng** cho dự án đó (đặc biệt tiêu chí "Sản phẩm" và "Code" phải cụ thể theo dự án) → **cập nhật bảng nhóm mục tiêu** trong file syllabus: thêm cột "Buổi", "Dự án" và "Sản phẩm đầu ra" vào hàng tương ứng → **ghi dự án + rubric vào file syllabus**
4.5. Quay lại bước 4.1 cho nhóm mục tiêu tiếp theo. Lặp lại cho đến khi tất cả nhóm mục tiêu đều có dự án.

Khi tất cả dự án đã được chọn, bảng nhóm mục tiêu sẽ có đủ 8 cột:

| # | Buổi | Dự án | Sản phẩm đầu ra | Nhóm mục tiêu | Kiến thức cốt lõi | Mục tiêu theo thang Bloom | Số buổi |

Bảng này vừa là bảng mục tiêu vừa là bảng tổng quan khoá học — **không cần bảng Tổng quan riêng**.

### Bước 5: Hoàn thiện syllabus
Sau khi tất cả dự án được chọn và ghi vào file:
- Bổ sung phần "Vật tư và công cụ cần thiết" cho toàn khoá học
- Bổ sung rubric chung cho các tiêu chí xuyên suốt (Quy trình EDP, Làm việc nhóm, Trình bày) — các tiêu chí "Sản phẩm" và "Code" đã được viết riêng trong từng dự án ở bước 2
- Bổ sung Peer feedback (nếu cần)
- Tạo các subfolder cho từng dự án
- Trình bày syllabus hoàn chỉnh cho người dùng duyệt lần cuối

## Cấu trúc "tổng quan dự án"

Khi đề xuất ý tưởng dự án (bước 2.2), trình bày theo format này:

```
Dự án [số]: [Tên] — số buổi
  **Câu hỏi dẫn dắt:** "..."

  **Mục tiêu (STEM/AI):**
  - ...

  **Sản phẩm đầu ra:** ...

  **Phần cứng:** Tên | số lượng
  **Phần mềm:** ...

  **Phân hoá:**
  - Yêu cầu cơ bản: ...
  - Yêu cầu nâng cao: ...
```

Sau khi người dùng chọn dự án (bước 4.4), bổ sung thêm rubric trước khi ghi vào file:

```
  **Rubric dự án:**

  | Tiêu chí | Chưa đạt (1) | Đạt (2) | Tốt (3) | Xuất sắc (4) |
  |----------|---------------|---------|---------|---------------|
  | Sản phẩm | [cụ thể theo dự án] | ... | ... | ... |
  | Code | [cụ thể theo dự án] | ... | ... | ... |
```

Tiêu chí "Sản phẩm" và "Code" phải **cụ thể theo từng dự án**, không dùng chung. Ví dụ:
- Dự án đèn SOS: Sản phẩm = "LED không phát đúng SOS" → "Phát SOS nhưng timing sai" → "Phát SOS đúng timing" → "Phát SOS + thêm ký tự Morse khác"
- Dự án xe robot: Sản phẩm = "Xe không chạy" → "Xe chạy được 1-2 hướng" → "Xe chạy đủ 4 hướng" → "Xe chạy 4 hướng + điều chỉnh tốc độ"

## Cấu trúc "syllabus hoàn chỉnh"

```markdown
# Syllabus: [Tên khoá học]

**Đối tượng:** ...
**Số buổi:** ...
**Mục tiêu cuối khoá:** ...

---

## Tổng quan khoá học & Nhóm mục tiêu

| # | Buổi | Dự án | Sản phẩm đầu ra | Nhóm mục tiêu | Kiến thức cốt lõi | Mục tiêu theo thang Bloom | Số buổi |
|---|------|-------|-----------------|---------------|-------------------|--------------------------|---------|
| ... | ... | ... | ... | ... | ... | ... | ... |

---

## Vật tư và công cụ cần thiết cho toàn khoá học

**Phần cứng:** Tên | Số lượng
**Phần mềm:** ...

---

## Đánh giá chung

**Rubric chung** (áp dụng cho tất cả dự án):

| Tiêu chí | Chưa đạt (1) | Đạt (2) | Tốt (3) | Xuất sắc (4) |
|----------|---------------|---------|---------|---------------|
| Quy trình EDP | ... | ... | ... | ... |
| Làm việc nhóm | ... | ... | ... | ... |
| Trình bày | ... | ... | ... | ... |

**Peer feedback** (đặc biệt các dự án cuối): Mẫu "Điều mình thích — Điều mình thắc mắc — Gợi ý cải tiến"

---

## Dự án 1: [Tên] — số buổi

**Câu hỏi dẫn dắt:** "..."

**Mục tiêu (STEM/AI):**
- ...

**Sản phẩm đầu ra:** ...

**Phần cứng:** Tên | số lượng
**Phần mềm:** ...

**Phân hoá:**
- Yêu cầu cơ bản: ...
- Yêu cầu nâng cao: ...

**Rubric dự án:**

| Tiêu chí | Chưa đạt (1) | Đạt (2) | Tốt (3) | Xuất sắc (4) |
|----------|---------------|---------|---------|---------------|
| Sản phẩm | [cụ thể theo dự án] | ... | ... | ... |
| Code | [cụ thể theo dự án] | ... | ... | ... |

---

(Tiếp tục cho các dự án khác)

---


```

## Lưu file

- Thư mục: `[tên-khoá-kebab-case]/`
- Tên file: `syllabus-[tên-khoá-kebab-case].md`
- Ví dụ: `arduino-robot-thcs/syllabus-arduino-robot-thcs.md`

Skill này cũng tạo sẵn các subfolder cho từng dự án, ví dụ:
```
arduino-robot-thcs/
  syllabus-arduino-robot-thcs.md
  du-an-1-den-giao-thong/
  du-an-2-chuong-bao-dong/
  ...
```

File syllabus này sẽ là input cho các skill tiếp theo trong pipeline (textbook-writer, lesson-plan-writer, slide-designer).
