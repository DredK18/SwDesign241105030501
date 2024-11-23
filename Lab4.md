# **Lab 4: Thiết Kế và Triển Khai Phần Mềm**
## Ca sử dụng Login
## **1. Mô Tả Tương Tác Giữa Các Đối Tượng Thiết Kế**

### **Mô tả**
- Người dùng nhập thông tin đăng nhập, bao gồm tên đăng nhập và mật khẩu, vào biểu mẫu đăng nhập.
- Hệ thống tiến hành xác thực thông tin thông qua **SecuritySubsystem**.
- Nếu thông tin hợp lệ, người dùng được cấp quyền truy cập vào hệ thống; nếu không, hệ thống hiển thị thông báo lỗi.


![Diagram1](https://www.planttext.com/api/plantuml/png/T9A_JiCm4CPtFyMf0rl5dW5LeW8agYu5YTL9eyHgue1zbiZSWO691q2YGWmWLO34GZnqICLx-0bu1Iv1a92MnTPPz_s---DFknfev0fDcZ0UOAQWDuu-Nfoz5J0jtsNK0wxXL8UAiUg4_XwCiaZ8WqobuC4uTiNo7B1yah2-MSzb1FBxQGTIkX5c53uQreX-2FkPH9Kb2K4zE7HsAG3Zyeq8A3emrXKGOn86HWdC9yRNkSQmgkQiN0G4SVOrQB7OPYhfXnovptL8if4h7lAskVmp0lQRsl_7T-ZiCoJ2sIlJrMxntZg0OrUi42wCA-xXicbZi_FE0axYyax64DIrxr98lI3uhbY8zin9LQ_FWoCgSovh_3NC6bV61g6SLl_W2m00__y30000)

---

## **2. Đơn Giản Hóa Biểu Đồ Tuần Tự Bằng Cách Sử Dụng Các Phân Hệ**

### **Mô tả**
- Tích hợp **LoginController** và **SecuritySubsystem** vào một gói duy nhất, gọi là **SecuritySubsystem**, để đơn giản hóa cấu trúc hệ thống.

![Diagram2](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTYSab-aOAIN_gn3GztpyrKI3cyCozTII6nM26qEBM8Ymj4AkZQAVZafsVckUKNvIfOAVXbFDorja2XvF2gF8KZ4uyqvwKhv464r1HoWNI9GZQGkxAK2w49Q49mQd9fKMP9PN1fKd5bSKago2JtXxlNPYgKP1pU0ZIZ91FDE2vCBRfeJWd9EBmWBqCX6Mo0Ff3xSDVI4eMaXxiMPYBR3jG5zeYLWaVcmztDUK0h7-xkLiX-k6j_YK9XwSDTYxcu75BpKa0X0W000F__0m00)

---

## **3. Mô Tả Hành Vi Liên Quan Đến Lưu Trữ**

### **Mô tả**
- Cơ sở dữ liệu lưu trữ thông tin người dùng, bao gồm tên đăng nhập và mật khẩu.
- **SecuritySubsystem** xử lý việc xác thực và không lưu trữ mật khẩu gốc để đảm bảo an toàn thông tin.

---

## **4. Cải Tiến Mô Tả Luồng Sự Kiện**

### **4.1 Luồng Chính**
1. Người dùng mở giao diện đăng nhập.
2. Nhập tên đăng nhập và mật khẩu.
3. Nhấn nút "Đăng nhập".
4. Hệ thống xác thực thông tin:
   - Nếu hợp lệ, người dùng được cấp quyền truy cập.
   - Nếu không, hiển thị thông báo lỗi và cho phép người dùng thử lại.

### **4.2 Luồng Phụ**
- Nếu người dùng nhấn "Hủy", hệ thống sẽ quay lại giao diện chính mà không thực hiện thêm hành động nào.

### **Lý do cải tiến**
- Việc chi tiết hóa luồng sự kiện giúp các nhà phát triển hiểu rõ hơn về quy trình, đặc biệt trong các trường hợp ngoại lệ hoặc khi người dùng hủy bỏ thao tác.

---

## **5. Hợp nhất các lớp và hệ thống con**

### **Mô tả**
- Để cải thiện sự nhất quán và dễ dàng bảo trì trong hệ thống, các lớp và phân hệ liên quan đến chức năng đăng nhập sẽ được hợp nhất thành một phân hệ duy nhất, gọi là **UnifiedSecurityModule**.
- Phân hệ này sẽ bao gồm các thành phần chính: **LoginController**, **Authenticator**, và **UserRepository**.

### **5.1 Lợi ích của việc hợp nhất**
1. **Giảm độ phức tạp**:
   - Tối giản các mối quan hệ giữa các đối tượng và hệ thống.
   - Giảm thiểu số lượng giao tiếp giữa các phân hệ.
2. **Tăng tính linh hoạt**:
   - Dễ dàng mở rộng hoặc thay đổi logic đăng nhập mà không ảnh hưởng đến các phần khác của hệ thống.
3. **Cải thiện bảo mật**:
   - Dữ liệu nhạy cảm được quản lý tập trung, giảm rủi ro bị lộ.

![Diagram7](https://www.planttext.com/api/plantuml/png/N8-n3S8m54HxJ_6LFWjGe21QQ40PmB8_niBOaVsD524APa6KB80BPl44h82JAk7AUtedtJTzca3SKpmRrd5nuWgXQgq-Q9Hx5D5hwhTEHeCLN1cK2CD3W8rJsgwT9U-CGJyXgqX7jAG59pVjsu1-XvqBklGz6ydV2jJrSkx30a9EBv0vFQqQdJaVZFboKSZdzmCkETtPZJLevV2E_G000F__0m00)

# Ca sử dụng Maintain Timecard
## 1. Mô tả sự tương tác giữa các đối tượng thiết kế

### Nội dung:
- Nhân viên cập nhật thời gian làm việc vào bảng chấm công, dữ liệu này được liên kết với các thông tin dự án được lấy từ hệ thống quản lý dự án.
- Sau khi nhập, thông tin chấm công sẽ được lưu trữ trong cơ sở dữ liệu.
  
![Diagram5](https://www.planttext.com/api/plantuml/png/Z98_IiH058VxESLZ-xs0XIpiAWgh26wXvMGo997viqmcOceB2oiF81f1X9L51QjCOJ7WFUO4Ni69oxe99fBk5U_tyPllpPVv6AKQAvrnXZ3HKi7WCBOF0iuJkn03m2diy3cJEQK8hISORiCiuPHW5UvAnM4B3fovWo1nvZ83xihd34ZioaSEnBwB23MsQ-cn55f9ngZoZ5Exy35NFcKGElC2pEEkVkOti8L0BI6FEbBoZ19zdAUQydsXQQImJgJmmAbla8EEgmgW4x51TOQ6NUKcVHlzTRDNQH6-XpFNxI_xp-pObSiv26zpgI5rvWOYdxu5Pk-vlv87aNvwfv-lMLr6wu6QRYTOum2dT9skbs_4VnSx_PtOWgnU8O1vLaztirNVm1OIBZO8X4PKXDMd_GO00F__0m00)
## 2. Đơn giản hóa biểu đồ chuỗi thông qua hệ thống con

### Nội dung:
- Thay vì thể hiện chi tiết từng lớp, các thành phần liên quan được nhóm vào các hệ thống con:
  - **TimecardSubsystem**: Gồm TimecardForm và TimecardController.
  - **ProjectManagementSubsystem**: Tương tác với ProjectSystemIntegration.
  - **DatabaseSubsystem**: Chịu trách nhiệm lưu trữ thông tin chấm công.
    
![Diagram6](https://www.planttext.com/api/plantuml/png/X94nJiCm68Ltd-AfUo_G0LMYR1GXqO7LSQmao7QgsAx8pC3C0H04YGLK0H9JF31OuXu-0LV0KLMWQbgsV_a-l_VyvJx6sj3AM2a8PQQiC3Z9_OF2el1FQW2gSIJdegmv9sHzONY0MI4verLwPXDTQyCbHfW6TuUa2ExAGeRssOBbeNsKOFvTPMGRYPxJghpWp4ofeXcNN9c_mkD8rqY3Uu68sclRtM_mZI9xkE6EU9C-pt-T3aExd4F57ai37TmDicYuXV3tCeuKPQo_s8GQcb3DD_fylbgOl5i3fb2Rysm3kugS-uQj8Yc8gEmB4D6VQYFCLcyclYbn-KiJCkOgxVx-6m00__y30000)
## 3. Mô tả hành vi liên quan đến lưu trữ dữ liệu

### Nội dung:
- DatabaseSubsystem thực hiện việc lưu trữ thông tin liên quan đến bảng chấm công và dự án.
- Dữ liệu từ đối tượng Timecard được ánh xạ và lưu vào các bảng TimecardRecords và ProjectRecords.
- Phương thức `storeTimecard()` được sử dụng để thực hiện lưu dữ liệu.

## 4. Tinh chỉnh mô tả luồng công việc
### 4.1 Luồng cơ bản:
- Nhân viên mở giao diện nhập thời gian làm việc.
- Danh sách các dự án và mã chi phí tương ứng được hệ thống quản lý dự án cung cấp.
- Nhân viên lựa chọn dự án phù hợp và nhập số giờ làm việc.
- Sau khi nhập, thông tin được lưu vào cơ sở dữ liệu và hiển thị thông báo xác nhận thành công.

### 4.2 Luồng thay thế:
- Khi không thể truy cập danh sách dự án:
  - Hệ thống hiển thị lỗi và cho phép nhân viên nhập lại thời gian làm việc cho mã dự án đã có.
- Nếu dữ liệu nhập vào không hợp lệ (như số giờ lớn hơn 24 trong một ngày):
  - Hệ thống thông báo lỗi và yêu cầu nhập lại thông tin chính xác.
- Nhân viên có quyền hủy thao tác và quay về giao diện chính.

### Lý do:
- Việc tinh chỉnh luồng công việc đảm bảo tất cả trường hợp bất thường và lỗi có thể xảy ra đều được xử lý triệt để, tránh ảnh hưởng tới quy trình.

## 5. Hợp nhất các lớp và hệ thống con
### Nội dung:
- **TimecardSubsystem**:
  - Bao gồm:
    - **TimecardForm**: Giao diện để nhập và chỉnh sửa thời gian làm việc.
    - **TimecardController**: Xử lý logic liên quan đến việc quản lý chấm công.
    - **Database**: Lưu trữ dữ liệu chấm công.
  - Mục tiêu: Gom nhóm các thành phần để tăng hiệu quả quản lý.
- **ProjectManagementSubsystem**:
  - Bao gồm:
    - **ProjectSystemIntegration**: Truy xuất thông tin dự án từ hệ thống quản lý dự án bên ngoài.
  - Mục tiêu: Đảm bảo tích hợp dễ dàng và rõ ràng giữa các hệ thống.
    
![Diagram8](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWb98PcvgSc9HId1fKd5bSKbghf92DPS242Jd91ONAy2atVABSh48E-VdbHJbv-Ia5Y59kYIM92Ob5gTorN8Xx0aeoizAJIxnJSm3SdDJyqfmM0XL5moMyimhIKqlIYp9pCy36OPfguAkhXrEBGfM2ZaFTosjL4Xvk7kzGaxcmztjfI3sHeN32_Eu75BpKa0X0G000F__0m00)

# Ca sử dụng Run Payroll
## 1. Mô tả sự tương tác giữa các đối tượng thiết kế

### Nội dung:
- Hệ thống tự động khởi chạy quy trình tính lương vào những ngày đã định trước.
- Dữ liệu chấm công, thông tin đơn hàng và dữ liệu nhân viên được lấy từ cơ sở dữ liệu để tính toán lương.
- Sau khi tính toán, phiếu lương được gửi đến dịch vụ in ấn hoặc hệ thống ngân hàng để xử lý thanh toán.
  
![Diagram9](https://www.planttext.com/api/plantuml/png/Z5B1IiD04BtdAuRU-mCzI8aA2XuAyT3hThDq5pUJiDaKyWKUFFNepGWY2A4UF2L83olzZ_q2Vy59GQmn1I-pCBnvxysR_MotqzmoOuj41upRrC0ezEqzQD_K6TNsZakGlhq5ItMDon6m7A8ojoA9k1HneOK9Wbu3nYSmOwL9jJvDqNOlDISG-cPZuMFjc-S2hAjHWjwzxYfS1d_Xn76j4i6PYQDYaUyLYEFADqybnBxTW5Pah00kgPK0Ts_7UCwJJAUb46VCiWNBnI0DIlU8i5Bk1OTPGeOtqRUDkMzhqEwTSc6qXarTXS41OdmaWhchE4bHlFXhT5XoPXJQI9YLuftfIuHCAjziYv_S3X7_4LN3MZJPF-84BbBtG3OfAjixrrHWtFsPu0i00F__0m00)

## 2. Đơn giản hóa biểu đồ chuỗi thông qua hệ thống con

### Nội dung:
- Gom các lớp liên quan vào các hệ thống con để giảm thiểu độ phức tạp:
  - **TimecardSubsystem**: Quản lý dữ liệu chấm công.
  - **EmployeeDatabaseSubsystem**: Lưu trữ thông tin nhân viên.
  - **BusinessServicesSubsystem**: Thực hiện các tính toán liên quan đến tiền lương.

![Diagram10](https://www.planttext.com/api/plantuml/png/R92nIWD148RxVOgVzFS28XAkqYvmZUswMR97DdDXRrQusiB2AgMT8c9rQBsBf3Z9UymJ-0gUWXPdch-OcM_cOpxpVjwo3XmtNcd3JS2ib7mFBwdVZfdlZ8EJV0iUSqUh6NIBgclPRYhZx39w6vIQ552SOQ6xq7XVnQlsfuaJb99U6HyxIIyHFFJau0zlXqTQgN_JuuPIqxhwPIybz_33EuoBdUGRmjerafxeABe8DN5bmtLjx0XV4BQkbhIFVmUdngT5SKpvl1aU22pfcIV6Qcvf-VqszGK00F__0m00)
## 3. Mô tả hành vi liên quan đến lưu trữ dữ liệu

### Nội dung:
- Dữ liệu chấm công và thông tin nhân viên được lưu trữ trong cơ sở dữ liệu.
- Kết quả của quá trình tính toán phiếu lương cũng được lưu trữ để phục vụ báo cáo và kiểm tra sau này.
  

## 4. Tinh chỉnh mô tả luồng công việc

### 4.1 Luồng cơ bản:
- Hệ thống tự động bắt đầu quy trình tính lương vào ngày đã được định trước.
- Dữ liệu chấm công và thông tin nhân viên được lấy từ cơ sở dữ liệu.
- Tiền lương được tính toán dựa trên dữ liệu chấm công, các khoản khấu trừ và đơn hàng (nếu có).
- Phiếu lương được gửi qua ngân hàng hoặc được in.

### 4.2 Luồng thay thế:
- Nếu hệ thống ngân hàng không hoạt động:
- Hệ thống sẽ thử gửi lại giao dịch trong một khoảng thời gian nhất định.
- Trong trường hợp gửi lương qua ngân hàng thất bại, hệ thống hiển thị thông báo lỗi.
- Nếu việc tính lương không hoàn tất, quy trình được ghi nhận lỗi và thông báo đến bộ phận phụ trách.


### Lý do:
- Việc tinh chỉnh luồng công việc đảm bảo rằng các trường hợp bất thường được xử lý, giúp giảm thiểu rủi ro trong quy trình tính lương.


## 5. Hợp nhất các lớp và hệ thống con

### Nội dung:
- **PayrollSubsystem**:
  - Bao gồm các thành phần:
    - **Timecard**: Xử lý dữ liệu chấm công.
    - **Paycheck**: Quản lý phiếu lương.
    - **Employee**: Thông tin nhân viên.
  - Mục tiêu: Gom nhóm các thành phần liên quan để quản lý hiệu quả.
- **IntegrationSubsystem**:
  - Bao gồm các thành phần:
    - **BankSystem**: Tích hợp để gửi tiền qua ngân hàng.
    - **PrintService**: Hỗ trợ in phiếu lương.
  - Mục tiêu: Đảm bảo khả năng tích hợp dễ dàng với các hệ thống bên ngoài.
    
![Diagram12](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bT1Od9sOdggWb90OcLHVavES6bISMLnIMgkaa8rbm8G9ESa5XShX6JcfYOd5gKW2G4r96Ua9cSZ2Rdc5kJaLwQcSjLo8Gpsp2j9JIzABCdCpyDXU41HPbv9S6fHMMPoAfAmKs9UTZ1OESWyTFSfwEhQAM0pMy5AeVZXxhKAAGztByrBvt98pKi1UHG0003__mC0)
