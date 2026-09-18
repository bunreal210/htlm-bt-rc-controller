# 🚗 Hướng dẫn sử dụng App Web Điều khiển Robot Bluetooth

## 📱 Yêu cầu

- **Điện thoại:** Android (Chrome, Edge) hoặc iPhone/iPad (Safari 14+)
- **File:** `robot_bluetooth_controller.html` (file HTML mà tôi vừa tạo)
- **Arduino:** Code `robot_car_control.ino` đã upload
- **HC05:** Đã pair với điện thoại qua Bluetooth

---

## 🚀 Cách sử dụng app web

### **Bước 1: Tải file HTML**
- Download file `robot_bluetooth_controller.html`
- Lưu vào điện thoại (Downloads, Documents, v.v.)

### **Bước 2: Mở file HTML trong trình duyệt**

**Android:**
1. Mở ứng dụng **Chrome** hoặc **Edge**
2. Nhấn menu (3 chấm) → **Open file** (hoặc **Open URL**)
3. Tìm file `robot_bluetooth_controller.html` → Mở

**iPhone/iPad:**
1. Mở ứng dụng **Safari**
2. Nhấn thanh địa chỉ → Nhập: `file:///...` rồi chọn file
3. Hoặc: Giữ file → **Open with Safari**

### **Bước 3: Kết nối Bluetooth**
1. App sẽ hiển thị: "🔌 Kết nối Bluetooth"
2. Nhấn nút **Kết nối Bluetooth**
3. Chọn **HC05** từ danh sách thiết bị
4. Chờ xác nhận (khoảng 2 giây)
5. Nếu thành công: Sẽ thấy "✓ Kết nối: HC05"

### **Bước 4: Điều khiển Robot**
- **⬆️ (Tiến):** Nhấn nút mũi tên lên
- **⬇️ (Lùi):** Nhấn nút mũi tên xuống
- **⬅️ (Rẽ trái):** Nhấn nút mũi tên trái
- **➡️ (Rẽ phải):** Nhấn nút mũi tên phải
- **⏹️ (Dừng):** Nhấn nút dừng ở giữa

**Hoặc dùng Keyboard:**
- **W** = Tiến
- **S** = Lùi
- **A** = Rẽ trái
- **D** = Rẽ phải
- **Space** = Dừng

---

## 🎨 Các tính năng của App

### **1. Status Bar (Thanh trạng thái)**
- **Đèn đỏ (•):** Chưa kết nối
- **Đèn xanh (•):** Đã kết nối thành công
- **Hiển thị tên:** "✓ Kết nối: HC05"

### **2. Nút Kết nối/Ngắt kết nối**
- **🔌 Kết nối Bluetooth:** Nhấn để tìm và kết nối HC05
- **Ngắt kết nối:** Tắt kết nối Bluetooth an toàn

### **3. D-PAD (Nút điều khiển)**
- **Giao diện:** Nút mũi tên 4 hướng + nút dừng giữa
- **Phản hồi:** Nút sẽ chuyển sang màu xanh khi nhấn
- **Đầu mềm:** Robot sẽ tăng tốc độ từ từ (không giật)

### **4. Motor Display (Hiển thị trạng thái motor)**
- **Motor Trái:** Hiển thị tốc độ motor trái (-255 đến 255)
- **Motor Phải:** Hiển thị tốc độ motor phải (-255 đến 255)
- **Thanh tiến độ:** Chiều cao thanh = tốc độ (0-100%)

**Ví dụ:**
- Nhấn "⬆️ Tiến" → Cả hai motor = 200 (78% tốc độ max)
- Nhấn "⬅️ Rẽ trái" → Motor trái = 67, motor phải = 200
- Nhấn "⏹️ Dừng" → Cả hai motor = 0

### **5. Chỉ báo LED**
- **Xám:** Chưa kết nối
- **Xanh sáng:** Đã kết nối (tương ứng LED trên Arduino pin 13)

---

## 🔧 Cấu hình HC05

### **Tìm HC05 trong danh sách Bluetooth:**

**Nếu HC05 không xuất hiện:**
1. Bật HC05 (cấp nguồn cho robot)
2. Bật Bluetooth trên điện thoại
3. Pair HC05 một lần (yêu cầu mã PIN: `1234` hoặc `0000`)
4. Sau khi pair, app sẽ tự động tìm thấy

**MAC Address HC05:**
- Thường là: `HC-05` hoặc `HC05`
- Nếu bị thay tên, tìm module có tên bắt đầu bằng "HC"

---

## ⚠️ Khắc phục sự cố

### **Vấn đề 1: "Trình duyệt này không hỗ trợ Web Bluetooth API"**
**Nguyên nhân:** Dùng trình duyệt không hỗ trợ
**Giải pháp:**
- Android: Dùng **Chrome** hoặc **Edge** (không phải Firefox hoặc Samsung Internet)
- iPhone: Dùng **Safari** (không phải Chrome)

### **Vấn đề 2: "Không tìm thấy HC05"**
**Nguyên nhân:** HC05 chưa bật hoặc chưa pair
**Giải pháp:**
1. Kiểm tra HC05 có cấp nguồn không (đèn LED nhấp nháy)
2. Pair HC05 với điện thoại trước:
   - Vào Settings → Bluetooth → Tìm HC05 → Pair (PIN: 1234)
3. Sau đó mở app → Kết nối

### **Vấn đề 3: "Kết nối Bluetooth lỗi"**
**Nguyên nhân:** Mã baud rate không khớp
**Giải pháp:**
1. Kiểm tra code Arduino: `bt.begin(9600);` phải = 9600
2. HC05 mặc định 9600, không cần cấu hình lại
3. Nếu vẫn lỗi, reset HC05:
   - Ngắt nguồn → Chờ 5 giây → Cấp lại nguồn

### **Vấn đề 4: "Gửi lệnh nhưng robot không chuyển động"**
**Nguyên nhân:** Dây kết nối L298N hoặc pin yếu
**Giải pháp:**
1. Kiểm tra dây kết nối motor
2. Kiểm tra pin 18650 có dung lượng không (kiểm tra voltage)
3. Test thủ công: Kết nối motor trực tiếp vào pin → xem có quay không
4. Nếu motor không quay, có thể L298N hỏng

### **Vấn đề 5: "Motor chuyển động nhưng không tăng/giảm tốc độ mượt"**
**Nguyên nhân:** Smooth acceleration không hoạt động
**Giải pháp:**
- Kiểm tra code Arduino: `accelStep = 5;`
- Nếu muốn nhanh hơn, thay thành `10`
- Nếu muốn mượt hơn, thay thành `2`

---

## 💡 Tính năng nâng cao

### **1. Tùy chỉnh tốc độ tối đa**
Sửa trong code Arduino:
```cpp
int maxSpeed = 200;  // Thay thành 150 để chậm hơn
```

### **2. Thêm lệnh quay 90 độ**
Sửa trong hàm `processCommand()`:
```cpp
case 'Q':  // Quay trái 90 độ
  targetLeft = -maxSpeed;
  targetRight = maxSpeed;
  break;

case 'E':  // Quay phải 90 độ
  targetLeft = maxSpeed;
  targetRight = -maxSpeed;
  break;
```

Rồi thêm nút trong HTML:
```html
<button class="dpad-btn" data-command="Q">🔄</button>
```

### **3. Tách pin RX/TX (nếu muốn dùng Serial monitor đồng thời)**
Hiện tại code dùng SoftwareSerial, vẫn có thể dùng Serial monitor qua USB.

---

## 📊 Giải thích giao diện

```
┌─────────────────────────────────┐
│   🚗 Robot Controller           │  ← Tiêu đề
│   Điều khiển robot qua BT       │
├─────────────────────────────────┤
│ • Chưa kết nối              [◆] │  ← Status bar (đèn chỉ báo)
├─────────────────────────────────┤
│   [🔌 Kết nối Bluetooth]        │  ← Nút kết nối
├─────────────────────────────────┤
│   Điều khiển hướng              │
│      ⬆️                          │
│   ⬅️ ⏹️ ➡️                      │  ← D-PAD (4 nút + nút dừng)
│      ⬇️                          │
│   💡 Nhấn: W/S/A/D/Space       │
├─────────────────────────────────┤
│  Motor Trái    Motor Phải       │
│    [0]          [0]              │  ← Hiển thị tốc độ motor
│    [░░░░░░░]   [░░░░░░░]        │
└─────────────────────────────────┘
```

---

## 🎯 Các tình huống test

### **Test 1: Kết nối**
1. Mở app → Nhấn "Kết nối Bluetooth"
2. Chọn HC05 → Chờ 2 giây
3. **Kỳ vọng:** Đèn xanh, hiển thị "✓ Kết nối: HC05"

### **Test 2: Điều khiển cơ bản**
1. Nhấn "⬆️ Tiến" → Robot tiến
2. Nhấn "⬇️ Lùi" → Robot lùi
3. Nhấn "⏹️ Dừng" → Robot dừng
4. **Kỳ vọng:** Robot chuyển động mượt mà

### **Test 3: Rẽ**
1. Nhấn "⬅️" → Robot rẽ trái
2. Nhấn "➡️" → Robot rẽ phải
3. **Kỳ vọng:** Motor trái/phải chạy với tốc độ khác nhau

### **Test 4: Keyboard**
1. Nhấn phím "W" → Robot tiến
2. Nhấn phím "Space" → Robot dừng
3. **Kỳ vọng:** Hoạt động như nhấn nút

---

## 📱 Lưu ý về các trình duyệt

| Trình duyệt | Web Bluetooth | Ghi chú |
|---|---|---|
| **Chrome (Android)** | ✅ Tốt nhất | Khuyến nghị sử dụng |
| **Edge (Android)** | ✅ Tốt | Dùng được tương tự Chrome |
| **Safari (iOS/iPad)** | ✅ Tốt | iOS 14.5+ hỗ trợ |
| **Firefox (Android)** | ❌ Không | Không hỗ trợ Web Bluetooth |
| **Samsung Internet** | ❌ Không | Không hỗ trợ Web Bluetooth |

---

## 🔐 Bảo mật

- App chạy hoàn toàn trên điện thoại (không gửi dữ liệu lên server)
- Kết nối Bluetooth là chuẩn công khai (HC05 không mã hóa)
- Nếu bảo mật cao, nên thêm mã PIN ở Arduino

---

## 📞 Hỗ trợ

Nếu gặp vấn đề:
1. Kiểm tra lại sơ đồ kết nối
2. Test code Arduino qua Serial Monitor
3. Pair HC05 thủ công trước khi dùng app
4. Thử lại với trình duyệt khác (Chrome trên Android)

Chúc bạn thành công! 🚀
