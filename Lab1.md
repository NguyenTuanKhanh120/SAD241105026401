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
![PlanText](https://www.planttext.com/api/plantuml/png/R90n3i8m34NtdCBAmjGBCA1MiB0XE86RM3Hg257igaA8ap5m9Av0WoWKmVhVj_ta-_LMic2Ixk1LHDFYda1l4Z45GN77eE6i0DH5VN0LetVcJR_O2WLhPFe1Ep9TSdBAOCXdi2N_NC6DYmmrIKyKuDLdDNM0mXxxK2nWSXdceDT1AA4Hw9qqMatfE37wv7fb33637QB_vT4nbvSDcHPC8ZjOEFIibIefsFoe1m000F__0m00) 
