# HRM Enterprise — Mobile App (Flutter 3.x)

Ứng dụng di động dành cho Nhân viên và Quản lý vận hành chi nhánh thuộc chuỗi doanh nghiệp **HRM Enterprise**. Hỗ trợ chấm công Wi-Fi 1 chạm, đăng ký & xem lịch ca kíp, nộp/duyệt đơn từ, tra cứu phiếu lương và cập nhật tin tức nội bộ.

---

## 📱 Điểm nổi bật & Thiết kế

- **Framework:** Flutter 3.x (Dart 3.x)
- **Thiết kế UI/UX:** Chuẩn Material 3, Font chữ `Public Sans`, Màu thương hiệu chủ đạo `#8E1B2F` (Burgundy Red)
- **Kiến trúc:** Feature-first Architecture, Repository Pattern, State Management
- **Hỗ trợ đa nền tảng:** Android, iOS, Web, Windows

---

## 🌟 Chức năng chính

### 1. Dành cho Nhân viên (Staff):
- 🔐 **Đăng nhập & Phiên an toàn:** Xác thực tài khoản với Identity Service qua API Gateway, lưu phiên đăng nhập an toàn.
- 📍 **Chấm công Wi-Fi 1 chạm:** Tự động phát hiện và kiểm tra BSSID / IP mạng Wi-Fi của chi nhánh được phân công. Báo lỗi ngay nếu chưa kết nối đúng mạng Wi-Fi hợp lệ.
- 📅 **Lịch làm việc cá nhân:** Xem lịch phân ca theo tuần, thông tin chi tiết từng ca (giờ bắt đầu/kết thúc, vai trò), đăng ký nhận ca trống.
- 📝 **Tạo Đơn từ nhanh:** Nộp đơn xin nghỉ phép, xin đi muộn / về sớm, làm thêm giờ (OT), tạm ứng lương, giải trình vi phạm chấm công kèm hình ảnh minh chứng.
- 💰 **Tra cứu Phiếu lương:** Xem chi tiết lương thực nhận hàng tháng, ngày công, phụ cấp, các khoản khấu trừ BHXH, thuế TNCN và tiền phạt.
- 📢 **Bảng tin & Thông báo:** Nhận thông báo tức thời, xem tin tức doanh nghiệp, sổ tay quy chế nội bộ.

### 2. Dành cho Quản lý (Manager):
- 📋 **Phê duyệt Đơn từ:** Xem danh sách đơn từ của nhân sự trong chi nhánh, phê duyệt hoặc từ chối kèm lý do phản hồi.
- 👥 **Giám sát Ca trực:** Theo dõi trạng thái nhân sự đi làm trong ca hiện tại của chi nhánh.
- 🔔 **Thông báo vận hành:** Nhận cảnh báo khi có nhân viên quên chấm công hoặc có đơn từ cần duyệt gấp.

---

## 🚀 Cài đặt & Khởi chạy

### Yêu cầu tiên quyết
- Flutter SDK >= 3.22.x
- Dart SDK >= 3.4.x
- Android Studio / Xcode (dành cho iOS)
- API Gateway backend đang chạy tại port 4000

### Các bước khởi chạy

```bash
# 1. Di chuyển vào thư mục mobile
cd mobile

# 2. Tải các package phụ thuộc
flutter pub get

# 3. Kiểm tra thiết bị kết nối
flutter devices

# 4. Chạy ứng dụng trên thiết bị / máy ảo
flutter run
```

### Cấu hình địa chỉ API Gateway

Chỉnh sửa địa chỉ máy chủ trong file cấu hình mạng:
`lib/src/core/network/api_client.dart`:

- **Android Emulator:** `http://10.0.2.2:4000`
- **iOS Simulator / macOS:** `http://localhost:4000`
- **Thiết bị thật (Cùng mạng LAN Wi-Fi):** `http://<IP_MÁY_DEV>:4000`

---

## 🔑 Tài khoản thử nghiệm

| Vai trò | Email | Mật khẩu |
|---|---|---|
| **Admin** | `admin@company.com` | `123456` |
| **Manager** | `manager@company.com` | `123456` |
| **Staff** | `nhanvien@company.com` | `123456` |

---

## 🌳 Cấu trúc thư mục

```text
mobile/
├── lib/
│   ├── main.dart                      # Điểm khởi chạy ứng dụng
│   └── src/
│       ├── app.dart                   # Cấu hình MaterialApp, theme, route
│       ├── core/                      # Constants, theme, router, network client, models
│       └── features/                  # Phân hệ chức năng
│           ├── auth/                  # Đăng nhập, xác thực, splash screen
│           ├── home/                  # Màn hình chính, widget chấm công Wi-Fi
│           ├── schedule/              # Lịch làm việc, đăng ký & xem ca
│           ├── leave_request/         # Đơn từ (nghỉ phép, OT, giải trình)
│           ├── salary/                # Tra cứu phiếu lương, tạm ứng lương
│           ├── approvals/             # Phê duyệt đơn từ (Manager)
│           ├── news/                  # Bảng tin nội bộ
│           ├── regulations/           # Quy chế & chính sách công ty
│           ├── notifications/         # Thông báo hệ thống
│           └── profile/               # Thông tin cá nhân, đổi mật khẩu, thiết bị
├── android/                           # Cấu hình native Android
├── ios/                               # Cấu hình native iOS
├── pubspec.yaml                       # Khai báo thư viện & assets
└── test/                              # Unit & Widget tests
```

---

## 🔗 Liên kết hệ thống HRM Enterprise

- **Web Portal (Next.js):** [HRM-QuanLyDuAn/frontend](https://github.com/HRM-QuanLyDuAn/frontend)
- **Backend SOA (Core Server):** [HRM-QuanLyDuAn/backend](https://github.com/HRM-QuanLyDuAn/backend)
