# Thiết Kế Hệ Thống Payroll System

## 1. Xác Định Các Lớp Chính Trong Hệ Thống

### **BankSystem**:
- **Lớp**:
  - `BankTransaction`: Quản lý thông tin về giao dịch ngân hàng.
  - `BankInformation`: Lưu thông tin ngân hàng (tên ngân hàng, mã định tuyến).
- **Giao diện**:
  - `IBankSystem`: Định nghĩa các thao tác liên quan đến ngân hàng, như gửi tiền (deposit).

### **PrintService**:
- **Lớp**:
  - `PaycheckPrinterImage`: Tạo hình ảnh in từ thông tin phiếu lương.
- **Giao diện**:
  - `IPrintService`: Định nghĩa các thao tác in ấn.

### **ProjectManagementDatabase**:
- **Lớp**:
  - `ChargeNumList`: Quản lý danh sách các mã dự án.
- **Giao diện**:
  - `IProjectManagementDatabase`: Định nghĩa các thao tác truy vấn và quản lý cơ sở dữ liệu.

---

## 2. Xác Định Các Thuộc Tính và Phương Thức

### **Lớp Paycheck**:
- **Thuộc tính**:
  - `amount: float`: Số tiền trong phiếu lương.
  - `employeeId: int`: Mã nhân viên được liên kết với phiếu lương.
- **Phương thức**:
  - `create(forAmount: float): Paycheck`: Tạo phiếu lương với số tiền cụ thể.
  - `getAmount(): float`: Lấy thông tin về số tiền trong phiếu lương.
  - `getEmployee(): Employee`: Lấy thông tin nhân viên của phiếu lương.

### **Giao diện IBankSystem**:
- **Phương thức**:
  - `deposit(aPaycheck: Paycheck, intoBank: BankInformation): void`: Gửi phiếu lương vào tài khoản ngân hàng.

---

## 3. Quan Hệ Giữa Các Lớp

- `Paycheck` **kết hợp** với `Employee` (quan hệ 1-1): Một phiếu lương được gắn với một nhân viên cụ thể.
- `IBankSystem` **sử dụng** `BankTransaction` (quan hệ phụ thuộc): Các thao tác ngân hàng sẽ tạo hoặc tương tác với các giao dịch.
- `PrintService` **sử dụng** `PaycheckPrinterImage` để tạo hình ảnh in từ phiếu lương.

#### Biểu đồ UML :
![PlanText](https://www.planttext.com/plantuml/png/N94xRiCm44HxdcAXoYvKf6KHE85Jg34Cw0GRQgKGviSWLm64m2TBaIFb2W5bIX7TaVDsPWVax_VF8J867gqHoc2CSCP9VP2wm9S00AW1hHyTI-YDHvur01K8cNQz3ozRkfUhFGyEnFU9tRvC68ZVxDNuYIYXvInk8lTObBM7GqiIMWxQ3LcYFDDq4hIxHzSGlT9eMb9Zq3oTHljEuS68NHSena8jEZN7r6h9dD49xLmrMsv2h4zLry__VILKJvKGsZ657XL1yuhkqawHoPQM3KYk8rrzr9osUaYeJ3a7xRYbyAaLFUHiKKgQxvKuaElIn_u1003__mC0)
---

## 4. Trạng Thái Của Các Lớp Quan Trọng

### **Trạng thái của `BankTransaction`**:
- **Trạng thái khởi đầu**: *Initialized*: Giao dịch được khởi tạo nhưng chưa gửi.
- **Trạng thái trung gian**: *Submitted*: Giao dịch đã được gửi đi.
- **Trạng thái hoàn thành**: *Completed*: Giao dịch đã được xử lý xong.

---

## 5. Phụ Thuộc Hệ Thống

- **PrintService** sử dụng giao diện `IBankSystem` để thực hiện thao tác liên quan đến phiếu lương được gửi qua ngân hàng.
- **ProjectManagementDatabase** cung cấp dữ liệu mã dự án mà **BankSystem** và **PrintService** có thể tham chiếu để thực hiện các giao dịch hoặc in báo cáo.

---
