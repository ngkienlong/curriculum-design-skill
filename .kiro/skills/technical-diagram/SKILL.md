---
name: technical-diagram
description: >
  Vẽ sơ đồ kỹ thuật điện tử chính xác (sơ đồ kết nối mạch, sơ đồ nguyên lý, pinout)
  cho các dự án Arduino/điện tử. Dùng khi cần tạo sơ đồ mạch điện, sơ đồ kết nối linh kiện, hoặc bất kỳ hình ảnh kỹ thuật nào yêu cầu chính xác về cực tính, chân nối, chiều dòng điện.
  Kể cả khi người dùng nói "vẽ sơ đồ mạch", "sơ đồ kết nối", "wiring diagram" — hãy dùng skill này thay vì create-svg chung chung.
metadata:
  author: kien-long
  version: "1.0"
---

## Khả năng

Vẽ sơ đồ kỹ thuật điện tử dạng SVG với độ chính xác tuyệt đối về cực tính, chân nối, và chiều dòng điện.

## Khi nào dùng

- Cần vẽ sơ đồ kết nối mạch (wiring diagram) cho Arduino
- Cần vẽ sơ đồ nguyên lý (schematic) đơn giản
- Cần vẽ pinout diagram cho linh kiện
- Cần vẽ sơ đồ kỹ thuật bất kỳ yêu cầu chính xác về điện

Skill này khác với `create-svg` ở chỗ: `create-svg` vẽ hình minh hoạ chung (infographic, minh hoạ khái niệm). Skill này chuyên cho sơ đồ điện tử — nơi sai 1 chân có thể cháy linh kiện.

## Nguyên tắc bắt buộc

### 1. Chính xác tuyệt đối

Mọi sơ đồ kỹ thuật phải chính xác 100%. Trước khi hoàn thành, kiểm tra:
- Cực tính linh kiện đúng
- Chiều dòng điện đúng
- Chân nối khớp với code mẫu (nếu có)
- Nhãn rõ ràng, không mơ hồ

### 2. Chiều dòng điện

Dòng điện quy ước chạy từ **+ (HIGH) → linh kiện → GND (-)**. Trong sơ đồ:
- Mũi tên chiều dòng điện luôn hiển thị
- Nguồn (+) ở bên trái hoặc trên
- GND (-) ở bên phải hoặc dưới

### 3. Nhãn bắt buộc

Mỗi sơ đồ phải có:
- Tên chân Arduino (13, GND, 5V, A0,...)
- Tên và giá trị linh kiện (LED, 220Ω, HC-SR04,...)
- Cực tính nếu có (+ / -, anode/cathode, Trig/Echo,...)
- Chiều dòng điện (mũi tên)

## Knowledge Base linh kiện

### LED
- **Chân dài** = Anode (+) — nối phía nguồn (qua điện trở)
- **Chân ngắn** = Cathode (-) — nối phía GND
- Luôn cần điện trở hạn dòng (thường 220Ω cho 5V)
- Dòng điện: Chân digital → Điện trở → Anode (+) → Cathode (-) → GND

### Điện trở
- Không có cực tính (nối chiều nào cũng được)
- Ghi rõ giá trị (220Ω, 10kΩ,...) trên sơ đồ
- Vẽ vạch màu nếu có thể

### Nút bấm (Push Button)
- 4 chân: 2 cặp nối thông khi nhấn
- Nối 1 chân vào chân digital Arduino, chân đối diện vào GND
- Cần điện trở kéo lên (pull-up) 10kΩ từ chân digital lên 5V, hoặc dùng `INPUT_PULLUP` trong code
- Khi dùng `INPUT_PULLUP`: nối nút giữa chân digital và GND (không cần điện trở ngoài)

### Buzzer thụ động (Passive Buzzer)
- **Chân +** (thường có dấu + hoặc chân dài hơn) — nối vào chân digital Arduino
- **Chân -** — nối vào GND
- Điều khiển bằng `tone(pin, frequency)` và `noTone(pin)`

### Cảm biến siêu âm HC-SR04
- 4 chân theo thứ tự: **VCC | Trig | Echo | GND**
- VCC → 5V Arduino
- Trig → Chân digital (output từ Arduino)
- Echo → Chân digital (input vào Arduino)
- GND → GND Arduino

### Motor DC
- 2 chân, không có cực tính cố định (đảo dây = đảo chiều quay)
- KHÔNG nối trực tiếp vào Arduino — phải qua driver (L298N, L293D)
- Cần nguồn riêng (pin) cho motor, chung GND với Arduino

### Driver Motor L298N
- **Input:** IN1, IN2 (motor A), IN3, IN4 (motor B) — nối vào chân digital Arduino
- **Output:** OUT1, OUT2 (motor A), OUT3, OUT4 (motor B) — nối vào motor
- **ENA, ENB:** Chân enable, nối vào chân PWM Arduino để điều chỉnh tốc độ
- **Nguồn:** 12V (hoặc pin) vào VCC, GND chung với Arduino, 5V output có thể cấp cho Arduino

### Servo SG90
- 3 dây: **Cam/Vàng** = Signal, **Đỏ** = VCC (5V), **Nâu/Đen** = GND
- Signal nối vào chân PWM Arduino
- Điều khiển bằng thư viện `Servo.h`, hàm `servo.write(angle)`

### Biến trở (Potentiometer)
- 3 chân: **Chân 1** → 5V, **Chân 2 (giữa)** → Chân analog Arduino, **Chân 3** → GND
- Đọc giá trị bằng `analogRead()`, trả về 0-1023

## Quy trình vẽ sơ đồ (schemdraw → SVG)

Skill này dùng **schemdraw** (thư viện Python chuyên vẽ sơ đồ mạch điện) với ký hiệu chuẩn quốc tế. Schemdraw tự động xử lý kết nối giữa các linh kiện — dây nối luôn chính xác.

### Cách sử dụng

Viết script Python trực tiếp dùng schemdraw, lưu vào cùng folder dự án:

```python
import schemdraw
import schemdraw.elements as elm

with schemdraw.Drawing(show=False) as d:
    d.config(fontsize=14)
    
    # Nguồn (chân Arduino)
    d += (start := elm.Dot(open=True).label('Arduino\nChân 13', loc='left'))
    
    # Điện trở
    d += elm.Resistor().right().label('220Ω')
    
    # LED
    d += elm.LED().down().label('LED')
    
    # Dây về GND
    d += elm.Line().left().tox(start.start)
    d += elm.Ground().label('GND')
    
    d.save('output.svg')
```

Chạy: `python3 script.py`

### Hoặc dùng JSON + render script

Viết file `.json` mô tả mạch, rồi chạy:
```bash
python3 .kiro/skills/technical-diagram/scripts/render_schemdraw.py <diagram.json> <output.svg>
```

Format JSON:
```json
{
  "title": "Sơ đồ kết nối LED",
  "fontsize": 14,
  "unit": 3,
  "circuit": [
    { "element": "Dot", "open": true, "label": "Arduino\nChân 13", "label_loc": "left", "id": "start" },
    { "element": "Resistor", "direction": "right", "label": "220Ω" },
    { "element": "LED", "direction": "down", "label": "LED" },
    { "element": "Line", "direction": "left", "to_x": "start" },
    { "element": "Ground", "label": "GND" }
  ]
}
```

### Schemdraw elements phổ biến

| Element | Mô tả | Ký hiệu |
|---------|--------|---------|
| `Dot(open=True)` | Điểm nối / đầu dây | ○ |
| `Resistor()` | Điện trở | zigzag |
| `LED()` | LED (có mũi tên chiều dòng) | ▷\| |
| `Line()` | Đoạn dây nối | — |
| `Ground()` | GND | ⏚ |
| `Switch()` / `Button()` | Công tắc / nút bấm | ⌇ |
| `Speaker()` | Buzzer / loa | 🔊 |
| `Motor()` | Motor | Ⓜ |
| `Capacitor()` | Tụ điện | \|\| |
| `Potentiometer()` | Biến trở | zigzag + mũi tên |
| `Battery()` | Pin | \|─\| |
| `SourceV()` | Nguồn điện áp | ⊕ |
| `Label()` / `Tag()` | Nhãn text | text |

### Lưu ý

- Schemdraw dùng **ký hiệu chuẩn quốc tế**, không phải hình ảnh thực tế của linh kiện
- Phù hợp cho sơ đồ nguyên lý (schematic) — nơi cần chính xác về kết nối
- Hình ảnh minh hoạ linh kiện thực tế (board Arduino, cảm biến,...) vẫn dùng SVG assets riêng

## Lưu file

- Sơ đồ schemdraw: lưu `.svg` vào folder dự án
- Script Python: lưu `.py` cạnh file JSON (nếu dùng JSON)
- Hình minh hoạ linh kiện: copy từ `assets/` vào folder dự án

## Thư viện hình ảnh linh kiện (assets)

Ngoài sơ đồ schemdraw, skill còn có thư viện hình ảnh linh kiện thực tế tại `.kiro/skills/technical-diagram/assets/`. Dùng cho hình minh hoạ trong textbook (không phải sơ đồ kết nối).

| File | Linh kiện |
|------|-----------|
| `arduino-uno.svg` | Board Arduino Uno |
| `led.svg` | LED |
| `dien-tro-220.svg` | Điện trở 220Ω |
| `dien-tro-10k.svg` | Điện trở 10kΩ |
| `nut-bam.svg` | Nút bấm |
| `buzzer.svg` | Buzzer thụ động |
| `hc-sr04.svg` | Cảm biến siêu âm HC-SR04 |
| `motor-dc.svg` | Motor DC |
| `l298n.svg` | Driver Motor L298N |
| `servo-sg90.svg` | Servo SG90 |
