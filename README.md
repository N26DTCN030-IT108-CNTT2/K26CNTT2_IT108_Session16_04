# K26CNTT2_IT108_Session16_04
# BÀI 4: SỰ CỐ XUNG ĐỘT PHIÊN ĐĂNG NHẬP TRÊN TRÌNH DUYỆT

**Lớp:** K26CNTT2  
**Môn học:** Nhập Môn Công Nghệ Thông Tin (IT108)  
**Mã sinh viên:** N26DTCN030  
**Họ và tên:** Lê Hồ Thanh Thảo  

---

## 📌 PHẦN 1: PHÂN TÍCH

**So sánh sự khác biệt về lưu trữ trạng thái giữa Incognito Mode và Dedicated Profile:**

| Tiêu chí | Incognito Mode (Ẩn danh) | Dedicated Profile (Cấu hình riêng biệt) |
| :--- | :--- | :--- |
| **Vùng lưu trữ dữ liệu** | Lưu tạm thời trên **RAM** của hệ thống trong suốt phiên làm việc. | Lưu trữ lâu dài trực tiếp trên **ổ cứng** của máy tính. |
| **Vòng đời phiên (Session)** | Tự động xóa sạch toàn bộ cookie, cache, lịch sử và trạng thái đăng nhập ngay khi đóng cửa sổ ẩn danh cuối cùng. | Tồn tại xuyên suốt qua các lần khởi động lại trình duyệt hoặc tắt/mở máy tính cho đến khi người dùng chủ động xóa. |
| **Tính năng đồng bộ (Cloud Sync)** | Không hỗ trợ lưu trữ đám mây hay đồng bộ hóa tài khoản cá nhân. | Hỗ trợ đồng bộ hóa toàn diện qua tài khoản (Mật khẩu, Bookmark, Tiện ích mở rộng, Lịch sử). |
| **Mục đích sử dụng tối ưu** | Tra cứu nhanh thông tin cá nhân trên thiết bị công cộng, tránh lưu vết lịch sử cục bộ. | Phân tách hoàn toàn các môi trường làm việc độc lập (Cá nhân, Công việc, Thử nghiệm) nhằm triệt tiêu xung đột phiên đăng nhập. |

---

## ⚙️ PHẦN 2: TRIỂN KHAI

### Quy trình thiết lập mô hình 3 Profile & Đồng bộ hóa Cloud Sync

Để giải quyết triệt để tình trạng văng tài khoản và xung đột hệ thống GreenLog, tiến hành thiết lập hệ thống 3 profile độc lập và cấu hình bảo vệ dữ liệu như sau:

1. **Khởi tạo 3 Profile độc lập:**
   * Mở Google Chrome, nhấn vào biểu tượng Avatar ở góc trên cùng bên phải và chọn **Add (Thêm)**.
   * Lần lượt thiết lập 3 không gian làm việc riêng biệt:
     * `Personal` (Dùng cho giải trí, mạng xã hội, tài khoản cá nhân).
     * `Work` (Dùng riêng cho học tập, hệ thống GreenLog và tài khoản quản trị).
     * `Sandbox` (Dùng cho môi trường kiểm thử, test tính năng mới).
2. **Kích hoạt tính năng Cloud Sync bảo vệ Bookmark:**
   * Đăng nhập tài khoản Google tương ứng vào từng Profile.
   * Bật tùy chọn **Turn on Sync (Bật đồng bộ hóa)** để toàn bộ Bookmarks, mật khẩu và cài đặt được lưu trữ an toàn trên đám mây, giúp khôi phục tức thì khi chuyển sang thiết bị mới.

---

## 🧪 PHẦN 3: KIỂM THỬ & BẢO MẬT

### Quy tắc sử dụng Guest Profile trên máy tính công cộng
Khi bắt buộc phải làm việc hoặc tra cứu tài liệu trên thiết bị của người khác / máy tính công cộng, việc sử dụng tài khoản chính hoặc chế độ ẩn danh thông thường vẫn tiềm ẩn rủi ro lộ lọt thông tin. Do đó, cần tuân thủ nghiêm ngặt quy tắc sau:

*   **Bắt buộc sử dụng Guest Profile (Khách):** Chế độ này tạo ra một không gian hoàn toàn cô lập, không chia sẻ bất kỳ dữ liệu nào với các profile khác trên máy.
*   **Xử lý sau khi kết thúc phiên:** Ngay khi đóng cửa sổ Guest, toàn bộ lịch sử duyệt web, cookie và các phiên đăng nhập tự động bị **tiêu hủy hoàn toàn**, ngăn chặn tuyệt đối tình trạng rò rỉ tài khoản hệ thống cho người sử dụng tiếp theo.
