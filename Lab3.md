# Lab 3. Identify design elements
# *1.Subsystem context diagrams*
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
### Phương thức 
- ### processPayment(aInstruction: PaymentInstruction): Xử lý các thanh toán chỉ định từ hệ thống khác.
  - #### Tham số: aInstruction(giao dịch thông tin cần thanh toán).
  - ####  Trả về: Một đối tượng PaymentConfirmationđược nhận dạng giao dịch trạng thái.
- #### getAccountBalance(): Lấy số dư tài khoản hiện tại từ ngân hàng.
  - #### Trả về: Đối tượng AccountBalancechứa thông tin về số dư tài khoản.
- #### sendStatement(aStatement: BankStatement): Gửi sao kê ngân hàng.
  - #### Tham số: aStatement(thông tin sao kê ngân hàng).
  - ####  Được gửi đến các dịch vụ khác, chẳng hạn như PrintService , để in hoặc lưu trữ.
### Mô tả giao tiếp:
- #### Payroll System gửi thông tin giao dịch (qua PaymentInstruction) tới BankSystem qua phương thức processPayment(). BankSystem trả về PaymentConfirmation xác nhận kết quả.
- #### BankSystem gửi sao kê ngân hàng (qua BankStatement) tới PrintService để in ấn.
- #### BankSystem cung cấp số dư tài khoản (qua AccountBalance) qua phương thức getAccountBalance() cho các hệ thống tài chính khác.

# **PrintService**
#### PrintService là một hệ thống con trong Payroll System, chịu trách nhiệm xử lý các yêu cầu in ấn. Cụ thể, nó đảm nhận việc nhận tài liệu cần in (như phiếu lương Payslip) và tương tác với máy in để hoàn tất quá trình in.
### Biểu đồ ngữ cảnh của hệ thống con PrintService
 ![PlanText](https://www.planttext.com/api/plantuml/png/h5B1JiCm3BtdAwnnO4XKkrTHDGauJE8mRIUEeHWMAKrAx0uguCiuy4dy0ccRL7IzxlRyx6S_E_dz_baJAyzDPSGbt3ZBtXbH6aK4YwrgGsGYQz0lG17CM92o78AYW0y1i5f1xLs9H5klBU_mjK7YvPNu4c78nZBwPrMYq0d1fY_Sep_g44avriIETPU-TMLJeUMbIWXoIF0QdEsR13yvH1Gdxfj7Qecn2hnxRyVr_iqSDfkQe55MTx9WvU9Ulnpu0OrnRsVmTMTPSx8pQgN4dY-Ac8cYJh53erWxImTTavY_H9OL9xVCWT0-qU0K_F0K14UjnCdHFxDiSW4nINUTayLv9bbSXrdTL_e3003__mC0 "PrintService")
### Interface: là giao diện trung gian cho phép các hệ thống khác tương tác với hệ thống PrintService để yêu cầu in tài liệu. Giao diện này định nghĩa các phương thức mà PrintService phải thực hiện để xử lý yêu cầu in.
### Phương thức 
##### printDocument(aDocument: Document, onPrinter: Printer): Phương thức này nhận tài liệu cần in và máy in để gửi tài liệu đến máy in.
- #### aDocument (Document): Tài liệu cần in (ví dụ: phiếu lương).
- #### onPrinter (Printer): Máy in cụ thể nơi tài liệu sẽ được gửi đến.
### Mô tả giao tiếp
- #### PayrollController gửi yêu cầu in phiếu lương (hoặc tài liệu khác) thông qua IPrintService.
  - #### Giao tiếp: PayrollController yêu cầu IPrintService thực hiện phương thức printDocument.
- #### IPrintService là giao diện, và phương thức printDocument sẽ được hiện thực trong lớp PrintService.
  - #### Giao tiếp: IPrintService gọi đến PrintService để thực hiện hành động in tài liệu.
- #### PrintService thực hiện in tài liệu vào máy in cụ thể (Printer).
  - #### Giao tiếp: PrintService sử dụng đối tượng Printer để thực hiện thao tác in tài liệu.
- #### Sau khi in xong, PrintService trả kết quả cho PayrollController, thông báo về trạng thái việc in (thành công, lỗi, v.v.).

# **ProjectManagementDatabase subsystems**
#### ProjectManagementDatabase subsystems là một hệ thống con trong hệ thống tổng thể, có vai trò cung cấp thông tin liên quan đến các dự án và các mã chi phí cho hệ thống Payroll. Đây là một cơ sở dữ liệu lưu trữ thông tin về các dự án đang thực hiện, các chi phí, và các dữ liệu liên quan, giúp Payroll System tính toán bảng lương chính xác.
### Biểu đồ ngữ cảnh của hệ thống con ProjectManagementDatabase subsystems
![PlanText](https://www.planttext.com/api/plantuml/png/f5AzJiCm4Dxz5ASoq0vHzwgoAW5392fLT6Ay9jVKoB63VG4YuCaOU2HU0Rj98qiPkztvFdr_yj_FxyOpEcvhBMxXpXfsLej2e_Smss4NDZsyQd8pG0-JLrYlYtwH4Zu5m789hosvRkVi2nLyZuppXVWMGI4tJEw81GbrcI1FS0Vq5FX6sC1O4G-Wt1pjl1dc4bQmPwTCjGXJGjEBxTk3xpnJ7KyVtHYhnstHO4KrcL6uZxTDVFYHeOaCmStDewfE_4nQs_Shh3qOLdnnb5o39frFKaRO4sbaPOq_gSQBQVDP9gVrhSxjA_9GHiOtXM9QyLUM9L55aZfofdutPChuFVu1003__mC0 "ProjectManagementDatabase")
### Interface:
- #### IProjectDatabase: là giao diện trung gian để tương tác với các hệ thống trong ProjectManagementDatabase
### Phương thức
- #### getProjectInfo(projectId: String): ProjectData
  - #### Mô tả: Truy vấn thông tin dự án dựa trên mã dự án projectId.
  - #### Đầu vào: projectId (String)
  - #### Đầu ra: ProjectData (Thông tin chi tiết về dự án)
 ### Mô tả giao tiếp
- #### PayrollController -> IProjectDatabase (Yêu cầu thông tin dự án)
- #### IProjectDatabase -> ProjectManagementDatabase (Truy vấn dữ liệu)
- #### ProjectManagementDatabase -> ProjectData (Trả về thông tin dự án)
- #### PayrollController sử dụng ProjectData cho các mục đích liên quan đến bảng lương và quản lý tài chính.
# *2.Analysis class to design element map*
### Mapping Analysis Classes to Design Elements

| **Analysis Class**          | **Design Element**               | **Description** |
|-----------------------------|----------------------------------|-----------------|
| **PayrollController**        | Controller                       | Coordinates the processing of requests in the system.      |
| **Employee**                 | Entity                           | Represents employee data and information.                  |
| **Payslip**                  | Entity                           | Represents employee payslips, storing payment details and salary breakdowns.   |
| **Printer**                  | Entity                           | Represents the printer for handling print jobs.            |
| **PrintService**             | Subsystem Proxy                  | Subsystem responsible for handling print requests from the Payroll System. |
| **BankSystem**               | Subsystem Proxy                  | Subsystem responsible for processing banking transactions. |
| **ProjectManagementDatabase**| Subsystem Proxy                  | Subsystem providing project and charge code information.   |
| **IPrintService**            | Interface                        | Interface providing printing functionalities in the system. |
| **IProjectDatabase**         | Interface                        | Interface providing functionalities to query project information. |

## **3. Design element to owning package map**

### Mapping Design Elements to Owning Packages

| **Design Element**               | **Owning Package**      |                                                                
|----------------------------------|-------------------------|
| **PayrollController**            |  controller             | 
| **Employee**                     |  entity                 | 
| **Payslip**                      |  entity                 |
| **Printer**                      |  entity                 |
| **PrintService**                 |  subsystem.print        | 
| **BankSystem**                   |  subsystem.bank         |
| **ProjectManagementDatabase**    |  subsystem.database     | 
| **IPrintService**                |  interfaces             | 
| **IProjectDatabase**             |  interfaces             | 

## **4. Architectural layers and their dependencies**
![PlanText](https://www.planttext.com/api/plantuml/png/b9I_Rjim4CPtFSNL7Je5sOt0o5zaSGAZyTBnJD4I6ufaICgjK6Jkt4VeK7GgiiT3Xpo9dg2lq2CbHKegDyXcMtVVT_UxJ_wp_NteF5fV5Z9va_ArK1pUdvqiZoxFvsV093gNl8DbVVzJPN0kK4CgwkrNbHXarvXnc2miTrnvz48hc6F5xGI-931GcIomibfAED7AXm-XvE20DTzcirWEiByFEQfKSZ1jlUKt9NVUqUFRPufMA7_5xKOm7hHSkNALyxm0O_NdYZJVpaMM-mzSIlsfDp2XB-WxAOm3iYCJesthSPlqorvcUTZKmARU_kZNFIuTCN8EvZeJx8M55rOpgjMxzcKeMIdHSt0eqLPn8DCqFLAGmMW4GGUrrI3ymOLE8NmrD37ShhKj7iseq07zqXdyi_dIbXMm-lwNWTDwUmSoS2Xx1AVe4OvO779y_sDKrrVn7gyvJe4gwA-e6Rn5vP35OSVEhpzovYzYGq4hXv5Mw5wLXIviZLP4ptAqD07JAHy4ugBUVXDmKwA2d4X0HZpk4DZ3TmO-8aj68xwtDnkDmXHAH_hFGhoxcbwlrBNHRL-9PAmoAWpHJsbeRWLlpZr02aAjzMwD_-3j9JjkZTJGziacJ-8vxS9D_V7C5C6W7s7iz7n1RoFImJWfjIM7H2pye_q5003__mC0 "Layers")
