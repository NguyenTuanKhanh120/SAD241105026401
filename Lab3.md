# Lab 3. Identify design elements
### Xác dịnh các phần tử thiết kế của hệ thống "Payroll System"
 # **BankSystem**
 #### Hệ thống con BankSystem là hệ thống Payroll System xử lý các giao dịch tài chính liên quan đến việc trả lương cho nhân viên.
1. **Nhận chỉ thị thanh toán (Payment Instructions):**
- ### Nhận yêu cầu thanh toán từ **Payroll System**, bao gồm các thông tin như:
    - ### Số tiền thanh toán.
    - ### Tài khoản ngân hàng của người nhận.
    - ### Các chi tiết giao dịch liên quan.
3. **Xử lý thanh toán (Payment Processing):**
- ### Xác thực thông tin giao dịch.
- ### Thực hiện giao dịch qua ngân hàng.
4. **Cung cấp số dư tài khoản (Account Balance):**
- ### Cung cấp thông tin số dư tài khoản cho các hệ thống liên quan để báo cáo và kiểm tra.
5. **Gửi sao kê ngân hàng (Bank Statements):**
- ### Tạo sao kê chi tiết về các giao dịch đã xử lý.
- ### Gửi sao kê đến các hệ thống khác, như dịch vụ in ấn (PrintService).
- 
## Biểu đồ ngữ cảnh của hệ thống con BankSystem.
![PlanText](https://www.planttext.com/api/plantuml/png/pLEnJiCm4Dqj-H-iCj0CKVSgYaeHGoI6YaoCnhYjXMD7lWiG0V-ExP8qRWipsvtzxkwzy_CAa3li6at9DRkr1ftreT0SWCqslFUfhdj0sSmO1vQSiA8GXugoP1-KCBPOC93cEU8QQP1L1j1r0fKrGCaN9M5CPL2wBHUI4ZM4h5fpyr9BzwfyKXGZPcZTEYiam4_ZEPzqPijXtkGm2qKxYJT2sCxWccjkX9nd7fmU1LmWNIFtccBlCVJWI6l8ir53tJt1OGaRPz_xSMKHVjpNCVMQOAnfGurNTdMlTdjyb5hRjtyfyywWmb7T-NYlIaP8MPw0l9UsoZNy5rHAxW8W8PJS1ruFKiVEi5UjDrPgopmlKpij_tHbwhpFF9-y6YMJ5mnzBwWxmvmk_kGwKKR9obEB_-yR "BankSystem")

### interface: là giao diện trung gian cho phép các hệ thống bên ngoài (như Payroll System) tương tác với BankSystem mà không cần biết cách thức thực hiện các giao dịch. Nó định nghĩa các phương thức như thanh toán, lấy số dư, và gửi sao kê để các hệ thống khác có thể sử dụng.
### Phương thức của interface:
- ### processPayment(aInstruction: PaymentInstruction): Xử lý các thanh toán chỉ định từ hệ thống khác.
  - #### Tham số: aInstruction(giao dịch thông tin cần thanh toán).
  - ####  Trả về: Một đối tượng PaymentConfirmationđược nhận dạng giao dịch trạng thái.
- #### getAccountBalance(): Lấy số dư tài khoản hiện tại từ ngân hàng.
  - #### Trả về: Đối tượng AccountBalancechứa thông tin về số dư tài khoản.
- #### sendStatement(aStatement: BankStatement): Gửi sao kê ngân hàng.
  - #### Tham số: aStatement(thông tin sao kê ngân hàng).
  - ####  Được gửi đến các dịch vụ khác, chẳng hạn như PrintService , để in hoặc lưu trữ.
