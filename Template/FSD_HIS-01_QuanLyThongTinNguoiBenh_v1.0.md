**TÀI LIỆU ĐẶC TẢ CHỨC NĂNG**

**FUNCTIONAL SPECIFICATION DOCUMENT (FSD)**

**PHÂN HỆ HIS-01**

**QUẢN LÝ THÔNG TIN NGƯỜI BỆNH**

_Một người — một hồ sơ · gộp phải khôi phục được · không giấy tờ vẫn khám được_

| **Thuộc tính** | **Nội dung** |
| --- | --- |
| Mã phân hệ | HIS-01 |
| Tên phân hệ | Quản lý thông tin người bệnh |
| Loại tài liệu | FSD — Đặc tả chức năng |
| Phạm vi | Field-level 11 nhóm chức năng HIS-01-010…110 |
| Thực thể sở hữu | TT-01 Hồ sơ người bệnh (TT01-S01..S05) · Mã người bệnh · Giấy tờ tùy thân · Thẻ BHYT theo thời hạn · Tiền sử & dị ứng · Lịch sử gộp hồ sơ · Nhật ký truy cập hồ sơ |
| Tài liệu nguồn | BRD_HIS-01_v1.1 · BRD_HIS_Master_v2.18 · FSD_HIS-03_v1.2 · FSD_HIS-05_v1.2 · FSD_HIS-10_v1.0 · FSD_HIS-17_v1.1 · FSD_HIS-18_v1.0 |
| Ranh giới chính | HIS-01 sở hữu DANH TÍNH và HỒ SƠ HÀNH CHÍNH của người bệnh. KHÔNG sở hữu lượt điều trị (HIS-03), nội dung lâm sàng (HIS-04/05/06), hay quy tắc an toàn thuốc (HIS-10) — HIS-01 lưu bản ghi dị ứng, HIS-10 biến nó thành quy tắc. |
| Phiên bản | 1.0 (Dự thảo) |
| Ngày phát hành | 21/08/2026 |
| Đơn vị xây dựng | ONENET |

# **KIỂM SOÁT TÀI LIỆU**

| **Phiên bản** | **Ngày** | **Người thực hiện** | **Nội dung** |
| --- | --- | --- | --- |
| 1.0 | 21/08/2026 | Chủ đầu tư & ONENET | Khởi tạo FSD phân hệ HIS-01 theo khuôn 13 chương / mẫu 10 mục. Đặc tả field-level TÁM chức năng chủ đạo. Trọng tâm là mục 5.6 — GỘP HỒ SƠ TRÙNG, thao tác duy nhất trong phân hệ có thể gây hại cho người bệnh nếu làm sai, và cũng là thao tác duy nhất phải KHÔI PHỤC ĐƯỢC. Nguồn tham chiếu là BRD HIS-01 v1.1 đọc trực tiếp từ bản .docx đã ban hành, vì nguồn dựng content_his01.js còn đứng ở v1.0. Tách dải mã ca kiểm thử TC-HIS01-BN-nn ngay từ bản đầu vì BRD đã dùng TC-HIS01-01…06 cho nghĩa khác. Tiêu chí nghiệm thu NT-HIS01-01…06 chép nguyên văn từ BRD. |

_Vị trí trong bộ tài liệu: VÌ SAO PHÂN HỆ NÀY LÀM SỚM TRONG PHẦN CÒN LẠI. HIS-01 là nền định danh mà mọi phân hệ khác đều đọc — HIS-03 gọi nó để tìm hoặc tạo hồ sơ, HIS-04/05/06/07 đọc tiền sử và dị ứng, HIS-16 đọc thông tin BHYT, HIS-18 gắn định danh vào bệnh án. Sai ở đây không dừng ở một phân hệ._

# **CHƯƠNG 1. GIỚI THIỆU**

## **1.1. Mục đích tài liệu**

BRD HIS-01 đặt ra nguyên tắc MỘT NGƯỜI — MỘT HỒ SƠ và liệt kê mười một nhóm chức năng để giữ nguyên tắc đó. Tài liệu này đặc tả cách hệ thống thực hiện: thuật toán phát hiện trùng, quy trình gộp không mất dữ liệu và khôi phục được, cách hồ sơ vô danh cấp cứu hợp nhất về hồ sơ thật, và cách bản ghi dị ứng đi tới được màn hình lâm sàng.

Nếu chỉ đọc một mục thì đọc mục 5.6. Gộp hồ sơ là thao tác duy nhất trong phân hệ này có thể gây hại trực tiếp cho người bệnh — gộp nhầm hai người khác nhau nghĩa là bệnh sử, dị ứng và kết quả xét nghiệm của người này xuất hiện trên hồ sơ của người kia.

## **1.2. Ba nguyên tắc chi phối cả tài liệu**

| **Nguyên tắc** | **Nghĩa cụ thể** | **Vì sao** |
| --- | --- | --- |
| **Một người — một hồ sơ** | **Một mã người bệnh duy nhất suốt đời; CCCD không trùng giữa hai hồ sơ đang hoạt động** | **Hồ sơ tách đôi thì bác sĩ chỉ thấy một nửa bệnh sử, và nửa còn lại có thể chứa dị ứng** |
| **Gộp phải KHÔI PHỤC ĐƯỢC** | **Mọi lần gộp lưu đủ dữ liệu để tách lại; hồ sơ bị gộp không xóa mà chuyển TT01-S04 giữ liên kết** | **Gộp nhầm là sự cố an toàn người bệnh, không phải lỗi dọn dữ liệu. Không khôi phục được thì sai lầm thành vĩnh viễn** |
| **Không giấy tờ vẫn khám được** | **Thiếu CCCD, thiếu thẻ BHYT, không biết tên — vẫn tạo được hồ sơ tạm ở TT01-S01** | **Chặn tạo hồ sơ vì thiếu giấy tờ là chặn việc khám bệnh. Giấy tờ bổ sung được sau; sức khỏe thì không chờ** |

## **1.3. Ngoài phạm vi**

| **Việc** | **Thuộc phân hệ** |
| --- | --- |
| Lượt khám, lượt điều trị, căn cứ hưởng và mức hưởng BHYT của một lượt | HIS-03 — HIS-01 chỉ lưu THẺ, không tính mức hưởng |
| Nội dung lâm sàng: diễn biến, y lệnh, kết quả | HIS-04/05/06/07/09 |
| QUY TẮC an toàn thuốc dựa trên dị ứng | HIS-10 — nguồn quy tắc duy nhất (BR-011). HIS-01 sở hữu BẢN GHI dị ứng |
| Cảnh báo tại điểm ra y lệnh | HIS-21 CDSS tiêu thụ dữ liệu của HIS-01 và HIS-10 |
| Danh mục hành chính (tỉnh/huyện/xã, dân tộc, nghề nghiệp) | HIS-20 / MDM — HIS-01 dùng, không định nghĩa lại |
| Kết nối VNeID, dữ liệu dân cư, cổng BHXH ở tầng hạ tầng | HIS-22 — HIS-01 gọi ở tầng nghiệp vụ |
| Ký số, khóa và lưu trữ tài liệu | HIS-18 |

# **CHƯƠNG 2. QUY ƯỚC, KÝ HIỆU & MÃ ĐỊNH DANH**

| **Ký hiệu** | **Ý nghĩa** | **Ví dụ** |
| --- | --- | --- |
| FS-HIS01-xxx-xxxx | Mã chức năng đặc tả, bám theo mã nhóm của BRD | FS-HIS01-070-0040 |
| TT01-Sxx | Trạng thái hồ sơ người bệnh | TT01-S04 Đã gộp |
| VLD-HIS01-xx | Quy tắc kiểm tra dữ liệu | VLD-HIS01-06 |
| ERR-HIS01-xx | Mã thông báo lỗi | ERR-HIS01-14 |
| TC-HIS01-BN-xx | Ca kiểm thử của FSD — dải TÁCH RIÊNG với BRD | TC-HIS01-BN-11 |
| NT-HIS01-xx | Tiêu chí nghiệm thu — CHÉP NGUYÊN VĂN từ BRD | NT-HIS01-04 |

_Quy ước mã: VÌ SAO TÁCH DẢI MÃ CA KIỂM THỬ. BRD HIS-01 đã dùng TC-HIS01-01…06. Nếu FSD dùng tiếp dải đó thì cùng một số sẽ mang hai nghĩa ở hai tài liệu — lỗi đã phải sửa ở sáu phân hệ khác trong ngày 20/08/2026. Tài liệu này dùng TC-HIS01-BN-nn ngay từ đầu, theo mnemonic MH-BN của mã màn hình._

# **CHƯƠNG 3. TỔNG QUAN CHỨC NĂNG**

| **Nhóm** | **Tên nhóm** | **Vai trò** | **Đặc tả chi tiết tại** |
| --- | --- | --- | --- |
| HIS-01-010 | Cấu hình & danh mục hồ sơ | VT-25 | Bảng tổng hợp mục 5.9 |
| HIS-01-020 | Định danh người bệnh | HC/ĐD | FS-HIS01-020-0010 |
| HIS-01-030 | Tạo & cập nhật hồ sơ hành chính | HC  | FS-HIS01-030-0010 |
| HIS-01-040 | Thẻ BHYT & giấy tờ tùy thân | HC  | FS-HIS01-040-0010 |
| HIS-01-050 | Tiền sử & dị ứng | BS/ĐD | FS-HIS01-050-0020 |
| HIS-01-060 | Tra cứu & tìm kiếm người bệnh | Mọi vai | Bảng tổng hợp mục 5.9 |
| **HIS-01-070** | **Phát hiện & gộp hồ sơ trùng** | **HC/VT-22** | **FS-HIS01-070-0010 · 070-0040** |
| HIS-01-080 | Lịch sử KCB & hồ sơ tổng hợp | BS  | Bảng tổng hợp mục 5.9 |
| HIS-01-090 | Vòng đời & vô hiệu hồ sơ | HC/VT-22 | FS-HIS01-090-0020 |
| HIS-01-100 | Tích hợp định danh | Hệ thống | Chương 10 |
| HIS-01-110 | Bảo mật & nhật ký truy cập | VT-23 | FS-HIS01-110-0010 |

## **3.2. Màn hình**

| **Mã** | **Màn hình** | **Vai trò** | **Nhóm** |
| --- | --- | --- | --- |
| MH-BN-01 | Hồ sơ người bệnh — màn hợp nhất 360 độ | Mọi vai | 030 · 040 · 050 · 080 |
| MH-BN-02 | Tra cứu & tìm kiếm | Mọi vai | 060 |
| MH-BN-03 | Gộp hồ sơ | HC / VT-22 | 070 |
| MH-BN-04 | Nhật ký truy cập | VT-23 | 110 |
| MH-BN-05 | Cấu hình | VT-25 | 010 |

# **CHƯƠNG 4. ĐẶC TẢ LUỒNG NGHIỆP VỤ**

## **4.1. Đóng góp vào QT-01 — bước định danh**

| **Bước** | **Việc** | **Vai trò** | **Trạng thái hồ sơ** |
| --- | --- | --- | --- |
| QT-01-020-a | Tra cứu theo CCCD / mã BN / thẻ BHYT | HC  | —   |
| QT-01-020-b | Không tìm thấy → tìm đa tiêu chí (họ tên, ngày sinh, địa chỉ) | HC  | —   |
| QT-01-020-c | Vẫn không thấy → tạo mới; hệ thống GỢI Ý hồ sơ nghi trùng trước khi lưu | HC  | TT01-S02 |
| QT-01-020-d | Không có giấy tờ hoặc không xác định được danh tính → tạo hồ sơ TẠM | HC / ĐD cấp cứu | TT01-S01 |
| QT-01-020-e | Có định danh sau → hợp nhất hồ sơ tạm về hồ sơ thật | HC  | TT01-S01 → S04 |
| QT-01-020-f | Trả mã người bệnh cho HIS-03 để mở lượt điều trị | Hệ thống | —   |

## **4.2. Quy trình gộp hồ sơ trùng**

| **Bước** | **Việc** | **Vai trò** | **Trạng thái** |
| --- | --- | --- | --- |
| GOP-010 | Hệ thống gắn cờ nghi trùng theo bộ tiêu chí khớp | Hệ thống | TT01-S03 |
| GOP-020 | Nhân viên rà cặp nghi trùng, so sánh song song hai hồ sơ | HC  | TT01-S03 |
| GOP-030 | Kiểm tra lịch sử KCB của cả hai trước khi quyết định | HC  | TT01-S03 |
| GOP-040 | Trình duyệt gộp theo phân cấp | VT-22 | TT01-S03 |
| GOP-050 | Thực hiện gộp: chọn hồ sơ GỐC, hợp nhất dữ liệu, KHÔNG mất gì | Hệ thống | nguồn → TT01-S04 |
| GOP-060 | Phát sự kiện tới mọi phân hệ tiêu thụ mã người bệnh | Hệ thống | —   |
| GOP-070 | Phát hiện gộp nhầm → TÁCH LẠI theo lịch sử gộp | VT-22 | TT01-S04 → S02 |

## **4.3. Luồng ngoại lệ**

| **Mã** | **Tình huống** | **Cách xử lý** |
| --- | --- | --- |
| NL-01 | Người bệnh cấp cứu không có giấy tờ, không nói được | Tạo hồ sơ TẠM ở TT01-S01 với định danh quy ước; KHÔNG chặn tiếp nhận và không chặn xử trí. Hợp nhất về sau. |
| NL-02 | Trẻ sơ sinh chưa có giấy khai sinh | Tạo hồ sơ riêng gắn với hồ sơ mẹ; định danh tạm theo quy tắc cấu hình; cập nhật khi có giấy tờ. |
| NL-03 | CCCD nhập vào đã tồn tại ở hồ sơ khác đang hoạt động | CHẶN tạo mới. Mở hồ sơ đã có để đối chiếu. Đây là chốt duy nhất chặn cứng ở nhóm tạo hồ sơ. |
| NL-04 | Hai hồ sơ trùng CCCD do dữ liệu nhập tay từ trước khi có chốt | Gắn cờ nghi trùng mức cao nhất; đưa lên đầu hàng đợi rà gộp. |
| NL-05 | Người bệnh đổi CCCD (cấp lại, đổi số) | Không tạo hồ sơ mới. Thêm giấy tờ mới vào cùng hồ sơ, giữ giấy tờ cũ trong lịch sử. |
| NL-06 | Cổng BHXH hoặc VNeID không phản hồi | Vẫn tạo và cập nhật được hồ sơ; đánh dấu CHƯA XÁC MINH và vào hàng đợi tra lại. Không chặn tiếp nhận. |
| NL-07 | Gộp nhầm hai người khác nhau, phát hiện sau nhiều tháng | Tách lại theo lịch sử gộp; phát sự kiện tới mọi phân hệ đã nhận sự kiện gộp; ghi nhận SỰ CỐ AN TOÀN NGƯỜI BỆNH. |
| NL-08 | Hồ sơ đã có dữ liệu quyết toán ĐÃ GỬI cơ quan BHXH mà nay bị gộp | Vẫn gộp được, nhưng bản hồ sơ quyết toán đã gửi GIỮ NGUYÊN mã cũ. Xem ghi chú ở mục 5.6. |
| NL-09 | Người bệnh đề nghị không cho khoa khác xem hồ sơ | Ghi nhận theo quy chế; hạn chế ở tầng phân quyền, KHÔNG xóa dữ liệu. |

# **CHƯƠNG 5. ĐẶC TẢ CHI TIẾT CHỨC NĂNG**

## **5.1. Nhóm 020 — Định danh & sinh mã người bệnh****FS-HIS01-020-0010 — Sinh mã người bệnh duy nhất & quản lý giấy tờ tùy thân**

**① Mô tả & mục đích**

Mã người bệnh là thứ mọi phân hệ khác dùng để trỏ về một con người. Nó phải duy nhất, không tái sử dụng, và không đổi suốt đời — kể cả khi người bệnh đổi tên, đổi CCCD hay đổi địa chỉ. Chức năng này sinh mã và gắn các loại giấy tờ tùy thân vào cùng một hồ sơ.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: nhân viên hành chính tiếp đón; điều dưỡng cấp cứu với hồ sơ tạm.
- Tác nhân phụ: hệ thống tra VNeID và dữ liệu dân cư qua HIS-22.
- Tiền điều kiện: quy tắc sinh mã đã cấu hình (010-0010).
- Kích hoạt: tạo hồ sơ mới; hoặc thêm giấy tờ vào hồ sơ đã có.

**③ Logic xử lý**

1\. Sinh MÃ NGƯỜI BỆNH theo quy tắc cấu hình. Mã là DUY NHẤT toàn hệ thống, KHÔNG tái sử dụng kể cả khi hồ sơ bị vô hiệu (BR-001).

2\. Mã KHÔNG mang thông tin có thể đổi — không nhúng năm sinh, giới tính, khoa hay năm tạo vào cấu trúc mã. Nhúng thông tin đổi được vào mã là tạo ra mã sai khi thông tin thay đổi.

3\. Một hồ sơ gắn được NHIỀU loại giấy tờ: CCCD, hộ chiếu, giấy khai sinh, thẻ quân nhân, giấy tờ tạm. Mỗi giấy tờ ghi loại, số, nơi cấp, ngày cấp, và trạng thái còn hay đã thay thế.

4\. CCCD là giấy tờ ĐẶC BIỆT: một số CCCD chỉ được gắn với MỘT hồ sơ đang hoạt động. Nhập CCCD đã tồn tại thì CHẶN tạo mới và mở hồ sơ đã có để đối chiếu (NL-03).

5\. Đổi CCCD (cấp lại, đổi số): thêm giấy tờ mới, đánh dấu giấy tờ cũ ĐÃ THAY THẾ, giữ trong lịch sử. KHÔNG tạo hồ sơ mới (NL-05).

6\. Xác minh qua VNeID hoặc dữ liệu dân cư nếu có kết nối: đối chiếu họ tên, ngày sinh, giới tính; lệch thì cảnh báo và ghi nhận, KHÔNG tự sửa dữ liệu.

7\. Dịch vụ xác minh không phản hồi: vẫn tạo được hồ sơ, đánh dấu CHƯA XÁC MINH, vào hàng đợi tra lại (NL-06).

8\. KHÔNG CÓ GIẤY TỜ vẫn tạo được hồ sơ, ở TT01-S01 Tạm. Đây là điều kiện để cấp cứu và trẻ sơ sinh làm việc được.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-PID (Mã người bệnh) | Mã  | —   | Sinh tự động theo cấu hình; DUY NHẤT; không tái sử dụng; không mang thông tin đổi được |
| FLD-DOC-TYPE (Loại giấy tờ) | Enum | ✱   | CCCD / hộ chiếu / khai sinh / quân nhân / tạm / khác |
| FLD-DOC-NUMBER (Số giấy tờ) | Text | ✱   | Với CCCD: chỉ một hồ sơ ĐANG HOẠT ĐỘNG được giữ một số (VLD-HIS01-02) |
| FLD-DOC-ISSUER / DATE | Text / Ngày | —   | Nơi cấp và ngày cấp |
| FLD-DOC-STATE (Trạng thái giấy tờ) | Enum | —   | Đang dùng / Đã thay thế — không xóa giấy tờ cũ |
| FLD-VERIFIED (Đã xác minh) | Enum | —   | Chưa xác minh / Đã xác minh VNeID / Đã xác minh dữ liệu dân cư |
| FLD-VERIFY-DIFF (Sai lệch khi xác minh) | Group | —   | Trường nào lệch, giá trị hai bên. GHI NHẬN, không tự sửa |
| FLD-PID-STATE (Trạng thái hồ sơ) | Enum | —   | TT01-S01…S05 |

**⑤ Quy tắc nghiệp vụ áp dụng**

- BR-001 MÃ NGƯỜI BỆNH DUY NHẤT VÀ KHÔNG TÁI SỬ DỤNG. Tái sử dụng mã của hồ sơ đã vô hiệu là cách nhanh nhất gán bệnh sử của người này cho người khác.
- MÃ KHÔNG MANG THÔNG TIN ĐỔI ĐƯỢC. Nhúng năm sinh vào mã thì người khai sai năm sinh sẽ mang mã sai suốt đời; nhúng khoa thì chuyển khoa là mã sai.
- CHẶN TRÙNG CCCD, NHƯNG KHÔNG CHẶN TẠO HỒ SƠ KHI THIẾU CCCD. Hai việc khác nhau. Trùng CCCD gần như chắc chắn là cùng một người nên chặn là đúng; thiếu CCCD là chuyện thường ngày ở cấp cứu nên chặn là sai.
- XÁC MINH LỆCH THÌ CẢNH BÁO, KHÔNG TỰ SỬA. Dữ liệu dân cư cũng có sai sót, và người trực tiếp làm việc với người bệnh mới quyết được bên nào đúng.
- Áp dụng BR-015 (phân quyền theo vai trò và phạm vi) và BR-007 (nhật ký truy cập).

**⑥ Hành vi màn hình**

- MH-BN-01 hiển thị mã người bệnh cố định ở đầu màn, sao chép được bằng một thao tác — đây là số mà mọi phân hệ khác hỏi tới.
- Nhóm giấy tờ hiển thị dạng danh sách, giấy tờ đã thay thế thu gọn nhưng không ẩn hẳn.
- Nhập CCCD trùng: hiện ngay hồ sơ đang giữ số đó, kèm nút mở để đối chiếu — không chỉ báo lỗi rồi để người dùng tự tìm.
- Trạng thái xác minh hiển thị thành nhãn rõ ràng; hồ sơ chưa xác minh không bị chặn dùng, chỉ hiện nhãn.
- Sai lệch khi xác minh hiển thị song song hai giá trị để người dùng chọn, không tự ghi đè.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-01 | Số CCCD đã tồn tại ở hồ sơ khác đang hoạt động | CHẶN tạo mới; mở hồ sơ đã có |
| ERR-HIS01-02 | Tái sử dụng mã người bệnh của hồ sơ đã vô hiệu | LỖI THIẾT KẾ — không được phép xảy ra |
| ERR-HIS01-03 | Quy tắc sinh mã cấu hình có nhúng thông tin đổi được | Cảnh báo khi cấu hình |
| ERR-HIS01-04 | Xác minh VNeID lệch họ tên hoặc ngày sinh | Cảnh báo; ghi nhận sai lệch; không tự sửa |
| ERR-HIS01-05 | Dịch vụ xác minh không phản hồi | Cảnh báo; vẫn tạo hồ sơ; vào hàng đợi tra lại |
| ERR-HIS01-06 | Hệ thống chặn tạo hồ sơ vì thiếu CCCD hoặc thiếu thẻ BHYT | LỖI THIẾT KẾ — không được phép xảy ra |

**⑧ Hậu điều kiện & đầu ra**

- Hồ sơ có mã người bệnh duy nhất, dùng được ngay cho HIS-03 mở lượt.
- Giấy tờ tùy thân lưu đủ lịch sử, đổi CCCD không sinh hồ sơ mới.
- Hồ sơ thiếu giấy tờ vẫn dùng được, ở TT01-S01.

**⑨ Sự kiện phát sinh**

- EVT-PATIENT-CREATED
- EVT-PATIENT-ID-VERIFIED
- EVT-IDENTITY-MISMATCH

**⑩ Truy vết & nghiệm thu**

- Quy tắc: BR-001 · BR-007 · BR-015
- Test: TC-HIS01-BN-01/02/03
- Nghiệm thu: NT-HIS01-01

## **5.2. Nhóm 030 & 060 — Tạo hồ sơ và gợi ý trùng ngay lúc tạo****FS-HIS01-030-0010 — Tạo hồ sơ mới với gợi ý hồ sơ nghi trùng**

**① Mô tả & mục đích**

Chỗ tốt nhất để chống trùng hồ sơ là NGAY LÚC TẠO, không phải lúc dọn dữ liệu về sau. Một hồ sơ trùng đã tạo ra sẽ sinh lượt khám, sinh chi phí, sinh bệnh án — và gộp về sau tốn gấp nhiều lần so với ngăn nó ra đời.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: nhân viên hành chính tiếp đón.
- Tiền điều kiện: bộ tiêu chí khớp đã cấu hình (070-0010).
- Kích hoạt: người dùng nhập đủ trường tối thiểu và bấm lưu hồ sơ mới.

**③ Logic xử lý**

1\. Trước khi lưu, chạy bộ TÌM KIẾM NGHI TRÙNG trên các trường vừa nhập — không chờ người dùng chủ động tra cứu.

2\. Bộ tiêu chí khớp là cấu hình, tối thiểu gồm: trùng CCCD (chắc chắn) · trùng họ tên đầy đủ và ngày sinh · trùng họ tên, giới tính và địa chỉ · trùng số thẻ BHYT · trùng số điện thoại và họ tên.

3\. Kết quả nghi trùng hiển thị TRƯỚC KHI LƯU, kèm mức tin cậy và những trường nào khớp. Người dùng chọn: mở hồ sơ đã có, hoặc xác nhận đây là người khác và vẫn tạo mới.

4\. Xác nhận tạo mới dù có nghi trùng: bắt buộc GHI LÝ DO ngắn từ danh mục, và ghi nhận người xác nhận. Cặp hồ sơ vẫn được gắn cờ nghi trùng để rà sau.

5\. Trùng CCCD là trường hợp riêng: CHẶN, không có đường xác nhận tạo mới (NL-03).

6\. Trường bắt buộc theo cấu hình (010-0040). Hồ sơ TẠM có bộ trường bắt buộc RÚT GỌN — đủ để phân biệt người bệnh trong ca trực, không đòi giấy tờ.

7\. Cập nhật hồ sơ: mọi thay đổi trường định danh (họ tên, ngày sinh, giới tính) đều ghi lịch sử giá trị cũ, không ghi đè mất dấu.

8\. Nhiều địa chỉ và nhiều người liên hệ: lưu thành danh sách có đánh dấu địa chỉ liên hệ chính, không ép thành một dòng.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-NAME (Họ tên) | Text | ✱   | Lưu lịch sử khi đổi |
| FLD-DOB (Ngày sinh) | Ngày | ✱   | Cho phép chỉ có năm khi không rõ ngày tháng; đánh dấu mức chính xác |
| FLD-DOB-PRECISION (Mức chính xác ngày sinh) | Enum | —   | Đủ ngày / chỉ tháng năm / chỉ năm — ảnh hưởng tiêu chí khớp |
| FLD-SEX (Giới tính) | Enum | ✱   | Theo danh mục HIS-20 |
| FLD-ADDRESS (Địa chỉ) | List | —   | Nhiều địa chỉ; đánh dấu địa chỉ liên hệ chính |
| FLD-CONTACT (Người liên hệ) | List | —   | Nhiều người; ghi quan hệ và mức ưu tiên liên hệ |
| FLD-DUP-CANDIDATES (Hồ sơ nghi trùng) | Group | —   | Hiện TRƯỚC khi lưu; mỗi dòng kèm mức tin cậy và trường khớp |
| FLD-DUP-OVERRIDE (Lý do vẫn tạo mới) | Enum+Text | ✱ khi có nghi trùng | Chọn từ danh mục; ghi người xác nhận |
| FLD-REQUIRED-SET (Bộ trường bắt buộc áp dụng) | Ref | —   | Bộ đầy đủ hoặc bộ rút gọn cho hồ sơ tạm |

**⑤ Quy tắc nghiệp vụ áp dụng**

- GỢI Ý TRÙNG CHẠY TRƯỚC KHI LƯU, KHÔNG PHẢI SAU. Sau khi lưu thì hồ sơ đã ra đời và bắt đầu tích dữ liệu.
- TRÙNG CCCD CHẶN; TRÙNG TIÊU CHÍ KHÁC CHỈ CẢNH BÁO. Hai người có thể trùng họ tên và ngày sinh — đó là chuyện thật, và chặn ở đó sẽ làm người dùng học cách nhập sai lệch đi để lách.
- XÁC NHẬN TẠO MỚI PHẢI CÓ LÝ DO VÀ CÓ TÊN NGƯỜI. Bỏ qua vô danh sẽ thành thói quen; bỏ qua có tên và thống kê được thì tự nó giới hạn.
- HỒ SƠ TẠM CÓ BỘ TRƯỜNG BẮT BUỘC RÚT GỌN. Đòi đủ trường ở phòng cấp cứu là đòi điều dưỡng chọn giữa nhập liệu và cứu người.
- MỨC CHÍNH XÁC NGÀY SINH ẢNH HƯỞNG TIÊU CHÍ KHỚP. Hai hồ sơ chỉ biết năm sinh mà cùng năm thì độ tin cậy thấp hơn nhiều so với trùng đủ ngày tháng năm.

**⑥ Hành vi màn hình**

- Màn tạo hồ sơ chạy tìm nghi trùng ngay khi người dùng nhập xong họ tên và ngày sinh, không chờ bấm lưu.
- Danh sách nghi trùng hiển thị bên cạnh biểu mẫu đang nhập, mỗi dòng NÊU RÕ TRƯỜNG NÀO KHỚP — người dùng cần thấy vì sao hệ thống nghi.
- Nút mở hồ sơ đã có đặt cạnh từng dòng nghi trùng; nút tạo mới đặt xa hơn và đổi màu khi có nghi trùng.
- Hồ sơ tạm có biểu mẫu riêng, ngắn, mở được bằng một thao tác từ màn tiếp nhận cấp cứu.
- Đổi trường định danh hiện cảnh báo nhẹ kèm giá trị cũ, để người dùng biết mình đang sửa thứ có ảnh hưởng rộng.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-07 | Trùng CCCD với hồ sơ đang hoạt động | CHẶN |
| ERR-HIS01-08 | Có nghi trùng mà tạo mới không ghi lý do | Chặn |
| ERR-HIS01-09 | Thiếu trường bắt buộc theo bộ đang áp dụng | Chặn |
| ERR-HIS01-10 | Ngày sinh trong tương lai hoặc quá xa quá khứ theo ngưỡng cấu hình | Chặn |
| ERR-HIS01-11 | Đổi trường định danh mà không lưu được giá trị cũ | LỖI THIẾT KẾ |

**⑧ Hậu điều kiện & đầu ra**

- Hồ sơ mới ở TT01-S02 (đầy đủ) hoặc TT01-S01 (tạm).
- Cặp hồ sơ có nghi trùng đã được gắn cờ để rà, kể cả khi người dùng chọn tạo mới.
- Mọi thay đổi trường định danh có lịch sử giá trị cũ.

**⑨ Sự kiện phát sinh**

- EVT-PATIENT-CREATED
- EVT-DUPLICATE-SUSPECTED
- EVT-DUPLICATE-OVERRIDDEN
- EVT-PATIENT-UPDATED

**⑩ Truy vết & nghiệm thu**

- Test: TC-HIS01-BN-04/05/06
- Nghiệm thu: NT-HIS01-03

## **5.3. Nhóm 040 — Thẻ BHYT theo thời hạn****FS-HIS01-040-0010 — Nhiều thẻ BHYT theo thời hạn & kiểm tra qua cổng BHXH**

**① Mô tả & mục đích**

Một người có nhiều thẻ BHYT nối tiếp nhau theo thời gian, và mỗi lượt khám phải tra đúng thẻ có hiệu lực TẠI NGÀY KHÁM. Lưu một thẻ hiện hành rồi ghi đè khi có thẻ mới là làm hỏng khả năng quyết toán các lượt cũ.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: nhân viên hành chính tiếp đón.
- Tác nhân phụ: hệ thống tra cổng BHXH qua HIS-22.
- Tiền điều kiện: hồ sơ người bệnh đã tồn tại.
- Kích hoạt: nhập thẻ mới; hoặc tới lượt khám cần tra thẻ.

**③ Logic xử lý**

1\. Mỗi thẻ là MỘT BẢN GHI RIÊNG với mã thẻ, nhóm đối tượng, nơi đăng ký ban đầu, HIỆU LỰC TỪ và HIỆU LỰC ĐẾN. Thẻ mới KHÔNG ghi đè thẻ cũ.

2\. Không cho hai thẻ chồng lấn khoảng hiệu lực. Trùng khoảng nghĩa là có ngày hệ thống không biết dùng thẻ nào.

3\. Tra thẻ cho một lượt: lấy thẻ có hiệu lực TẠI NGÀY KHÁM, không lấy thẻ mới nhất. Cùng nguyên tắc với bảng ánh xạ danh mục của HIS-17 và danh mục tài liệu của HIS-18.

4\. Kiểm tra qua cổng BHXH: lưu kết quả tra kèm THỜI ĐIỂM TRA và nguyên văn phản hồi. Kết quả tra là bằng chứng tại thời điểm đó, không tra lại về sau.

5\. Cổng không phản hồi: vẫn nhận thẻ, đánh dấu CHƯA XÁC MINH, vào hàng đợi tra lại. KHÔNG chặn tiếp nhận (NL-06).

6\. Thẻ hết hạn: KHÔNG xóa, chuyển trạng thái hết hiệu lực và giữ nguyên trong lịch sử — các lượt cũ vẫn phải tra được thẻ đã dùng lúc đó.

7\. HIS-01 lưu thẻ và kết quả tra; HIS-03 dùng dữ liệu này để xác định căn cứ hưởng và mức hưởng của lượt. HIS-01 KHÔNG tính mức hưởng.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-BH-CARD (Mã thẻ) | Text | ✱   | Định dạng theo quy định hiện hành |
| FLD-BH-GROUP (Nhóm đối tượng) | Ref | ✱   | Một chiều của bảng tra mức hưởng ở HIS-03 |
| FLD-BH-REGPLACE (Nơi đăng ký ban đầu) | Ref | ✱   | —   |
| FLD-BH-FROM / TO (Hiệu lực) | Ngày | ✱ / — | Không chồng lấn với thẻ khác của cùng người (VLD-HIS01-08) |
| FLD-BH-CHECKED (Đã tra cổng) | Cờ  | —   | —   |
| FLD-BH-CHECKTIME (Thời điểm tra) | DateTime | —   | Kết quả là bằng chứng TẠI THỜI ĐIỂM đó |
| FLD-BH-RESPONSE (Phản hồi cổng) | Blob | —   | Lưu NGUYÊN VĂN; không diễn giải lại |
| FLD-BH-STATE (Trạng thái thẻ) | Enum | —   | Đang hiệu lực / Hết hiệu lực / Chưa xác minh |

**⑤ Quy tắc nghiệp vụ áp dụng**

- THẺ MỚI KHÔNG GHI ĐÈ THẺ CŨ. Quyết toán một lượt của tháng trước cần thẻ của tháng trước. Ghi đè là làm mất khả năng giải trình khi giám định.
- TRA THEO NGÀY KHÁM, KHÔNG THEO NGÀY TRA. Cùng nguyên tắc hiệu lực theo thời gian đã áp ở HIS-17 và HIS-18 — ba phân hệ, cùng một cái bẫy.
- CỔNG BHXH CHẾT KHÔNG CHẶN TIẾP NHẬN. Người bệnh đang đứng trước quầy; hạ tầng của bên thứ ba không phải lý do để họ chờ.
- LƯU NGUYÊN VĂN PHẢN HỒI CỔNG. Khi cơ quan BHXH và bệnh viện hiểu khác nhau về tình trạng một thẻ, bản ghi nguyên văn là thứ giải quyết tranh chấp.
- HIS-01 KHÔNG TÍNH MỨC HƯỞNG. Mức hưởng là kết quả tra bảng theo nhóm đối tượng, cấp chuyên môn kỹ thuật và căn cứ hưởng — việc của HIS-03. Nhân đôi logic ở hai nơi thì hai nơi sẽ lệch nhau.

**⑥ Hành vi màn hình**

- MH-BN-01 hiển thị thẻ BHYT dạng DÒNG THỜI GIAN các thẻ nối tiếp, thấy ngay chỗ đứt quãng không có thẻ.
- Thẻ đang hiệu lực nổi bật; thẻ cũ thu gọn nhưng mở xem được.
- Kết quả tra cổng hiện kèm thời điểm tra; quá ngưỡng cấu hình thì hiện nhãn cần tra lại.
- Thẻ chưa xác minh không chặn thao tác nào, chỉ hiện nhãn.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-12 | Hai thẻ chồng lấn khoảng hiệu lực | Chặn |
| ERR-HIS01-13 | Ghi đè thẻ cũ thay vì thêm thẻ mới | Chặn |
| ERR-HIS01-14 | Cổng BHXH không phản hồi | Cảnh báo; vẫn nhận thẻ; vào hàng đợi tra lại |
| ERR-HIS01-15 | Cổng trả về thẻ không hợp lệ | Cảnh báo; ghi nhận nguyên văn; KHÔNG chặn tiếp nhận |
| ERR-HIS01-16 | Hệ thống chặn tiếp nhận vì thẻ chưa xác minh | LỖI THIẾT KẾ |

**⑧ Hậu điều kiện & đầu ra**

- Người bệnh có lịch sử thẻ liên tục, tra được thẻ đúng của bất kỳ ngày nào trong quá khứ.
- Kết quả tra cổng lưu kèm thời điểm và nguyên văn phản hồi.

**⑨ Sự kiện phát sinh**

- EVT-BHYT-CARD-ADDED
- EVT-BHYT-VERIFIED
- EVT-BHYT-VERIFY-FAILED

**⑩ Truy vết & nghiệm thu**

- Test: TC-HIS01-BN-07/08
- Nghiệm thu: NT-HIS01-02

## **5.4. Nhóm 050 — Tiền sử & dị ứng****FS-HIS01-050-0020 — Bản ghi dị ứng & đường đi tới màn hình lâm sàng**

**① Mô tả & mục đích**

Một bản ghi dị ứng chỉ có giá trị nếu nó XUẤT HIỆN TRƯỚC MẶT người sắp kê thuốc. Ghi vào hồ sơ rồi để đó là ghi cho có. Chức năng này đặc tả bản ghi và — quan trọng hơn — đường đi của nó tới nơi cần dùng.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: bác sĩ và điều dưỡng ghi nhận dị ứng.
- Tác nhân tiêu thụ: HIS-10 (quy tắc an toàn thuốc), HIS-21 (CDSS), mọi màn lâm sàng.
- Tiền điều kiện: hồ sơ người bệnh đã tồn tại.
- Kích hoạt: ghi nhận dị ứng mới; hoặc mở bất kỳ màn lâm sàng nào của người bệnh.

**③ Logic xử lý**

1\. Mỗi dị ứng là một bản ghi: TÁC NHÂN (thuốc, hoạt chất, nhóm thuốc, thức ăn, khác) · BIỂU HIỆN · MỨC ĐỘ · MỨC CHẮC CHẮN · người ghi nhận · thời điểm · nguồn thông tin.

2\. MỨC CHẮC CHẮN là trường bắt buộc, ba giá trị: ĐÃ KHẲNG ĐỊNH (có bằng chứng lâm sàng) · NGHI NGỜ · NGƯỜI BỆNH KHAI. Ba mức này dẫn tới ba cách xử lý khác nhau ở HIS-10.

3\. Dị ứng thuốc ghi theo HOẠT CHẤT chứ không theo tên thương mại. Ghi theo tên thương mại thì cùng hoạt chất dưới tên khác sẽ lọt qua.

4\. Phát sự kiện tới HIS-10 mỗi lần thêm hoặc đổi dị ứng. HIS-10 là NGUỒN QUY TẮC AN TOÀN THUỐC DUY NHẤT (BR-011) — HIS-01 cấp dữ liệu, không tự dựng quy tắc cảnh báo.

5\. Cảnh báo dị ứng hiển thị NỔI BẬT trên mọi màn lâm sàng của người bệnh: khám, điều trị, cấp cứu, kê đơn, thực hiện thuốc. Vị trí và hình thức thống nhất toàn hệ thống.

6\. GỠ hoặc SỬA một dị ứng đã khẳng định: bắt buộc ghi lý do và người thực hiện; bản ghi cũ giữ trong lịch sử, không xóa.

7\. Tiền sử bệnh ghi tương tự nhưng không sinh cảnh báo chặn; nó là bối cảnh cho bác sĩ đọc, và là nguồn cho CDSS của HIS-21.

8\. Văn bản đồng ý (consent) lưu kèm loại, phạm vi, thời hạn, người ký; ký số qua HIS-18 khi áp dụng.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-ALG-AGENT (Tác nhân) | Ref | ✱   | Với thuốc: HOẠT CHẤT từ danh mục, không phải tên thương mại (VLD-HIS01-11) |
| FLD-ALG-TYPE (Loại tác nhân) | Enum | ✱   | Hoạt chất / nhóm thuốc / thức ăn / môi trường / khác |
| FLD-ALG-REACTION (Biểu hiện) | Text | ✱   | —   |
| FLD-ALG-SEVERITY (Mức độ) | Enum | ✱   | Nhẹ / trung bình / nặng / phản vệ |
| FLD-ALG-CERTAINTY (Mức chắc chắn) | Enum | ✱   | Đã khẳng định / Nghi ngờ / Người bệnh khai — quyết định cách HIS-10 xử lý |
| FLD-ALG-SOURCE (Nguồn thông tin) | Enum | ✱   | Người bệnh khai / hồ sơ cũ / kết quả xét nghiệm / biến cố ghi nhận tại viện |
| FLD-ALG-BY / TIME | Mã người hành nghề / DateTime | ✱   | Snapshot |
| FLD-ALG-REMOVEREASON (Lý do gỡ) | Text | ✱ khi gỡ | Bắt buộc; bản ghi cũ giữ trong lịch sử |
| FLD-HIST-CONDITION (Tiền sử bệnh) | Group | —   | Bệnh, thời gian, tình trạng hiện tại |
| FLD-CONSENT (Văn bản đồng ý) | Group | —   | Loại, phạm vi, thời hạn, người ký; ký số qua HIS-18 |

**⑤ Quy tắc nghiệp vụ áp dụng**

- DỊ ỨNG THUỐC GHI THEO HOẠT CHẤT. Đây là quy tắc quan trọng nhất của mục này. Ghi theo tên thương mại thì bản ghi chỉ chặn được đúng biệt dược đó, còn cùng hoạt chất dưới tên khác sẽ đi qua — và đó chính là cách phản vệ xảy ra ở người đã có bản ghi dị ứng.
- MỨC CHẮC CHẮN LÀ TRƯỜNG BẮT BUỘC. Không phân biệt được ĐÃ KHẲNG ĐỊNH với NGƯỜI BỆNH KHAI thì HIS-10 buộc phải xử lý mọi bản ghi như nhau — hoặc chặn quá nhiều tới mức bị bỏ qua, hoặc chặn quá ít tới mức vô dụng.
- HIS-01 CẤP DỮ LIỆU, HIS-10 DỰNG QUY TẮC. BR-011 quy định HIS-10 là nguồn quy tắc an toàn thuốc duy nhất. HIS-01 tự dựng cảnh báo riêng là tạo ra hai bộ quy tắc lệch nhau.
- GỠ DỊ ỨNG PHẢI CÓ LÝ DO VÀ CÓ TÊN. Gỡ một bản ghi phản vệ là quyết định lâm sàng nặng, không phải dọn dữ liệu.
- CẢNH BÁO HIỂN THỊ THỐNG NHẤT TOÀN HỆ THỐNG. Mỗi màn một kiểu thì người dùng phải học lại ở từng chỗ, và sẽ có chỗ họ không nhận ra.

**⑥ Hành vi màn hình**

- Dải cảnh báo dị ứng đặt ở VỊ TRÍ CỐ ĐỊNH trên đầu mọi màn lâm sàng, cùng màu, cùng hình thức — không giấu trong tab phụ.
- Dị ứng mức phản vệ hiển thị khác biệt rõ so với các mức khác.
- Mức chắc chắn hiển thị ngay cạnh tác nhân, để người đọc biết đây là dữ kiện hay là lời khai.
- Ô nhập tác nhân là ô CHỌN TỪ DANH MỤC HOẠT CHẤT, không phải ô gõ tự do.
- Gỡ dị ứng mở hộp thoại bắt ghi lý do; không có nút xóa nhanh.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-17 | Ghi dị ứng thuốc theo tên thương mại thay vì hoạt chất | Chặn |
| ERR-HIS01-18 | Thiếu mức chắc chắn | Chặn |
| ERR-HIS01-19 | Gỡ dị ứng mà không ghi lý do | Chặn |
| ERR-HIS01-20 | Xóa vĩnh viễn bản ghi dị ứng | CHẶN — chỉ gỡ có lịch sử |
| ERR-HIS01-21 | Màn lâm sàng không hiển thị dải cảnh báo dị ứng | LỖI THIẾT KẾ |
| ERR-HIS01-22 | HIS-01 tự dựng quy tắc cảnh báo thuốc thay vì gọi HIS-10 | LỖI THIẾT KẾ |

**⑧ Hậu điều kiện & đầu ra**

- Dị ứng ghi theo hoạt chất, có mức chắc chắn, có nguồn.
- HIS-10 nhận được dữ liệu để dựng quy tắc; HIS-21 nhận được để đưa vào CDSS.
- Cảnh báo hiển thị nổi bật và thống nhất trên mọi màn lâm sàng.

**⑨ Sự kiện phát sinh**

- EVT-ALLERGY-RECORDED
- EVT-ALLERGY-REMOVED
- EVT-HISTORY-UPDATED
- EVT-CONSENT-RECORDED

**⑩ Truy vết & nghiệm thu**

- Quy tắc: BR-011 (HIS-10 là nguồn quy tắc duy nhất)
- Test: TC-HIS01-BN-09/10
- Nghiệm thu: NT-HIS01-05

## **5.5. Nhóm 070 — Phát hiện hồ sơ nghi trùng****FS-HIS01-070-0010 — Bộ tiêu chí khớp & hàng đợi rà nghi trùng**

**① Mô tả & mục đích**

Phát hiện trùng là bài toán đánh đổi: bộ tiêu chí lỏng cho ra hàng nghìn cặp nghi trùng mà phần lớn là nhiễu, và nhân viên sẽ bỏ qua cả hàng đợi. Bộ tiêu chí chặt bỏ sót đúng những cặp cần tìm. Cách giải là PHÂN MỨC — không phải một ngưỡng duy nhất.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: hệ thống chạy theo lịch và chạy khi tạo hồ sơ.
- Tác nhân xử lý: nhân viên hành chính rà hàng đợi trên MH-BN-03.
- Tiền điều kiện: bộ tiêu chí khớp đã cấu hình.
- Kích hoạt: tạo hoặc sửa hồ sơ; hoặc lịch quét định kỳ toàn bộ dữ liệu.

**③ Logic xử lý**

1\. Bộ tiêu chí là CẤU HÌNH, mỗi tiêu chí có trọng số và mức tin cậy riêng. Đổi tiêu chí không phải phát hành lại phần mềm.

2\. Ba mức tin cậy: CHẮC CHẮN (trùng CCCD) · CAO (trùng họ tên đầy đủ, ngày sinh đủ, giới tính) · TRUNG BÌNH (trùng họ tên và địa chỉ, hoặc trùng thẻ BHYT, hoặc trùng số điện thoại và họ tên).

3\. Chuẩn hóa trước khi so: bỏ dấu, chuẩn hóa khoảng trắng, chuẩn hóa cách viết tên đệm, chuẩn hóa địa chỉ theo danh mục hành chính. So chuỗi thô sẽ bỏ sót phần lớn trường hợp thật.

4\. MỨC CHÍNH XÁC NGÀY SINH tham gia tính điểm: hai hồ sơ chỉ biết năm sinh mà cùng năm thì tin cậy thấp hơn nhiều so với trùng đủ ngày tháng năm.

5\. Cặp nghi trùng vào HÀNG ĐỢI RÀ, sắp theo mức tin cậy rồi theo SỐ LƯỢT KHÁM của hồ sơ — hồ sơ nhiều dữ liệu thì gộp nhầm hại hơn, mà để trùng cũng hại hơn.

6\. Cặp đã được người dùng XÁC NHẬN LÀ HAI NGƯỜI KHÁC NHAU thì ghi vào danh sách loại trừ, không hiện lại ở lần quét sau. Danh sách loại trừ xem lại được.

7\. Thống kê: số cặp phát hiện, số cặp đã gộp, số cặp loại trừ, số hồ sơ trùng lọt qua bị phát hiện muộn. Con số cuối là thước đo bộ tiêu chí có đủ chặt không.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-DUP-PAIR (Cặp hồ sơ) | Group | ✱   | Hai mã người bệnh |
| FLD-DUP-LEVEL (Mức tin cậy) | Enum | ✱   | CHẮC CHẮN / CAO / TRUNG BÌNH |
| FLD-DUP-MATCHED (Trường khớp) | List | ✱   | Nêu rõ trường nào khớp — người rà cần biết vì sao hệ thống nghi |
| FLD-DUP-SCORE (Điểm khớp) | Number | —   | Từ trọng số cấu hình |
| FLD-DUP-STATE (Trạng thái cặp) | Enum | —   | Chờ rà / Đã gộp / Đã loại trừ |
| FLD-DUP-EXCLUDEBY (Người loại trừ) | Ref | ✱ khi loại trừ | Kèm lý do |
| FLD-DUP-ENCOUNTERS (Số lượt của mỗi hồ sơ) | Number | —   | Dùng để sắp thứ tự rà |

**⑤ Quy tắc nghiệp vụ áp dụng**

- PHÂN MỨC, KHÔNG DÙNG MỘT NGƯỠNG. Một ngưỡng duy nhất buộc phải chọn giữa nhiễu và bỏ sót. Ba mức cho phép xử lý khác nhau: chắc chắn thì chặn ngay lúc tạo, cao thì đưa lên đầu hàng đợi, trung bình thì rà khi rảnh.
- CHUẨN HÓA TRƯỚC KHI SO. Tên tiếng Việt có dấu, viết hoa thường lẫn lộn, tên đệm khi có khi không. So chuỗi thô là bỏ sót phần lớn cặp thật.
- SẮP HÀNG ĐỢI THEO SỐ LƯỢT KHÁM. Hồ sơ đã tích nhiều dữ liệu thì cả hai hướng sai đều đắt hơn — nên rà trước.
- DANH SÁCH LOẠI TRỪ PHẢI XEM LẠI ĐƯỢC. Loại trừ nhầm cũng là một loại sai, và nếu danh sách là hố đen thì không ai phát hiện được.
- ĐO SỐ HỒ SƠ TRÙNG PHÁT HIỆN MUỘN. Đây là chỉ số duy nhất nói được bộ tiêu chí có đủ chặt không. Đếm số cặp phát hiện được chỉ nói lên bộ tiêu chí lỏng tới đâu.

**⑥ Hành vi màn hình**

- MH-BN-03 hàng đợi hiển thị theo mức tin cậy, mỗi dòng nêu rõ TRƯỜNG NÀO KHỚP và số lượt khám của hai hồ sơ.
- Mở một cặp thì hiện hai hồ sơ SO SÁNH SONG SONG, trường khớp tô sáng, trường lệch tô khác màu.
- Nút loại trừ nằm cạnh nút gộp, cùng kích thước — hai lựa chọn ngang nhau, không đẩy người dùng về một phía.
- Danh sách đã loại trừ mở xem lại được bằng một bộ lọc, không bị ẩn hẳn.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-23 | So khớp trên chuỗi thô, không chuẩn hóa | LỖI THIẾT KẾ |
| ERR-HIS01-24 | Loại trừ cặp nghi trùng mà không ghi lý do | Chặn |
| ERR-HIS01-25 | Bộ tiêu chí chôn cứng trong mã nguồn | LỖI THIẾT KẾ |

**⑧ Hậu điều kiện & đầu ra**

- Cặp nghi trùng có mức tin cậy và trường khớp cụ thể, sắp theo mức độ ảnh hưởng.
- Cặp đã loại trừ không hiện lại nhưng xem lại được.
- Thống kê đủ để đánh giá bộ tiêu chí, kể cả số hồ sơ trùng phát hiện muộn.

**⑨ Sự kiện phát sinh**

- EVT-DUPLICATE-SUSPECTED
- EVT-DUPLICATE-EXCLUDED

**⑩ Truy vết & nghiệm thu**

- Test: TC-HIS01-BN-11/12
- Nghiệm thu: NT-HIS01-03

## **5.6. Nhóm 070 — GỘP HỒ SƠ: không mất dữ liệu và khôi phục được**

_Vì sao mục này quan trọng nhất: ĐÂY LÀ MỤC TRỌNG TÂM CỦA TÀI LIỆU. Gộp hồ sơ là thao tác DUY NHẤT trong phân hệ này có thể gây hại trực tiếp cho người bệnh: gộp nhầm hai người khác nhau nghĩa là bệnh sử, dị ứng và kết quả xét nghiệm của người này xuất hiện trên hồ sơ của người kia — và bác sĩ tiếp theo sẽ điều trị theo dữ liệu sai mà không có dấu hiệu gì cho thấy nó sai. Vì vậy gộp phải KHÔI PHỤC ĐƯỢC, và đây là yêu cầu không thương lượng._

## **FS-HIS01-070-0040 — Thực hiện gộp, lan tỏa sự kiện & tách lại khi gộp nhầm**

**① Mô tả & mục đích**

Hợp nhất hai hồ sơ về một, giữ toàn bộ dữ liệu của cả hai, báo cho mọi phân hệ đang dùng mã cũ, và lưu đủ thông tin để tách lại nếu phát hiện gộp nhầm. Ba yêu cầu này phải cùng đạt; thiếu một là hỏng cả ba.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: nhân viên hành chính thực hiện; VT-22 trưởng phòng hoặc người được phân cấp DUYỆT.
- Tác nhân tiêu thụ: mọi phân hệ lưu mã người bệnh — HIS-03, HIS-04/05/06, HIS-16, HIS-17, HIS-18, HIS-22.
- Tiền điều kiện: cặp ở TT01-S03; đã rà lịch sử KCB của cả hai (070-0020).
- Kích hoạt: người có thẩm quyền duyệt gộp trên MH-BN-03.

**③ Logic xử lý**

1\. Chọn HỒ SƠ GỐC (giữ lại) và HỒ SƠ NGUỒN (bị gộp vào). Mặc định gốc là hồ sơ có nhiều lượt khám hơn, nhưng người dùng đổi được kèm lý do.

2\. TRƯỚC KHI GỘP, hệ thống lập BẢN CHỤP TOÀN VẸN của cả hai hồ sơ: mọi trường, mọi liên kết, mọi danh sách con. Đây là dữ liệu để tách lại về sau.

3\. GỘP DỮ LIỆU theo quy tắc rõ ràng cho từng loại: trường đơn trị (họ tên, ngày sinh) lấy từ hồ sơ gốc, giá trị của nguồn lưu vào lịch sử · danh sách (địa chỉ, giấy tờ, thẻ BHYT, người liên hệ) HỢP NHẤT cả hai, khử trùng lặp · dị ứng và tiền sử HỢP NHẤT, KHÔNG khử trùng mà giữ cả hai bản ghi với nguồn khác nhau.

4\. Vì sao dị ứng không khử trùng lặp: hai bản ghi cùng hoạt chất nhưng khác mức chắc chắn hoặc khác nguồn là hai thông tin khác nhau. Khử trùng là mất một thông tin.

5\. MỌI DỮ LIỆU LÂM SÀNG của hồ sơ nguồn — lượt khám, bệnh án, kết quả, chi phí — chuyển tham chiếu sang hồ sơ gốc. KHÔNG sao chép, KHÔNG xóa.

6\. Hồ sơ nguồn chuyển TT01-S04 Đã gộp, GIỮ NGUYÊN mã cũ và giữ liên kết trỏ tới hồ sơ gốc. Tra mã cũ vẫn ra được, và tự chuyển hướng tới hồ sơ gốc.

7\. Lưu BẢN GHI LỊCH SỬ GỘP: hai mã, ai thực hiện, ai duyệt, thời điểm, lý do, bản chụp toàn vẹn trước gộp, và danh sách mọi bản ghi đã đổi tham chiếu.

8\. PHÁT SỰ KIỆN EVT-PATIENT-MERGED tới mọi phân hệ tiêu thụ mã người bệnh. Phân hệ nào lưu mã cũ phải cập nhật hoặc phải xử lý được việc mã cũ trỏ tới hồ sơ mới.

9\. TÁCH LẠI khi phát hiện gộp nhầm: dựng lại hai hồ sơ từ bản chụp, trả từng bản ghi lâm sàng về đúng hồ sơ theo danh sách đã lưu, phát EVT-PATIENT-UNMERGED. Hồ sơ nguồn trở lại TT01-S02.

10\. Tách lại phải ghi nhận là SỰ CỐ AN TOÀN NGƯỜI BỆNH, không phải thao tác dọn dữ liệu — vì trong khoảng thời gian bị gộp nhầm, có thể đã có người điều trị theo dữ liệu sai.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-MRG-TARGET (Hồ sơ gốc) | Ref | ✱   | Mặc định là hồ sơ nhiều lượt hơn; đổi được kèm lý do |
| FLD-MRG-SOURCE (Hồ sơ nguồn) | Ref | ✱   | Sẽ chuyển TT01-S04 |
| FLD-MRG-SNAPSHOT (Bản chụp trước gộp) | Blob | ✱   | TOÀN VẸN cả hai hồ sơ — điều kiện để tách lại (VLD-HIS01-14) |
| FLD-MRG-MOVED (Danh sách bản ghi đã đổi tham chiếu) | List | ✱   | Từng bản ghi lâm sàng; điều kiện để trả về đúng chỗ khi tách |
| FLD-MRG-BY / APPROVER | Ref | ✱   | Người thực hiện và NGƯỜI DUYỆT phải khác nhau (VLD-HIS01-15) |
| FLD-MRG-REASON (Lý do gộp) | Text | ✱   | —   |
| FLD-MRG-TIME | DateTime | ✱   | —   |
| FLD-MRG-FIELDCHOICE (Lựa chọn từng trường đơn trị) | Group | —   | Giá trị nào giữ lại; giá trị kia vào lịch sử |
| FLD-UNM-REASON (Lý do tách lại) | Text | ✱ khi tách | Bắt buộc; ghi nhận sự cố |
| FLD-UNM-IMPACT (Đánh giá ảnh hưởng) | Text | ✱ khi tách | Trong thời gian bị gộp nhầm đã có điều trị nào dựa trên dữ liệu sai không |

**⑤ Quy tắc nghiệp vụ áp dụng**

- GỘP PHẢI KHÔI PHỤC ĐƯỢC — yêu cầu không thương lượng. Không có bản chụp toàn vẹn và danh sách bản ghi đã chuyển thì không tách lại được, và một lần gộp nhầm thành vĩnh viễn.
- KHÔNG XÓA HỒ SƠ NGUỒN. Chuyển TT01-S04 và giữ mã cũ. Mã cũ có thể đang nằm trong giấy tờ đã in, trong hồ sơ quyết toán đã gửi, trong hệ thống của đối tác — xóa là làm hỏng mọi thứ trỏ tới nó.
- DỊ ỨNG VÀ TIỀN SỬ HỢP NHẤT, KHÔNG KHỬ TRÙNG. Hai bản ghi cùng hoạt chất khác mức chắc chắn là hai thông tin. Khử trùng lặp ở đây là mất dữ liệu an toàn.
- NGƯỜI THỰC HIỆN VÀ NGƯỜI DUYỆT PHẢI KHÁC NHAU. Cùng nguyên tắc hai người với đếm gạc của HIS-09: thao tác không đảo ngược được về mặt hậu quả lâm sàng thì cần hai cặp mắt.
- TÁCH LẠI LÀ SỰ CỐ AN TOÀN NGƯỜI BỆNH. Phải đánh giá trong thời gian bị gộp nhầm đã có ai điều trị theo dữ liệu sai chưa. Coi nó là thao tác dọn dữ liệu là bỏ qua đúng phần nguy hiểm.

**⑥ Hành vi màn hình**

- MH-BN-03 so sánh SONG SONG hai hồ sơ, cột trái gốc cột phải nguồn, trường lệch tô màu.
- Với từng trường đơn trị lệch nhau, người dùng chọn giá trị giữ lại — không để hệ thống tự quyết im lặng.
- Trước khi xác nhận, hiện BẢNG TÓM TẮT ẢNH HƯỞNG: bao nhiêu lượt khám, bao nhiêu bệnh án, bao nhiêu dòng chi phí sẽ đổi tham chiếu.
- Nút duyệt gộp chỉ hiện với vai có thẩm quyền, và không hiện với chính người đã lập đề nghị.
- Hồ sơ ở TT01-S04 mở được, hiển thị nhãn rõ ĐÃ GỘP kèm liên kết tới hồ sơ gốc; không hiện như hồ sơ bình thường.
- Chức năng tách lại nằm trong lịch sử gộp, có cảnh báo rõ đây là xử lý sự cố chứ không phải thao tác thường ngày.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-26 | Gộp mà không lập được bản chụp toàn vẹn | CHẶN |
| ERR-HIS01-27 | Người duyệt trùng người thực hiện | CHẶN |
| ERR-HIS01-28 | Xóa hồ sơ nguồn thay vì chuyển TT01-S04 | CHẶN |
| ERR-HIS01-29 | Khử trùng lặp bản ghi dị ứng khi gộp | LỖI THIẾT KẾ |
| ERR-HIS01-30 | Gộp hai hồ sơ có CCCD KHÁC NHAU và cả hai đã xác minh | CHẶN — gần như chắc chắn là hai người |
| ERR-HIS01-31 | Tách lại mà không ghi lý do và đánh giá ảnh hưởng | Chặn |
| ERR-HIS01-32 | Phân hệ tiêu thụ không xử lý được EVT-PATIENT-MERGED | LỖI TÍCH HỢP — cảnh báo quản trị |

**⑧ Hậu điều kiện & đầu ra**

- Một hồ sơ gốc mang đủ dữ liệu của cả hai; không bản ghi nào bị mất.
- Hồ sơ nguồn ở TT01-S04, tra mã cũ vẫn ra và tự chuyển hướng.
- Lịch sử gộp đủ để tách lại; đã kiểm chứng bằng ca thử tách thật, không chỉ bằng việc có trường lưu.
- Mọi phân hệ tiêu thụ đã nhận sự kiện gộp.

**⑨ Sự kiện phát sinh**

- EVT-PATIENT-MERGED
- EVT-PATIENT-UNMERGED
- EVT-MERGE-APPROVED
- EVT-MERGE-INCIDENT

**⑩ Truy vết & nghiệm thu**

- Test: TC-HIS01-BN-13/14/15/16/17
- Nghiệm thu: NT-HIS01-04

## **5.7. Nhóm 090 — Hợp nhất hồ sơ vô danh cấp cứu****FS-HIS01-090-0020 — Hồ sơ tạm và đường hợp nhất về hồ sơ thật**

**① Mô tả & mục đích**

Người bệnh cấp cứu không giấy tờ, không nói được, không ai đi kèm — vẫn phải xử trí ngay. Hồ sơ tạm là cách hệ thống không cản đường. Nhưng hồ sơ tạm chỉ có giá trị nếu có đường rõ ràng để hợp nhất về hồ sơ thật khi biết danh tính, và đường đó phải giữ nguyên toàn bộ dữ liệu cấp cứu.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: điều dưỡng hoặc nhân viên tiếp đón cấp cứu tạo hồ sơ tạm.
- Tác nhân phụ: nhân viên hành chính hợp nhất khi có định danh.
- Tiền điều kiện: —
- Kích hoạt: tiếp nhận cấp cứu không xác định danh tính; hoặc khi có thông tin định danh sau đó.

**③ Logic xử lý**

1\. Tạo hồ sơ tạm với bộ trường bắt buộc RÚT GỌN: định danh quy ước theo quy tắc cấu hình, giới tính ước lượng, tuổi ước lượng, đặc điểm nhận dạng nếu có. KHÔNG đòi CCCD, KHÔNG đòi thẻ BHYT.

2\. Định danh quy ước phải PHÂN BIỆT ĐƯỢC trong ca trực — nếu cùng lúc có nhiều ca vô danh thì phải khác nhau rõ ràng, không để hai người cùng mang một nhãn.

3\. Hồ sơ tạm ở TT01-S01, dùng được ngay cho mọi việc lâm sàng: mở lượt, ra y lệnh, làm xét nghiệm, phẫu thuật. KHÔNG chức năng nào bị chặn vì hồ sơ đang ở trạng thái tạm.

4\. Khi có định danh: tra xem người bệnh đã có hồ sơ thật chưa. Có thì HỢP NHẤT hồ sơ tạm vào hồ sơ thật theo đúng cơ chế gộp ở FS-HIS01-070-0040. Chưa có thì NÂNG CẤP hồ sơ tạm thành hồ sơ đầy đủ, giữ nguyên mã.

5\. Hợp nhất giữ nguyên TOÀN BỘ dữ liệu cấp cứu — đây là phần dữ liệu quan trọng nhất của người bệnh trong giai đoạn đó, không được mất.

6\. Nâng cấp tại chỗ giữ nguyên mã người bệnh: mã đã in trên vòng tay, đã ghi trên mẫu bệnh phẩm, đã gắn vào kết quả. Đổi mã là làm hỏng những thứ đó.

7\. Hồ sơ tạm quá hạn cấu hình mà chưa có định danh: cảnh báo leo thang tới phòng KHTH. KHÔNG tự vô hiệu, vì dữ liệu lâm sàng vẫn có giá trị.

8\. Thống kê hồ sơ tạm chưa hợp nhất theo số ngày quá hạn — nếu con số này tăng dần thì quy trình xác minh danh tính ở khâu tiếp đón đang có vấn đề.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-TMP-LABEL (Định danh quy ước) | Text | ✱   | Theo quy tắc cấu hình; PHÂN BIỆT ĐƯỢC giữa các ca vô danh cùng lúc |
| FLD-TMP-SEX (Giới tính ước lượng) | Enum | ✱   | Sửa được khi có thông tin |
| FLD-TMP-AGE (Tuổi ước lượng) | Number | —   | Khoảng tuổi; ảnh hưởng liều thuốc |
| FLD-TMP-MARKS (Đặc điểm nhận dạng) | Text | —   | Phục vụ nhận diện và xác minh sau |
| FLD-TMP-CREATED (Thời điểm tạo) | DateTime | ✱   | Mốc tính thời gian chưa hợp nhất |
| FLD-TMP-RESOLVE (Cách xử lý khi có định danh) | Enum | —   | HOP_NHAT vào hồ sơ có sẵn / NANG_CAP tại chỗ |
| FLD-TMP-TARGET (Hồ sơ đích khi hợp nhất) | Ref | ✱ khi hợp nhất | Đi theo cơ chế gộp của 070-0040 |

**⑤ Quy tắc nghiệp vụ áp dụng**

- KHÔNG CHỨC NĂNG NÀO BỊ CHẶN VÌ HỒ SƠ TẠM. Đây là quy tắc quan trọng nhất của mục. Chặn ra y lệnh, chặn xét nghiệm hay chặn phẫu thuật vì hồ sơ chưa đủ giấy tờ là đặt thủ tục hành chính lên trên tính mạng — cùng nguyên tắc với HIS-05-070-0060 (cấp cứu hưởng đầy đủ) và BR-VP-02 (tiền không chặn điều trị).
- NÂNG CẤP TẠI CHỖ GIỮ NGUYÊN MÃ. Mã đã in trên vòng tay và trên nhãn bệnh phẩm. Đổi mã ở giữa đợt điều trị là tạo ra hai định danh cho cùng một người trong cùng một đợt.
- HỢP NHẤT ĐI THEO CƠ CHẾ GỘP, không dựng cơ chế riêng. Hồ sơ tạm cũng phải khôi phục được nếu hợp nhất nhầm — và ghép nhầm ca cấp cứu vào hồ sơ người khác là loại nhầm nguy hiểm nhất.
- HỒ SƠ TẠM QUÁ HẠN KHÔNG TỰ VÔ HIỆU. Dữ liệu lâm sàng của giai đoạn cấp cứu vẫn có giá trị dù không bao giờ biết được người bệnh là ai.
- ĐỊNH DANH QUY ƯỚC PHẢI PHÂN BIỆT ĐƯỢC. Hai ca vô danh cùng lúc mang cùng một nhãn là công thức của nhầm người bệnh.

**⑥ Hành vi màn hình**

- Biểu mẫu hồ sơ tạm ngắn, mở được bằng MỘT thao tác từ màn tiếp nhận cấp cứu.
- Hồ sơ tạm hiển thị nhãn rõ trên mọi màn, nhưng nhãn KHÔNG kèm bất kỳ nút chặn nào.
- Màn hợp nhất hiện dữ liệu cấp cứu của hồ sơ tạm ở vị trí nổi bật — đây là thứ tuyệt đối không được mất.
- Danh sách hồ sơ tạm chưa hợp nhất trên MH-BN-02, sắp theo số ngày quá hạn.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-33 | Chặn bất kỳ chức năng lâm sàng nào vì hồ sơ ở TT01-S01 | LỖI THIẾT KẾ |
| ERR-HIS01-34 | Hai hồ sơ tạm cùng lúc mang cùng định danh quy ước | Chặn |
| ERR-HIS01-35 | Nâng cấp hồ sơ tạm mà đổi mã người bệnh | CHẶN |
| ERR-HIS01-36 | Hợp nhất làm mất dữ liệu cấp cứu | LỖI THIẾT KẾ |
| ERR-HIS01-37 | Hồ sơ tạm quá hạn cấu hình chưa có định danh | Cảnh báo leo thang; KHÔNG tự vô hiệu |

**⑧ Hậu điều kiện & đầu ra**

- Người bệnh cấp cứu không giấy tờ được xử trí ngay, không chờ thủ tục.
- Có định danh thì hợp nhất hoặc nâng cấp, giữ nguyên toàn bộ dữ liệu cấp cứu.
- Hồ sơ tạm chưa hợp nhất theo dõi được và không biến mất.

**⑨ Sự kiện phát sinh**

- EVT-TEMP-PATIENT-CREATED
- EVT-TEMP-PATIENT-RESOLVED
- EVT-TEMP-PATIENT-OVERDUE

**⑩ Truy vết & nghiệm thu**

- Test: TC-HIS01-BN-18/19/20
- Nghiệm thu: NT-HIS01-01 · NT-HIS01-04

## **5.8. Nhóm 110 — Nhật ký truy cập hồ sơ****FS-HIS01-110-0010 — Nhật ký thao tác trên hồ sơ & cảnh báo truy cập bất thường**

**① Mô tả & mục đích**

Hồ sơ người bệnh chứa thông tin riêng tư nhất mà bệnh viện giữ. Rò rỉ xảy ra qua việc XEM chứ không qua việc sửa, nên nhật ký phải ghi cả thao tác xem — cùng nguyên tắc đã áp cho tài liệu EMR ở HIS-18.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân chính: hệ thống ghi tự động.
- Tác nhân đọc: VT-23 kiểm toán trên MH-BN-04.
- Tiền điều kiện: —
- Kích hoạt: mọi thao tác trên hồ sơ người bệnh.

**③ Logic xử lý**

1\. Ghi nhật ký: tạo · sửa · XEM · tìm kiếm trả về kết quả · gộp · tách · vô hiệu · xuất dữ liệu.

2\. Mỗi dòng gồm thời điểm, người thực hiện (mã người hành nghề VÀ mã tài khoản), thao tác, hồ sơ, thiết bị, kết quả.

3\. NHẬT KÝ CHỈ GHI THÊM: không sửa, không xóa, không phân quyền nào mở được (BR-007).

4\. CẢNH BÁO TRUY CẬP BẤT THƯỜNG theo dấu hiệu cấu hình: xem hồ sơ không thuộc phạm vi phân công · xem số lượng hồ sơ vượt ngưỡng trong khoảng thời gian · tìm kiếm theo họ tên trả về nhiều kết quả rồi mở lần lượt · xem hồ sơ của người cùng họ hoặc cùng địa chỉ với người xem · xuất dữ liệu hàng loạt.

5\. Cảnh báo gửi tới VT-23 và phòng KHTH; KHÔNG tự khóa tài khoản — chặn nhầm một bác sĩ đang cần xem hồ sơ gây hại hơn là để họ xem rồi rà lại.

6\. Phân quyền theo VAI TRÒ VÀ PHẠM VI (BR-015): phạm vi gắn với phân công đang hiệu lực, không gắn với chức danh.

7\. Báo cáo kiểm toán hai chiều: ai đã xem hồ sơ này, và người này đã xem những hồ sơ nào.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-LOG-TIME | DateTime | ✱   | Từ nguồn thời gian tin cậy |
| FLD-LOG-PRACTITIONER / ACCOUNT | Mã / Ref | ✱   | Ghi CẢ HAI |
| FLD-LOG-ACTION | Enum | ✱   | Bao gồm XEM và TÌM KIẾM |
| FLD-LOG-PATIENT | Ref | ✱   | —   |
| FLD-LOG-DEVICE | Text | ✱   | —   |
| FLD-LOG-RESULT | Enum | ✱   | Thành công / bị từ chối quyền |
| FLD-LOG-ALERT | Group | —   | Dấu hiệu nào kích hoạt cảnh báo |

**⑤ Quy tắc nghiệp vụ áp dụng**

- BR-007 GHI NHẬT KÝ CẢ THAO TÁC XEM. Với hồ sơ người bệnh, rò rỉ xảy ra qua việc xem. Hệ thống chỉ ghi tạo/sửa/xóa là bỏ sót đúng loại sự cố hay xảy ra nhất.
- GHI CẢ THAO TÁC TÌM KIẾM TRẢ VỀ KẾT QUẢ. Tìm theo họ tên một người nổi tiếng rồi không mở hồ sơ nào vẫn là một hành vi đáng ghi nhận.
- NHẬT KÝ CHỈ GHI THÊM, KHÔNG TRỪ QUẢN TRỊ. Nghiệm thu phải rà mã nguồn và rà quyền cơ sở dữ liệu, không thử được bằng giao diện.
- CẢNH BÁO KHÔNG TỰ KHÓA TÀI KHOẢN. Cùng nguyên tắc với HIS-18 và với BR-VP-02.
- PHẠM VI GẮN VỚI PHÂN CÔNG, KHÔNG GẮN CHỨC DANH. Gắn với chức danh thì một bác sĩ xem được hồ sơ mọi khoa suốt đời làm việc.

**⑥ Hành vi màn hình**

- MH-BN-04 tra hai chiều: theo hồ sơ và theo người dùng.
- Danh sách cảnh báo sắp theo mức nghiêm trọng, mỗi dòng nêu rõ dấu hiệu nào kích hoạt.
- Không có nút xóa hay sửa ở bất kỳ đâu trong vùng nhật ký.
- Người dùng xem hồ sơ ngoài phân công thấy thông báo việc này được ghi nhận — minh bạch tốt hơn giám sát ngầm.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-38 | Có chức năng sửa hoặc xóa dòng nhật ký | LỖI THIẾT KẾ |
| ERR-HIS01-39 | Thao tác XEM không được ghi nhật ký | LỖI THIẾT KẾ |
| ERR-HIS01-40 | Hệ thống tự khóa tài khoản khi có cảnh báo | LỖI THIẾT KẾ |
| ERR-HIS01-41 | Xem hồ sơ ngoài phạm vi phân công | Cho xem theo tình huống; sinh cảnh báo |

**⑧ Hậu điều kiện & đầu ra**

- Mọi thao tác trên hồ sơ có trong nhật ký, kể cả xem và tìm kiếm.
- Nhật ký không sửa và không xóa được.
- Cảnh báo truy cập bất thường hoạt động và tới đúng người.

**⑨ Sự kiện phát sinh**

- EVT-PATIENT-VIEWED
- EVT-PATIENT-SEARCHED
- EVT-ABNORMAL-ACCESS-ALERT

**⑩ Truy vết & nghiệm thu**

- Quy tắc: BR-007 · BR-015
- Test: TC-HIS01-BN-21/22
- Nghiệm thu: NT-HIS01-06

## **5.9. Bảng tổng hợp chức năng còn lại**

| **Mã chức năng** | **Nội dung** | **Ghi chú** |
| --- | --- | --- |
| FS-HIS01-010-0010…0040 | Cấu hình quy tắc sinh mã · danh mục hành chính · nhóm đối tượng · trường bắt buộc | Tất cả là cấu hình ở HIS-20, không chôn trong mã nguồn |
| FS-HIS01-030-0030/0040/0050 | Nhiều địa chỉ · nhiều người liên hệ · đính kèm ảnh và giấy tờ số hóa | Đã mô tả trong logic của 030-0010 |
| FS-HIS01-050-0010/0030 | Tiền sử bệnh · văn bản đồng ý | Đã mô tả trong logic của 050-0020 |
| FS-HIS01-060-0010/0020/0030 | Tra cứu theo mã · tìm đa tiêu chí · gợi ý trùng khi tạo | Bộ tiêu chí dùng chung với 070-0010 |
| FS-HIS01-070-0020/0030/0050 | Kiểm lịch sử trước gộp · phê duyệt phân cấp · lịch sử gộp | Đã mô tả trong logic của 070-0040 |
| FS-HIS01-080-0010/0020/0030 | Lịch sử KCB · cây hồ sơ bệnh án · tổng hợp nổi bật cho lần khám | Đọc từ HIS-03/04/05/06 và HIS-18; HIS-01 không lưu bản sao |
| FS-HIS01-090-0010/0030 | Vô hiệu hồ sơ · tách hồ sơ bị gộp nhầm | Tách lại đã mô tả tại 070-0040 |
| FS-HIS01-100-0010/0020/0030 | Tích hợp VNeID · dữ liệu dân cư · tra thẻ BHYT | Qua HIS-22; xem chương 10 |
| FS-HIS01-110-0020/0030 | Phân quyền theo vai trò và phạm vi · cảnh báo bất thường | Đã mô tả trong logic của 110-0010 |

# **CHƯƠNG 6. ĐẶC TẢ MÀN HÌNH**

## **6.1. MH-BN-03 — Gộp hồ sơ**

| **Vùng** | **Nội dung** | **Thao tác** |
| --- | --- | --- |
| 1\. Hàng đợi nghi trùng | Sắp theo mức tin cậy rồi số lượt khám; mỗi dòng nêu TRƯỜNG NÀO KHỚP | Chọn cặp |
| 2\. So sánh song song | Hai hồ sơ hai cột; trường khớp tô sáng, trường lệch tô khác màu | Cuộn đồng bộ |
| 3\. Chọn hồ sơ gốc | Mặc định hồ sơ nhiều lượt hơn; đổi được kèm lý do | Chọn |
| 4\. Chọn giá trị từng trường lệch | Không để hệ thống tự quyết im lặng | Chọn từng trường |
| 5\. Bảng tóm tắt ảnh hưởng | Bao nhiêu lượt, bệnh án, dòng chi phí sẽ đổi tham chiếu | Chỉ đọc |
| 6\. Trình duyệt & duyệt | Nút duyệt KHÔNG hiện với người đã lập đề nghị | Trình / duyệt |
| 7\. Lịch sử gộp | Các lần gộp đã thực hiện, có nút tách lại kèm cảnh báo | Xem / tách lại |

_Ràng buộc thiết kế: VÙNG 5 LÀ THỨ NGĂN PHẦN LỚN LỖI GỘP NHẦM. Người duyệt nhìn thấy con số cụ thể — ví dụ hồ sơ này có 47 lượt khám và 12 bệnh án nội trú — sẽ dừng lại kiểm kỹ hơn nhiều so với khi chỉ thấy hai cái tên giống nhau. Con số làm cho hậu quả trở nên cụ thể._

## **6.2. Các màn còn lại**

| **Màn** | **Vùng chính** | **Đặc điểm đáng lưu ý** |
| --- | --- | --- |
| MH-BN-01 | Hồ sơ 360 độ: hành chính, giấy tờ, thẻ BHYT, dị ứng, tiền sử, lịch sử KCB | Dải cảnh báo dị ứng ở VỊ TRÍ CỐ ĐỊNH đầu màn; thẻ BHYT dạng dòng thời gian |
| MH-BN-02 | Tra cứu đa tiêu chí; danh sách kèm nghi trùng | Có bộ lọc hồ sơ tạm chưa hợp nhất, sắp theo số ngày quá hạn |
| MH-BN-04 | Nhật ký truy cập, tra hai chiều | Không có nút xóa hay sửa ở bất kỳ đâu |
| MH-BN-05 | Cấu hình: quy tắc sinh mã, trường bắt buộc, bộ tiêu chí khớp | Bộ tiêu chí khớp là cấu hình, đổi không cần phát hành lại phần mềm |

# **CHƯƠNG 7. MÁY TRẠNG THÁI HỒ SƠ NGƯỜI BỆNH**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp được** |
| --- | --- | --- | --- |
| TT01-S01 | Tạm (chưa xác minh) | Hồ sơ vô danh hoặc tối thiểu, ví dụ cấp cứu | S02, S04 |
| TT01-S02 | Hoạt động | Hồ sơ đầy đủ, đang sử dụng | S03, S04, S05 |
| TT01-S03 | Nghi trùng | Đã gắn cờ nghi trùng, chờ xử lý | S02, S04 |
| **TT01-S04** | **Đã gộp (retired)** | **Đã gộp vào hồ sơ gốc; GIỮ mã cũ và giữ liên kết truy vết** | **S02 (tách lại)** |
| TT01-S05 | Vô hiệu | Ngừng sử dụng theo quy định | —   |

_Cách đọc bảng trạng thái: BA ĐIỀU PHẢI ĐỌC KỸ. Thứ nhất, TT01-S01 KHÔNG chặn chức năng lâm sàng nào — nó chỉ là nhãn cho biết hồ sơ chưa xác minh danh tính. Thứ hai, TT01-S04 có đường quay lại S02: đây là hình thức kỹ thuật của yêu cầu GỘP PHẢI KHÔI PHỤC ĐƯỢC, và nếu đường này không tồn tại thì mọi thứ khác trong mục 5.6 là vô nghĩa. Thứ ba, mã người bệnh của hồ sơ ở S04 KHÔNG được tái sử dụng và KHÔNG bị xóa — nó có thể đang nằm trong giấy tờ đã in, trong hồ sơ quyết toán đã gửi, hoặc trong hệ thống của đối tác._

# **CHƯƠNG 8. QUY TẮC NGHIỆP VỤ**

| **Quy tắc** | **Nội dung** | **Áp dụng tại** |
| --- | --- | --- |
| BR-001 | Mã người bệnh duy nhất, không tái sử dụng | FS-HIS01-020-0010 |
| BR-004 | Kế thừa dữ liệu — không nhập lại thông tin đã có | Toàn phân hệ; HIS-03 gọi HIS-01 chứ không nhập lại |
| BR-007 | Ghi nhật ký truy cập, kể cả thao tác XEM | FS-HIS01-110-0010 |
| BR-011 | HIS-10 là nguồn quy tắc an toàn thuốc duy nhất | FS-HIS01-050-0020 — HIS-01 cấp dữ liệu dị ứng, không dựng quy tắc |
| BR-015 | Phân quyền theo vai trò và phạm vi | FS-HIS01-110-0010 |

## **8.1. Ba chốt chặn cứng của phân hệ, và vì sao chỉ ba**

| **Chặn** | **Ở đâu** | **Vì sao chặn là đúng** |
| --- | --- | --- |
| **Trùng CCCD khi tạo mới** | **FS-HIS01-020-0010** | **Trùng CCCD gần như chắc chắn là cùng một người. Cho tạo là tự tay sinh ra hồ sơ trùng** |
| **Gộp không lập được bản chụp** | **FS-HIS01-070-0040** | **Không có bản chụp thì không tách lại được, và gộp nhầm thành vĩnh viễn** |
| **Người duyệt trùng người thực hiện** | **FS-HIS01-070-0040** | **Thao tác có hậu quả lâm sàng không đảo ngược cần hai cặp mắt — cùng nguyên tắc đếm gạc hai người của HIS-09** |

_Chặn cái gì và đánh đổi với cái gì: MỌI THỨ CÒN LẠI ĐỀU KHÔNG CHẶN, VÀ ĐÓ LÀ CHỦ Ý. Thiếu CCCD không chặn · thiếu thẻ BHYT không chặn · cổng BHXH chết không chặn · VNeID không phản hồi không chặn · hồ sơ đang ở trạng thái tạm không chặn bất kỳ chức năng lâm sàng nào. Lý do giống hệt các phân hệ khác: những thứ đó là bản ghi hành chính, sửa được sau; còn chặn thì rơi vào người bệnh đang đứng trước quầy hoặc đang nằm trên cáng. Ba chốt ở trên khác về bản chất — chúng ngăn dữ liệu của hai người trộn vào nhau, và cái đó thì không sửa được sau một cách an toàn._

# **CHƯƠNG 9. QUY TẮC KIỂM TRA DỮ LIỆU**

| **Mã** | **Quy tắc kiểm tra** | **Mức** |
| --- | --- | --- |
| VLD-HIS01-01 | Mã người bệnh duy nhất toàn hệ thống và không tái sử dụng | Chặn ở tầng thiết kế |
| VLD-HIS01-02 | Một số CCCD chỉ gắn với một hồ sơ ĐANG HOẠT ĐỘNG | Chặn |
| VLD-HIS01-03 | Quy tắc sinh mã không nhúng thông tin đổi được | Cảnh báo khi cấu hình |
| VLD-HIS01-04 | KHÔNG chặn tạo hồ sơ vì thiếu CCCD hoặc thiếu thẻ BHYT | Chặn ở tầng thiết kế |
| VLD-HIS01-05 | Xác minh lệch thì cảnh báo, không tự ghi đè dữ liệu | Chặn ở tầng thiết kế |
| VLD-HIS01-06 | Gợi ý nghi trùng chạy TRƯỚC khi lưu hồ sơ mới | Chặn ở tầng thiết kế |
| VLD-HIS01-07 | Tạo mới dù có nghi trùng phải ghi lý do và người xác nhận | Chặn |
| VLD-HIS01-08 | Hai thẻ BHYT của cùng người không chồng lấn khoảng hiệu lực | Chặn |
| VLD-HIS01-09 | Tra thẻ BHYT theo NGÀY KHÁM, không theo ngày tra | Chặn ở tầng thiết kế |
| VLD-HIS01-10 | Thẻ cũ không bị ghi đè khi có thẻ mới | Chặn |
| VLD-HIS01-11 | Dị ứng thuốc ghi theo HOẠT CHẤT, không theo tên thương mại | Chặn |
| VLD-HIS01-12 | Mức chắc chắn của dị ứng là trường bắt buộc | Chặn |
| VLD-HIS01-13 | Bản ghi dị ứng không xóa vĩnh viễn được; gỡ phải có lý do và lịch sử | Chặn |
| VLD-HIS01-14 | Gộp phải lập được bản chụp toàn vẹn và danh sách bản ghi đã chuyển | Chặn |
| VLD-HIS01-15 | Người duyệt gộp khác người thực hiện gộp | Chặn |
| VLD-HIS01-16 | Hồ sơ nguồn không bị xóa; chuyển TT01-S04 giữ mã và giữ liên kết | Chặn |
| VLD-HIS01-17 | Không khử trùng lặp bản ghi dị ứng và tiền sử khi gộp | Chặn ở tầng thiết kế |
| VLD-HIS01-18 | Không gộp hai hồ sơ có CCCD khác nhau và cả hai đã xác minh | Chặn |
| VLD-HIS01-19 | Tách lại phải ghi lý do và đánh giá ảnh hưởng lâm sàng | Chặn |
| VLD-HIS01-20 | Hồ sơ ở TT01-S01 KHÔNG chặn bất kỳ chức năng lâm sàng nào | Chặn ở tầng thiết kế |
| VLD-HIS01-21 | Nâng cấp hồ sơ tạm giữ nguyên mã người bệnh | Chặn |
| VLD-HIS01-22 | Định danh quy ước của hai hồ sơ tạm cùng lúc phải phân biệt được | Chặn |
| VLD-HIS01-23 | So khớp nghi trùng phải chuẩn hóa trước khi so | Chặn ở tầng thiết kế |
| VLD-HIS01-24 | Nhật ký ghi cả thao tác XEM và TÌM KIẾM trả về kết quả | Chặn ở tầng thiết kế |
| VLD-HIS01-25 | Nhật ký không có chức năng sửa hoặc xóa ở bất kỳ phân quyền nào | Chặn ở tầng thiết kế |
| VLD-HIS01-26 | Cảnh báo truy cập bất thường KHÔNG tự khóa tài khoản | Chặn ở tầng thiết kế |

# **CHƯƠNG 10. TÍCH HỢP & SỰ KIỆN**

## **10.1. Hợp đồng dữ liệu**

| **Chiều** | **Nội dung** | **Dữ liệu** | **Ghi chú** |
| --- | --- | --- | --- |
| HIS-03 → HIS-01 | Tìm hoặc tạo hồ sơ khi tiếp nhận | Tiêu chí tìm; dữ liệu tạo mới | HIS-03 gọi HIS-01, không tự tạo hồ sơ |
| HIS-01 → HIS-03 | Mã người bệnh, thẻ BHYT có hiệu lực tại ngày khám | Mã, thẻ, nhóm đối tượng, nơi ĐKBĐ | HIS-03 tính căn cứ hưởng và mức hưởng, HIS-01 KHÔNG tính |
| HIS-01 → HIS-04/05/06/07/09 | Hồ sơ, tiền sử, DỊ ỨNG | Bản ghi dị ứng kèm hoạt chất, mức độ, MỨC CHẮC CHẮN | Hiển thị nổi bật trên mọi màn lâm sàng |
| **HIS-01 → HIS-10** | **Dữ liệu dị ứng để dựng quy tắc an toàn thuốc** | **Hoạt chất, mức độ, mức chắc chắn, nguồn** | **BR-011 — HIS-10 dựng quy tắc, HIS-01 KHÔNG tự cảnh báo** |
| HIS-01 → HIS-21 | Tiền sử và dị ứng làm đầu vào CDSS | Bản ghi tiền sử và dị ứng | HIS-21 tiêu thụ, không sửa |
| HIS-01 → HIS-16/17 | Thông tin người bệnh và thẻ BHYT phục vụ viện phí, quyết toán | Mã, họ tên, thẻ có hiệu lực tại ngày khám | —   |
| HIS-01 → HIS-18 | Định danh gắn vào bệnh án điện tử | Mã người bệnh, họ tên | —   |
| **HIS-01 → TẤT CẢ** | **Sự kiện GỘP hồ sơ** | **Mã gốc, mã nguồn, thời điểm, danh sách bản ghi đổi tham chiếu** | **Mọi phân hệ lưu mã người bệnh PHẢI xử lý được sự kiện này** |
| HIS-01 ⇄ HIS-22 | VNeID, dữ liệu dân cư, cổng BHXH | Yêu cầu xác minh; phản hồi nguyên văn | HIS-22 lo hạ tầng |
| HIS-20 → HIS-01 | Danh mục hành chính, nhóm đối tượng, quy tắc sinh mã, bộ tiêu chí khớp, trường bắt buộc | Cấu hình | Tất cả là cấu hình |

_Việc cần xác nhận thêm: MỘT VẤN ĐỀ LIÊN PHÂN HỆ CẦN CHỦ ĐẦU TƯ BIẾT. Khi gộp hai hồ sơ mà một trong hai đã có hồ sơ quyết toán ĐÃ GỬI cơ quan BHXH, mã người bệnh trên bản đã gửi không đổi được — vì bản đã gửi là BẤT BIẾN theo quy tắc BR-BH-06 của HIS-17. Hệ quả: hồ sơ quyết toán cũ mang mã cũ, hồ sơ mới mang mã gốc, và khi đối soát kỳ sẽ thấy hai mã cho cùng một người. Cách xử lý trong thiết kế hiện tại: giữ liên kết ở TT01-S04 để tra mã cũ vẫn ra hồ sơ gốc, và ghi rõ trong hồ sơ đối soát. Nếu cơ quan BHXH có yêu cầu khác thì cần biết sớm — đây là câu hỏi nên bổ sung vào phiếu thu thập._

## **10.2. Sự kiện phát ra**

| **Sự kiện** | **Khi nào** | **Ai tiêu thụ** |
| --- | --- | --- |
| EVT-PATIENT-CREATED | Tạo hồ sơ mới | HIS-03, HIS-22 |
| EVT-PATIENT-UPDATED | Sửa trường định danh | Mọi phân hệ hiển thị tên người bệnh |
| EVT-DUPLICATE-SUSPECTED | Phát hiện cặp nghi trùng | MH-BN-03, hàng đợi rà |
| **EVT-PATIENT-MERGED** | **Gộp hồ sơ** | **MỌI phân hệ lưu mã người bệnh** |
| **EVT-PATIENT-UNMERGED** | **Tách lại khi gộp nhầm** | **MỌI phân hệ; kèm ghi nhận sự cố** |
| EVT-ALLERGY-RECORDED | Ghi nhận dị ứng | HIS-10, HIS-21, màn lâm sàng |
| EVT-BHYT-CARD-ADDED | Thêm thẻ BHYT | HIS-03, HIS-16, HIS-17 |
| EVT-TEMP-PATIENT-CREATED | Tạo hồ sơ tạm cấp cứu | HIS-05, hàng đợi hợp nhất |
| EVT-TEMP-PATIENT-RESOLVED | Hợp nhất hoặc nâng cấp hồ sơ tạm | HIS-05, HIS-03 |
| EVT-ABNORMAL-ACCESS-ALERT | Truy cập bất thường | VT-23, phòng KHTH |

# **CHƯƠNG 11. DANH MỤC THÔNG BÁO & MÃ LỖI**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-HIS01-01…06 | Định danh: trùng CCCD, tái sử dụng mã, mã nhúng thông tin đổi được, xác minh lệch, dịch vụ không phản hồi, chặn vì thiếu giấy tờ | Chặn 01; lỗi thiết kế 02 và 06; cảnh báo 03/04/05 |
| ERR-HIS01-07…11 | Tạo hồ sơ: trùng CCCD, nghi trùng không lý do, thiếu trường bắt buộc, ngày sinh vô lý, mất lịch sử giá trị cũ | Chặn (trừ 11 là lỗi thiết kế) |
| ERR-HIS01-12…16 | Thẻ BHYT: chồng lấn hiệu lực, ghi đè thẻ cũ, cổng không phản hồi, thẻ không hợp lệ, chặn tiếp nhận vì chưa xác minh | Chặn 12/13; cảnh báo 14/15; lỗi thiết kế 16 |
| ERR-HIS01-17…22 | Dị ứng: ghi theo tên thương mại, thiếu mức chắc chắn, gỡ không lý do, xóa vĩnh viễn, màn không hiện cảnh báo, HIS-01 tự dựng quy tắc | Chặn (trừ 21 và 22 là lỗi thiết kế) |
| ERR-HIS01-23…25 | Phát hiện trùng: so chuỗi thô, loại trừ không lý do, tiêu chí chôn cứng | Chặn 24; lỗi thiết kế 23 và 25 |
| **ERR-HIS01-26…32** | **Gộp hồ sơ: không lập được bản chụp, người duyệt trùng người thực hiện, xóa hồ sơ nguồn, khử trùng dị ứng, gộp hai CCCD khác nhau đã xác minh, tách không lý do, phân hệ không xử lý được sự kiện gộp** | **CHẶN (trừ 29 lỗi thiết kế, 32 lỗi tích hợp)** |
| ERR-HIS01-33…37 | Hồ sơ tạm: chặn chức năng lâm sàng, trùng định danh quy ước, đổi mã khi nâng cấp, mất dữ liệu cấp cứu, quá hạn hợp nhất | Chặn 34/35; lỗi thiết kế 33/36; cảnh báo 37 |
| ERR-HIS01-38…41 | Nhật ký: có chức năng sửa hoặc xóa, không ghi thao tác xem, tự khóa tài khoản, xem ngoài phân công | Lỗi thiết kế 38/39/40; cảnh báo 41 |

_Cách đọc nhóm lỗi thiết kế: MƯỜI MÃ ĐƯỢC ĐÁNH LÀ LỖI THIẾT KẾ chứ không phải lỗi vận hành: 02, 06, 11, 16, 21, 22, 23, 25, 29, 33, 36, 38, 39, 40. Chúng mô tả những thứ KHÔNG ĐƯỢC PHÉP TỒN TẠI trong hệ thống. Nghiệm thu nhóm này phải rà mã nguồn và rà phân quyền cơ sở dữ liệu, không thử được bằng giao diện — cùng cách nghiệm thu đã áp cho HIS-09 và HIS-18._

# **CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (ĐO ĐƯỢC)**

| **Nhóm** | **Yêu cầu** | **Cách nghiệm thu** |
| --- | --- | --- |
| Tốc độ | Tra cứu theo mã hoặc CCCD phản hồi dưới 1 giây | Đo trên khối lượng dữ liệu thật |
| Tốc độ | Gợi ý nghi trùng khi tạo hồ sơ phản hồi dưới 2 giây | Đo tại quầy tiếp đón giờ cao điểm |
| Tốc độ | Tạo hồ sơ tạm cấp cứu hoàn tất dưới 30 giây kể cả thao tác nhập | Đo bằng người dùng thật tại phòng cấp cứu |
| Chịu tải | Quét nghi trùng toàn bộ dữ liệu chạy trong khung giờ thấp điểm, không ảnh hưởng nghiệp vụ | Chạy thử trên khối lượng thật |
| Toàn vẹn | Không tồn tại chức năng xóa hồ sơ, xóa bản ghi dị ứng, hay sửa nhật ký ở bất kỳ phân quyền nào | RÀ MÃ NGUỒN và rà quyền cơ sở dữ liệu |
| **Khôi phục** | **Tách lại hồ sơ đã gộp trả về đúng trạng thái trước gộp, kiểm chứng bằng ca thử tách THẬT** | **Không nghiệm thu bằng việc có trường lưu bản chụp; phải tách thật rồi đối chiếu** |
| Lưu trữ | Định cỡ đủ cho nhật ký ghi cả thao tác xem và tìm kiếm | Ước lượng từ số lượt truy cập tháng đầu |

# **CHƯƠNG 13. MA TRẬN TRUY VẾT & NGHIỆM THU**

## **13.1. Truy vết chức năng — kiểm thử**

| **Chức năng đặc tả** | **Nội dung** | **Ca kiểm thử** |
| --- | --- | --- |
| FS-HIS01-020-0010 | Sinh mã & giấy tờ tùy thân | TC-HIS01-BN-01/02/03 |
| FS-HIS01-030-0010 | Tạo hồ sơ & gợi ý trùng | TC-HIS01-BN-04/05/06 |
| FS-HIS01-040-0010 | Thẻ BHYT theo thời hạn | TC-HIS01-BN-07/08 |
| FS-HIS01-050-0020 | Dị ứng & đường tới màn lâm sàng | TC-HIS01-BN-09/10 |
| FS-HIS01-070-0010 | Phát hiện nghi trùng | TC-HIS01-BN-11/12 |
| FS-HIS01-070-0040 | GỘP & tách lại | TC-HIS01-BN-13/14/15/16/17 |
| FS-HIS01-090-0020 | Hồ sơ tạm & hợp nhất | TC-HIS01-BN-18/19/20 |
| FS-HIS01-110-0010 | Nhật ký truy cập | TC-HIS01-BN-21/22 |

## **13.2. Bộ ca kiểm thử**

| **Mã** | **Tình huống** | **Kết quả mong đợi** | **Chức năng** |
| --- | --- | --- | --- |
| TC-HIS01-BN-01 | Tạo hồ sơ với CCCD đã tồn tại ở hồ sơ đang hoạt động | CHẶN; mở hồ sơ đã có để đối chiếu | 020-0010 |
| TC-HIS01-BN-02 | Người bệnh đổi CCCD cấp lại | Không tạo hồ sơ mới; thêm giấy tờ mới, giấy cũ chuyển ĐÃ THAY THẾ | 020-0010 |
| TC-HIS01-BN-03 | VNeID trả họ tên khác với dữ liệu đang có | Cảnh báo, hiện hai giá trị song song; KHÔNG tự ghi đè | 020-0010 |
| TC-HIS01-BN-04 | Nhập họ tên và ngày sinh trùng một hồ sơ đã có | Hiện nghi trùng TRƯỚC khi lưu, nêu rõ trường nào khớp | 030-0010 |
| TC-HIS01-BN-05 | Xác nhận tạo mới dù có nghi trùng, không ghi lý do | Chặn (ERR-HIS01-08) | 030-0010 |
| TC-HIS01-BN-06 | Tạo hồ sơ tại phòng cấp cứu, không có giấy tờ | Tạo được ở TT01-S01 với bộ trường rút gọn; không chặn gì | 030-0010 |
| TC-HIS01-BN-07 | Người bệnh có thẻ cũ hết hạn 30/06 và thẻ mới từ 01/07; khám ngày 15/06 | Tra ra THẺ CŨ, không phải thẻ mới nhất | 040-0010 |
| TC-HIS01-BN-08 | Cổng BHXH không phản hồi khi tiếp nhận | Vẫn tiếp nhận; thẻ đánh dấu chưa xác minh; vào hàng đợi tra lại | 040-0010 |
| TC-HIS01-BN-09 | Ghi dị ứng bằng tên biệt dược | Chặn; bắt chọn hoạt chất từ danh mục | 050-0020 |
| TC-HIS01-BN-10 | Ghi dị ứng phản vệ với một hoạt chất, sau đó mở màn kê đơn | Dải cảnh báo hiện nổi bật; HIS-10 nhận được dữ liệu và dựng quy tắc | 050-0020 |
| TC-HIS01-BN-11 | Hai hồ sơ trùng họ tên, cùng năm sinh nhưng chỉ biết năm | Xếp mức TRUNG BÌNH, không phải CAO — mức chính xác ngày sinh tham gia tính điểm | 070-0010 |
| TC-HIS01-BN-12 | Loại trừ một cặp nghi trùng, chạy quét lại | Cặp không hiện lại; vẫn xem được trong danh sách loại trừ | 070-0010 |
| **TC-HIS01-BN-13** | **Gộp hai hồ sơ, một hồ sơ có 47 lượt khám và 12 bệnh án** | **Bảng tóm tắt ảnh hưởng hiện đúng con số TRƯỚC khi duyệt; sau gộp không bản ghi nào mất** | **070-0040** |
| TC-HIS01-BN-14 | Người lập đề nghị gộp tự bấm duyệt | Chặn; nút duyệt không hiện với chính người đó | 070-0040 |
| TC-HIS01-BN-15 | Hai hồ sơ đều có bản ghi dị ứng cùng hoạt chất, khác mức chắc chắn | Giữ CẢ HAI bản ghi, không khử trùng lặp | 070-0040 |
| **TC-HIS01-BN-16** | **Phát hiện gộp nhầm sau 3 tháng, thực hiện TÁCH LẠI** | **Hai hồ sơ trở về đúng trạng thái trước gộp; từng bản ghi lâm sàng về đúng chỗ; ghi nhận SỰ CỐ kèm đánh giá ảnh hưởng** | **070-0040** |
| TC-HIS01-BN-17 | Tra mã người bệnh của hồ sơ đã ở TT01-S04 | Vẫn ra kết quả; tự chuyển hướng tới hồ sơ gốc; hiện nhãn ĐÃ GỘP | 070-0040 |
| TC-HIS01-BN-18 | Hai ca cấp cứu vô danh cùng lúc | Hai định danh quy ước KHÁC NHAU, phân biệt được rõ ràng | 090-0020 |
| TC-HIS01-BN-19 | Hồ sơ tạm đã có bệnh án và kết quả xét nghiệm, nay biết danh tính và người bệnh đã có hồ sơ cũ | Hợp nhất giữ NGUYÊN toàn bộ dữ liệu cấp cứu; đi theo cơ chế gộp nên tách lại được | 090-0020 |
| TC-HIS01-BN-20 | Hồ sơ tạm biết danh tính nhưng chưa có hồ sơ cũ | NÂNG CẤP tại chỗ, GIỮ NGUYÊN mã người bệnh đã in trên vòng tay | 090-0020 |
| TC-HIS01-BN-21 | Nhân viên tìm kiếm theo họ tên rồi mở lần lượt 15 hồ sơ | Ghi nhật ký cả thao tác tìm kiếm và từng lần xem; sinh cảnh báo bất thường; KHÔNG tự khóa tài khoản | 110-0010 |
| TC-HIS01-BN-22 | Quản trị cố xóa một dòng nhật ký | Không tồn tại chức năng; kiểm chứng bằng rà quyền cơ sở dữ liệu | 110-0010 |

## **13.3. Tiêu chí nghiệm thu**

Sáu tiêu chí dưới đây LẤY NGUYÊN VĂN từ chương 9.1 của BRD HIS-01 v1.1. FSD không đặt tiêu chí riêng.

| **Mã** | **Tiêu chí (nguyên văn BRD)** | **Đặc tả tại** |
| --- | --- | --- |
| NT-HIS01-01 | Sinh mã BN duy nhất; chặn tạo trùng CCCD. | 020-0010 · 090-0020 |
| NT-HIS01-02 | Kiểm tra thẻ BHYT trực tuyến và lưu kết quả. | 040-0010 |
| NT-HIS01-03 | Tìm kiếm & gợi ý trùng chính xác; giảm tạo trùng. | 030-0010 · 070-0010 |
| NT-HIS01-04 | Gộp hồ sơ không mất dữ liệu; có lịch sử & khôi phục được. | 070-0040 · 090-0020 |
| NT-HIS01-05 | Cảnh báo dị ứng hiển thị ở màn hình lâm sàng. | 050-0020 |
| NT-HIS01-06 | Nhật ký truy cập hồ sơ đầy đủ, không sửa được. | 110-0010 |

_Lưu ý nghiệm thu: NT-HIS01-04 CÓ HAI VẾ, VÀ VẾ THỨ HAI DỄ BỊ NGHIỆM THU HÌNH THỨC. Chứng minh gộp không mất dữ liệu thì dễ — đếm bản ghi trước và sau. Chứng minh KHÔI PHỤC ĐƯỢC thì phải TÁCH THẬT một ca đã gộp rồi đối chiếu từng bản ghi, không nghiệm thu bằng việc hệ thống có trường lưu bản chụp. Đây là điểm cần ghi rõ trong biên bản nghiệm thu._

# **PHỤ LỤC. VIỆC CẦN XÁC NHẬN VỚI BỆNH VIỆN**

Năm mục dưới đây phát sinh khi đặc tả tài liệu này. Đề nghị bổ sung vào phiếu thu thập thông tin gộp ngày 20/08/2026 thành nhóm H.

| **Mã đề nghị** | **Nội dung** | **Giả định đang dùng** |
| --- | --- | --- |
| H1  | Quy tắc sinh mã người bệnh hiện hành của bệnh viện | Chuỗi tuần tự không mang thông tin; nếu đang dùng mã có nhúng năm hoặc khoa thì phải bàn phương án chuyển đổi |
| H2  | Quy tắc đặt định danh quy ước cho ca cấp cứu vô danh | Theo mẫu VD-&lt;ngày&gt;-&lt;số thứ tự trong ngày&gt;; phải phân biệt được nhiều ca cùng lúc |
| H3  | Phân cấp duyệt gộp hồ sơ: ai được duyệt | Trưởng phòng KHTH hoặc người được ủy quyền; người duyệt khác người thực hiện |
| H4  | Ngưỡng thời gian hồ sơ tạm chưa hợp nhất thì cảnh báo | 7 ngày nhắc, 30 ngày leo thang phòng KHTH |
| H5  | Khi gộp hồ sơ mà một bên đã có quyết toán ĐÃ GỬI: cơ quan BHXH yêu cầu xử lý thế nào | Giữ mã cũ trên bản đã gửi, ghi rõ liên kết trong hồ sơ đối soát. Cần xác nhận với cơ quan BHXH |

_Đề nghị hỏi sớm: H5 LÀ MỤC ĐÁNG HỎI SỚM. Nó nằm ở chỗ giao giữa hai quy tắc bất biến của hai phân hệ: hồ sơ quyết toán đã gửi là bất biến (BR-BH-06 của HIS-17), và mã người bệnh của hồ sơ đã gộp không được xóa (mục 5.6 của tài liệu này). Cả hai đều đúng, nhưng khi gặp nhau thì cần biết cơ quan BHXH chấp nhận cách xử lý nào._

# **KẾT LUẬN**

FSD HIS-01 đặc tả cấp trường tám chức năng của nền định danh người bệnh. Trọng tâm là mục 5.6 — gộp hồ sơ trùng, thao tác duy nhất trong phân hệ có thể gây hại trực tiếp cho người bệnh.

Ba yêu cầu của việc gộp phải cùng đạt: không mất dữ liệu · báo được cho mọi phân hệ đang dùng mã cũ · và KHÔI PHỤC ĐƯỢC. Thiếu yêu cầu thứ ba thì hai yêu cầu đầu cũng mất giá trị, vì một lần gộp nhầm sẽ thành vĩnh viễn — và trong khoảng thời gian bị gộp nhầm, bác sĩ điều trị theo bệnh sử và dị ứng của người khác mà không có dấu hiệu nào cho thấy dữ liệu sai.

Điểm thứ hai đáng giữ khi bảo trì tài liệu: phân hệ này chỉ có BA chốt chặn cứng, và cả ba đều nhằm ngăn dữ liệu của hai người trộn vào nhau. Mọi thứ còn lại — thiếu CCCD, thiếu thẻ BHYT, cổng BHXH chết, hồ sơ còn ở trạng thái tạm — đều KHÔNG chặn, vì đó là bản ghi hành chính sửa được sau, còn người bệnh thì đang đứng trước quầy hoặc đang nằm trên cáng.