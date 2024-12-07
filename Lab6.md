# Thiết kế lớp
### 1. BankSystem
#### Xác định các operations

deposit(aPaycheck: Paycheck, intoBank: BankInformation): Xử lý việc gửi tiền, sử dụng BankSystemInterface để gửi giao dịch.

validateBankInfo(bankInfo: BankInformation): Xác minh thông tin tài khoản ngân hàng.

logTransaction(transaction: BankTransaction): Lưu lại thông tin về giao dịch đã được thực hiện.

![Diagram1](https://www.planttext.com/api/plantuml/png/h591QiCm4Bph5JhQO7z0X19wywKj91zOot8Y8ccDj0g4jY_heK_g5sh5SQAsfb2e3c9NipFI3FfuUry70a_H6iQq8-Lxa8etz-0EcrCWPVapu-Fgr811Km5FS99x9G-2prN5Ho8cXk1fRroFtW9fTANWHzGTUsLC6WY1_xDkKZY2qHsGcaUAzb8iiLf4SsOPt6qzk00o8GNTwecMWR-OQAw9JMv2REreXlPg-rV13B-8SR0O7GdU6mIQZh9tFWxAmqt_saw37YDfjtk8jbLUy0tviJj3qginhGA7RxpgwtrL9Z7ponzMaeVyiwnUwZhBXsLGNTyj9YVcrCgbwVmkjbQkIp_r4m00__y30000)

#### Các trạng thái (states):

Initialized: Hệ thống ngân hàng được khởi động và sẵn sàng nhận yêu cầu giao dịch.

ValidatingBankInfo: Đang trong quá trình xác minh thông tin ngân hàng.

ProcessingTransaction: Xử lý giao dịch.

SubmittingTransaction: Gửi giao dịch thông qua BankSystemInterface.

TransactionCompleted: Giao dịch đã được thực hiện thành công.

TransactionFailed: Giao dịch không thành công.

![Diagram2](https://www.planttext.com/api/plantuml/png/V95DJiD038NtSmelAL8la0MgAW7A3Yc83M8npJYLnSGJpK-bzceiE19Nm4ue2YMm7C_tdktdZxVtJSesvj9xytpz0klr3JJ7bB6lcJ9PJoTqK46Z46mjlqw_nlocLAj4pLruafgpcGABU8jxOd0uX4JvQcKM8DK-Hil9jlf-YA75b8ZtAXSSIFZOJ_018tM4xYyZNQI2cWzQXjs5t9ZbHXSZD6NNa_oC6zmZOxGPnrbca5aMZ2cMLfqbE95LSsTeGpzup19Pcg2kU7_yn-lEaYyHprwtCOOeAq6UcGxVcyXjvhs_4Z4_JCv5iq5sUlnF0000__y30000)

#### Các thuộc tính (attributes):
Paycheck: Chứa thông tin về số tiền và chi tiết nhân viên.

BankInformation: Bao gồm tên ngân hàng và mã định tuyến.

BankTransaction: Thông tin chi tiết giao dịch, loại giao dịch, và mã định tuyến.

![Diagram3](https://www.planttext.com/api/plantuml/png/T5913e8m4BppYXuXWG_qOD34WnSrqG-iTK42RKbP3iJuCWy-oIz8GQ2GqDDsTsTtPjhl-nDN18PgMNYYWAfYPsZ40qNEdXwp1wIk5N6M51geImc3GEWdscpTMi17RDUM8lLrFt3HRNeloq8tYBOmnDxB-nFOWSgl1bG5WZAjrdamchfE9Hgm0U_muxLlDBgcJAN7MjxGS7OXqzvSBRfSuCBvlj0PCU03lgGwQHXKjUHdkWwgTKs2gqk1n1cb5RQpEIFFVi7uPb6qcHnT6ccB2nAhFPE1CQgx_Hq_0000__y30000)

#### Các phụ thuộc (dependencies):

Phụ thuộc vào BankSystemInterface để thực hiện các giao dịch.

![Diagram4](https://www.planttext.com/api/plantuml/png/h9B1Yi8m48RlynGvLjY-G12HHGHlWhx0cCPri9sKp2Y8kq_cmKVQLzYAxThMdiIS9lDd_dpvoU_bEXN5g8SY1sBrSOlEcq_aFV7NwYJg2tC6KwtCbq58an9FRkVTtffbNNsOJNL-mTjWcycPLwHSHjOS0sNm0-1o535pOcH7cB_D-ZOlXqr1kex8WaufSAAFsfgMy0JKqfOnE2yIOarLtlSlsJRybTL_hylVLbfEztOt__5tclQJWtwIQJePVeojuqb6WpCDwQ3OHOP1_zx505FFsUqx_G400F__0m00)

### 2. PrintService
#### Xác định các thao tác (operations):

PrintService.print: Xử lý lệnh in với thông tin Paycheck và thiết bị in.

PaycheckPrinterImage.create: Tạo nội dung hình ảnh từ thông tin Paycheck để in.

PrintInterface.print: Tiến hành in trực tiếp qua giao diện máy in.

![Diagram5](https://www.planttext.com/api/plantuml/png/h58n3i8m3Dpp2ezKeX-8468e0niIVC1A3KIaJPMabIhWPGmyYI-Gj14eg6naii_s-NpAy_vOMOV6jPLYidPa3YW8DblZansPJlhimi2_9a2p1djn8d7ci8tH79mUsibuS0mo3fsM9Rin9XHQ2t_Y2tF243hQL7YaYUdiFJDqV2aW4vTRgikzBYZecSdGcSvD7n2BdkE3nxsH5x3IRUqu79H6Dq9KDKhtH0KvbCfoM4SWiAHEBwvvddZ5adAUBzztS6WjsP_rKIXFtCeckgDyjlA6X3_m0W00__y30000)
#### Các trạng thái (states):

Ready: Đợi lệnh in được gửi tới.

Processing: Chuyển đổi thông tin từ Paycheck thành PrinterImage.

Printing: Gửi dữ liệu in tới thiết bị thông qua PrinterInterface.

Complete: Hoàn thành quá trình in.

![Diagram6](https://www.planttext.com/api/plantuml/png/R9112i8m44NtESKiLUW5kf22A7GdkXGNCHbB94tB91NgrLnu9AzWnzIsIBS_x_q_vFryPJv82arfnMbrXYHPmm6bRY65t9bWf3KFX3qP5uv8TwDGY0WmkgTAeVV65Naf2-oacid54fIq5hNu1wBK8Lt24zzG4Sg06doZ6BusrhQp9b-OmfQeeYXnY-5d8ORMOM9JbRL5BavZ0BVgCXcPKNRIs9570kIjldpiwsyHK-UNPUWq_-O7003__mC0)
####Các thuộc tính (attributes):

Employee: Lưu thông tin liên quan đến nhân viên.

Paycheck: Gồm số tiền lương và chi tiết của nhân viên.

PrinterImage: Dữ liệu được định dạng để in.

![Diagram7](https://www.planttext.com/api/plantuml/png/V55B3i8W4Drp2fPjOY_0mjI52tScUe49JcjZWOPEJOpnP2uyabSGMgcj65cHzvZt6PxtHzuIMEfKpMGDRSktS957b2T-PTmVKARJ97XH6w0UaXQ1C2cCNKsvL8op_RCIQU2JT3hjuBLgQdD1z4IuiniB0Mob2Ur6GOakn1pVMz0jIAgC3W6Rj-cNFMy67H44fzdZcKNqFXMHPHGoPD2WKF0TERHaetbI-GvYriYfdarr-2Y51GnLn-rdsVApcwYwPyUslzbtwNza7uZbg0_--ry0003__mC0)
####Các phụ thuộc (dependencies):

IPrintService và PrinterInterface là các giao diện cần thiết để thực hiện quá trình in.

PaycheckPrinterImage kết nối dữ liệu từ Paycheck thành hình ảnh in.

![Diagram8](https://www.planttext.com/api/plantuml/png/UhzxlqDnIM9HIMbk3bTcNabgKLfYSgg2Pq0Ha1ESMbIM2UHLSoa0GG58IACWiJ8v8pKvsqeX8B6oA3ydHmSYaLe4584mN591kZIj5ChoCrEuQhcuadCIYuiLg6SaI6joVbvPQb59IBvdRc9wAgOPcb2zO6aaHq1aWVQZkWki34CKPZ7KkSMfUIaX-L0PZKoG5cHRa7oC6dusDRgwADxdGf7MrRM3kGkB1C9rLkYUriIX7EviAuNIujHYBWUWku7n2m000F__0m00)
### 3. ProjectManagementDatabase
#### Xác định các thao tác (operations):

getChargeNumbers(criteria: String): Tìm kiếm danh sách các ChargeNumbers dựa trên tiêu chí đã nhập.

initialize(): Thiết lập kết nối cơ sở dữ liệu.

ChargeNumList.add: Thêm các ChargeNumbers mới vào danh sách.

![Diagram9](https://www.planttext.com/api/plantuml/png/f99DQiCm48NtEeMMxi8N4AM4E9j2MmezmKIQE5Fi4PN6XVwTB8iSALUeNF-qmeGMgfqUCzzxFEbqEAwYG92kRHInODY1HNrz7_mZMjc0m1OYwZUbqwbHgZs46k-wTeiX5ZPGMY4m-a42SNrXz3nmGr7KXrAsWHZr2Bm5XXfRvF-Z-orY4eA6Nh7op8bFdeiq-Up9VNl_18zssdvfbNSu6GowGm5guYmk8RtvI07d1haOS2QpMkJOhCUKVefXX_iSkTUUEWmlKpj_QdZnMfVlPNc-SNN-BShoAajfT1Sn_hAGDsFq3iNkLQvcSwaRjK9s_P_x1000__y30000)
#### Các trạng thái (states):

Ready: Đã sẵn sàng xử lý yêu cầu tìm kiếm.

Fetching: Nhận và chuẩn bị truy vấn tiêu chí tìm kiếm trong cơ sở dữ liệu.

Processing: Thực hiện truy vấn và xử lý kết quả trả về.

Returning: Tạo danh sách kết quả và trả lại dữ liệu.

![Diagram10](https://www.planttext.com/api/plantuml/png/T90n2i9044NxESMMAkG25XA81D88fXMBoMPC5ZOHPcS5lPg5H_8AxeOa2D7s___-VERzVALEaCLt5awRiqgIdIfgIsghYjw8GMiUfFOeMA4ZWC6BePn4jwPlCZP2R3003KdM8ZTqy5r5x5PhfT5Qgc4HZWr7JtmFubGU6cR_5kx-mUBAE6w8A3rQ08kw62v9FFT1BSbvAowGGquvhpKvT_7sDpY8EPgmVcQ8-Se0Yyvn5NmpavPINyVVVW000F__0m00)
#### Các thuộc tính (attributes):

ChargeNum: Thông tin chi tiết về một ChargeNumber.

ChargeNumList: Danh sách các ChargeNumbers.

![Diagram11](https://www.planttext.com/api/plantuml/png/R55Doi8m4Dtd55rMq0iK4V-M8eWd69EXNo2cCfc88fxCXKVo2gQjVdMgtMNUcta_VTpkqy107FTEQGSXP8i_e1BNSRz3oYuggpzhYcpBP7tPlWq6JVR0jl82q8J0c7VquI_ge10YwghwqYiR-AKDnkIwcSkjTEHOMTDmIkIPStaQrOlZJzgakxu4XXq4t4IaypjPyiP85cG-mX0TXq8wQZ0yeOufOtznq2TtklD5vJrghlxxrEqWTT8kon9RC7ydJ8TaCQFHH1OeamcuiVADVtXIK_Ic_lrF0000__y30000)
#### Các phụ thuộc (dependencies):

DBChargeNumbers: Giao diện kết nối với cơ sở dữ liệu.

ChargeNumList và ChargeNum: Quản lý dữ liệu kết quả từ truy vấn.

![Diagram12](https://www.planttext.com/api/plantuml/png/f99DRi8m48NtFeMNwI8Ni112efjABMh52GPd4gPA9f8zHhI5ax7WI5m1vuUI5X0BlFFpcs_ynZxizXClu2HKfI8MT3bOr2_lhlv4AyyWi02F-aVfk78KkvmkmHKu2zK2dK-ierX4OFHS777nP7HdU2KlQgkKBS5xtVFUWA702lbXSbD4J49GqZScyN1LKtPkE6JrFJItknFllxV1zax8iiIsela3kkXoIZ6jcMCyghads4xulLUZuHfj4Fm8wBxkp-tY2KQRDBqzHtLxmcaw7aOqtR3LG3exkfntO5TI6nqyUZL1pk9FEW800F__0m00)
