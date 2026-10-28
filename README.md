# D-n-b-m-t-qu-c-gia-Ss1
# ⚡ Personal AI Assistant (Web Edition)
### Trợ Lý Cá Nhân Trực Tuyến - Tự Nhiên & Siêu Tốc

> Một ứng dụng Web AI trợ lý cá nhân tinh gọn, có cảm xúc và cách nói chuyện tự nhiên như người thật, kết nối trực tiếp với **Google Gemini API** mà không cần cài đặt môi trường backend phức tạp.

---

## ✨ Tính Năng Nổi Bật

- **🗣️ Trò chuyện tự nhiên:** Xưng hô *"mình - bạn"*, biết lắng nghe, động viên, dùng từ ngữ đời thường gần gũi y như người thật.
- **⚡ Phản hồi siêu tốc:** Kết nối dòng mô hình tối ưu **Gemini Flash-Lite** và **Gemini Flash**, nhả chữ chỉ sau 1–2 giây.
- **🛡️ Tự động phục hồi:** Có cơ chế tự động chuyển đổi mô hình và tự thử lại khi gặp tình trạng nghẽn mạng từ Google.
- **🔒 An toàn tuyệt đối:** API Key được lưu tại `localStorage` của trình duyệt, không lưu trên server, không lo rò rỉ mã bảo mật lên GitHub.
- **🚀 Chạy mọi lúc mọi nơi:** Hoạt động độc lập bằng file `index.html`, bật được thành trang web online cho điện thoại thông qua **GitHub Pages**.

---

## 🚀 Hướng Dẫn Sử Dụng

### 1. Lấy API Key (Miễn phí 100%)
1. Truy cập vào [Google AI Studio](https://aistudio.google.com/).
2. Đăng nhập Gmail ➡️ Bấm **Get API key** ➡️ **Create API key**.
3. Copy dãy ký tự API Key nhận được.

### 2. Bắt đầu trò chuyện
1. Mở file `index.html` trên trình duyệt (hoặc truy cập qua đường link GitHub Pages).
2. Dán API Key vào ô trên cùng ➡️ Bấm **Lưu & Kích Hoạt Key**.
3. Bắt đầu trò chuyện hoặc bấm các nút tác vụ nhanh (Tâm sự xả stress, Lên lịch ngày mai, Soạn tin nhắn...)!

---

## 📁 Cấu Trúc Dự Án

```text
├── index.html       # Toàn bộ giao diện (UI) và logic kết nối Gemini API
└── README.md        # Tài liệu hướng dẫn sử dụng dự án
