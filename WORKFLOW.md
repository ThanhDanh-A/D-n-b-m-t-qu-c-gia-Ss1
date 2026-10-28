# 🔄 QUY TRÌNH HOẠT ĐỘNG DỰ ÁN (WORKFLOW)

Tài liệu này mô tả chi tiết luồng xử lý kỹ thuật, cách quản lý dữ liệu và cơ chế vận hành của ứng dụng Trợ Lý Cá Nhân AI.

---

## 1. Sơ Đồ Luồng Xử Lý (Data & Logic Flow)
[1. Người dùng nhập tin nhắn]
│
▼
[2. Frontend nạp Soul Prompt]
- Gắn tính cách: Xưng mình/bạn, thân thiện, đời thường
- Định dạng hội thoại: alternating turn (user / model)
│
▼
[3. Gọi Google Gemini API] (Model chính: gemini-3.5-flash-lite)
│
┌─────┴────────────────────────┐
▼ (Thành công) ▼ (Nếu gặp lỗi quá tải / High Demand)
[4. Nhận dữ liệu JSON] [4b. Cơ chế Dự phòng (Fallback)]
│ - Tự động chuyển sang gemini-3.8-flash
│ - Thử lại tối đa 3 lần
│ - Nếu quá 12s -> Hủy qua AbortController
│ │
└────────────────────────┬───────────┘
▼
[5. Xử lý & Hiển thị]
- Tách nội dung (loại bỏ thought part nếu có)
- Dùng Marked.js biên dịch Markdown thành HTML
- Cuộn màn hình tự động xuống câu trả lời mới
code
Code
---

## 2. Quy Trình Bảo Mật Khóa API (Security Workflow)

1. **Không lưu trữ cứng (No Hardcode):** Tuyệt đối không nhúng chuỗi API Key vào mã nguồn khi đẩy lên Git.
2. **Lưu trữ cục bộ (Client-side Storage):** Khóa được lưu trữ tại `localStorage` của trình duyệt người dùng.
3. **Gọi trực tiếp (Direct Client-to-API):** Dữ liệu truyền trực tiếp từ trình duyệt đến máy chủ Google qua HTTPS, không qua bất kỳ máy chủ trung gian nào.

---

## 3. Quy Trình Xử Lý Lỗi (Error Handling Workflow)

| Tình Huống Lỗi | Nguyên Nhân | Cách Hệ Thống Tự Động Xử Lý |
| :--- | :--- | :--- |
| **Lỗi 503 / 429 (High Demand)** | Máy chủ Google quá tải | Tự động chuyển từ model Flash-Lite sang Flash 3.8 dự phòng. |
| **Treo mạng / Phản hồi lâu** | Đường truyền chập chờn | Kích hoạt `AbortController` ngắt sau 12 giây, báo người dùng thử lại. |
| **Gửi dồn tin nhắn** | Người dùng bấm gửi liên tục | Tự động vô hiệu hóa (`disabled`) nút gửi và ô nhập liệu trong lúc AI đang suy nghĩ. |
