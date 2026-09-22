# TÀI LIỆU ĐẶC TẢ CHỨC NĂNG (FSD)

## HỆ THỐNG QUẢN LÝ SINH VIÊN

_Tự động hóa - Real-time - Minh bạch_

### Thuộc tính

| Thuộc tính | Nội dung |
| --- | --- |
| Mã phân hệ | QLSV (Gồm QLSV-01 đến QLSV-06) |
| Tên phân hệ | Hệ thống Quản lý Sinh viên |
| Loại tài liệu | FSD — Đặc tả chức năng |
| Phạm vi | Đặc tả field-level các nhóm chức năng cốt lõi: Hồ sơ, Điểm danh QR động, Quản lý Điểm & Khảo thí, Thanh toán |
| Thực thể sở hữu | TT-01 Hồ sơ sinh viên, TT-07/08 Điểm danh, TT-09 Bảng điểm, TT-10 Đơn từ |
| Tài liệu nguồn | Tài liệu Yêu cầu Nghiệp vụ (BRD-QLSV-v3.1) |
| Phiên bản | 1.0 (Dự thảo) |

## MỤC LỤC

1.  [CHƯƠNG 1. GIỚI THIỆU](#chương-1-giới-thiệu)
2.  [CHƯƠNG 2. QUY ƯỚC, KÝ HIỆU & MÃ ĐỊNH DANH](#chương-2-quy-ước-ký-hiệu--mã-định-danh)
3.  [CHƯƠNG 3. TỔNG QUAN CHỨC NĂNG & MÀN HÌNH](#chương-3-tổng-quan-chức-năng--màn-hình)
4.  [CHƯƠNG 4. ĐẶC TẢ LUỒNG NGHIỆP VỤ](#chương-4-đặc-tả-luồng-nghiệp-vụ)
5.  [CHƯƠNG 5. ĐẶC TẢ CHI TIẾT CHỨC NĂNG](#chương-5-đặc-tả-chi-tiết-chức-năng)
6.  [CHƯƠNG 6. ĐẶC TẢ MÀN HÌNH CHÍNH](#chương-6-đặc-tả-màn-hình-chính)
7.  [CHƯƠNG 7. MÁY TRẠNG THÁI HỒ SƠ](#chương-7-máy-trạng-thái-hồ-sơ)
8.  [CHƯƠNG 8. QUY TẮC NGHIỆP VỤ & CHỐT CHẶN CỨNG](#X8748706814a802b9a6f8ddc6de3fd06fe41dfa3)
9.  [CHƯƠNG 9. QUY TẮC KIỂM TRA DỮ LIỆU (VALIDATION)](#Xfda6019664bce8448f68e25afb295445b62edd1)
10. [CHƯƠNG 10. TÍCH HỢP & SỰ KIỆN](#chương-10-tích-hợp--sự-kiện)
11. [CHƯƠNG 11. DANH MỤC THÔNG BÁO LỖI (ERRORS)](#chương-11-danh-mục-thông-báo-lỗi-errors)
12. [CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR ĐO ĐƯỢC)](#X899a6d99a625da90f912b8e1fa83a470f44603f)
13. [CHƯƠNG 13. MA TRẬN TRUY VẾT & NGHIỆM THU](#chương-13-ma-trận-truy-vết--nghiệm-thu)

## CHƯƠNG 1. GIỚI THIỆU

### 1.1. Mục đích tài liệu

Dựa trên BRD-QLSV-v3.1, tài liệu FSD này đặc tả chi tiết cách hệ thống thực hiện các nghiệp vụ: quản lý hồ sơ sinh viên xuyên suốt, điểm danh bằng QR Động (real-time), tự động xét điều kiện điểm số, và tích hợp thanh toán. Tài liệu hướng dẫn đội ngũ phát triển xây dựng các chốt chặn (validation) và thuật toán để đảm bảo quy chế đào tạo được áp dụng khắt khe và chính xác.

### 1.2. Ba nguyên tắc chi phối cả tài liệu

| Nguyên tắc | Nghĩa cụ thể | Vì sao |
| --- | --- | --- |
| **Tự động hóa & Khách quan** | Điểm danh tự động qua QR; hệ thống tự tính điểm tổng kết và xét Đạt/Trượt/Cấm thi. | Tránh sai sót thủ công và đảm bảo sự công bằng, minh bạch tối đa trong đào tạo. |
| **Real-time & Đồng bộ** | Thay đổi trạng thái học tập lập tức chặn đăng nhập và gỡ khỏi lớp; QR điểm danh làm mới 10s/lần. | Sinh viên bảo lưu/thôi học không được phép tiếp tục truy cập dữ liệu; QR động chống gian lận điểm danh hộ. |
| **Truy vết toàn diện (Audit Trail)** | Mọi sửa đổi điểm sau chốt, sửa điểm danh thủ công, duyệt đơn từ đều được ghi Log (Who, When, Old/New). | Quyết định liên quan đến điểm số, tài chính và bằng cấp không được phép thay đổi mà không có dấu vết giải trình. |

### 1.3. Ngoài phạm vi

- Việc Tuyển sinh đầu vào không thuộc phạm vi hệ thống này.
- Quản lý Nhân sự & Lương Giảng viên (chấm công, hợp đồng) không thuộc phạm vi.
- Không tính mức hưởng thư viện / KTX.

## CHƯƠNG 2. QUY ƯỚC, KÝ HIỆU & MÃ ĐỊNH DANH

| Ký hiệu | Ý nghĩa | Ví dụ |
| --- | --- | --- |
| **FS-QLSV-xxx-xxxx** | Mã chức năng đặc tả | FS-QLSV-030-0010 |
| **TTxx-Sxx** | Trạng thái thực thể (Sinh viên, Bảng điểm) | S1 (Đang học), G1 (Đạt) |
| **VLD-QLSV-xx** | Quy tắc kiểm tra dữ liệu | VLD-QLSV-06 |
| **ERR-QLSV-xx** | Mã thông báo lỗi | ERR-QLSV-14 |

## CHƯƠNG 3. TỔNG QUAN CHỨC NĂNG & MÀN HÌNH

### 3.1. Nhóm chức năng chính

| Nhóm | Tên nhóm | Vai trò | Đặc tả chi tiết tại |
| --- | --- | --- | --- |
| **QLSV-01** | Quản lý Sinh viên & Học tập (Tạo hồ sơ, Phân lớp) | Quản nhiệm | FS-QLSV-010-0010 |
| **QLSV-02** | Đào tạo & Thời khóa biểu | Quản nhiệm | Theo QT-05 |
| **QLSV-03** | Điểm danh bằng QR Động | Giảng viên, SV | FS-QLSV-030-0010 |
| **QLSV-04** | Điểm & Khảo thí (Nhập điểm, Tự động xét Đạt/Trượt) | Giảng viên, Admin | FS-QLSV-040-0020 |
| **QLSV-05** | Dịch vụ Sinh viên (Đơn từ) | SV, Quản nhiệm | Theo QT-10 |
| **QLSV-06** | Thanh toán (Payment Gateway) | SV, Kế toán | Theo QT-11 |
| **QLSV-07** | Đăng ký học lại & Kỷ luật | SV, Quản nhiệm | FS-QLSV-070-0010 |

### 3.2. Màn hình

| Mã  | Màn hình | Vai trò | Nhóm |
| --- | --- | --- | --- |
| MH-QN-01 | Dashboard Quản nhiệm & Danh sách SV | Quản nhiệm | QLSV-01 |
| MH-QN-02 | Import hồ sơ Sinh viên | Quản nhiệm | QLSV-01 |
| MH-QN-09 | Chốt sổ điểm | Quản nhiệm | QLSV-04 |
| MH-GV-02 | TKB cá nhân Giảng viên | Giảng viên | QLSV-02 |
| MH-GV-03 | Mở phiên Điểm danh (QR) | Giảng viên | QLSV-03 |
| MH-SV-03 | Quét QR Điểm danh | Sinh viên | QLSV-03 |
| MH-SV-07 | Hóa đơn & Thanh toán | Sinh viên | QLSV-06 |
| MH-SV-08 | Đăng ký Học lại | Sinh viên | QLSV-07 |
| MH-KT-02 | Đối soát giao dịch | Kế toán | QLSV-06 |

## CHƯƠNG 4. ĐẶC TẢ LUỒNG NGHIỆP VỤ

### 4.1. Quy trình Tiếp nhận & Xử lý hồ sơ trùng lặp (Import/Tạo mới)

| Bước | Việc | Vai trò | Trạng thái |
| --- | --- | --- | --- |
| 1   | Upload/Tạo mới danh sách sinh viên qua biểu mẫu. | Quản nhiệm | —   |
| 2   | Hệ thống rà quét tự động sự tồn tại của CCCD, Mã SV và Email. | Hệ thống | —   |
| 3   | **Hồ sơ trùng**: Phát hiện trùng CCCD/Mã SV với hồ sơ đang tồn tại, hệ thống lập tức CHẶN lưu, bôi đỏ dòng dữ liệu vi phạm. | Hệ thống | ERR-QLSV-01 |
| 4   | **Ngoại lệ đổi CCCD**: Sinh viên cập nhật lại thẻ CCCD (cấp lại, đổi số) → Không sinh mã SV hay hồ sơ mới. Thêm số mới và đưa số cũ vào lịch sử (Đã thay thế). | Hệ thống | —   |
| 5   | Hoàn tất import đối với những bản ghi hợp lệ. Khởi tạo tài khoản truy cập. | Hệ thống | S0 → S1 |

### 4.2. Luồng Ngoại lệ & Sự cố thường gặp

| Mã  | Tình huống | Cách xử lý |
| --- | --- | --- |
| NL-01 | **Gian lận điểm danh QR:** Sinh viên dùng camera thường hoặc app bên thứ 3 quét QR để điểm danh hộ bạn ở nhà. | Chặn hoàn toàn. App ngoài sẽ hiển thị Token mã hóa vô nghĩa. Đồng thời, SV bắt buộc phải đăng nhập và dùng đúng tài khoản FAP cá nhân. Hệ thống đối chiếu trực tiếp định danh tài khoản với lịch học và thời gian môn học thực tế; điểm danh chỉ hợp lệ khi quét bằng đúng tài khoản chính chủ của SV có mặt trong danh sách lớp. |
| NL-02 | **Mất kết nối mạng khi quét QR:** WiFi trường chập chờn, SV không thể quét mã trong giờ học. | Giảng viên sử dụng chức năng Điểm danh thủ công (Manual Attendance). Yêu cầu Ghi Log thao tác. |
| NL-03 | **Payment Gateway chết / Không trả Webhook:** Tiền đã trừ ở ví SV nhưng Webhook/IPN không gọi về Server trường. | Giao dịch treo ở “Pending”. Cung cấp nút Query Transaction cho Kế toán để tra soát với VNPay/MoMo và gạch nợ thủ công (Lưu Log). |
| NL-04 | **Quá số lượng lớp chứa:** Xếp lịch học lại hoặc phân lớp tân sinh viên vượt quá MaxCapacity (30 SV/lớp). | Chặn gán vào lớp, đưa SV vào danh sách Waitlisted để Quản nhiệm mở lớp bổ sung. |

### 4.3. Quy trình Xét điều kiện dự thi & Tổng kết điểm (Đóng góp QT-09)

| Bước | Việc | Vai trò | Trạng thái |
| --- | --- | --- | --- |
| 1   | Hệ thống quét tỷ lệ vắng mặt: Nếu ≥ 20% → Chốt CẤM THI | Hệ thống | G3 (Fail) → G5 |
| 2   | Vắng < 20%: Tính Tổng điểm theo tỷ trọng thành phần | Hệ thống | G0 (In Progress) |
| 3   | Quét điều kiện liệt: FE < 4.0 HOẶC Tổng < 5.0 → Chốt THI LẠI | Hệ thống | G4 (Retake) |
| 4   | Xét điều kiện học lại: Đang G4 mà thi lại FE vẫn trượt → Chốt HỌC LẠI | Hệ thống | G5 (Re-study) |
| 5   | Các SV thỏa mãn toàn bộ (Vắng < 20%, FE ≥ 4.0, Tổng ≥ 5.0) → Chốt ĐẠT | Hệ thống | G1 (Passed) |

## CHƯƠNG 5. ĐẶC TẢ CHI TIẾT CHỨC NĂNG

### 5.1. Nhóm 030 — FS-QLSV-030-0010 — Điểm danh bằng QR Code Động

**① Mô tả & mục đích** Điểm danh là nghiệp vụ nhạy cảm, dễ gian lận. Hệ thống sử dụng QR Code động sinh ra tại lớp, refresh liên tục để chống chụp ảnh gửi ra ngoài. Sinh viên quét mã thông qua App để hệ thống xác thực.

**② Logic xử lý**

1.  Khi GV mở phiên, hệ thống sinh mã QR động (chứa Token mã hóa) hiển thị lên màn hình, tự động refresh 10 giây/lần.
2.  SV sử dụng App nội bộ để quét mã. App gửi Token lên Server. Server giải mã và ghi nhận “Present”.
3.  Chỉ thiết bị/App hệ thống mới giải mã được (chặn Zalo/Camera ngoài).
4.  Mỗi sinh viên chỉ được ghi nhận “Present” 1 lần duy nhất trong Slot.
5.  Hết giờ, GV đóng phiên. SV chưa quét bị hệ thống tự động đánh “Absent”.

**③ Đặc tả trường dữ liệu** | Trường (Mã) | Kiểu | ✱ | Validate | |—|—|—|—| | FLD-QR-TOKEN | String | ✱ | Token động mã hóa, refresh 10s (VLD-QLSV-03) | | FLD-SESS-STATUS | Enum | ✱ | Opening / Closed | | FLD-REC-STATUS | Enum | ✱ | Present / Absent | | FLD-REC-TIME | DateTime | — | Thời điểm SV quét mã thành công | | FLD-MANUAL-EDIT | Boolean| — | True nếu QN/GV sửa thủ công (Bắt buộc ghi Log) |

**④ Quy tắc nghiệp vụ áp dụng**

- **BR-013:** QR Code phải refresh tự động 10s/lần để chống gian lận.
- **BR-017:** Tỷ lệ vắng mặt ≥ 20% → Tự động đánh FAIL (FE) không qua xét duyệt.
- **BR-018:** Sửa điểm danh thủ công chỉ dành cho GV phụ trách/Quản nhiệm/Admin và phải ghi Activity Log.

### 5.2. Nhóm 040 — FS-QLSV-040-0020 — Xét điều kiện điểm số tự động

**① Mô tả & mục đích** Loại bỏ hoàn toàn cảm tính của con người trong việc quyết định SV có qua môn hay không. Hệ thống số hóa tuyệt đối Quy chế Đào tạo FPT thành thuật toán cứng.

**② Logic xử lý**

1.  Điểm thành phần làm tròn 1 chữ số thập phân (Hệ cơ số 10.0).
2.  Khi Quản nhiệm “Chốt sổ”, hệ thống khóa quyền sửa điểm của GV (BR-020).
3.  Đánh giá tuần tự:
    - Vắng ≥ 20% → Trượt thẳng (G3 → G5).
    - FE < 4.0 hoặc Tổng < 5.0 → Thi lại (G4).
    - Đang G4 thi lại vẫn trượt → Học lại (G5).
    - Thỏa mãn tất cả → Đạt (G1).
4.  Bất kỳ sửa đổi điểm nào sau “Chốt sổ” chỉ thực hiện bởi Admin, và **bắt buộc** nhập lý do giải trình (Lưu Log).

**③ Đặc tả trường dữ liệu** | Trường (Mã) | Kiểu | ✱ | Validate | |—|—|—|—| | FLD-SCORE-QUIZ | Float | — | Từ 0.0 đến 10.0 | | FLD-SCORE-FINAL | Float | — | Điểm thi cuối kỳ (FE) | | FLD-SCORE-TOTAL | Float | — | Tự tính dựa trên tỷ trọng thành phần | | FLD-GRADE-STATUS | Enum | ✱ | G0 (Đang học), G1, G3, G4, G5 | | FLD-LOG-REASON | Text | ✱ | Bắt buộc khi Admin sửa điểm sau chốt (VLD-QLSV-08) |

### 5.3. Nhóm 070 — FS-QLSV-070-0010 — Đăng ký Học lại & Kỷ luật

**① Mô tả & mục đích** Số hóa quy trình xử lý môn trượt, tính lệ phí học lại tự động theo khoảng cách học kỳ, và khóa các tài khoản bị kỷ luật.

**② Logic xử lý**

1.  SV chỉ được chọn môn đang ở trạng thái G3, G4, G5.
2.  Với G4 (Thi lại): Chỉ đóng phí thi lại, xếp lịch thi.
3.  Với G3/G5 (Học lại): Tính phí tự động. 50% nếu học lại ngay kỳ liền kề; 100% nếu cách ≥ 1 kỳ.
4.  Trạng thái S5 (Đình chỉ): Chặn mọi quyền đăng ký và thông báo rõ thời hạn.
5.  Hết đình chỉ (S5 → S1): Bị áp phí 150% đơn giá môn học do phạt kỷ luật.

**③ Quy tắc nghiệp vụ áp dụng**

- **BR-038:** Chặn SV đang đình chỉ (S5). Không có ngoại lệ.
- **BR-039:** Thu phí 150% với SV vừa hết hạn đình chỉ.

### 5.4. Bảng tổng hợp chức năng còn lại

| Mã chức năng | Nội dung | Ghi chú |
| --- | --- | --- |
| FS-QLSV-010-0020 | Phân lớp chuyên ngành | Tự động/thủ công gán danh sách, tự động check sĩ số (CurrentSize). |
| FS-QLSV-020-0010 | Xếp Thời khóa biểu Auto-scheduling | Phát hiện và chặn Deadlock môn học, Conflict phòng/giảng viên. |
| FS-QLSV-050-0010 | Dịch vụ nộp đơn từ (Hành chính) | SV nộp (Nghỉ học, Phúc khảo), QN xử lý, đổi trạng thái đơn. |
| FS-QLSV-060-0010 | Thanh toán & Đối soát giao dịch | Gọi API Payment, Query API thủ công cho Kế toán, xuất File. |
| FS-QLSV-110-0010 | Nhật ký truy cập & Activity Log | Ghi nhận 100% mọi thao tác cập nhật điểm, gạch nợ thủ công, thay đổi trạng thái SV. Không cấp quyền Xóa Log. |

## CHƯƠNG 6. ĐẶC TẢ MÀN HÌNH CHÍNH

### 6.1. MH-GV-03 & MH-SV-03 — Màn hình Điểm danh

- **Màn chiếu GV:** Hiển thị QR Code kích thước lớn chiếm 80% màn hình, đếm ngược 10 giây bên dưới để refresh QR mới.
- **App SV:** Bật camera với vùng nhận diện định sẵn, hiện trạng thái “Thành công” nền xanh lá khi quét đúng mã hợp lệ.

### 6.2. MH-QN-09 — Màn hình Chốt sổ điểm

- Danh sách SV với các cột điểm thành phần.
- Cột “Tổng” và “Trạng thái” (Passed/Failed) được tô đậm.
- Nút “Chốt sổ” yêu cầu xác nhận 2 lần. Sau khi chốt, Grid nhập điểm của GV bị khóa (Disabled).

## CHƯƠNG 7. MÁY TRẠNG THÁI HỒ SƠ

### 7.1. Trạng thái Sinh viên (TT-01)

| Mã  | Trạng thái | Điều kiện vào | Chuyển tiếp được |
| --- | --- | --- | --- |
| S0  | Mới (Initialized) | Vừa Import | → S1 (Khi gán lớp) |
| S1  | Đang học (Active) | Có lớp, đang học | → S2, S3, S4, S5 |
| S2  | Bảo lưu (Suspended) | Có QĐ tạm ngừng | → S1 (Tái nhập) |
| S5  | Đình chỉ | Vi phạm kỷ luật | → S1 (Hết hạn 1 kỳ) |

### 7.2. Trạng thái Bảng điểm Môn học (TT-09)

| Mã  | Trạng thái | Điều kiện vào | Chuyển tiếp được |
| --- | --- | --- | --- |
| G0  | In Progress | Đang theo học | → G1, G3, G4 |
| G1  | Passed | Vắng<20% & FE≥4.0 & Tổng≥5.0 | (Trạng thái cuối môn) |
| G3  | Fail (Cấm thi) | Vắng ≥ 20% | → G5 (Học lại) |
| G4  | Retake (Thi lại) | FE<4.0 hoặc Tổng<5.0 | → G1 (Đạt), G5 (Trượt tiếp) |
| G5  | Re-study (Học lại) | Từ G3 hoặc trượt G4 | → G0 (Đăng ký học lại kỳ mới) |

## CHƯƠNG 8. QUY TẮC NGHIỆP VỤ & CHỐT CHẶN CỨNG

| Quy tắc (BR) | Nội dung chốt chặn | Áp dụng tại | Vì sao chặn là đúng |
| --- | --- | --- | --- |
| **BR-001/002** | Mã SV, CCCD, Email phải duy nhất | FS-QLSV-010 | Tránh nhầm lẫn dữ liệu giữa hai người. |
| **BR-003** | Bảo lưu/Thôi học lập tức bị gỡ khỏi lớp | QT-02 | SV đã thôi học không được phép tồn tại trong TKB và danh sách điểm danh. |
| **BR-017** | Vắng ≥ 20% chốt Fail thẳng | FS-QLSV-030 | Tuân thủ tuyệt đối quy chế đào tạo, không có ngoại lệ cảm tính. |
| **BR-020** | Sau “Chốt sổ”, GV không được sửa điểm | FS-QLSV-040 | Đảm bảo tính toàn vẹn của bảng điểm cuối kỳ đã công bố. |

## CHƯƠNG 9. QUY TẮC KIỂM TRA DỮ LIỆU (VALIDATION)

| Mã  | Quy tắc kiểm tra | Mức xử lý |
| --- | --- | --- |
| VLD-QLSV-01 | Trùng lặp CCCD/Email khi import | **CHẶN**, highlight dòng lỗi |
| VLD-QLSV-02 | Lớp học vượt quá sĩ số tối đa (MaxCapacity) | **CHẶN** |
| VLD-QLSV-03 | Quét QR Code đã quá hạn 10s | **CHẶN**, yêu cầu quét lại |
| VLD-QLSV-04 | GV sửa điểm thành phần ngoài dải 0.0 - 10.0 | **CHẶN**, viền ô màu đỏ |
| VLD-QLSV-05 | Admin sửa điểm sau chốt sổ mà không nhập Lý do | **CHẶN** |

## CHƯƠNG 10. TÍCH HỢP & SỰ KIỆN

| Chiều tích hợp | Nội dung | Dữ liệu giao tiếp | Ghi chú |
| --- | --- | --- | --- |
| **Hệ thống → VNPay/MoMo** | Thanh toán học phí, lệ phí | URL Thanh toán (Checksum, Số tiền) | SSL/TLS, Secret Key |
| **VNPay/MoMo → Hệ thống** | Trả kết quả (Webhook/IPN) | Mã giao dịch, Trạng thái thanh toán | Gạch nợ tự động (QT-11) |
| **Hệ thống → Mailing Service** | Gửi Email cảnh báo vắng, kết quả duyệt đơn | Địa chỉ Email, Nội dung HTML | Xử lý hàng đợi bất đồng bộ |

### Sự kiện hệ thống (Events)

- EVT-STUDENT-ATTENDANCE-FAILED: Kích hoạt khi SV chạm mốc vắng 20%, hệ thống chốt G3 và gửi Email.
- EVT-PAYMENT-SUCCESS: Kích hoạt khi nhận Webhook thành công, tự động gạch nợ và đổi trạng thái Hóa đơn sang “Paid”.

## CHƯƠNG 11. DANH MỤC THÔNG BÁO LỖI (ERRORS)

| Mã lỗi | Điều kiện | Loại |
| --- | --- | --- |
| **ERR-QLSV-01** | Trùng lặp Mã SV/CCCD khi import danh sách | Chặn lưu |
| **ERR-QLSV-02** | Xếp GV dạy 2 lớp trùng Slot | Chặn lưu (Xung đột TKB) |
| **ERR-QLSV-03** | GV báo nghỉ sát giờ (Cách < 12 tiếng) | Chặn báo nghỉ trên app |
| **ERR-QLSV-04** | SV quét QR Code ngoài hệ thống / Fake QR | Chặn giải mã |
| **ERR-QLSV-05** | Checksum VNPay trả về không khớp | Cảnh báo Admin, Chặn gạch nợ |

## CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR ĐO ĐƯỢC)

| Nhóm | Yêu cầu | Cách đo kiểm |
| --- | --- | --- |
| **Tốc độ** | Thời gian chạy xếp TKB tự động cho toàn trường ≤ 30s | Chạy giả lập 200 SV & 10 GV |
| **Tốc độ** | Xác thực QR Code phản hồi ≤ 2 giây | Test tải với 200 SV quét đồng thời |
| **Toàn vẹn** | Mật khẩu tài khoản phải Hash một chiều | Truy vấn Database rà soát bản rõ |
| **Truy vết** | Không có chức năng xóa Log trên giao diện | Rà soát phân quyền DB |

## CHƯƠNG 13. MA TRẬN TRUY VẾT & NGHIỆM THU

### Tiêu chí nghiệm thu (Acceptance Criteria)

| Mã  | Tiêu chí nghiệm thu | Đặc tả tại |
| --- | --- | --- |
| **NT-QLSV-01** | Nhập danh sách SV thành công, không trùng CCCD/Mã SV. | QT-01, VLD-QLSV-01 |
| **NT-QLSV-02** | Thuật toán xếp lịch chạy ra TKB không có xung đột (Conflict) phòng/GV. | QT-05 |
| **NT-QLSV-03** | QR Code điểm danh refresh mỗi 10s, chặn các phần mềm quét ngoài. | QT-07, FS-QLSV-030 |
| **NT-QLSV-04** | Hệ thống tự động chuyển trạng thái môn G1/G3/G4/G5 chuẩn xác theo % vắng và FE. | QT-09, FS-QLSV-040 |
| **NT-QLSV-05** | Thanh toán thành công qua IPN VNPay tự động chuyển Hóa đơn sang Paid. | QT-11 |
| **NT-QLSV-06** | SV bị đình chỉ (S5) tuyệt đối không thể đăng ký học lại. | QT-13, FS-QLSV-070 |

_(Tài liệu được trích xuất và chuẩn hóa từ BRD Quản Lý Sinh Viên v3.1)_