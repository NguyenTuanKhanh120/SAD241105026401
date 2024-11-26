## Tổng hợp các ca sử dụng chính:
- ### Employee
- ### Timecard
- ### Paycheck
- ### PurchaseOder
- ### ProjectManagementDatabase
- ### BankSystem
## *I.Phân tích tất cả các ca sử dụng còn lại trong hệ thống Payroll System.*
### *1. Paycheck (Bảng lương)*
### Bảng lương là kết quả của việc tính toán tiền lương dựa trên số giờ làm việc, lương cơ bản và các khoản hoa hồng. Bảng lương có thể được tạo và phân phối cho nhân viên vào các kỳ thanh toán định kỳ.
### Ca sử dụng:
- ### Run Payroll: Hệ thống tự động tính toán bảng lương cho tất cả nhân viên vào mỗi kỳ thanh toán (thứ Sáu hoặc cuối tháng). Hệ thống sử dụng thông tin từ bảng chấm công, đơn hàng mua (với nhân viên nhận hoa hồng), và các thông tin khác để tính toán.
- ### Generate Paycheck: Dựa trên các yếu tố như giờ làm việc, tỷ lệ lương, và hoa hồng (nếu có), hệ thống sẽ tạo bảng lương cho từng nhân viên và chuyển chúng đến hệ thống ngân hàng (cho các nhân viên chọn phương thức thanh toán chuyển khoản).
### Biểu đồ Sequence: 
![PlanText]()
### *2. PurchaseOrder (Đơn hàng)*
### Đơn hàng là đối tượng được sử dụng bởi nhân viên có hoa hồng (Commissioned Employees) để ghi nhận các giao dịch bán hàng. Mỗi đơn hàng có thể được dùng để tính toán hoa hồng cho nhân viên.
### Ca sử dụng:
- ### Maintain Purchase Order: Nhân viên bán hàng có thể tạo, chỉnh sửa hoặc xóa các đơn hàng mà họ đã thực hiện trong hệ thống. Thông tin về khách hàng, sản phẩm bán, và ngày thực hiện sẽ được ghi lại.
- ### Calculate Commission: Các đơn hàng bán sẽ được dùng để tính hoa hồng cho nhân viên bán hàng. Tỷ lệ hoa hồng có thể dao động từ 10% đến 35% tùy theo chính sách của công ty.
### Biểu đồ Sequence: 
![PlanText]()
### *3. ProjectManagementDatabase (Cơ sở dữ liệu quản lý dự án)*
### Cơ sở dữ liệu này lưu trữ thông tin về các dự án, mã công việc, và các chi tiết liên quan. Các thông tin này sẽ được sử dụng trong bảng chấm công để phân bổ giờ làm việc cho các dự án cụ thể.
### Ca sử dụng:
- ### Maintain Timecard: Khi nhân viên ghi nhận giờ làm việc vào bảng chấm công, hệ thống sẽ lấy danh sách các mã công việc (charge number) từ cơ sở dữ liệu quản lý dự án để nhân viên có thể chọn mã phù hợp cho công việc mà họ đã làm.
### Biểu đồ Sequence: 
![PlanText]()
### *4. BankSystem (Hệ thống ngân hàng)*
### Hệ thống ngân hàng xử lý các giao dịch thanh toán cho nhân viên, đặc biệt là những nhân viên chọn phương thức thanh toán chuyển khoản trực tiếp.
### Ca sử dụng:
- ### Run Payroll: Sau khi tính toán bảng lương, hệ thống sẽ gửi thông tin thanh toán cho ngân hàng để xử lý các giao dịch chuyển khoản cho nhân viên chọn phương thức này.
- ### Process Payment: Hệ thống ngân hàng nhận thông tin từ hệ thống Payroll và thực hiện các giao dịch thanh toán cho nhân viên qua chuyển khoản ngân hàng.
### Biểu đồ Sequence: 
![PlanText]()
## *II. Mô phỏng Java cho ca sử dụng Maintain Timecard*
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
