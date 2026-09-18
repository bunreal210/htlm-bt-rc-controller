# 🚗 Robot Bluetooth Controller

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: Arduino](https://img.shields.io/badge/Platform-Arduino-blue)](https://www.arduino.cc/)
[![Web: HTML5](https://img.shields.io/badge/Web-HTML5-orange)](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
[![Bluetooth: Supported](https://img.shields.io/badge/Bluetooth-Supported-green)](https://www.bluetooth.com/)

Ứng dụng web **HTML5** điều khiển xe robot qua Bluetooth sử dụng **Web Bluetooth API**. Giao diện đẹp, dễ dùng, chạy trực tiếp trên trình duyệt Chrome/Safari.

---

## 🎯 Tính năng chính

✅ **Điều khiển D-PAD** - 4 nút mũi tên + nút dừng  
✅ **Keyboard Controls** - Phím W/A/S/D/Space  
✅ **Real-time Display** - Hiển thị tốc độ motor trực tiếp  
✅ **Smooth Acceleration** - Gia tốc mượt không giật  
✅ **Responsive Design** - Chạy trên desktop, tablet, điện thoại  
✅ **Web Bluetooth API** - Kết nối Bluetooth không cần app thêm  
✅ **Cross-platform** - Android (Chrome) + iOS/iPad (Safari)  
✅ **Real-time Status** - Chỉ báo kết nối/ngắt trực quan  

---

## 📱 Yêu cầu hệ thống

### **Phần cứng:**
- Arduino R3 / Uno / Nano / Mega
- Module L298N (driver motor)
- Module HC05 (Bluetooth Serial)
- 2× motor DC 5V
- 2× pin 18650 (7.4V khi series)
- Dây nối, breadboard

### **Phần mềm - Điện thoại:**
- **Android:** Chrome, Microsoft Edge (phiên bản gần đây)
- **iOS/iPad:** Safari 14.5 trở lên
- **Bluetooth:** BLE được bật

### **Phần mềm - Development:**
- Arduino IDE (để upload code)
- Text editor (để sửa code)
- Git (tuỳ chọn)

---

## 🔧 Sơ đồ kết nối

```
┌──────────────┐
│  Arduino R3  │
│              │
│ Pin 5 (ENA)  ├──→ L298N ENA
│ Pin 6 (IN1)  ├──→ L298N IN1
│ Pin 7 (IN2)  ├──→ L298N IN2
│ Pin 9 (ENB)  ├──→ L298N ENB
│ Pin 10 (IN3) ├──→ L298N IN3
│ Pin 11 (IN4) ├──→ L298N IN4
│ Pin 2 (RX)   ├──→ HC05 TX
│ Pin 3 (TX)   ├──→ HC05 RX
│ GND          ├──→ L298N GND + HC05 GND
│ 5V           ├──→ HC05 5V
└──────────────┘

┌──────────────┐        ┌──────────────┐
│ 2× 18650     │        │   L298N      │
│ (+12V)       ├────────├───────────→  │
│ (GND)        ├────────├───────────→  │
└──────────────┘        └──────────────┘
                            │
                    ┌───────┴────────┐
                    │                │
                 Motor L         Motor R
```

---

## 🚀 Cách bắt đầu

### **1. Upload Code Arduino**

```bash
# Clone repository
git clone https://github.com/YOUR_USERNAME/robot-controller.git
cd robot-controller

# Mở Arduino IDE
# File → Open → robot_car_control.ino

# Chọn Board: Arduino Uno
# Chọn Port: COM port của Arduino
# Nhấn Upload
```

**Hoặc copy-paste code:**
1. Mở Arduino IDE
2. Copy nội dung từ `robot_car_control.ino`
3. Paste vào Arduino IDE
4. Upload

### **2. Mở App Web trên Điện thoại**

**Android (Chrome):**
1. Mở Chrome
2. Menu (⋯) → Open file
3. Chọn `robot_bluetooth_controller.html`

**iOS (Safari):**
1. Tìm file `robot_bluetooth_controller.html`
2. Open with → Safari

**Hoặc dùng link GitHub Pages:**
```
https://YOUR_USERNAME.github.io/robot-controller/robot_bluetooth_controller.html
```

### **3. Kết nối Bluetooth**
1. Pair HC05 qua Settings Bluetooth (PIN: `1234`)
2. Mở app → Nhấn "🔌 Kết nối Bluetooth"
3. Chọn **HC05** từ danh sách
4. Chờ kết nối thành công (đèn xanh)
5. Bắt đầu điều khiển!

---

## 📖 Cách sử dụng

### **Nút điều khiển (D-PAD):**
```
        ⬆️
      Tiến
        
    ⬅️  ⏹️  ➡️
   Trái Dừng Phải
   
        ⬇️
      Lùi
```

### **Keyboard (Máy tính / Bluetooth keyboard):**
| Phím | Hành động |
|---|---|
| **W** | Tiến |
| **S** | Lùi |
| **A** | Rẽ trái |
| **D** | Rẽ phải |
| **Space** | Dừng |

### **Lệnh Bluetooth (Serial):**
```
F - Forward (Tiến)
B - Backward (Lùi)
L - Left (Rẽ trái)
R - Right (Rẽ phải)
S - Stop (Dừng)
```

---

## 📚 Cấu trúc File

```
robot-controller/
├── README.md                          # File hướng dẫn này
├── robot_bluetooth_controller.html    # App web chính
├── robot_car_control.ino              # Code Arduino
├── HUONG_DAN_APP_WEB.md              # Hướng dẫn chi tiết app web
├── GIAI_THICH_CODE.md                # Giải thích toàn bộ code
└── HUONG_DAN_GITHUB_WEB_LINK.md      # Hướng dẫn tạo link web
```

---

## 🔌 Chi tiết Kết nối

### **Arduino → L298N:**
| Arduino Pin | L298N Pin | Chức năng |
|---|---|---|
| 5 (PWM) | ENA | Tốc độ motor trái |
| 6 | IN1 | Hướng motor trái (1) |
| 7 | IN2 | Hướng motor trái (2) |
| 9 (PWM) | ENB | Tốc độ motor phải |
| 10 | IN3 | Hướng motor phải (1) |
| 11 | IN4 | Hướng motor phải (2) |
| GND | GND | Đất chung |

### **Arduino → HC05:**
| Arduino Pin | HC05 Pin | Chức năng |
|---|---|---|
| Pin 2 | RX | Nhận dữ liệu |
| Pin 3 | TX | Gửi dữ liệu |
| 5V | 5V | Cấp điện |
| GND | GND | Đất chung |

### **Power Supply:**
| Nguồn | Dùng cho | Voltage |
|---|---|---|
| 2× 18650 (Series) | L298N | 7.4V |
| Arduino USB/5V | Arduino + HC05 | 5V |
| L298N GND | Chung toàn bộ | GND |

---

## ⚙️ Cấu hình

### **Tốc độ Motor:**
```cpp
int maxSpeed = 200;  // Thay thành 150 để chậm hơn, 255 để nhanh hơn
```

### **Độ mượt gia tốc:**
```cpp
int accelStep = 5;   // Thay thành 10 để tăng tốc nhanh hơn
```

### **Baud Rate Bluetooth:**
```cpp
bt.begin(9600);      // HC05 mặc định 9600, không cần đổi
```

---

## 🐛 Khắc phục sự cố

| Vấn đề | Nguyên nhân | Giải pháp |
|---|---|---|
| App không load | Trình duyệt không hỗ trợ | Dùng Chrome (Android) hoặc Safari (iOS) |
| Không tìm HC05 | HC05 chưa bật hoặc chưa pair | Pair HC05 qua Settings trước, PIN: 1234 |
| Kết nối lỗi | Baud rate không khớp | Kiểm tra `bt.begin(9600)` trong code |
| Robot không chuyển động | Dây kết nối lỏng hoặc pin yếu | Kiểm tra dây nối, test voltage pin |
| Motor không tăng tốc | Smooth acceleration không hoạt động | Kiểm tra Arduino có run code không |

---

## 📊 Thông số kỹ thuật

| Thông số | Giá trị |
|---|---|
| Baud Rate | 9600 bps |
| PWM Frequency | ~490 Hz (Arduino default) |
| Motor Max Speed | 200/255 (78%) |
| Acceleration Step | 5/20ms (gia tốc 0→255 trong ~1 giây) |
| Communication | Bluetooth Serial (HC05) |
| Web API | Web Bluetooth API |
| Protocols | GATT (Generic Attribute Profile) |

---

## 🎓 Học tập

### **File giải thích:**
- **`GIAI_THICH_CODE.md`** - Giải thích chi tiết từng dòng code Arduino
- **`HUONG_DAN_APP_WEB.md`** - Hướng dẫn sử dụng app web
- **`HUONG_DAN_GITHUB_WEB_LINK.md`** - Cách tạo link web từ GitHub

### **Khái niệm chính:**
- **SoftwareSerial** - UART ảo trên Pin 2,3
- **L298N** - Cầu H điều khiển motor DC
- **PWM** - Điều chế độ rộng xung (tốc độ)
- **Smooth Acceleration** - Tăng tốc dần (không giật)
- **Web Bluetooth API** - Kết nối Bluetooth từ web browser

---

## 📱 Chia sẻ

### **Link chạy trực tiếp:**
```
https://YOUR_USERNAME.github.io/robot-controller/robot_bluetooth_controller.html
```

### **QR Code:**
Dùng https://qr-code-generator.com/ để tạo QR từ link trên

### **URL rút gọn:**
```
https://bit.ly/robot-controller
```

---

## 📝 Ghi chú

- ✅ Tested on: Arduino Uno, Chrome Android, Safari iOS
- ✅ Web Bluetooth requires HTTPS (GitHub Pages hỗ trợ)
- ✅ HC05 mặc định PIN: `1234` hoặc `0000`
- ✅ Motor được kiểm soát qua PWM + Digital pins
- ✅ Smooth acceleration ngăn dòng điện đột ngột

---

## 🔐 Bảo mật

- App chạy **hoàn toàn trên điện thoại** (không gửi dữ liệu lên server)
- Kết nối Bluetooth là chuẩn công khai (HC05 không mã hóa)
- Nếu cần bảo mật cao, thêm mã PIN xác thực ở Arduino

---

## 📄 License

MIT License - Tự do sử dụng, chỉnh sửa, chia sẻ

---

## 👨‍💻 Tác giả

**Vinh** - STEM Lab BDQ, Hưng Yên, Vietnam  
📧 Email: your-email@example.com  
🔗 GitHub: https://github.com/YOUR_USERNAME

---

## 🙏 Cảm ơn

- Arduino Community
- Web Bluetooth API Documentation
- HC05 Community Support

---

## 📞 Liên hệ & Hỗ trợ

Nếu gặp vấn đề:
1. Kiểm tra lại **sơ đồ kết nối**
2. Xem **hướng dẫn khắc phục sự cố** ở trên
3. Tạo **Issue** trên GitHub
4. Liên hệ qua email

---

## 🚀 Bắt đầu ngay

```bash
# 1. Clone repository
git clone https://github.com/YOUR_USERNAME/robot-controller.git

# 2. Mở file HTML trên điện thoại
# Hoặc: https://YOUR_USERNAME.github.io/robot-controller/robot_bluetooth_controller.html

# 3. Upload code Arduino
# Dùng Arduino IDE → Upload robot_car_control.ino

# 4. Kết nối & điều khiển!
```

**Happy Coding! 🎉**

---

*Last updated: 2026-09-18*  
*Made with ❤️ for STEM Lab BDQ*
