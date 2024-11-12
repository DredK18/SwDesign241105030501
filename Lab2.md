1. Ca Sử Dụng: Generate Reports
   
Mô tả: Tạo các báo cáo tổng hợp về lương, giờ làm, và các chi phí khác liên quan đến nhân viên và dự án.
Các lớp phân tích:
ReportGenerator: Lớp chuyên tạo báo cáo từ các dữ liệu của Employee, Paycheck, và Timecard.
Employee, Timecard, Paycheck: Cung cấp dữ liệu cho báo cáo.
Biểu đồ tuần tự:
Người dùng gửi yêu cầu tạo báo cáo.
ReportGenerator truy cập dữ liệu từ Employee, Timecard, và Paycheck để tổng hợp báo cáo.

![Diagram1](https://www.planttext.com/api/plantuml/png/R94nQiCm58PtdUBXlHVmKBAKBXrAIOUEgY8iKVjPo7B0OmwHCP0qb4Ac39ca8OCWzz09UeNA1b7iUX5wqlU9_qS_xhfe3DMchKf2cQarl3PS0sqWwpSPKV5ICgae6dZXgjRcaIFNj4TxQd8s5XugLTOTvmEPXZ7oJ3icEFiOa3ICaQMiEADwDI1fo0WPajxTJsFbyEPFBR1WlrimmHvgUFTnON4XqmfHJxboU0hsgmCZ_0KBC181XVz4M4j_mZapnPqnbP31NbieR-VR0OivEpMPiGiPt0vAlw_-Yz7iY-UmrC4UOHtSvgzVxEksyH4Ht56H1STL_DXV0000__y30000)

Biểu đồ lớp:

![Diagram2](https://www.planttext.com/api/plantuml/png/X92n3i8W48Ptde9HXxu0W-cWCMv6JPmHBYqfSCr1XyRuP0u-agyWXhOQOvI1uUF_BlznlzxA42N5pbcch0o1xw15YclmG38YyJFZprDb0FbvDXT3a5tO8AvSQx4768p2QC4tFa85b86N3WJVHpA-ogJ5OA91Fz5fs5RsgWRLZCEamyv7mPVOdInafbETHDBzyWx6WPAaHw_6Zi8HgG7zI_vSkYWMqpw2IwKW10XVOsFJFx6ns5ki1A_Jlpy0003__mC0)

Nhiệm vụ và Quan hệ:
ReportGenerator kết nối với các lớp chứa dữ liệu để tổng hợp.
Employee, Timecard, Paycheck cung cấp dữ liệu cho báo cáo.


2. Ca Sử Dụng: Update Employee Information
   
Mô tả: Quản lý việc cập nhật thông tin cá nhân, lương, và vị trí công việc của nhân viên.
Các lớp phân tích:
Employee: Lưu thông tin về nhân viên, như tên, vị trí, và lương.
EmployeeManager: Lớp chịu trách nhiệm cập nhật thông tin trong Employee.
Biểu đồ tuần tự:
Quản trị viên gửi yêu cầu cập nhật thông tin.
EmployeeManager thực hiện cập nhật dữ liệu trong Employee.

![Diagram3](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aO9ZIcvcda9YiO8IcAN4LG2KpapEB4ZCAr5mpIt8oQzCJVLDp4jCJoq2AqCJmwu1HQKI5nV45bqxT1Ej528FhofLI7wuQpcON5kWa9S1f4eKIZ8ERybBLoW1QilBEBmeJw4iy_2gF2vq5o4PQQNWJ8812hhON1DnU64on80y5ETWsWlK3VOKgfwC_CCByXHA7kvQMiBba9gN0Wfd00000F__0m00)

Biểu đồ lớp:

![Diagram4](https://www.planttext.com/api/plantuml/png/N8yx3i8m38RtdC8Z3Br01jG1XWvCdC0GKqLAx2WFf0fnCWQEn1LeQAb4lVcp_eVVprURCiPSl5CNXod1mGSd0z4H6NkAS5TGfmI3cNx7Zg-oeNdHYsQhuIRMg8TQcSqkZJKQEiuq6a-0qO_wKuwM-ua4IJPRuN-Qq64SDEobd1tLW7NFfjajSHhyboRL4flwsmS00F__0m00)

Nhiệm vụ và Quan hệ:
EmployeeManager quản lý và cập nhật dữ liệu cho Employee.
Employee cung cấp thông tin cập nhật cho các quá trình khác trong hệ thống.


3. Ca Sử Dụng: Manage Project Allocation
   
Mô tả: Xử lý phân công dự án cho nhân viên và quản lý thời gian làm việc liên quan đến từng dự án.
Các lớp phân tích:
Project: Đại diện cho dự án, chứa các mã số dự án và ngân sách.
EmployeeProjectAssignment: Theo dõi mối quan hệ giữa Employee và Project.

Biểu đồ tuần tự:
Người quản lý phân công Employee vào một Project.
EmployeeProjectAssignment cập nhật thông tin về dự án và nhân viên.

![Diagram5](https://www.planttext.com/api/plantuml/png/d96n2i9038RtUuhGtHVe81KH9y71mVLeZ_QapPKs2hvDAxWK70IdTd2u9-aJ-0fUzOGMB8XB4lB_-KZ8exbxEV6CzadCk4ygWnL77eeCU0wEhHsM6elqPSgHO96aiJeAiSxKJlWqotCPOYACqesCgjyXWvcXnH9U3bixZ7tMcqp75t5XgKi4ZFG9uI1rPQ8k50HjSmMZiF4JUbWNDf6k4g18tp04adyJRTE5ULjVKaCnYVhSNp26OsztOQjB_ur1Y9Gk4AYjpyGyWK7toIS0003__mC0)

Biểu đồ lớp:

![Diagram6](https://www.planttext.com/api/plantuml/png/X9112i8m44NtEKMM2lO2MKW5NNGdw0NIPWYHP58ogI3YoLnu9AzWQz8i2k8i__nvVsRUprTDKOOuECiwAudumVNMtm2EmL-WYpiYez41HdvdV2hvLMRRsMVZ2h8Y2cB3-zGJF9lMWb-zKUp15caPNXabU8CHD8Gae7GZyHI3GPsKtfE9ncDH2oo7pAmStYoHxQ0qZ3lj_T1QcCP_trnLsxAZu4wYr41__CVvwFGfOZMWcXxy0G00__y30000)

Nhiệm vụ và Quan hệ:
Employee kết nối với Project qua EmployeeProjectAssignment.
Quan hệ này giúp tính toán chi phí theo từng dự án khi kết hợp với Timecard và Paycheck.


Code java mô phỏng Maintain Timecard:

Lớp Employee đại diện cho nhân viên:

      class Employee {
    private int id;
    private String name;

    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }

    public int getId() {
        return id;
    }

    public String getName() {
        return name;
    }
      }

Lớp Timecard lưu trữ thông tin giờ làm việc của nhân viên:

      class Timecard {
    private int employeeId;
    private Date date;
    private double hoursWorked;

    public Timecard(int employeeId, Date date, double hoursWorked) {
        this.employeeId = employeeId;
        this.date = date;
        this.hoursWorked = hoursWorked;
    }

    public int getEmployeeId() {
        return employeeId;
    }

    public Date getDate() {
        return date;
    }

    public double getHoursWorked() {
        return hoursWorked;
    }

    public void setHoursWorked(double hoursWorked) {
        this.hoursWorked = hoursWorked;
    }

    @Override
    public String toString() {
        return "Timecard{" +
                "employeeId=" + employeeId +
                ", date=" + date +
                ", hoursWorked=" + hoursWorked +
                '}';
    }
      }

Lớp TimecardManager quản lý các thao tác thêm, cập nhật, và hiển thị Timecard:

      class TimecardManager {
    private List<Timecard> timecards = new ArrayList<>();

    // Thêm mới Timecard cho một nhân viên
    public void addTimecard(Employee employee, Date date, double hoursWorked) {
        Timecard timecard = new Timecard(employee.getId(), date, hoursWorked);
        timecards.add(timecard);
        System.out.println("Added: " + timecard);
    }

    // Cập nhật Timecard dựa trên mã nhân viên và ngày
    public void updateTimecard(int employeeId, Date date, double newHoursWorked) {
        for (Timecard timecard : timecards) {
            if (timecard.getEmployeeId() == employeeId && timecard.getDate().equals(date)) {
                timecard.setHoursWorked(newHoursWorked);
                System.out.println("Updated: " + timecard);
                return;
            }
        }
        System.out.println("Timecard not found for update.");
    }

    // Hiển thị tất cả Timecard của một nhân viên
    public void displayTimecards(int employeeId) {
        System.out.println("Timecards for Employee ID " + employeeId + ":");
        for (Timecard timecard : timecards) {
            if (timecard.getEmployeeId() == employeeId) {
                System.out.println(timecard);
            }
        }
    }
      }

Lớp MaintainTimecardUseCase mô phỏng ca sử dụng Maintain Timecard:

      public class MaintainTimecardUseCase {
      public static void main(String[] args) {
        Employee emp = new Employee(1, "Alice");
        TimecardManager manager = new TimecardManager();

        // Thêm Timecard mới
        Date date1 = new Date();
        manager.addTimecard(emp, date1, 8.0);

        // Cập nhật Timecard
        manager.updateTimecard(emp.getId(), date1, 9.5);

        // Hiển thị Timecard của nhân viên
        manager.displayTimecards(emp.getId());
    }
      }
