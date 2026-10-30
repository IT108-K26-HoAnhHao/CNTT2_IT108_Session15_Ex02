
## Phần 1: Phân tích tình huống

### Tại sao hành động của An được gọi là vi phạm "Quy tắc Cờ Đỏ Bảo mật"?

Hành động của An phạm phải các lỗi bảo mật nghiêm trọng (Cờ Đỏ Bảo mật) sau đây:

1. **Sử dụng chế độ chia sẻ quá rộng ("Anyone with the link"):** 
   - Việc mở quyền truy cập công khai cho bất kỳ ai có đường dẫn khiến tài liệu mất đi lớp kiểm soát danh tính. Bất cứ ai tình cờ có được link đều có thể truy cập mà không cần xác thực tài khoản.
2. **Lạm dụng mức quyền cao nhất (Editor) cho đối tượng không đáng tin cậy/chưa được kiểm chứng:** 
   - Cấp quyền `Editor` cho phép người nhận không chỉ xem mà còn có toàn quyền chỉnh sửa, thêm, hoặc **xóa dữ liệu**. Đối với dữ liệu nhạy cảm (như danh sách SĐT khách hàng), việc cấp quyền này mang rủi ro cực kỳ cao.
3. **Thiếu kiểm soát phân phối thông tin:** 
   - Không giới hạn người xem bằng email cụ thể (Restrict access) dẫn đến việc link bị phát tán công khai lên mạng xã hội (Hội nhóm bất động sản), biến dữ liệu nội bộ thành tài nguyên công cộng cho kẻ xấu lợi dụng trục lợi hoặc phá hoại.

---

## Phần 2: Sửa lỗi & Thiết lập cấu trúc phân quyền chuẩn

Để khắc phục và đảm bảo an toàn tuyệt đối cho tài liệu, An cần thiết lập lại cấu trúc phân quyền như sau:

### (1) Mức quyền nào cho cộng tác viên?
- **Mức quyền khuyên dùng:** `Commenter` (hoặc tối đa là `Viewer` nếu cộng tác viên chỉ cần đọc dữ liệu để lấy thông tin).
- **Lý do:** Cộng tác viên chỉ cần đọc hoặc góp ý, tuyệt đối không cần quyền `Editor` trực tiếp trên file gốc chứa dữ liệu khách hàng. Nếu cần chỉnh sửa nội dung, họ nên đề xuất qua mục bình luận để chủ sở hữu kiểm duyệt trước khi cập nhật.

### (2) Chế độ chia sẻ nào là an toàn 100%?
- **Chế độ an toàn tuyệt đối:** **Restricted (Chỉ những người được thêm mới có quyền truy cập)**.
- **Cách thực hiện:** Thay vì dùng "Anyone with the link", An bắt buộc phải nhập chính xác địa chỉ email cá nhân hoặc email công việc của từng cộng tác viên được cấp phép để chia sẻ.

### (3) Cần bật tính năng gì để ngăn cộng tác viên tự ý mời thêm người lạ?
- **Tính năng cần kích hoạt trong cài đặt chia sẻ nâng cao:**
  - Bật tùy chọn: **"Disable options to download, print, and copy for commenters and viewers"** (Tắt quyền tải xuống, in và sao chép đối với người xem/nhận xét - nếu dùng Google Drive).
  - Bật tùy chọn: **"Prevent editors from changing access and adding new people"** (Chặn người chỉnh sửa thay đổi quyền truy cập hoặc thêm người mới). Điều này đảm bảo chỉ có duy nhất **Chủ sở hữu (Owner)** mới có quyền quản lý danh sách thành viên tham gia tài liệu.