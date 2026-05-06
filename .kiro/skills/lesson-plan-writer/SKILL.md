---
name: lesson-plan-writer
description: >
  Viết giáo án (lesson plan) chi tiết cho từng dự án trong syllabus STEM/AI.
  Dùng khi người dùng muốn viết giáo án, kế hoạch bài dạy, hoặc hướng dẫn giảng dạy
  cho giáo viên dựa trên syllabus và giáo trình đã có.
  Kể cả khi người dùng nói "soạn giáo án", "viết lesson plan", "lên kế hoạch dạy" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "2.0"
---

## Khả năng

Viết giáo án chi tiết cho giáo viên, theo quy trình EDP, cho từng dự án trong syllabus STEM/AI.

## Khi nào dùng

- Người dùng muốn viết giáo án / lesson plan
- Người dùng đã có syllabus (và có thể có giáo trình) và muốn tạo kế hoạch giảng dạy
- Người dùng nói "soạn giáo án", "viết lesson plan", "kế hoạch bài dạy"

## Input

- **Bắt buộc:** File syllabus (ở root khoá: `[tên-khoá]/syllabus-[tên-khoá].md`)
- **Bắt buộc:** File giáo trình tương ứng (`[tên-khoá]/[du-an-X-tên]/textbook-[tên-dự-án].md`)
- **Tuỳ chọn:** Dự án cụ thể muốn viết (nếu không chỉ định → viết tất cả)

## Template giáo án

Cấu trúc giáo án **bắt buộc** tuân theo template chuẩn EDP THCS/THPT tại:
#[[file:.kiro/skills/lesson-plan-writer/references/[Template] Giáo án EDP THCS THPT.md]]

Khi viết giáo án, phải đọc file template này và tuân thủ chính xác:
- Giữ nguyên cấu trúc heading, thứ tự các mục, format bảng
- Điền nội dung cụ thể cho từng dự án vào các chỗ trống (…) trong template
- Với dự án 1 buổi: dùng phần Buổi 1 (kết thúc ở bước 6. Tổng kết)
- Với dự án 2 buổi: dùng cả phần Buổi 1 và Buổi 2
- Luôn có bảng "Thông tin tài liệu" và "Phân bổ các hoạt động" ở cuối

## Quy trình thực hiện

### Bước 1: Đọc syllabus + giáo trình
Đọc file syllabus để hiểu tổng quan. Đọc giáo trình tương ứng để nắm nội dung chi tiết.

### Bước 2: Đọc template giáo án
Đọc file template để nắm cấu trúc chuẩn trước khi viết.

### Bước 3: Viết giáo án cho từng dự án
Với mỗi dự án, viết 1 file giáo án theo đúng template. Giáo án là tài liệu cho **giáo viên**, khác với giáo trình (cho học sinh). Viết lần lượt, **hỏi người dùng sau mỗi dự án**.

### Bước 4: Lưu file

## Nguyên tắc viết giáo án

- Giáo án là cho **giáo viên**, không phải học sinh. Viết rõ GV cần làm gì, nói gì, hỏi gì.
- Mỗi hoạt động phải có thời gian cụ thể (ghi vào chỗ `X phút` trong heading). Tổng thời gian = thời lượng buổi học.
- Luôn có hoạt động hands-on trong mỗi buổi, không có buổi nào chỉ nghe giảng lý thuyết.
- Câu hỏi gợi mở giúp GV dẫn dắt thay vì giảng.
- Phần "1.2.1. Khởi động" phải kích thích hứng thú, tạo tò mò cho HS.
- Phần "Nghiên cứu kiến thức nền" phải có hoạt động thực hành khám phá, không chỉ đọc/nghe.
- Phần "Chế tạo mẫu" cần ghi rõ checkpoint kiểm tra tiến độ và hỗ trợ phân hoá.

## Chiến lược chọn hoạt động dẫn dắt

Khi viết phần dẫn dắt / đặt vấn đề cho mỗi hoạt động trong giáo án, **bắt buộc** tham khảo file:
#[[file:.kiro/skills/lesson-plan-writer/references/activity-lead-in-mapping.md]]

### Quy trình chọn chiến lược dẫn dắt

1. **Xác định loại hoạt động:** Hoạt động đang viết thuộc nhóm nào? (Khám phá kiến thức mới, Thực hành, Tư duy bậc cao, Tương tác, Phản ánh...)
2. **Tra bảng ánh xạ:** Dựa vào nhóm hoạt động, chọn chiến lược dẫn dắt phù hợp từ bảng tương ứng trong file mapping.
3. **Viết cụ thể:** Không chỉ ghi tên chiến lược mà phải viết ra câu hỏi / tình huống / hoạt động dẫn dắt cụ thể, sát với nội dung dự án đang soạn.

### Nguyên tắc bắt buộc

- **Đa dạng hoá:** Không lặp lại cùng một chiến lược dẫn dắt trong cùng một giáo án.
- **Phù hợp lứa tuổi:**
  - Tiểu học: Ưu tiên kể chuyện, trò chơi, demo trực quan, mời HS lên tham gia.
  - THCS: Ưu tiên thử thách, thí nghiệm, thảo luận nhóm, tình huống thực.
  - THPT: Ưu tiên case study, tranh luận, dự án, câu hỏi phản biện.
- **Phù hợp vị trí trong buổi học:**
  - Đầu buổi: Chiến lược tạo hứng thú (kể chuyện, thử thách, câu hỏi gây tò mò).
  - Giữa buổi: Chiến lược duy trì tập trung (thực hành, thí nghiệm, trò chơi).
  - Cuối buổi: Chiến lược phản ánh (exit ticket, 3-2-1, cliffhanger).
- **Hook trong 2 phút đầu:** Mỗi hoạt động phải bắt đầu bằng yếu tố thu hút ngay.
- **Cân bằng câu hỏi đóng/mở:** Tỷ lệ gợi ý 30% đóng / 70% mở cho STEM.

## Lưu file

- Lưu vào subfolder của dự án tương ứng: `[tên-khoá]/[du-an-X-tên]/lesson-plan-[slug-dự-án].md`

**Quy tắc đặt tên:** Slug trong tên file phải trùng với slug trong tên folder.
- Folder `du-an-1-den-sos` → file `lesson-plan-den-sos.md`
- Folder `du-an-3-cam-bien-lui-xe` → file `lesson-plan-cam-bien-lui-xe.md`
- Ví dụ đầy đủ: `arduino-robot-thcs/du-an-1-den-sos/lesson-plan-den-sos.md`
