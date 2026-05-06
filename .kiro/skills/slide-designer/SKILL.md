---
name: slide-designer
description: >
  Soạn slide dạy học (infographic) dạng HTML cho từng dự án trong syllabus STEM/AI.
  Dùng khi người dùng muốn tạo slide, bài trình chiếu, infographic cho buổi dạy.
  Kể cả khi người dùng nói "làm slide", "soạn bài trình chiếu", "tạo infographic dạy học" — hãy dùng skill này.
metadata:
  author: kien-long
  version: "1.0"
---

## Khả năng

Tạo slide dạy học dạng HTML infographic cho từng dự án, dựa trên giáo án và giáo trình.

## Khi nào dùng

- Người dùng muốn tạo slide / bài trình chiếu cho buổi dạy
- Người dùng muốn tạo infographic dạy học
- Người dùng nói "làm slide", "soạn bài trình chiếu", "tạo infographic"

## Input

- **Bắt buộc:** File giáo án (`[tên-khoá]/[du-an-X-tên]/lesson-plan-[slug-dự-án].md`)
- **Khuyến khích:** File giáo trình tương ứng (`[tên-khoá]/[du-an-X-tên]/textbook-[slug-dự-án].md`)
- **Tuỳ chọn:** Dự án cụ thể (nếu không chỉ định → làm tất cả)

## Quy trình thực hiện

### Bước 1: Đọc giáo án + giáo trình
Đọc giáo án để nắm flow buổi học. Đọc giáo trình để lấy nội dung chi tiết.

### Bước 2: Thiết kế slide cho từng dự án
Mỗi dự án tạo 1 file HTML. Viết lần lượt, **hỏi người dùng sau mỗi dự án**.

### Bước 3: Lưu file

## Thiết kế slide HTML

### Nguyên tắc thiết kế

- **Infographic style:** Ít chữ, nhiều hình minh hoạ, icon, sơ đồ. Không phải slide PowerPoint truyền thống.
- **Responsive:** Hiển thị tốt trên máy chiếu (16:9) và màn hình.
- **Màu sắc:** Dùng palette sáng, thân thiện. Mỗi bước EDP có 1 màu riêng để dễ nhận biết.
- **Font:** Dùng Google Fonts (Nunito hoặc tương tự) — tròn, dễ đọc.
- **Navigation:** Dùng phím mũi tên hoặc click để chuyển slide.

### Cấu trúc slide

Mỗi file HTML là 1 bộ slide hoàn chỉnh cho 1 dự án, gồm các slide sau:

1. **Slide tiêu đề:** Tên dự án + câu hỏi dẫn dắt + hình minh hoạ
2. **Slide mục tiêu:** Mục tiêu buổi học (dạng checklist visual)
3. **Slide EDP overview:** Sơ đồ 6 bước EDP, highlight bước sẽ thực hiện hôm nay
4. **Slide cho mỗi bước EDP:**
   - Tên bước + icon
   - Hướng dẫn ngắn gọn cho học sinh
   - Hình minh hoạ / sơ đồ
   - Câu hỏi gợi mở (nếu có)
5. **Slide kiến thức:** Giải thích visual các khái niệm quan trọng (sơ đồ, infographic)
6. **Slide hướng dẫn thực hành:** Các bước thực hiện (dạng step-by-step visual)
7. **Slide code mẫu:** (nếu có) Code với syntax highlighting
8. **Slide thử thách nâng cao:** Cho học sinh nhanh
9. **Slide trình bày:** Hướng dẫn format trình bày
10. **Slide tổng kết:** Tóm tắt điều đã học + preview buổi sau

### Template HTML cơ bản

```html
<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Tên dự án] — Slide dạy học</title>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
  <style>
    /* Reset & Base */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Nunito', sans-serif; background: #1a1a2e; overflow: hidden; }

    /* Slide container */
    .slide-deck { width: 100vw; height: 100vh; position: relative; }
    .slide {
      width: 100%; height: 100%;
      position: absolute; top: 0; left: 0;
      display: none; padding: 60px 80px;
      flex-direction: column; justify-content: center;
    }
    .slide.active { display: flex; }

    /* EDP color palette */
    .edp-1 { background: linear-gradient(135deg, #667eea, #764ba2); color: white; }
    .edp-2 { background: linear-gradient(135deg, #f093fb, #f5576c); color: white; }
    .edp-3 { background: linear-gradient(135deg, #4facfe, #00f2fe); color: #1a1a2e; }
    .edp-4 { background: linear-gradient(135deg, #43e97b, #38f9d7); color: #1a1a2e; }
    .edp-5 { background: linear-gradient(135deg, #fa709a, #fee140); color: #1a1a2e; }
    .edp-6 { background: linear-gradient(135deg, #a18cd1, #fbc2eb); color: #1a1a2e; }

    /* Typography */
    h1 { font-size: 3rem; font-weight: 800; margin-bottom: 20px; }
    h2 { font-size: 2.2rem; font-weight: 700; margin-bottom: 16px; }
    p, li { font-size: 1.4rem; line-height: 1.6; }

    /* Navigation */
    .nav-hint {
      position: fixed; bottom: 20px; right: 30px;
      font-size: 0.9rem; opacity: 0.5; color: white;
    }
    .slide-counter {
      position: fixed; bottom: 20px; left: 30px;
      font-size: 0.9rem; opacity: 0.5; color: white;
    }

    /* Code block */
    pre {
      background: #2d2d2d; color: #f8f8f2;
      padding: 24px; border-radius: 12px;
      font-size: 1.1rem; overflow-x: auto;
      margin: 16px 0;
    }
  </style>
</head>
<body>
  <div class="slide-deck" id="deck">
    <!-- Slides go here -->
  </div>

  <div class="slide-counter" id="counter"></div>
  <div class="nav-hint">← → hoặc click để chuyển slide</div>

  <script>
    const slides = document.querySelectorAll('.slide');
    let current = 0;

    function showSlide(n) {
      slides[current].classList.remove('active');
      current = (n + slides.length) % slides.length;
      slides[current].classList.add('active');
      document.getElementById('counter').textContent = `${current + 1} / ${slides.length}`;
    }

    document.addEventListener('keydown', (e) => {
      if (e.key === 'ArrowRight' || e.key === ' ') showSlide(current + 1);
      if (e.key === 'ArrowLeft') showSlide(current - 1);
    });

    document.addEventListener('click', (e) => {
      if (e.clientX > window.innerWidth / 2) showSlide(current + 1);
      else showSlide(current - 1);
    });

    showSlide(0);
  </script>
</body>
</html>
```

### Tuỳ chỉnh theo cấp độ

- **Tiểu học:** Font lớn hơn, nhiều emoji/icon, ít chữ, màu sắc tươi sáng.
- **THCS:** Cân bằng text và visual, có sơ đồ kỹ thuật.
- **THPT:** Có thể thêm sơ đồ phức tạp, code block, biểu đồ dữ liệu.

## Lưu file

- Lưu vào subfolder của dự án tương ứng: `[tên-khoá]/[du-an-X-tên]/slide-[slug-dự-án].html`

**Quy tắc đặt tên:** Slug trong tên file phải trùng với slug trong tên folder.
- Folder `du-an-1-den-sos` → file `slide-den-sos.html`
- Folder `du-an-3-cam-bien-lui-xe` → file `slide-cam-bien-lui-xe.html`
- Ví dụ đầy đủ: `arduino-robot-thcs/du-an-1-den-sos/slide-den-sos.html`
