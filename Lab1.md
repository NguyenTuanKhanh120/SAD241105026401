# Phân Tích Kiến Trúc và Ca Sử Dụng Hệ Thống "Payroll System"
## **1. Phân tích kiến trúc**
### Kiến trúc hệ thống có thể theo mô hình Client-Server, trong đó:
- #### Client : Giao diện người dùng chạy trên nền tảng Windows cho phép nhân viên nhập thông tin bảng chấm công, đơn đặt hàng và thay đổi các tùy chọn cá nhân. Server (Cơ sở dữ liệu DB2 của Acme): Lưu trữ thông tin của nhân viên và các dữ liệu liên quan đến dự án, mã chi phí. Ứng dụng lương: Chạy tự động vào thứ Sáu và ngày cuối tháng để tính toán và thanh toán lương. 
- #### Server (Cơ sở dữ liệu DB2 của Acme): Lưu trữ thông tin của nhân viên và các dữ liệu liên quan đến dự án, mã chi phí.
- #### Ứng dụng lương: Chạy tự động vào thứ Sáu và ngày cuối tháng để tính toán và thanh toán lương.
### Lý do lựa chọn kiến trúc: Kiến trúc Client-Server giúp phân tách rõ ràng giữa phần giao diện người dùng và phần xử lý dữ liệu, đồng thời dễ dàng quản lý bảo mật và yêu cầu hiệu suất.
### Ý nghĩa từng thành phần: 
- ### Client: Cung cấp giao diện đơn giản và an toàn cho nhân viên để tương tác với hệ thống.
- #### Server: Chịu trách nhiệm xử lý dữ liệu, tính toán và lưu trữ thông tin liên quan đến các khoản thanh toán.
- #### Ứng dụng lương: Thực hiện các quy trình thanh toán tự động và xử lý báo cáo.
## **Biểu đồ Package**
![PlanText](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWf9pJcPgNecIGZKNLoqNGZWujQWijGWah004S677WeASpEJ4aipyF0MVn4g82h2IMYvKbIw99Ob9YSMf19G5foQN5cMML2AKAK01L3bG0nUNGsfU2iZLN000003__mC0) 

## **2. Cơ Chế Phân Tích**
### Cơ chế cần giải quyết :
- #### Xử lý công việc của bảng : Xác định số giờ làm việc của nhân viên, xử lý giờ làm thêm (lương giờ).
- #### Tính toán lương cố định và hoa hồng : Đảm bảo tính toán chính xác cho nhân viên theo lương cố định và hoa hồng bán hàng.
- #### Phương thức thanh toán : Cho phép nhân viên lựa chọn phương thức thanh toán (email, chuyển khoản, nhận tại văn phòng).
- #### Bảo mật và phân quyền : Đảm bảo rằng chỉ có nhân viên và quản trị viên có quyền truy cập và chỉnh sửa thông tin của mình.
- #### Lý do : Những cơ chế này là cần thiết để hệ thống hoạt động chính xác, bảo mật và hiệu quả, đồng thời đảm bảo rằng lương được tính toán đúng và nhân viên được thanh toán đúng hạn.2. Cơ Chế Phân Tích
### Cơ chế cần giải quyết :
- #### Xử lý công việc của bảng : Xác định số giờ làm việc của nhân viên, xử lý giờ làm thêm (lương giờ).
- #### Tính toán lương cố định và hoa hồng : Đảm bảo tính toán chính xác cho nhân viên theo lương cố định và hoa hồng bán hàng.
- #### Phương thức thanh toán : Cho phép nhân viên lựa chọn phương thức thanh toán (email, chuyển khoản, nhận tại văn phòng).
- #### Bảo mật và phân quyền : Đảm bảo rằng chỉ có nhân viên và quản trị viên có quyền truy cập và chỉnh sửa thông tin của mình.
- #### Lý do : Những cơ chế này là cần thiết để hệ thống hoạt động chính xác, bảo mật và hiệu quả, đồng thời đảm bảo rằng lương được tính toán đúng và nhân viên được thanh toán đúng hạn.
## **3. Thanh toán Phân Tích Ca Sử Dụng**
 ### Các lớp phân tích cho ca sử dụng Payment :
- #### Nhân viên : Đại diện cho nhân viên, có thuộc tính như characterId, name, PaymentMethod, HourlyRate, CommissionRate, vv
- #### Hệ thống tính lương : Xử lý tính toán lương, bao gồm các phương thức như tính toánHourlyPayment(), tính toánFixedPayment(), generatePayslip().
- #### BankPayment : Thực hiện thanh toán qua chuyển khoản ngân hàng.
- #### EmailThanh toán : Gửi phiếu lương qua email.
### Biểu đồ Sequence :
![PlanText](https://www.planttext.com/api/plantuml/png/L95DJiGm34RtEOKrArXKx2k4HaKHsuXo0TEw8iBv8KubUZOM78ahaBGTcAxzlkTypi_NzraofZmxLZZaa42xo64X0XJGAfQP7Mn4d-5aS4c16Vf5ChbJ9Kn_H3hqxr0uHpwlG6UEW7Pe-K1eevI6vg6uMdYcZvaaGzm0PVhBv15vc1apWI1ZMk3cBSo9bxl9Vj8804DmpehOu6yLSeRrAIy9lKoKL05WatMc1PF2G2BmMfbypNG6cdtZ9LlCVhB9qQY8XM2jS2NKHTYJ7-kZXMq4-WFqlsqhBhLKOVTYkeKdyfHghJrTRd7VD6jalr9j5fbosNykqVfLlm000F__0m00)
### Phân Tích Biểu Đồ Sequence "Select Payment" 
- #### Nhân viên yêu cầu thanh toán.
- #### Hệ thống tính toán lương theo giờ hoặc lương cố định và hoa hồng.
- #### Lựa chọn phương thức thanh toán (chuyển tài khoản ngân hàng hoặc email).
- #### Hệ thống thực hiện thanh toán và tạo phiếu lương.
### Nhiệm vụ của từng lớp :
- #### Nhân viên : Cung cấp thông tin về nhân viên và phương thức thanh toán.
- #### Hệ thống lương : Thực hiện các phép tính lương và hoa hồng, tạo phiếu lương.
- #### Thanh toán ngân hàng : Chịu trách nhiệm chuyển tiền vào tài khoản ngân hàng.
- #### EmailThanh toán : Gửi phiếu lương qua email.
### Thuộc tính và quan hệ :
- #### Nhân viên có quan hệ 1-n với Hệ thống tính lương (mỗi nhân viên có thể có một hoặc nhiều phiếu lương).
- #### PayrollSystem có mối quan hệ với BankPayment và EmailPayment , tùy chọn theo phương thức thanh toán của nhân viên.
  #### Biểu đồ lớp : Biểu đồ lớp sẽ mô tả các lớp trên, với các thuộc tính và phương thức của từng lớp, đồng thời chỉ ra các quan hệ giữa chúng.

## **4. Phân Tích Ca Sử Dụng Duy Trì Timecard**
### Các lớp phân tích cho ca sử dụng Maintenance Timecard :
- #### Nhân viên : Đại diện cho nhân viên, có thuộc tính như nhân viênId, tên, timecardEntries.
- #### Timecard : Lưu trữ các bản ghi thời gian làm việc của nhân viên, có thuộc tính như ngày, giờĐã làm việc.
- #### TimecardSystem : Xử lý các thao tác nhập, sửa và xem bảng chấm công.
### Biểu đồ Sequence :
![PlanText](https://www.planttext.com/api/plantuml/png/R95DRW8n34RtEON5YagCsAEgObJD1HZeFagCi9gVKU8CojbOz4YzGfFEC2nWw-_vENP-Rp_xo39miaP8nJv0PmVZCoB82DrSQxKbLmkj60fCYWRf65P7igXaqD3do6XN5Jb-zg-XEHMYW-QZOZle76E0gm_VSF4fH2377dXk48LPq2zfI4l69GLq7FA3sK5VdZhbKmRhsh2PrNKAwZVHBie3ZeHNAFjPh-cSNmok40V24RUduNayOQo-kx2N8qukGlsmbONVcsP2bekbVvs6c9J26C_9c2psw7JzYJy0003__mC0)
### Phân Tích Biểu Đồ Sequence "Maintain Timecard"
- #### Nhân viên nhập thông tin về giờ làm việc vào bảng chấm công.
- #### Kiểm tra hệ thống và lưu thông tin vào TimecardSystem .
- #### Quản trị viên có thể thay đổi hoặc duyệt bảng chấm công.
#### Nhiệm vụ của từng lớp :
- #### Nhân viên : Nhập thông tin giờ làm vào bảng chấm công.
- #### TimecardSystem : Kiểm tra và lưu trữ bảng chấm công thông tin, thực hiện các thao tác như chỉnh sửa và xóa.
- #### Timecard : Lưu trữ thông tin chi tiết về thời gian làm việc.
#### Thuộc tính và quan hệ :
- #### Nhân viên có quan hệ 1-n với Timecard ( mỗi nhân viên có nhiều bản ghi thời gian).
- #### TimecardSystem xử lý các thao tác với Timecard .

## **5. Hợp nhất kết quả phân tích**
### Tổng quan về 2 ca sử dụng:
### 1. Ca Sử Dụng: Select Payment
#### Mô tả: Ca sử dụng này mô tả quy trình tính toán lương và thực hiện thanh toán cho nhân viên, bao gồm các bước từ việc tính toán lương đến việc lựa chọn phương thức thanh toán (chuyển khoản ngân hàng hoặc qua email).
## 2. Ca Sử Dụng: Maintain Timecard
### Mô tả: Ca sử dụng này mô tả quá trình quản lý bảng chấm công của nhân viên, từ việc nhập giờ làm việc đến việc sửa chữa và duyệt bảng chấm công.
## Hợp nhất các kết quả phân tích:
### Hai ca sử dụng trên đều nhằm mục đích xử lý các yếu tố liên quan đến việc thanh toán lương cho nhân viên, nhưng với các chức năng riêng biệt:
- #### Ca "Select Payment" tập trung vào việc xử lý yêu cầu thanh toán của nhân viên, với các phương thức thanh toán khác nhau (chuyển khoản, bưu điện, nhận trực tiếp).
- #### Ca "Maintain Timecard" giúp hệ thống quản lý và tính toán thời gian làm việc, từ đó xác định số tiền lương phải trả cho nhân viên, dựa trên thời gian và phương thức thanh toán.
### Biểu đồ Sequence hợp nhất:  
![PlanText](https://www.planttext.com/api/plantuml/png/X5HBJiCm4Dtd57C1nBvIKG4LnAvguG23CrMj-XCyqrOv6mkEn1MmqoIAqxJi4izxyzuRJ_Bx_RDWmI07QmfKuWCiRMLyJTI-FfPMkwAA4ArqXKxWNLjI6CfDpK9sifGThh0EtfW9-1EwVQnQSfATBorgqnMA-Rpt1F600iF9Xpti_24-QYSUfDM5-RpeiNSF8wimWsNY3-Z5237WHFG6ZvHhRNsmADgxnbQR3FXCLcZKmQ0G0wF1K8_jP9E8_TVqTI0MgDgeUNtA_veaQ8gk-iGb2jvEyKAYTiFC5p9ZNyzTa8PWQa1NWlBMQkQOlVCxqQbFEuDNSXHIZuXcewjkOea9bcJdIs0ofD8u_vlKfW5smYtzKdwmK97qjXqHG3DyHWX8GCTR2iMGaDjV1Q-8-VhT39VqcXWbJ94XSvKDnScs0uAZnfQHHjLyU13egEd4pGrGgOMpNJzZfXSbyUwNaT8pRg_9HrMcs-hRPyk-Y3xJB-8F003__mC0)
