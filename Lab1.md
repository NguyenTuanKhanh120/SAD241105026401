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

# **2. Cơ Chế Phân Tích**
## Cơ chế cần giải quyết :
- ### Xử lý công việc của bảng : Xác định số giờ làm việc của nhân viên, xử lý giờ làm thêm (lương giờ).
- ### Tính toán lương cố định và hoa hồng : Đảm bảo tính toán chính xác cho nhân viên theo lương cố định và hoa hồng bán hàng.
- ### Phương thức thanh toán : Cho phép nhân viên lựa chọn phương thức thanh toán (email, chuyển khoản, nhận tại văn phòng).
- ### Bảo mật và phân quyền : Đảm bảo rằng chỉ có nhân viên và quản trị viên có quyền truy cập và chỉnh sửa thông tin của mình.
- ### Lý do : Những cơ chế này là cần thiết để hệ thống hoạt động chính xác, bảo mật và hiệu quả, đồng thời đảm bảo rằng lương được tính toán đúng và nhân viên được thanh toán đúng hạn.2. Cơ Chế Phân Tích
## Cơ chế cần giải quyết :
- ### Xử lý công việc của bảng : Xác định số giờ làm việc của nhân viên, xử lý giờ làm thêm (lương giờ).
- ### Tính toán lương cố định và hoa hồng : Đảm bảo tính toán chính xác cho nhân viên theo lương cố định và hoa hồng bán hàng.
- ### Phương thức thanh toán : Cho phép nhân viên lựa chọn phương thức thanh toán (email, chuyển khoản, nhận tại văn phòng).
- ### Bảo mật và phân quyền : Đảm bảo rằng chỉ có nhân viên và quản trị viên có quyền truy cập và chỉnh sửa thông tin của mình.
- ### Lý do : Những cơ chế này là cần thiết để hệ thống hoạt động chính xác, bảo mật và hiệu quả, đồng thời đảm bảo rằng lương được tính toán đúng và nhân viên được thanh toán đúng hạn.
# **3. Thanh toán Phân Tích Ca Sử Dụng**
 ## Các lớp phân tích cho ca sử dụng Payment :
- ### Nhân viên : Đại diện cho nhân viên, có thuộc tính như characterId, name, PaymentMethod, HourlyRate, CommissionRate, vv
- ### Hệ thống tính lương : Xử lý tính toán lương, bao gồm các phương thức như tính toánHourlyPayment(), tính toánFixedPayment(), generatePayslip().
- ### BankPayment : Thực hiện thanh toán qua chuyển khoản ngân hàng.
- ### EmailThanh toán : Gửi phiếu lương qua email.
## Biểu đồ Sequence :
- ### Nhân viên yêu cầu thanh toán.
- ### Hệ thống tính toán lương theo giờ hoặc lương cố định và hoa hồng.
- ### Lựa chọn phương thức thanh toán (chuyển tài khoản ngân hàng hoặc email).
- ### Hệ thống thực hiện thanh toán và tạo phiếu lương.
## Nhiệm vụ của từng lớp :
- ### Nhân viên : Cung cấp thông tin về nhân viên và phương thức thanh toán.
- ### Hệ thống lương : Thực hiện các phép tính lương và hoa hồng, tạo phiếu lương.
- ### Thanh toán ngân hàng : Chịu trách nhiệm chuyển tiền vào tài khoản ngân hàng.
- ### EmailThanh toán : Gửi phiếu lương qua email.
## Thuộc tính và quan hệ :
- ### Nhân viên có quan hệ 1-n với Hệ thống tính lương (mỗi nhân viên có thể có một hoặc nhiều phiếu lương).
- ### PayrollSystem có mối quan hệ với BankPayment và EmailPayment , tùy chọn theo phương thức thanh toán của nhân viên.
  ### Biểu đồ lớp : Biểu đồ lớp sẽ mô tả các lớp trên, với các thuộc tính và phương thức của từng lớp, đồng thời chỉ ra các quan hệ giữa chúng.
# **Biểu đồ lớp mô tả lớp phân tích**
![PlanText](https://www.planttext.com/api/plantuml/svg/b5HBRjim4Dth50GtiOlOQBTP14cG1EcYW94Mw9gc9XPXKbGv91AtwCcww95wXOvaYgOaEq6u8J0pRpxl3VdlpzyhzCBvO7GXjK1aTwRHTWV0VXMCpe91D7mksGNxwfsgDz5J2mDZMoDs1ch_1Nnb9u3A1gTtZyAti5iRrXgYHrfZ5AAozTJB68QrKVwRCY25AsVpQ7Rm8m3wrRuacNyNSOW-D0rHngnqPRtWT-ksK8xBRS0_jDvK27j31qhXMK7gmLcjLyvAGBGk5cPC2Ys3fh8FtUnzhpsfbAidV3vk8q7lrGkKxq5ke0P7GCAWLiqfJ7GFfcWD1zR02wLnA6F7p-tUapFKcyQWZAM-ECaWrW8XiVG4NbQvTtPaw-PP-n4NcbROey1yraC7DwBUHYPJyMOlsYi4dpDXR2384UNl34qxJebGbw-GVzu-auxf94AMyJhuYf8fANosIE9WXLb0S1apRJx4P-k6PDrOgq7KmypMgP-GxMS5Shi25r_VDBEGdkodyfwnHw0LfGYiL8D5-Ztu9yuM2yO_BfSV-E4zNZ1U2UJZkClkdZmYYgP-A7pY6S4YbxnV_BSW-HeGB6x0cx21reHhPSw6IMizn2JvEPAWC9v-kRmSIKwHkTgd0559Ykv4HDOa6NbnHQsrdpgT_m000F__0m00)
# 3. Thanh toán Phân Tích Ca Sử Dụng
## Các lớp phân tích cho ca sử dụng Payment :
- ## Nhân viên : Đại diện cho nhân viên, có thuộc tính như characterId, name, PaymentMethod, HourlyRate, CommissionRate, vv
- ## Hệ thống tính lương : Xử lý tính toán lương, bao gồm các phương thức như tính toánHourlyPayment(), tính toánFixedPayment(), generatePayslip().
- ## BankPayment : Thực hiện thanh toán qua chuyển khoản ngân hàng.
- ## EmailThanh toán : Gửi phiếu lương qua email.
 ## Biểu đồ Sequence :
- ## Nhân viên yêu cầu thanh toán.
- ## Hệ thống tính toán lương theo giờ hoặc lương cố định và hoa hồng.
- ## Lựa chọn phương thức thanh toán (chuyển tài khoản ngân hàng hoặc email).
- ## Hệ thống thực hiện thanh toán và tạo phiếu lương.
 ## Nhiệm vụ của từng lớp :
- ## Nhân viên : Cung cấp thông tin về nhân viên và phương thức thanh toán.
- ## Hệ thống lương : Thực hiện các phép tính lương và hoa hồng, tạo phiếu lương.
- ## Thanh toán ngân hàng : Chịu trách nhiệm chuyển tiền vào tài khoản ngân hàng.
- ## EmailThanh toán : Gửi phiếu lương qua email.
 ## Thuộc tính và quan hệ :
- ## Nhân viên có quan hệ 1-n với Hệ thống tính lương (mỗi nhân viên có thể có một hoặc nhiều phiếu lương).
- ## PayrollSystem có mối quan hệ với BankPayment và EmailPayment , tùy chọn theo phương thức thanh toán của nhân viên.
## Biểu đồ lớp : Biểu đồ lớp sẽ mô tả các lớp trên, với các thuộc tính và phương thức của từng lớp, đồng thời chỉ ra các quan hệ giữa chúng.
![PlanText](https://www.planttext.com/api/plantuml/png/V5BBJiCm4BpxArQ-q21ImRL2KGz50eaJHUBirglKgfr4MGTK8RwC0v_4B-0aTa8UIYwEPcVMi-Fz_VxPaXMbhOncHos8uC4KEhyWmYS3zyM07dYIi86zBLMM-aec38unYOLhPp2pmme0LGUZxAioU1IbN5d_usW1YpppNU57m6WLESQp8diVe8HzCMysG9tPq7LgLWfRczsvmoEdl2hfBI_FM9DtUNNGw1saQ1_xQcDXKATXlUdKSQAfl_s5B1hl4a18sUKGudNo4FqDB8HJ5VKaanZ_3RmeTvFrqSuyxKpQhL2YnkLxcxclu0Mri2hFwAGAOjqwyJiESGpyThs-vlt3RO2tYq6SZT9g5ScSn8XCfEWae_P9SuxwE7v5DNcBcQmN_Gy00F__0m00)
# **5. Hợp nhất kết quả phân tích**
![PlanText](https://www.planttext.com/api/plantuml/png/b5LDRjGm5Dxd54_PT0RDLB2jK5MX5XMfI8KYiNRZrunLEmx-0KQ8DOTWnGaum2nOS98vGQ-0azXEugHJaOtZx_bxFzzxSHvsVywq8SfOmRCZkDhlVjPm8MekjuXPmOdMSGlVCd3F6j03RoYSm8rHh2gzfI82KunYxVmBh4nggScsWT-YsSY9gusqYc_V4zCuF9VsbgEt5588fZMJrTGAeEsjOEO34rWGHHV6lxXZ0Llwame_MTJckijY4U3F3B-4etgnTCGhfitB09rctxEeL02zKc4RbGhHfqfHdxfR1WNhZrBT8qrhAj5SzjOsft7DOtlhAPvPpYLyizK6HP9s1_ha0GYbKSRGSkSrZCCA3cXhwwR0IHS6EXoakuBx5ioCsqnNEY95ZeVZZkHmlLUIysib2zHQAYz82aT92i8Borrbb-rqXj6PKMVIeqXzpRuY_HzcYHKgHtGSpLdz6CURa_9QA5RLxE9mrjr-PZRH4CRr66wRSjvPsWaSsNHlIzaZmL-HwjxNxhCQ857ckXF-W4Wh84BQzagPcV8BuJ8OXnb2COx6YXvGTHKawjNrOTvPKi5cl_i19TllVXCe_lugW3V1itXTvYzoMAyXVtvy_2plxuOJoBixIkVfsTDsdKoVOrYD6kxSkxypyopvQAE3QJH1AbBYOz4IFyDOuUjnr4bEIS9UfJpCwbEKOTSTpJVyITgeYusGhe6ES-QMvWVs3m00__y30000)
