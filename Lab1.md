# **1. Phân tích kiến trúc**
## Kiến trúc hệ thống có thể theo mô hình Client-Server, trong đó:
- ### Client : Giao diện người dùng chạy trên nền tảng Windows cho phép nhân viên nhập thông tin bảng chấm công, đơn đặt hàng và thay đổi các tùy chọn cá nhân. Server (Cơ sở dữ liệu DB2 của Acme): Lưu trữ thông tin của nhân viên và các dữ liệu liên quan đến dự án, mã chi phí. Ứng dụng lương: Chạy tự động vào thứ Sáu và ngày cuối tháng để tính toán và thanh toán lương. 
- ### Server (Cơ sở dữ liệu DB2 của Acme): Lưu trữ thông tin của nhân viên và các dữ liệu liên quan đến dự án, mã chi phí.
- ### Ứng dụng lương: Chạy tự động vào thứ Sáu và ngày cuối tháng để tính toán và thanh toán lương.
## Lý do lựa chọn kiến trúc: Kiến trúc Client-Server giúp phân tách rõ ràng giữa phần giao diện người dùng và phần xử lý dữ liệu, đồng thời dễ dàng quản lý bảo mật và yêu cầu hiệu suất.
## Ý nghĩa từng thành phần: 
- ## Client: Cung cấp giao diện đơn giản và an toàn cho nhân viên để tương tác với hệ thống.
- ## Server: Chịu trách nhiệm xử lý dữ liệu, tính toán và lưu trữ thông tin liên quan đến các khoản thanh toán.
- ## Ứng dụng lương: Thực hiện các quy trình thanh toán tự động và xử lý báo cáo.
# **Biểu đồ Package mô tả kiến trúc.**
![PlanText](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWf9pJcPgNecIGZKNLoqNGZWujQWijGWah004S677WeASpEJ4aipyF0MVn4g82h2IMYvKbIw99Ob9YSMf19G5foQN5cMML2AKAK01L3bG0nUNGsfU2iZLN000003__mC0) 
