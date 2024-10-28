1. Phân Tích Kiến Trúc
Mục Đích
Phân tích yêu cầu hệ thống để đề xuất kiến trúc thích hợp cho bài toán Payroll System.

Kiến trúc Đề xuất: Kiến trúc Ba Tầng với Cách Tiếp Cận Hướng Dịch Vụ (SOA)
Kiến trúc Ba Tầng (Three-tier Architecture): Chúng ta sử dụng cấu trúc ba tầng gồm Tầng Trình Diễn, Tầng Ứng Dụng, và Tầng Dữ Liệu. Mỗi tầng chịu trách nhiệm thực hiện một nhiệm vụ độc lập, giúp bảo mật dữ liệu và quản lý quyền truy cập, đồng thời đảm bảo tính linh hoạt và khả năng bảo trì của hệ thống.
Hướng Dịch Vụ (SOA): Bằng cách phân tách hệ thống thành các dịch vụ độc lập như Payroll Service, Employee Service và Reporting Service, chúng ta có thể nâng cấp, thay đổi từng dịch vụ mà không ảnh hưởng đến hệ thống toàn diện. Điều này tạo điều kiện dễ dàng cho việc triển khai các tính năng mới, chẳng hạn thêm phương thức thanh toán hoặc cập nhật quy tắc tính lương.
Tích hợp Cơ sở Dữ liệu Cũ: Một lớp tích hợp giữa hệ thống mới và cơ sở dữ liệu DB2 trên mainframe giúp duy trì dữ liệu từ các hệ thống cũ mà không cần thay đổi cấu trúc. Giải pháp này giảm thiểu chi phí và nguy cơ khi nâng cấp hệ thống.

![Diagram1](https://www.planttext.com/api/plantuml/png/b5H1IiD05Dtd59ziN7NZ0QIq1Rk81J4Kjo669DJEX3PPYBXsuSOkHSJ6KXGnj48tPf0kfkGUSmAlu4-3KfkndMQHa9dttd_lPtw-sBpQ3wrU67NFjS2oEvRhW6u8TX-0sUDln8CQ7rxeSAa1NZRj1fGu90JzYCygYq54S3-cKCURlWuvz2qA3L-mQm8jDviAzk13WtyGjmGLx8Muq11id3-SVYUaWQvTQUkU3EhwDefvkMe0RIH8l1NOcaX758v4ceIbUbZfnlQMV3YE44Z0u9_GylWJWRRFNyb6ogbWoPAGrq37TK-auovsOIR9jaeqUO8jDR9f5kV8rO1DJ0Ic9zW01NyBDFaGNmqgqZYK93K5UuV5hM1tY38HH7yiIMiKZK534p3o3aOoIPwWMtGpGcHjlnIddiLm8jZZgemarrv-9cpeY7GU0i5KFhY8dLXWv-kXXy4y2B1npqJRT5IWKZduxu38bmk6oYTMvM_-tgegQqtIP3EqWtSbzXRdIXebtmhs2XN98AgJLGwQfXvs5z7jOxLZb_vk5kJIe6rbg9YlEkGCV-RV0000__y30000)

2. Cơ Chế Phân Tích
Mục Đích
Đề xuất và phân tích các cơ chế cần thiết để đảm bảo hệ thống Payroll hoạt động hiệu quả và đáp ứng yêu cầu bài toán.

Các Cơ Chế Cần Thiết
Ghi nhận thời gian làm việc và thanh toán:

Nhân viên làm theo giờ: Hệ thống cần ghi nhận giờ làm việc hàng ngày, tính toán lương dựa trên số giờ và hệ số lương làm thêm.
Nhân viên lương cố định: Ghi nhận thời gian làm việc cho mục đích theo dõi. Lương sẽ được trả vào cuối tháng.
Nhân viên nhận hoa hồng: Ghi nhận các đơn hàng để tính phần trăm hoa hồng, và tổng hợp thanh toán bao gồm lương cơ bản và hoa hồng.
Báo cáo và truy vấn thông tin:

Nhân viên có thể tra cứu thông tin như số giờ làm việc, tổng số giờ cho từng dự án, tổng lương từ đầu năm, và số ngày nghỉ còn lại.
Tự động hóa quy trình thanh toán:

Hệ thống sẽ tự động thực hiện thanh toán vào mỗi thứ Sáu và ngày làm việc cuối tháng. Dữ liệu được tổng hợp từ lần thanh toán trước đến ngày thanh toán hiện tại để đảm bảo chính xác.

3. Phân Tích Ca Sử Dụng: Chọn Phương Thức Thanh Toán
Các Lớp Phân Tích
Employee: Đại diện cho nhân viên trong hệ thống với các thuộc tính như EmployeeID, tên, địa chỉ.
PaymentMethod: Đại diện cho các phương thức thanh toán có sẵn, với các thuộc tính như MethodID và MethodName (như "Lấy tại chỗ", "Gửi qua bưu điện", "Chuyển khoản").
PaymentInformation: Lưu trữ chi tiết về phương thức thanh toán đã chọn, như PaymentMethodID, địa chỉ, tên ngân hàng và số tài khoản (nếu chọn "Chuyển khoản").
Mô Tả Quy Trình và Trách Nhiệm của Lớp
Employee: Chọn phương thức thanh toán và cung cấp thông tin liên quan.
PaymentMethod: Lưu trữ các phương thức thanh toán khả dụng.
PaymentInformation: Lưu trữ và xác thực chi tiết thanh toán cụ thể.

Biểu đồ chuỗi:

![Diagram2](https://www.planttext.com/api/plantuml/png/f9F1IiD048Rl-nH3JYtK5-X12bKG12aqUD-k8Hji9p7T205l7gI8OD-WLKGi21KyPGyzREXxx1Fu2kvQgxIDaceEItR2VF_C1tcJiqPVq5WalIwXJ8GnxFUYRfXw7ebCEM11H550YwOz3qNRYyy3jlffZmhQeNsFa6KdxEokDK0T6DVo1bjyFfsFqNVDxOcvd29tGpN6IfMiTHZ65wyEgPeam7Jsc3GBEAPxw-oA8s8jNnY8G6Up293hx1aTk03dBA7GcKyJo8U1bbUB8kD9gkKbmYaFTNQFJj74InSsq-0-gQ9KSfKGsXMmsAzW20BcAIifGR-fiuSelzNocbhcm4YoXDz55VNbG_l-8N5G_M6AaejlB5M3LRg79wiQDhJ_ISEHh-xmG8tGFrQZjfP3Lus2mmLnAoykLwzcdG2_YHMX9WXexy1jeGPzam32H2od_gUs3GarA1LgRJRCONxkTm000F__0m00)

Biểu đồ lớp:

![Diagram3](https://www.planttext.com/api/plantuml/png/l5CzJiCm6Drz2ezK8XUe42eYI23H2Ac1tNK-6gk9OsndY80P8QQU09MHXGDaO0ZY7Zb1hu1JvJyHR6Jx_Dxx_BxtERlqSwOqaJeE0uHeG9J2vtdwvFfvkk4hroVSTwDio_4zmljFmbqCIb-H90Ikvw3zo3k0K0HH0d1XJ_52IyPNav8U2uze-8jzY4MRCSKTmGGzLjvElxUBF7sry_JZaXcVSUthbd7lh6pyVtuSFtlZDonxhmAoyB1R2MZ3wXrzRVBqXM1gqdxkGRyPA6TH403jRQBbhGFKzi9zwIO2wWiR1QFhQr5LSyA2HcOAmptnF0bA3QKsayQB3I9IJDUg9U5hXuJGcurG6iLSEt6u1DdkDVxqBEjuk7WqV0e5hra8QkscGBe9TiCvUh2iQleHf4XYxBmpD48pu9xvZtu0003__mC0)


4. Phân Tích Ca Sử Dụng: Duy Trì Thời Gian Làm Việc
Các Lớp Phân Tích
Employee: Đại diện cho nhân viên, có thể xem và nhập thời gian làm việc.
Timecard: Thẻ thời gian chứa thông tin thời gian làm việc của nhân viên theo từng kỳ.
TimecardEntry: Chi tiết về thời gian làm việc theo ngày và dự án.
Project: Đại diện cho dự án mà nhân viên tham gia.
Mô Tả Quy Trình và Trách Nhiệm của Lớp
Employee: Thêm, sửa, hoặc xóa các mục thời gian làm việc, gửi thẻ thời gian để phê duyệt.
Timecard: Lưu trữ và tính tổng thời gian làm việc trong kỳ.
TimecardEntry: Lưu trữ thông tin từng ngày làm việc.
Project: Quản lý và lưu thông tin dự án.
Quan Hệ Giữa Các Lớp
Employee - Timecard: Quan hệ một - nhiều, nhân viên có thể có nhiều thẻ thời gian.
Timecard - TimecardEntry: Quan hệ một - nhiều, mỗi thẻ thời gian có nhiều mục thời gian.
TimecardEntry - Project: Quan hệ nhiều - một, các mục thời gian làm việc có thể liên kết với một dự án.

Biểu đồ chuỗi:

![Diagram4](https://www.planttext.com/api/plantuml/png/Z5JFIW916B_FKtpilHS8Z58X8LaGHOhei8tXBAsZwApGkOE7JjAXGmIQI208HNNP9JfC-1xp1Br2tyx8akveULZH-VtRx_ljViUV-ptXTKNO2eX7HRiBZila8uU-BsVS0Qy7Rfrq4E5Jl-Dn0Kv9nGCGJCL3teIyYYRuHPcAfYsWyeqtDQbKonSAMtYLC25283-WgE8Na6E-v5NAnODLuYQFZ4CLjSqvnaStgc7LGfsGN0vSvCyxqCIJ1pGUjPOWoEM8MuUTFHCQTk54paAWAdeA8K3FApZF9W2Ma3a85OrzuWK2JYqvuMie9uY9RvV8CmBuCKReQFpA_pEv27eNTXVA5i_UdpOrF6bRRLeglaTztY0fnImY3TVmE8EU75EyhayPVxpYlz4x9qlMhraMjn3NnhvnGNqvif3JgBXWP1SqcISQmg91MTkYaVJYKCLptpgMRSLeRcAHjQaVuxthsh_GR2nJdCDCMeHFEbY-U60scIx5QAxSg-ZYNZ64O7Bi9ohWwDRfX8wDNbuyXzRefc7PE9VCj75xgff1dKji6OBkrXhb9bigeU0rr_EuIHAd1DQM8rtUgT1RELBHfqWGaNv0zr4Atr4_0000__y30000)


Biểu đồ lớp:

![Diagram5](https://www.planttext.com/api/plantuml/png/Z5DDIiD05Dxd58-kTD4B197Q1YfO2fBY_ZaDcO7CJ4rcIekuTkqHghXGS26uQX0NEKbEu1MS8Qb9QbgRpS2Rzxw_D_bEltg9mbXf7ZaamYI1pdcUteEYUVeWGkZdwoTp49gldpcGx4E47RXrm7nTYBJkemW75Fb0Yl3es8MvPDFoTe5aGZKPCZb2ViK2Ok-lfOm25CwTiw4Rq-nHm9nbhw92vZYcACoGSC5NCHDXUQ7-LER89h7SAWgAioPnJLYeMQliIjDUrnphqzl48Ixxg3pKBdYeWbhv8b0sZqPTnGPgGf6rm0mrQ_GId9bGL8kjIdXZTvVQse0e-mGlJzyXMzKIdgAWFXBgwJEJw8WbwgHGSBfPBYwziiUNrkc6ij5RKVk6j8ZABDF88FN4AeGjenmB0OrY8WkJBZ2XB4NpaNIxEpRamislvPQP_n-s2uiyVIl6MniiJ8jHrxQbB-WSi83T4DhI6RQPSu3KFI6eVBsIJYyGK_jN_m000F__0m00)


5. Hợp Nhất Kết Quả Phân Tích cho Ca Sử Dụng "Duy Trì Thời Gian Làm Việc" và "Chọn Phương Thức Thanh Toán"
Giới thiệu
Tài liệu này hợp nhất quy trình "Duy Trì Thời Gian Làm Việc" và "Chọn Phương Thức Thanh Toán" để nhân viên có thể quản lý thời gian làm việc và lựa chọn phương thức nhận lương.

Mục tiêu
Đảm bảo rằng nhân viên có thể dễ dàng nhập thời gian làm việc, chọn phương thức thanh toán, và gửi dữ liệu cho hệ thống xử lý.

Các bên liên quan
Nhân viên: Người nhập thời gian làm việc và chọn phương thức thanh toán.
Hệ thống: Quản lý quy trình thời gian làm việc và thanh toán.
Cơ sở dữ liệu: Lưu trữ thông tin về thời gian làm việc và thanh toán.
Các Lớp Phân Tích và Thuộc Tính
Employee: EmployeeID, Tên, Địa chỉ.
Timecard: StartDate, EndDate, SubmittedDate, Status.
TimecardEntry: Date, HoursWorked, ChargeNumber.
PaymentMethod: MethodID, MethodName.
PaymentInformation: PaymentMethodID, Address, BankName, AccountNumber.
Quy Trình Thực Hiện
Nhập Thời Gian Làm Việc: Nhân viên xem thẻ thời gian, nhập giờ cho từng ngày, và gửi để phê duyệt.
Chọn Phương Thức Thanh Toán: Nhân viên chọn phương thức thanh toán và cung cấp thông tin bổ sung (nếu cần). Hệ thống xác thực và lưu trữ thông tin.
