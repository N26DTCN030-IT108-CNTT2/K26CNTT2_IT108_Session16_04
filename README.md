# K26CNTT2_IT108_Session16_04
# 🛠️ Session 16 - Bài tập 04: Sự Cố Xung Đột Phiên Đăng Nhập Trên Trình Duyệt

> **Môn học:** Nhập Môn Công Nghệ Thông Tin  
> **Lớp:** K26CNTT2  
> **Họ và tên:** Lê Hồ Thanh Thảo  
> **Mã sinh viên:** N26DTCN030  

---

## 📌 1. Bối Cảnh & Mục Tiêu

Một quản trị viên điều phối cần quản lý đồng thời 3 tài khoản:
1. Tài khoản cá nhân.
2. Tài khoản quản trị hệ thống **GreenLog**.
3. Tài khoản kiểm thử (**Sandbox**).

Nếu dùng chung một cửa sổ trình duyệt, các cookie và session sẽ đè lên nhau gây ra hiện tượng **Session Conflict** (Xung đột phiên đăng nhập). Bài tập này đưa ra giải pháp xử lý triệt để vấn đề trên và tối ưu hóa không gian làm việc.

---

## 📑 2. Phần 1: Phân Tích Kỹ Thuật

### So sánh Incognito Mode vs Dedicated Profile

| Tiêu chí | Incognito Mode (Chế độ ẩn danh) | Dedicated Profile (Hồ sơ riêng biệt) |
| :--- | :--- | :--- |
| **Lưu trữ trạng thái** | Tạm thời trên **RAM** | Lâu dài trên **Ổ cứng (Disk)** |
| **Vòng đời dữ liệu** | Xóa sạch Cookie, Cache, Lịch sử ngay khi đóng cửa sổ | Lưu trữ bền vững qua các phiên làm việc |
| **Đồng bộ Cloud Sync** | ❌ Không hỗ trợ | ✅ Hỗ trợ đầy đủ (Bookmark, History, Extension) |
| **Trường hợp sử dụng** | Duyệt web nhanh, thao tác tạm thời trên máy lạ | Quản lý nhiều tài khoản làm việc cố định |

> **Kết luận:** Việc sử dụng **Dedicated Profile** là giải pháp tối ưu nhất để duy trì 3 không gian làm việc tách biệt mà không lo văng tài khoản.

---

## 🚀 3. Phần 2: Triển Khai Giải Pháp

### 3.1. Thiết lập 3 Profiles độc lập
Tạo 3 Profile riêng biệt trên trình duyệt (Chrome/Edge):
* **Profile 1 - Personal:** Dùng cho mục đích giải trí,
