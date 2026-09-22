# TÀI LIỆU ĐẶC TẢ CHỨC NĂNG (FSD)

## HỆ THỐNG QUẢN LÝ SINH VIÊN

_Tự động hóa - Real-time - Minh bạch_

### Thuộc tính

| Thuộc tính        | Nội dung                                                                                                                                                                          |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mã phân hệ       | QLSV (Gồm QLSV-01 đến QLSV-06)                                                                                                                                                  |
| Tên phân hệ      | Hệ thống Quản lý Sinh viên                                                                                                                                                    |
| Loại tài liệu    | FSD — Đặc tả chức năng                                                                                                                                                       |
| Phạm vi            | Đặc tả field-level các nhóm chức năng cốt lõi: Hồ sơ, Đào tạo, Điểm danh QR động, Quản lý Điểm & Khảo thí, Hành chính, Thanh toán, Đăng ký học lại |
| Thực thể sở hữu | TT-01 Hồ sơ SV, TT-06 TKB, TT-07/08 Điểm danh, TT-09 Bảng điểm, TT-10 Đơn từ, TT-11 Hóa đơn, TT-12 Giao dịch, TT-15 ĐK Học lại, TT-18 Thông báo                 |
| Tài liệu nguồn   | Tài liệu Yêu cầu Nghiệp vụ (BRD-QLSV-v4.0)                                                                                                                                   |
| Phiên bản         | 2.0 (Bản hoàn chỉnh)                                                                                                                                                            |

## MỤC LỤC

1. [CHƯƠNG 1. GIỚI THIỆU](#chương-1-giới-thiệu)
2. [CHƯƠNG 2. QUY ƯỚC, KÝ HIỆU &amp; MÃ ĐỊNH DANH](#chương-2-quy-ước-ký-hiệu--mã-định-danh)
3. [CHƯƠNG 3. TỔNG QUAN CHỨC NĂNG &amp; MÀN HÌNH](#chương-3-tổng-quan-chức-năng--màn-hình)
4. [CHƯƠNG 4. ĐẶC TẢ LUỒNG NGHIỆP VỤ](#chương-4-đặc-tả-luồng-nghiệp-vụ)
5. [CHƯƠNG 5. ĐẶC TẢ CHI TIẾT CHỨC NĂNG](#chương-5-đặc-tả-chi-tiết-chức-năng)
6. [CHƯƠNG 6. ĐẶC TẢ MÀN HÌNH CHÍNH](#chương-6-đặc-tả-màn-hình-chính)
7. [CHƯƠNG 7. MÁY TRẠNG THÁI HỒ SƠ](#chương-7-máy-trạng-thái-hồ-sơ)
8. [CHƯƠNG 8. QUY TẮC NGHIỆP VỤ &amp; CHỐT CHẶN CỨNG](#chương-8-quy-tắc-nghiệp-vụ--chốt-chặn-cứng)
9. [CHƯƠNG 9. QUY TẮC KIỂM TRA DỮ LIỆU (VALIDATION)](#chương-9-quy-tắc-kiểm-tra-dữ-liệu-validation)
10. [CHƯƠNG 10. TÍCH HỢP &amp; SỰ KIỆN](#chương-10-tích-hợp--sự-kiện)
11. [CHƯƠNG 11. DANH MỤC THÔNG BÁO LỖI (ERRORS)](#chương-11-danh-mục-thông-báo-lỗi-errors)
12. [CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR ĐO ĐƯỢC)](#chương-12-yêu-cầu-phi-chức-năng-nfr-đo-được)
13. [CHƯƠNG 13. MA TRẬN TRUY VẾT &amp; NGHIỆM THU](#chương-13-ma-trận-truy-vết--nghiệm-thu)

## CHƯƠNG 1. GIỚI THIỆU

### 1.1. Mục đích tài liệu

Dựa trên BRD-QLSV-v4.0, tài liệu FSD này đặc tả chi tiết cách hệ thống thực hiện các nghiệp vụ: quản lý hồ sơ sinh viên xuyên suốt, đào tạo và thời khóa biểu, điểm danh bằng QR Động (real-time), tự động xét điều kiện điểm số, dịch vụ sinh viên trực tuyến, và tích hợp thanh toán. Tài liệu hướng dẫn đội ngũ phát triển xây dựng các chốt chặn (validation) và thuật toán để đảm bảo quy chế đào tạo được áp dụng khắt khe và chính xác.

### 1.2. Ba nguyên tắc chi phối cả tài liệu

| Nguyên tắc                                  | Nghĩa cụ thể                                                                                                                                              | Vì sao                                                                                                                                      |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tự động hóa & Khách quan**       | Điểm danh tự động qua QR; hệ thống tự tính điểm tổng kết và xét Đạt/Trượt/Cấm thi. Xếp lịch học, tính lệ phí học lại tự động. | Tránh sai sót thủ công và đảm bảo sự công bằng, minh bạch tối đa trong đào tạo.                                             |
| **Real-time & Đồng bộ**              | Thay đổi trạng thái học tập lập tức chặn đăng nhập và gỡ khỏi lớp; QR điểm danh làm mới 10s/lần.                                        | Sinh viên bảo lưu/thôi học không được phép tiếp tục truy cập dữ liệu; QR động chống gian lận điểm danh hộ.             |
| **Truy vết toàn diện (Audit Trail)** | Mọi sửa đổi điểm sau chốt, sửa điểm danh thủ công, duyệt đơn từ đều được ghi Log (Who, When, Old/New).                                  | Quyết định liên quan đến điểm số, tài chính và bằng cấp không được phép thay đổi mà không có dấu vết giải trình. |

### 1.3. Ngoài phạm vi

- Việc Tuyển sinh đầu vào không thuộc phạm vi hệ thống này.
- Quản lý Nhân sự & Lương Giảng viên (chấm công, hợp đồng) không thuộc phạm vi.
- Không tính mức hưởng thư viện / KTX.
- Native Mobile App (iOS/Android). Hệ thống sử dụng Progressive Web App (PWA).

## CHƯƠNG 2. QUY ƯỚC, KÝ HIỆU & MÃ ĐỊNH DANH

| Ký hiệu                  | Ý nghĩa                                          | Ví dụ                     |
| -------------------------- | -------------------------------------------------- | --------------------------- |
| **FS-QLSV-xxx-xxxx** | Mã chức năng đặc tả                          | FS-QLSV-030-0010            |
| **TTxx-Sxx/Gxx**     | Trạng thái thực thể (Sinh viên, Bảng điểm) | S1 (Đang học), G1 (Đạt) |
| **VLD-QLSV-xx**      | Quy tắc kiểm tra dữ liệu                       | VLD-QLSV-06                 |
| **ERR-QLSV-xx**      | Mã thông báo lỗi                               | ERR-QLSV-14                 |

## CHƯƠNG 3. TỔNG QUAN CHỨC NĂNG & MÀN HÌNH

### 3.1. Nhóm chức năng chính

| Nhóm             | Tên nhóm                                                        | Vai trò               | Đặc tả chi tiết tại |
| ----------------- | ----------------------------------------------------------------- | ---------------------- | ------------------------ |
| **QLSV-01** | Quản lý Sinh viên & Học tập (Tạo hồ sơ, Phân lớp)       | Quản nhiệm           | FS-QLSV-010-0010         |
| **QLSV-02** | Đào tạo & Thời khóa biểu                                    | Quản nhiệm           | FS-QLSV-020-0010         |
| **QLSV-03** | Điểm danh bằng QR Động                                       | Giảng viên, SV       | FS-QLSV-030-0010         |
| **QLSV-04** | Điểm & Khảo thí (Nhập điểm, Tự động xét Đạt/Trượt) | Giảng viên, Admin    | FS-QLSV-040-0020         |
| **QLSV-05** | Dịch vụ Sinh viên (Đơn từ)                                  | SV, Quản nhiệm       | FS-QLSV-050-0010         |
| **QLSV-06** | Thanh toán (Payment Gateway)                                     | SV, Kế toán          | FS-QLSV-060-0010         |
| **QLSV-07** | Đăng ký học lại & Kỷ luật                                  | SV, Quản nhiệm       | FS-QLSV-070-0010         |
| **QLSV-08** | Notification Center (Thông báo)                                 | Tất cả Người dùng | FS-QLSV-080-0010         |

### 3.2. Màn hình

| Mã       | Màn hình                             | Vai trò     | Nhóm   |
| --------- | -------------------------------------- | ------------ | ------- |
| MH-QN-01  | Dashboard Quản nhiệm & Danh sách SV | Quản nhiệm | QLSV-01 |
| MH-QN-02  | Import hồ sơ Sinh viên              | Quản nhiệm | QLSV-01 |
| MH-QN-04  | Phân lớp chuyên ngành              | Quản nhiệm | QLSV-01 |
| MH-QN-06  | Xếp Thời khóa biểu                 | Quản nhiệm | QLSV-02 |
| MH-QN-08  | Duyệt đơn từ Sinh viên            | Quản nhiệm | QLSV-05 |
| MH-QN-09  | Chốt sổ điểm                       | Quản nhiệm | QLSV-04 |
| MH-QN-10  | Quản lý Đăng ký Học lại         | Quản nhiệm | QLSV-07 |
| MH-QN-11  | Quản lý Kỷ luật                    | Quản nhiệm | QLSV-07 |
| MH-GV-02  | TKB cá nhân Giảng viên             | Giảng viên | QLSV-02 |
| MH-GV-03  | Mở phiên Điểm danh (QR)            | Giảng viên | QLSV-03 |
| MH-GV-05  | Nhập/Import điểm                    | Giảng viên | QLSV-04 |
| MH-SV-03  | Quét QR Điểm danh (PWA Camera)      | Sinh viên   | QLSV-03 |
| MH-SV-05  | Nộp đơn từ trực tuyến            | Sinh viên   | QLSV-05 |
| MH-SV-07  | Hóa đơn & Thanh toán               | Sinh viên   | QLSV-06 |
| MH-SV-08  | Đăng ký Học lại                   | Sinh viên   | QLSV-07 |
| MH-KT-02  | Đối soát giao dịch                 | Kế toán    | QLSV-06 |
| MH-ALL-02 | Notification Center                    | All Users    | QLSV-08 |

## CHƯƠNG 4. ĐẶC TẢ LUỒNG NGHIỆP VỤ

### 4.1. Quy trình Tiếp nhận & Xử lý hồ sơ trùng lặp (Import/Tạo mới)

| Bước | Việc                                                                                                                                                                                                  | Vai trò     | Trạng thái |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | ------------ |
| 1      | Upload/Tạo mới danh sách sinh viên qua biểu mẫu.                                                                                                                                                 | Quản nhiệm | —           |
| 2      | Hệ thống rà quét tự động sự tồn tại của CCCD, Mã SV và Email.                                                                                                                             | Hệ thống   | —           |
| 3      | **Hồ sơ trùng**: Phát hiện trùng CCCD/Mã SV với hồ sơ đang tồn tại, hệ thống lập tức CHẶN lưu, bôi đỏ dòng dữ liệu vi phạm.                                            | Hệ thống   | ERR-QLSV-01  |
| 4      | **Ngoại lệ đổi CCCD**: Sinh viên cập nhật lại thẻ CCCD (cấp lại, đổi số) → Không sinh mã SV hay hồ sơ mới. Thêm số mới và đưa số cũ vào lịch sử (Đã thay thế). | Hệ thống   | —           |
| 5      | Hoàn tất import đối với những bản ghi hợp lệ. Khởi tạo tài khoản truy cập.                                                                                                               | Hệ thống   | S0 → S1     |

### 4.2. Luồng Ngoại lệ & Sự cố thường gặp

| Mã   | Tình huống                                                                                                                           | Cách xử lý                                                                                                                                                                                                                                                                      |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NL-01 | **Gian lận điểm danh QR:** Sinh viên dùng camera thường hoặc app bên thứ 3 quét QR để điểm danh hộ bạn ở nhà. | Chặn hoàn toàn. App ngoài sẽ hiển thị Token mã hóa vô nghĩa. Đồng thời, SV bắt buộc phải đăng nhập và dùng đúng tài khoản FAP cá nhân. Hệ thống đối chiếu trực tiếp định danh tài khoản với lịch học và thời gian môn học thực tế. |
| NL-02 | **Mất kết nối mạng khi quét QR:** WiFi trường chập chờn, SV không thể quét mã trong giờ học.                      | Giảng viên sử dụng chức năng Điểm danh thủ công (Manual Attendance). Yêu cầu Ghi Log thao tác.                                                                                                                                                                        |
| NL-03 | **Payment Gateway chết / Không trả Webhook:** Tiền đã trừ ở ví SV nhưng Webhook/IPN không gọi về Server trường.   | Giao dịch treo ở “Pending”. Cung cấp nút Query Transaction cho Kế toán để tra soát với VNPay/MoMo và gạch nợ thủ công (Lưu Log).                                                                                                                                 |
| NL-04 | **Quá số lượng lớp chứa:** Xếp lịch học lại hoặc phân lớp tân sinh viên vượt quá MaxCapacity (30 SV/lớp).     | Chặn gán vào lớp, đưa SV vào danh sách Waitlisted để Quản nhiệm mở lớp bổ sung.                                                                                                                                                                                     |

### 4.3. Quy trình Xét điều kiện dự thi & Tổng kết điểm

| Bước | Việc                                                                                 | Vai trò   | Trạng thái         |
| ------ | ------------------------------------------------------------------------------------- | ---------- | -------------------- |
| 1      | Hệ thống quét tỷ lệ vắng mặt: Nếu ≥ 20% → Chốt CẤM THI                    | Hệ thống | G0 → G3 (Fail)      |
| 2      | Vắng < 20%: Tính Tổng điểm theo tỷ trọng thành phần                          | Hệ thống | G0 (In Progress)     |
| 3      | Quét điều kiện liệt: FE < 4.0 HOẶC Tổng < 5.0 → Chốt THI LẠI                | Hệ thống | G0 → G4 (Retake)    |
| 4      | Xét điều kiện học lại: Đang G4 mà thi lại FE vẫn trượt → Chốt HỌC LẠI | Hệ thống | G4 → G5 (Re-study)  |
| 5      | Các SV thỏa mãn toàn bộ (Vắng < 20%, FE ≥ 4.0, Tổng ≥ 5.0) → Chốt ĐẠT    | Hệ thống | G0/G4 → G1 (Passed) |

## CHƯƠNG 5. ĐẶC TẢ CHI TIẾT CHỨC NĂNG

### 5.1. Nhóm 01 — FS-QLSV-010-0010 — Quản lý Sinh viên & Học tập

**① Mô tả & mục đích** Quản lý hồ sơ đầu vào của sinh viên, bao gồm tạo mới (import), quản lý tài khoản, cập nhật trạng thái học tập và phân lớp.
**② Logic xử lý**

1. Nhận file Excel/CSV từ Quản nhiệm, validate các cột (CCCD, Mã SV, Email).
2. Tạo tài khoản đăng nhập tương ứng, gửi email thông tin ban đầu.
3. Chặn đăng nhập với các tài khoản ở trạng thái Thôi học (S3) hoặc chuyển trạng thái Limited đối với Bảo lưu (S2). Tự động gỡ khỏi danh sách lớp hiện tại.
4. Phân lớp tự động dựa vào chuyên ngành học (Max 30 SV/lớp theo cấu hình lớp). Không cho phép một SV học 2 lớp chuyên ngành khác nhau cùng kỳ.

**③ Đặc tả trường dữ liệu**

| Trường (Mã)     | Kiểu  | ✱ | Validate                                |
| ------------------ | ------ | -- | --------------------------------------- |
| FLD-STUDENT-ID     | String | ✱ | Unique (VLD-QLSV-01), Format (HExxxxxx) |
| FLD-STUDENT-CCCD   | String | ✱ | Unique (VLD-QLSV-01), 12 chữ số       |
| FLD-STUDENT-STATUS | Enum   | ✱ | S0, S1, S2, S3, S4, S5                  |

**④ Quy tắc nghiệp vụ áp dụng**

- **BR-001/002:** Unique Student ID, CCCD, Email.
- **BR-003:** Chuyển trạng thái S2/S3 lập tức gỡ khỏi lớp hiện tại và khóa/hạn chế ứng dụng.
- **BR-004:** Sĩ số lớp ≤ MaxCapacity.
- **BR-005:** SV chỉ thuộc 1 lớp cùng học kỳ.

### 5.2. Nhóm 02 — FS-QLSV-020-0010 — Đào tạo & Thời khóa biểu

**① Mô tả & mục đích** Xếp lịch học tự động cho hàng trăm lớp, kiểm tra tiên quyết, tránh xung đột giảng viên/phòng học. Quản lý trạng thái buổi học (báo nghỉ, dạy bù).
**② Logic xử lý**

1. Duyệt cấu trúc cây môn học để kiểm tra và chặn vòng lặp (Deadlock).
2. Khi Auto-scheduling, kiểm tra số lượng Slot/môn và tạo đủ lịch. Hệ thống cảnh báo và chặn lưu nếu trùng lặp GV hoặc Phòng học trong cùng 1 thời gian (Slot).
3. Cho phép báo nghỉ (yêu cầu báo trước 12 tiếng) và đặt lịch học bù. Lịch bù phải kiểm tra xung đột TKB của sinh viên trong lớp đó.

**③ Quy tắc nghiệp vụ áp dụng**

- **BR-006, BR-007:** Mã môn duy nhất, không deadlock.
- **BR-008, BR-009:** Tránh trùng lặp (Conflict) TKB (GV và Phòng).
- **BR-010:** Đảm bảo đủ số Slot cho môn học.
- **BR-011, BR-012:** Quy định về thời gian báo nghỉ và không conflict lịch học bù đối với sinh viên.

### 5.3. Nhóm 03 — FS-QLSV-030-0010 — Điểm danh bằng QR Code Động (Chi tiết sâu)

**① Mô tả & Mục đích** 
Điểm danh là nghiệp vụ nhạy cảm, dễ gian lận. Hệ thống sử dụng QR Code động sinh ra tại lớp, đồng bộ qua SignalR (WebSockets) để refresh liên tục nhằm chống chụp ảnh gửi ra ngoài.

**② Đặc tả phần tử UI (UI Elements)**
*   **Màn hình Giảng viên (MH-GV-03):**
    *   `btnOpenSession`: Nút mở phiên. Click gọi API `POST /api/attendance/open`.
    *   `imgQrCode`: Vùng hiển thị mã QR (Render bằng thư viện QRCoder base64).
    *   `lblCountdown`: Label đếm ngược 10->0, kích hoạt event refresh khi về 0.
    *   `gridAttendance`: Bảng danh sách lớp. Cột: [STT, MSSV, Họ tên, Trạng thái, Thời gian quét]. Tự động cập nhật dòng thành màu xanh (Present) qua SignalR khi có SV quét thành công.
*   **Màn hình Sinh viên (MH-SV-03 - PWA):**
    *   `camScanner`: Vùng hiển thị Camera sử dụng WebRTC API. Bắt buộc xin quyền cấp Camera từ trình duyệt.
    *   `lblResult`: Label hiển thị thông báo "Điểm danh thành công" (Màu xanh) hoặc lỗi (Màu đỏ).

**③ Đặc tả Thuật toán (Algorithm) & Giao tiếp**
1.  **Thuật toán sinh Token QR:** Server sử dụng thuật toán AES-256 mã hóa chuỗi `Payload = {SessionID} + {Timestamp} + {ClassID}` cùng với SecretKey. Sinh ra `DynamicQRToken`.
2.  **Luồng quét mã (Sequence):**
    *   SV quét QR -> App gửi `POST /api/attendance/scan` (Body: `Token`).
    *   Server giải mã AES-256 lấy `Timestamp`.
    *   **Validation 1 (VLD-QLSV-03):** `if (CurrentTime - Timestamp > 10s) throw ExpiredTokenError` (Báo lỗi "Mã QR đã hết hạn").
    *   **Validation 2 (BR-016):** `if (Request.ClientIP not in School_WiFi_Ranges) throw InvalidIPError` (Báo lỗi "Bạn không ở trong phạm vi trường").
    *   **Validation 3:** `if (Student not in ClassID) throw InvalidStudentError`.
    *   Nếu pass, cập nhật DB `TT-08` thành `Present`, gán `ScannedAt = Now`.
    *   Server push event qua SignalR đến `ClassID` group để cập nhật UI của Giảng viên ngay lập tức.
3.  **Thuật toán chốt phiên:** Khi GV ấn `btnCloseSession`, hệ thống chạy lệnh UPDATE: `UPDATE TT08 SET Status = 'Absent' WHERE SessionID = @sessId AND Status != 'Present'`.

**④ Đặc tả trường dữ liệu (DB Fields)** 

| Trường (Mã)  | Kiểu    | ✱ | Validate                                             |
| --------------- | -------- | -- | ---------------------------------------------------- |
| FLD-QR-TOKEN    | String   | ✱ | Token động mã hóa AES-256, max 255 chars         |
| FLD-SESS-STATUS | Enum     | ✱ | Opening / Closed                                     |
| FLD-REC-STATUS  | Enum     | ✱ | Present / Absent                                     |
| FLD-REC-TIME    | DateTime | — | Thời điểm SV quét mã thành công               |
| FLD-MANUAL-EDIT | Boolean  | — | True nếu QN/GV sửa thủ công (Bắt buộc ghi Log) |
| FLD-DEVICE-ID   | String   | — | Lưu chuỗi User-Agent / Fingerprint của trình duyệt SV để chống 1 máy quét cho 2 tài khoản |

**⑤ Quy tắc nghiệp vụ (BR)**
- **BR-013:** QR Code phải refresh tự động 10s/lần.
- **BR-014, BR-016:** IP ràng buộc dải mạng của trường học.
- **BR-017:** Tỷ lệ vắng mặt ≥ 20% → Tự động đánh CẤM THI.
- **BR-018:** Bất cứ thao tác sửa điểm danh thủ công nào trên grid đều hiển thị Popup bắt buộc điền `Reason` (Tối thiểu 10 ký tự) và ghi vào bảng `Activity Log`.

### 5.4. Nhóm 04 — FS-QLSV-040-0020 — Xét điều kiện điểm số tự động (Chi tiết sâu)

**① Mô tả & Mục đích** 
Loại bỏ hoàn toàn cảm tính con người. Số hóa cứng Quy chế Đào tạo vào thuật toán (Rule Engine) chạy tự động ngầm (Background Job) ngay khi môn học kết thúc hoặc khi Quản nhiệm chốt sổ.

**② Đặc tả phần tử UI (UI Elements)**
*   **Màn hình Nhập điểm (MH-GV-05):**
    *   `gridScores`: DataGrid. Các cột điểm (Quiz, Lab, Assign) được gen động dựa trên bảng Cấu hình tỷ trọng (TT-20) của môn học đó.
    *   `txtScore`: Input field (Type=number, step=0.1, min=0.0, max=10.0). Trigger sự kiện `onBlur` tự động lưu bản nháp ngầm (Auto-save) và gọi hàm tính `Total` tạm thời.
*   **Màn hình Chốt sổ (MH-QN-09):**
    *   `btnLockGrades`: Nút "Chốt sổ". Khi bấm sẽ hiện Dialog cảnh báo: *"Sau khi chốt sổ, không thể sửa đổi điểm ngoài trừ Admin. Bạn có chắc chắn?"* Kèm yêu cầu nhập mật khẩu cấp 2.
    *   Khi Grid ở trạng thái "Locked", toàn bộ Input fields trên màn hình MH-GV-05 của Giảng viên sẽ bị Disabled (Read-only).

**③ Đặc tả Thuật toán (Algorithm)**
Hàm xử lý nghiệp vụ: `EvaluateStudentGrade(StudentID, SubjectCode)`
```csharp
// 1. Lấy thông tin điểm danh và cấu hình
var totalSlots = GetTotalSlots(SubjectCode);
var absentCount = GetAbsentSlots(StudentID, SubjectCode);

// 2. Chốt cấm thi (BR-023)
if ((float)absentCount / totalSlots >= 0.2f) {
    UpdateStatus(StudentID, SubjectCode, GradeStatus.G3_Fail);
    TriggerEvent("EVT-STUDENT-ATTENDANCE-FAILED", StudentID);
    return;
}

// 3. Tính điểm tổng kết
var weights = GetGradeWeights(SubjectCode); // Từ TT-20
float totalScore = 0.0f;
totalScore += (GetScore(StudentID, "Quiz") * weights["Quiz"]);
totalScore += (GetScore(StudentID, "Assign") * weights["Assign"]);
totalScore += (GetScore(StudentID, "Lab") * weights["Lab"]);
var feScore = GetScore(StudentID, "FE");
totalScore += (feScore * weights["FE"]);

totalScore = Math.Round(totalScore, 1); // Round 1 decimal (BR-024)

// 4. Quét điều kiện liệt và chốt Đạt/Trượt
if (feScore < 4.0f || totalScore < 5.0f) {
    var hasRetaken = CheckIfRetakenFE(StudentID, SubjectCode); // BR-025b
    if (hasRetaken) {
        UpdateStatus(StudentID, SubjectCode, GradeStatus.G5_Restudy);
    } else {
        UpdateStatus(StudentID, SubjectCode, GradeStatus.G4_Retake);
    }
} else {
    UpdateStatus(StudentID, SubjectCode, GradeStatus.G1_Passed);
}
```

**④ Đặc tả API & Audit Trail**
- Khi Admin sửa điểm sau "Chốt sổ", hệ thống không cho phép dùng form bình thường mà phải sử dụng API Endpoint riêng: `POST /api/grades/override`.
- **Payload Request:** `{ "studentId": "HE123", "component": "FE", "oldScore": 3.0, "newScore": 5.0, "reason": "Sửa lỗi chấm sót câu 3 theo đơn phúc khảo #PK102" }`.
- Nếu `reason` có độ dài < 20 ký tự, API trả về `400 Bad Request` (VLD-QLSV-05).
- Dữ liệu Payload lập tức được Serialize thành chuỗi JSON và nhét vào trường `OldValue` và `NewValue` của bảng `TT-14 - Activity Log`.

**⑤ Quy tắc nghiệp vụ (BR)**
- **BR-019:** Thang điểm 10.0, step 0.1.
- **BR-021, BR-022, BR-023:** Điều kiện liệt (FE<4, Tổng<5, Vắng>=20%).
- **BR-025b, BR-025c:** Kiểm tra số lần thi lại và học lại bằng hàm đếm Aggregate Count trong DB.

### 5.5. Nhóm 05 — FS-QLSV-050-0010 — Dịch vụ Hành chính (Đơn từ)

**① Mô tả & mục đích** Số hóa cổng thủ tục hành chính để SV có thể gửi yêu cầu (nghỉ học, chuyển lớp, phúc khảo) tới Quản nhiệm.
**② Logic xử lý**

1. SV chọn loại đơn, nhập nội dung, đính kèm minh chứng, nộp.
2. Hệ thống kiểm tra số đơn Pending/Processing (Tối đa 3).
3. Nếu loại đơn là Phúc khảo, kiểm tra hạn chót nộp đơn (trong 7 ngày sau công bố điểm).
4. Đơn có lệ phí sẽ sinh hóa đơn. Phải thanh toán xong đơn mới chuyển Processing.
5. Quản nhiệm phê duyệt/từ chối, hệ thống gửi Email Noti. SV có quyền Hủy đơn khi đang Pending.

**③ Quy tắc nghiệp vụ áp dụng**

- **BR-026:** Tối đa 3 đơn cùng loại chưa xử lý (Pending/Processing).
- **BR-027:** Tuân thủ hạn chót.
- **BR-028:** Lưu log khi QN đổi trạng thái.
- **BR-029:** Chỉ hủy đơn khi đang ở trạng thái Pending.

### 5.6. Nhóm 06 — FS-QLSV-060-0010 — Thanh toán (Payment Gateway)

**① Mô tả & mục đích** Tích hợp cổng VNPay/MoMo để tự động hóa gạch nợ học phí, lệ phí đơn từ, phí học lại. Hỗ trợ kế toán đối soát.
**② Logic xử lý**

1. Hóa đơn Unpaid hiển thị trong cổng thanh toán của SV.
2. Tạo URL mã hóa theo cấu trúc của Gateway, đợi IPN Webhook trả về (Session 15 phút).
3. Webhook trả về: Checksum hợp lệ + Số tiền đúng → Chuyển TT hóa đơn sang Paid.
4. Quá hạn DueDate → Chuyển hóa đơn sang Overdue (thông qua Background Job daily).
5. Cho phép kế toán bấm Query Transaction thủ công để gạch nợ khi rớt Webhook.

**③ Quy tắc nghiệp vụ áp dụng**

- **BR-030:** Mã phiên 15 phút.
- **BR-031:** Trùng khớp số tiền 100%.
- **BR-032, BR-033, BR-034, BR-035:** Quyền xem báo cáo đối soát, gạch nợ phải lưu DB/Log rõ ràng.
- **BR-045, BR-046:** Chuyển Overdue và khóa chức năng SV liên quan khi nợ phí (chặn xem bảng điểm, chặn đăng ký).

### 5.7. Nhóm 07 — FS-QLSV-070-0010 — Đăng ký Học lại & Kỷ luật

**① Mô tả & mục đích** Số hóa quy trình xử lý môn trượt, tính lệ phí học lại tự động theo khoảng cách học kỳ, và khóa các tài khoản bị kỷ luật.
**② Logic xử lý**

1. SV chỉ được chọn môn đang ở trạng thái G3, G4, G5.
2. Với G4 (Thi lại): Chỉ đóng phí thi lại (20% đơn giá), chờ hệ thống xếp lịch thi.
3. Với G3/G5 (Học lại): Tính phí tự động. 50% nếu học lại ngay kỳ liền kề; 100% nếu cách ≥ 1 kỳ.
4. Trạng thái S5 (Đình chỉ): Chặn mọi quyền đăng ký và thông báo rõ thời hạn đình chỉ.
5. Hết đình chỉ (S5 → S1): Bị áp phí 150% đơn giá môn học do phạt kỷ luật.
6. Sau khi thanh toán phí học lại, hệ thống tự động xếp lớp. Nếu lớp đầy (CurrentSize = MaxCapacity), chuyển trạng thái SV vào Waitlisted.

**③ Quy tắc nghiệp vụ áp dụng**

- **BR-036, BR-037:** Chọn môn hợp lệ, phí 50% và 100% theo khoảng cách kỳ.
- **BR-038:** Chặn SV đang đình chỉ (S5). Không có ngoại lệ.
- **BR-039:** Thu phí phạt 150% với SV vừa hết hạn đình chỉ.
- **BR-040:** Tự động đưa vào Waitlist nếu lớp đầy.
- **BR-041, BR-043:** Thời hạn kỷ luật đình chỉ là 1 học kỳ. Tái phạm đình chỉ lần 2 → Buộc thôi học (S3).
- **BR-042:** Phí thi lại Final Exam (G4) là 20%.

### 5.8. Nhóm 08 — FS-QLSV-080-0010 — Notification Center

**① Mô tả & mục đích** Hệ thống thông báo In-app dành cho tất cả người dùng, lưu trữ và xóa tự động.
**② Logic xử lý**

1. Các Module khác phát sinh event (TKB đổi, Điểm mới, Phê duyệt đơn, Cảnh báo vắng, Hóa đơn mới), hệ thống tự sinh bản ghi Notification.
2. UI hiển thị chuông thông báo (đánh dấu Read/Unread).
3. Cronjob chạy ngầm xóa thông báo cũ (Quá hạn lưu trữ).

**③ Quy tắc nghiệp vụ áp dụng**

- **BR-047:** Thông báo lưu trữ tối đa 90 ngày, quá hạn hệ thống tự động xóa. Có thể đánh dấu "Đã đọc".

## CHƯƠNG 6. ĐẶC TẢ MÀN HÌNH CHÍNH

### 6.1. MH-GV-03 & MH-SV-03 — Màn hình Điểm danh

- **Màn chiếu GV:** Hiển thị QR Code kích thước lớn chiếm 80% màn hình, đếm ngược 10 giây bên dưới để refresh QR mới.
- **App SV:** Bật camera với vùng nhận diện định sẵn, hiện trạng thái “Thành công” nền xanh lá khi quét đúng mã hợp lệ. Ứng dụng PWA hỗ trợ trên mobile browser.

### 6.2. MH-QN-09 — Màn hình Chốt sổ điểm

- Danh sách SV với các cột điểm thành phần.
- Cột “Tổng” và “Trạng thái” (Passed/Failed) được tô đậm.
- Nút “Chốt sổ” yêu cầu xác nhận 2 lần. Sau khi chốt, Grid nhập điểm của GV bị khóa (Disabled).

### 6.3. MH-SV-08 — Đăng ký Học lại

- Hiển thị danh sách các môn ở trạng thái trượt (G3, G4, G5).
- Tùy chọn “Đăng ký thi lại” đối với G4, hiển thị phí 20%. Tùy chọn “Đăng ký học lại” đối với G3/G5 hiển thị phí 50%, 100% (hoặc 150% nếu có án kỷ luật).
- Bấm nút “Thanh toán” gọi đến Payment Gateway.

### 6.4. MH-KT-02 — Đối soát giao dịch (Kế toán)

- Hiển thị danh sách giao dịch, lọc theo Ngày và Trạng thái.
- Các giao dịch Pending có nút “Query API thủ công” bên cạnh để chủ động gọi lệnh tra soát lên cổng thanh toán.

### 6.5. MH-QN-11 — Quản lý Kỷ luật

- Giao diện tra cứu danh sách kỷ luật, thời gian hiệu lực.
- Form cập nhật đình chỉ: chọn SV, nhập lý do, thời gian (mặc định 1 học kỳ). Hệ thống chuyển đổi S1 -> S5.

## CHƯƠNG 7. MÁY TRẠNG THÁI HỒ SƠ

### 7.1. Trạng thái Sinh viên (TT-01)

| Mã | Trạng thái             | Điều kiện vào        | Chuyển tiếp được       |
| --- | ------------------------ | ------------------------ | --------------------------- |
| S0  | Mới (Initialized)       | Vừa Import              | → S1 (Khi gán lớp)       |
| S1  | Đang học (Active)      | Có lớp, đang học     | → S2, S3, S4, S5           |
| S2  | Bảo lưu (Suspended)    | Có QĐ tạm ngừng      | → S1 (Tái nhập), S3      |
| S3  | Thôi học (Dropped)     | Nghỉ học vĩnh viễn   | (Trạng thái cuối)        |
| S4  | Tốt nghiệp (Graduated) | Đủ điều kiện BR-044 | (Trạng thái cuối)        |
| S5  | Đình chỉ              | Vi phạm kỷ luật       | → S1 (Hết hạn 1 kỳ), S3 |

### 7.2. Trạng thái Bảng điểm Môn học (TT-09)

| Mã | Trạng thái         | Điều kiện vào                | Chuyển tiếp được                 |
| --- | -------------------- | -------------------------------- | ------------------------------------- |
| G0  | In Progress          | Đang theo học                  | → G1, G3, G4                         |
| G1  | Passed               | Vắng<20% & FE≥4.0 & Tổng≥5.0 | (Trạng thái cuối môn)             |
| G3  | Fail (Cấm thi)      | Vắng ≥ 20%                     | → G5 (Đăng ký học lại)          |
| G4  | Retake (Thi lại)    | FE<4.0 hoặc Tổng<5.0           | → G1 (Đạt), G5 (Trượt tiếp)     |
| G5  | Re-study (Học lại) | Từ G3 hoặc trượt G4          | → G0 (Đăng ký học lại kỳ mới) |

### 7.3. Trạng thái Đơn từ (TT-10)

| Trạng thái | Ý nghĩa                                 | Chuyển tiếp được                        |
| ------------ | ----------------------------------------- | -------------------------------------------- |
| Pending      | SV vừa nộp đơn                        | → Processing, Approved, Rejected, Cancelled |
| Processing   | Đang xử lý / Chờ thanh toán lệ phí | → Approved, Rejected                        |
| Approved     | QN đã duyệt                            | (Trạng thái cuối)                         |
| Rejected     | QN từ chối                              | (Trạng thái cuối)                         |
| Cancelled    | SV tự hủy                               | (Trạng thái cuối)                         |

### 7.4. Trạng thái Hóa đơn (TT-11)

| Trạng thái | Ý nghĩa                            | Chuyển tiếp được         |
| ------------ | ------------------------------------ | ----------------------------- |
| Unpaid       | Chưa thanh toán                    | → Paid, Overdue, Cancelled   |
| Paid         | Thanh toán thành công qua Gateway | (Trạng thái cuối)          |
| Overdue      | Quá hạn thanh toán                | → Paid (Nộp bù), Cancelled |
| Cancelled    | Hủy bỏ                             | (Trạng thái cuối)          |

### 7.5. Trạng thái Giao dịch (TT-12) & Đăng ký Học lại (TT-15)

- **TT-12 (Giao dịch)**: Pending → Success, Failed.
- **TT-15 (ĐK Học lại)**: Pending → Paid → Assigned / Waitlisted → Assigned. (Cancelled nếu SV tự hủy trước thanh toán).

## CHƯƠNG 8. QUY TẮC NGHIỆP VỤ & CHỐT CHẶN CỨNG

| Quy tắc (BR)        | Nội dung chốt chặn                                     | Áp dụng tại | Vì sao chặn là đúng                                                                |
| -------------------- | --------------------------------------------------------- | -------------- | --------------------------------------------------------------------------------------- |
| **BR-001/002** | Mã SV, CCCD, Email phải duy nhất                       | FS-QLSV-010    | Tránh nhầm lẫn dữ liệu giữa hai người.                                          |
| **BR-003**     | Bảo lưu/Thôi học lập tức bị gỡ khỏi lớp         | QT-02          | SV đã thôi học không được phép tồn tại trong TKB và danh sách điểm danh. |
| **BR-007**     | Không thiết lập vòng lặp tiên quyết                | QT-04          | Đảm bảo tính liền mạch của chương trình đào tạo.                           |
| **BR-017**     | Vắng ≥ 20% chốt Fail thẳng                            | FS-QLSV-030    | Tuân thủ tuyệt đối quy chế đào tạo, không có ngoại lệ cảm tính.          |
| **BR-020**     | Sau “Chốt sổ”, GV không được sửa điểm          | FS-QLSV-040    | Đảm bảo tính toàn vẹn của bảng điểm cuối kỳ đã công bố.                 |
| **BR-026**     | SV chỉ nộp tối đa 3 đơn Pending/Processing          | QT-10          | Chống Spam hệ thống và giúp QN xử lý tập trung.                                 |
| **BR-030/031** | Session 15 phút, số tiền khớp 100%                    | QT-11          | Đảm bảo an toàn thanh toán, tránh sai sót/gian lận tài chính.                 |
| **BR-038**     | Chặn đăng ký với SV đình chỉ (S5)                 | QT-13          | Chấp hành quy chế kỷ luật nghiêm khắc.                                           |
| **BR-044**     | Xét Tốt nghiệp: Pass hết, trả nợ hết, không ở S5 | QT-02          | Điều kiện tiên quyết để nhận bằng cử nhân.                                   |
| **BR-046**     | SV có Overdue bị chặn đăng ký & xem điểm          | QT-11/13       | Bắt buộc hoàn thành nghĩa vụ tài chính với trường.                           |

## CHƯƠNG 9. QUY TẮC KIỂM TRA DỮ LIỆU (VALIDATION)

| Mã         | Quy tắc kiểm tra                                      | Mức xử lý                                                                                      |
| ----------- | ------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| VLD-QLSV-01 | Trùng lặp CCCD/Email/MSSV khi import                  | **CHẶN**, highlight dòng lỗi                                                             |
| VLD-QLSV-02 | Lớp học vượt quá sĩ số tối đa (MaxCapacity)    | **CHẶN**, đưa vào danh sách chờ                                                       |
| VLD-QLSV-03 | Quét QR Code đã quá hạn 10s                        | **CHẶN**, yêu cầu quét lại                                                             |
| VLD-QLSV-04 | GV sửa điểm thành phần ngoài dải 0.0 - 10.0      | **CHẶN**, viền ô màu đỏ                                                               |
| VLD-QLSV-05 | Admin sửa điểm sau chốt sổ mà không nhập Lý do | **CHẶN**, popup cảnh báo yêu cầu nhập Log                                             |
| VLD-QLSV-06 | Mật khẩu tài khoản không đủ độ mạnh           | **CHẶN**, hiển thị thông báo format đúng (≥ 8 ký tự, 1 hoa, 1 số, 1 đặc biệt) |
| VLD-QLSV-07 | Deadlock vòng lặp môn tiên quyết                   | **CHẶN** lưu môn học                                                                    |

## CHƯƠNG 10. TÍCH HỢP & SỰ KIỆN

| Chiều tích hợp                        | Nội dung                                           | Dữ liệu giao tiếp                     | Ghi chú                            |
| ---------------------------------------- | --------------------------------------------------- | ---------------------------------------- | ----------------------------------- |
| **Hệ thống → VNPay/MoMo**       | Thanh toán học phí, lệ phí                     | URL Thanh toán (Checksum, Số tiền)    | SSL/TLS, Secret Key                 |
| **VNPay/MoMo → Hệ thống**       | Trả kết quả (Webhook/IPN)                        | Mã giao dịch, Trạng thái thanh toán | Gạch nợ tự động (QT-11)        |
| **Hệ thống → Mailing Service**  | Gửi Email cảnh báo vắng, kết quả duyệt đơn | Địa chỉ Email, Nội dung HTML         | Xử lý hàng đợi bất đồng bộ |
| **Google/Microsoft → Hệ thống** | Đăng nhập SSO                                    | Mã token SSO (Email)                    | Giới hạn miền @fpt.edu.vn        |

### Sự kiện hệ thống (Events)

- EVT-STUDENT-ATTENDANCE-FAILED: Kích hoạt khi SV chạm mốc vắng 20%, hệ thống chốt G3 và gửi Email.
- EVT-PAYMENT-SUCCESS: Kích hoạt khi nhận Webhook thành công, tự động gạch nợ và đổi trạng thái Hóa đơn sang “Paid”.
- EVT-NOTIFICATION-CREATED: Kích hoạt gửi noti in-app và qua email khi có tác vụ cần người dùng chú ý.

## CHƯƠNG 11. DANH MỤC THÔNG BÁO LỖI (ERRORS)

| Mã lỗi              | Điều kiện                                     | Loại                             |
| --------------------- | ------------------------------------------------ | --------------------------------- |
| **ERR-QLSV-01** | Trùng lặp Mã SV/CCCD khi import danh sách    | Chặn lưu                        |
| **ERR-QLSV-02** | Xếp GV dạy 2 lớp trùng Slot / Trùng phòng  | Chặn lưu (Xung đột TKB)       |
| **ERR-QLSV-03** | GV báo nghỉ sát giờ (Cách < 12 tiếng)      | Chặn báo nghỉ trên app        |
| **ERR-QLSV-04** | SV quét QR Code ngoài hệ thống / Fake QR     | Chặn giải mã                   |
| **ERR-QLSV-05** | Checksum VNPay trả về không khớp             | Cảnh báo Admin, Chặn gạch nợ |
| **ERR-QLSV-06** | Sinh viên trong trạng thái S5 đăng ký học | Chặn lệnh, Cảnh báo kỷ luật |

## CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR ĐO ĐƯỢC)

| Nhóm                 | Mã NFR | Yêu cầu                                        | Cách đo kiểm / Ngưỡng                         |
| --------------------- | ------- | ------------------------------------------------ | -------------------------------------------------- |
| **Hiệu năng** | NFR-01  | Thời gian đăng nhập & cấp Token             | ≤ 1 giây                                         |
| **Tốc độ**   | NFR-04  | Thời gian chạy xếp TKB tự động             | Chạy giả lập 200 SV & 10 GV, hoàn tất ≤ 30s  |
| **Tốc độ**   | NFR-07  | Xác thực QR Code phản hồi                    | Test tải 200 SV quét đồng thời, ≤ 2 giây    |
| **Tốc độ**   | NFR-07b | Tính điểm 200 SV                              | ≤ 30 giây                                        |
| **Toàn vẹn**  | NFR-16  | Mật khẩu tài khoản phải Hash một chiều    | Bcrypt/Argon2, truy vấn DB rà soát bản rõ     |
| **Bảo mật**   | NFR-15  | Giao dịch Payment qua SSL/TLS                   | Kiểm tra config chứng chỉ số HTTPS             |
| **Truy vết**   | NFR-19  | Không có chức năng xóa Log trên giao diện | Rà soát phân quyền DB, bắt buộc ghi log 100% |
| **Vận hành**  | NFR-18  | Concurrent Users                                 | Hỗ trợ 200 SV điểm danh cùng lúc             |
| **Vận hành**  | NFR-20  | Backup Data                                      | Daily backup, lưu trữ 30 ngày                   |

## CHƯƠNG 13. MA TRẬN TRUY VẾT & NGHIỆM THU

### Tiêu chí nghiệm thu (Acceptance Criteria)

| Mã                  | Tiêu chí nghiệm thu                                                                                            | Đặc tả tại     |
| -------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------ |
| **NT-QLSV-01** | Nhập danh sách SV thành công, không trùng CCCD/Mã SV.                                                      | QT-01, VLD-QLSV-01 |
| **NT-QLSV-02** | Thuật toán xếp lịch chạy ra TKB không có xung đột (Conflict) phòng/GV.                                  | QT-05              |
| **NT-QLSV-03** | QR Code điểm danh refresh mỗi 10s, chặn các phần mềm quét ngoài.                                         | QT-07, FS-QLSV-030 |
| **NT-QLSV-04** | Hệ thống tự động chuyển trạng thái môn G1/G3/G4/G5 chuẩn xác theo % vắng và FE.                      | QT-09, FS-QLSV-040 |
| **NT-QLSV-05** | Thanh toán thành công qua IPN VNPay tự động chuyển Hóa đơn sang Paid. Mất webhook có Query gạch tay. | QT-11, FS-QLSV-060 |
| **NT-QLSV-06** | SV bị đình chỉ (S5) tuyệt đối không thể đăng ký học lại. SV G3 đăng ký bị tính phí 50/100%.   | QT-13, FS-QLSV-070 |
| **NT-QLSV-07** | Đơn từ bị giới hạn nộp, QN duyệt có email gửi.                                                          | QT-10, FS-QLSV-050 |

_(Tài liệu được trích xuất và chuẩn hóa từ BRD Quản Lý Sinh Viên v4.0 theo khung sườn FSD v1.0)_
