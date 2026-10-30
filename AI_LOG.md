# Nhật ký kiểm tra HTML

## Phạm vi

- Ngày kiểm tra: 30/10/2026.
- Tệp kiểm tra: `index.html`.
- Mục tiêu: tìm lỗi HTML ảnh hưởng biểu mẫu liên hệ và ghi lại lỗi cùng cách xử lý.

## Lỗi đã phát hiện và xử lý

| Dữ kiện trong mã ban đầu | Ảnh hưởng | Cách xử lý |
|---|---|---|
| Trường email khai báo `type="texr"` thay vì `type="email"`. | Trình duyệt không áp dụng kiểm tra định dạng email; giá trị sai định dạng vẫn có thể qua kiểm tra mặc định. | Đổi thành `type="email"`. |
| Form dùng `action="ket-qua.html"` nhưng dự án không có trang kết quả này. | Gửi form sẽ điều hướng tới đường dẫn không tồn tại. | Bỏ `action`; thêm xử lý submit phía trình duyệt trong `js/main.js`, ngăn điều hướng và thông báo đây chỉ là form mô phỏng. |
| Nút kiểm tra khai báo `type="button"` và không có xử lý sự kiện. | Bấm nút không kích hoạt kiểm tra hợp lệ của form hoặc phản hồi nào. | Đổi thành `type="submit"` để trình duyệt kiểm tra các ràng buộc `required`, `type`, `minlength`, `maxlength`; JavaScript hiển thị thông báo sau khi form hợp lệ. |
| Họ tên khai báo `minlength="0"`. | Không đặt ra độ dài tối thiểu hữu ích. | Đặt giới hạn 2–80 ký tự. |
| Sau khi sửa form không có vùng thông báo cho công nghệ hỗ trợ. | Người dùng trình đọc màn hình khó nhận biết kết quả kiểm tra thành công. | Thêm vùng trạng thái `role="status"` và `aria-live="polite"`. |

## Kết quả và giới hạn kiểm chứng

- Đã rà soát mã nguồn và xác nhận các thuộc tính/form handler được cập nhật trong `index.html` và `js/main.js`.
- Chưa xác nhận bằng thao tác trình duyệt. Cần thử form rỗng, email sai định dạng, tên ngắn hơn 2 ký tự, nội dung ngoài giới hạn và dữ liệu hợp lệ; xác nhận không điều hướng, không gửi và không lưu dữ liệu.
- Đây là ghi nhận lỗi và chỉnh sửa thực tế trong mã, không phải xác nhận GitHub Pages đã triển khai phiên bản mới.