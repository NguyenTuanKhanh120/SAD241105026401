## Phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.
### *1.Login*
### Mục đích: Cho phép người dùng đăng nhập vào hệ thống Payroll.
### Các bước chính:
- #### Người dùng nhập tên và mật khẩu.
- #### Hệ thống kiểm tra thông tin đăng nhập và xác thực người dùng.
- #### Luồng thay thế: Nếu thông tin không hợp lệ, hiển thị thông báo lỗi.
### *2. Maintain Employee Information*
### Mục đích: Cho phép Quản trị viên Payroll thêm, cập nhật hoặc xóa thông tin nhân viên.
### Các bước chính:
- #### Chọn chức năng cần thực hiện (Thêm, Cập nhật, Xóa).
- #### Nhập thông tin cần thiết.
- #### Hệ thống xử lý và lưu trữ thay đổi.
- #### Luồng thay thế: Hiển thị thông báo nếu nhân viên không tồn tại hoặc việc xóa bị hủy.
### *3. Create Administrative Report*
### Mục đích: Cho phép Quản trị viên Payroll tạo báo cáo tổng giờ làm hoặc lương năm đến thời điểm hiện tại.
### Các bước chính:
- #### Chọn loại báo cáo và cung cấp các tiêu chí (khoảng thời gian, tên nhân viên).
- #### Hệ thống tạo báo cáo dựa trên tiêu chí được nhập.
- #### Người dùng có thể lưu báo cáo.
- #### Luồng thay thế: Thông báo nếu thông tin không đủ hoặc định dạng không hợp lệ.
### *4. Create Employee Report*
### Mục đích: Nhân viên tự tạo các báo cáo cá nhân, ví dụ: tổng giờ làm, thời gian nghỉ phép.
### Các bước chính:
- #### Chọn loại báo cáo (Tổng giờ làm, Dự án cụ thể, Nghỉ phép/Số ngày bệnh, Lương năm-to-date).
- #### Nhập tiêu chí thời gian và chọn số dự án (nếu cần).
- #### Nhận báo cáo và lưu lại nếu muốn.
- #### Luồng thay thế: Hiển thị lỗi nếu thông tin không đầy đủ.
### *5. Run Payroll*
### Mục đích: Hệ thống tự động tính toán và xử lý trả lương vào các ngày cụ thể.
### Các bước chính:
- #### Lấy danh sách nhân viên cần trả lương.
- #### Tính toán lương dựa trên thời gian làm việc, đơn đặt hàng, thông tin nhân viên, và khấu trừ.
- #### In hoặc gửi tiền vào tài khoản ngân hàng.
- #### Luồng thay thế: Hệ thống cố gắng gửi lại giao dịch ngân hàng nếu hệ thống ngân hàng không khả dụng.
### *6. Maintain Purchase Order*
### Mục đích: Nhân viên hoa hồng thêm, cập nhật, hoặc xóa đơn đặt hàng để nhận tiền hoa hồng.
### Các bước chính:
- #### Chọn chức năng (Tạo, Cập nhật, Xóa).
- #### Nhập thông tin đơn đặt hàng.
- #### Hệ thống xử lý thay đổi.
- #### Luồng thay thế: Báo lỗi nếu thông tin đơn đặt hàng không hợp lệ hoặc đã bị đóng.

## *2. Mô phỏng Java cho ca sử dụng Maintain Timecard*
```markdown
```java
class Timecard {
    private String employeeId;
    private int hoursWorked;
    private boolean isSubmitted;

    public Timecard(String employeeId) {
        this.employeeId = employeeId;
        this.hoursWorked = 0;
        this.isSubmitted = false;
    }

    public void addHours(int hours) {
        if (isSubmitted) {
            System.out.println("Error: Timecard already submitted. Cannot add hours.");
            return;
        }
        if (hours < 0 || hours > 24) {
            System.out.println("Error: Hours must be between 0 and 24.");
            return;
        }
        this.hoursWorked += hours;
        System.out.println("Added " + hours + " hours. Total hours: " + this.hoursWorked);
    }

    public void submit() {
        if (isSubmitted) {
            System.out.println("Error: Timecard already submitted.");
            return;
        }
        isSubmitted = true;
        System.out.println("Timecard submitted successfully.");
    }

    public void display() {
        System.out.println("Timecard for Employee: " + employeeId);
        System.out.println("Total Hours Worked: " + hoursWorked);
        System.out.println("Status: " + (isSubmitted ? "Submitted" : "Draft"));
    }
}
public class Main {
    public static void main(String[] args) {
        // Khởi tạo timecard cho nhân viên
        Timecard timecard = new Timecard("E12345");

        // Thêm giờ làm việc
        timecard.addHours(8);
        timecard.addHours(6);

        // Hiển thị thông tin timecard
        timecard.display();

        // Gửi timecard
        timecard.submit();

        // Cố gắng thêm giờ sau khi gửi
        timecard.addHours(5);

        // Hiển thị timecard sau khi gửi
        timecard.display();
    }
}
