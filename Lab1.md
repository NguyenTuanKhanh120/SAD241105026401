# **1. Phân tích kiến trúc**
## Kiến trúc 3 lớp (3-Tier Architecture):
- ### Lớp người dùng: Giao diện trên nền tảng Windows cho phép người dùng nhập thông tin, thay đổi cài đặt và xem báo cáo. Đây là nơi người dùng tương tác trực tiếp với hệ thống.
- ### Lớp ứng dụng: Đây là bộ phận xử lý logic tính toán lương, hoa hồng, quản lý bảng chấm công và tạo phiếu lương. Logic này cũng sẽ tự động tính toán và tạo báo cáo theo yêu cầu.
- ### Lớp dữ liệu: Hệ thống sẽ sử dụng cơ sở dữ liệu DB2 để lưu trữ dữ liệu về nhân viên, dấu chấm công và các đơn vị đặt hàng. Dữ liệu được truy cập từ các ứng dụng nhưng không được cập nhật trực tiếp   vào cơ sở dữ liệu dự án.
  
