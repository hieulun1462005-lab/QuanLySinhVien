**TÀI LIỆU ĐẶC TẢ CHỨC NĂNG**

**FUNCTIONAL SPECIFICATION DOCUMENT (FSD)**

**PHÂN HỆ QLSV — HỆ THỐNG QUẢN LÝ SINH VIÊN**

_Tự động hóa & Khách quan · Real-time & Đồng bộ · Truy vết toàn diện_

| **Thuộc tính** | **Nội dung** |
| --- | --- |
| Mã phân hệ | QLSV (Gồm QLSV-01 đến QLSV-08) |
| Tên phân hệ | Hệ thống Quản lý Sinh viên |
| Loại tài liệu | FSD — Đặc tả chức năng |
| Phạm vi | Đặc tả field-level các nhóm chức năng cốt lõi: Xác thực & Tài khoản, Hồ sơ & Phân lớp, Đào tạo & TKB, Điểm danh QR động, Quản lý Điểm & Khảo thí, Dịch vụ Hành chính, Thanh toán, Học lại & Kỷ luật, Notification Center. |
| Thực thể sở hữu | TT-00 Tài khoản, TT-01 Hồ sơ SV, TT-02 Lớp, TT-03 Giảng viên, TT-04 Môn học, TT-05 Chuyên ngành, TT-06 TKB, TT-07/08 Điểm danh, TT-09 Bảng điểm, TT-10 Đơn từ, TT-11 Hóa đơn, TT-12 Giao dịch, TT-15 ĐK Học lại, TT-18 Thông báo, TT-20 Cấu hình tỷ trọng |
| Tài liệu nguồn | BRD-QLSV-v5.3 & Bộ Mockup Giao diện chuẩn (41 file HTML + 1 CSV) |
| Ranh giới chính | QLSV sở hữu TÀI KHOẢN, HỒ SƠ HỌC TẬP, QUY TRÌNH ĐÀO TẠO của Sinh viên. KHÔNG sở hữu dữ liệu tuyển sinh, không tính lương giảng viên. |
| Phiên bản | 3.1 (Cập nhật theo BRD v5.3 & Cấu trúc Mockup mới nhất) |
| Ngày phát hành | 28/09/2026 |
| Đơn vị xây dựng | ONENET |

# **KIỂM SOÁT TÀI LIỆU**

| **Phiên bản** | **Ngày** | **Người thực hiện** | **Nội dung** |
| --- | --- | --- | --- |
| 1.0 | 18/09/2026 | Khảo sát BA | Khởi tạo tài liệu Draft ban đầu. |
| 2.0 | 21/09/2026 | Team Dev | Đặc tả kỹ thuật các luồng chức năng theo BRD v4.0. |
| 2.1 | 23/09/2026 | BA & Team Dev | Chuẩn hóa FSD theo khuôn 13 chương / mẫu 10 mục của Template chuẩn. Mapping lại toàn bộ mã định danh theo BRD v5.0. |
| 3.0 | 28/09/2026 | BA & Team Dev | **Cập nhật toàn diện**: Bổ sung đầy đủ 8 nhóm chức năng, đặc tả field-level cho tất cả 36+ màn hình, validation rules chi tiết, error codes, state machines, tích hợp hoàn chỉnh với BRD v5.0 và Mockup. |
| 3.1 | 02/10/2026 | BA & Team Dev | Đối chiếu FSD với 41 file Mockup: bổ sung MH-01-8-HoSoSinhVien, MH-02-1-1/MH-02-1-2/MH-02-1-3 (trang con danh mục GV/Chuyên ngành/Môn học). Cập nhật đặc tả UI Chương 6 cho 4 MH mới. Đồng bộ với BRD v5.3. |

_Vị trí trong bộ tài liệu: FSD này là cầu nối giữa BRD (nghiệp vụ) và mã nguồn. Mọi ràng buộc (BR), mã lỗi (ERR), luồng ngoại lệ đều được dịch thành quy tắc xử lý phần mềm, đặc biệt tập trung vào máy trạng thái và các thuật toán lõi (QR động, xét điểm tự động)._

# **CHƯƠNG 1. GIỚI THIỆU**

## **1.1. Mục đích tài liệu**

Dựa trên BRD-QLSV-v5.0 và hệ thống giao diện Mockup (36+ file HTML), tài liệu FSD này đặc tả chi tiết cách hệ thống thực hiện các nghiệp vụ: xác thực & quản lý tài khoản phân quyền, quản lý hồ sơ sinh viên xuyên suốt, đào tạo và thời khóa biểu, điểm danh bằng QR Động (real-time), tự động xét điều kiện điểm số, dịch vụ sinh viên trực tuyến, tích hợp thanh toán, đăng ký học lại/thi lại, và hệ thống thông báo.

## **1.2. Ba nguyên tắc chi phối cả tài liệu**

| **Nguyên tắc** | **Nghĩa cụ thể** | **Vì sao** |
| --- | --- | --- |
| **Tự động hóa & Khách quan** | Điểm danh tự động qua QR; hệ thống tự tính điểm tổng kết và xét Đạt/Trượt/Cấm thi. Xếp lịch học, tính lệ phí học lại tự động. | Tránh sai sót thủ công và đảm bảo sự công bằng, minh bạch tối đa trong đào tạo. |
| **Real-time & Đồng bộ** | Thay đổi trạng thái học tập lập tức chặn đăng nhập và gỡ khỏi lớp; QR điểm danh làm mới 10s/lần. | Sinh viên bảo lưu/thôi học không được phép tiếp tục truy cập dữ liệu; QR động chống gian lận điểm danh hộ. |
| **Truy vết toàn diện (Audit Trail)** | Mọi sửa đổi điểm sau chốt, sửa điểm danh thủ công, duyệt đơn từ đều được ghi Log (Who, When, Old/New). | Quyết định liên quan đến điểm số, tài chính và bằng cấp không được phép thay đổi mà không có dấu vết giải trình. |

## **1.3. Ngoài phạm vi**

| **Việc** | **Thuộc phân hệ / Trạng thái** |
| --- | --- |
| Việc Tuyển sinh đầu vào | Nằm ngoài hệ thống, hệ thống chỉ nhận data đầu vào. |
| Quản lý Nhân sự & Lương Giảng viên | Không thuộc phạm vi, hệ thống chỉ xếp lịch dạy. |
| Native Mobile App (iOS/Android) | Hệ thống sử dụng Progressive Web App (PWA). |

## **1.4. Định nghĩa vai trò người dùng (Actors)**

| **Mã** | **Vai trò** | **Mô tả** | **Quyền chính** |
| --- | --- | --- | --- |
| VT-00 | Admin hệ thống | Quản trị viên tổng, toàn quyền | CRUD tài khoản, nhật ký, backup/restore, sửa điểm sau chốt |
| VT-01 | Cán bộ Quản nhiệm (QN) | Quản nhiệm học tập & tài chính | Import SV, phân lớp, xếp TKB, duyệt đơn, tra soát giao dịch, gạch nợ thủ công, xem báo cáo |
| VT-02 | Giảng viên (GV) | Giảng viên cơ hữu/thỉnh giảng | Mở QR điểm danh, nhập điểm, báo nghỉ/bù, xem lịch dạy |
| VT-03 | Sinh viên (SV) | Sinh viên đang học | Quét QR, xem TKB/điểm/lịch thi, nộp đơn, thanh toán |

# **CHƯƠNG 2. QUY ƯỚC, KÝ HIỆU & MÃ ĐỊNH DANH**

| **Ký hiệu** | **Ý nghĩa** | **Ví dụ** |
| --- | --- | --- |
| FS-QLSV-xxx-xxxx | Mã chức năng đặc tả | FS-QLSV-03-100-0010 |
| TTxx-Sxx/Gxx | Trạng thái thực thể (Sinh viên, Bảng điểm) | S1 (Đang học), G1 (Đạt) |
| VLD-QLSV-xx | Quy tắc kiểm tra dữ liệu | VLD-QLSV-06 |
| ERR-QLSV-xx | Mã thông báo lỗi | ERR-QLSV-14 |
| TC-QLSV-xx | Ca kiểm thử của FSD | TC-QLSV-01 |
| NT-QLSV-xx | Tiêu chí nghiệm thu (Từ BRD) | UC-01.NT01 |
| MH-xx-x | Mã màn hình giao diện (Mockup) | MH-01-2 |
| BR-xxx | Quy tắc nghiệp vụ (Business Rule) | BR-017 |
| FLD-xxx-xxx | Mã trường dữ liệu (Field) | FLD-STUDENT-ID |

# **CHƯƠNG 3. TỔNG QUAN CHỨC NĂNG & MÀN HÌNH**

## **3.1. Nhóm chức năng chính**

| **Nhóm** | **Tên nhóm** | **Vai trò** | **Đặc tả chi tiết tại** |
| --- | --- | --- | --- |
| QLSV-00-100 | Xác thực & Quản lý Tài khoản | Admin, Tất cả | FS-QLSV-00-100-0010 |
| QLSV-01-100 | Quản lý Sinh viên & Học tập (Tạo hồ sơ, Phân lớp) | Cán bộ Quản nhiệm (QN) | FS-QLSV-01-100-0010 |
| QLSV-02-100 | Đào tạo & Thời khóa biểu (Danh mục, CTĐT, TKB) | Quản nhiệm, GV, SV | FS-QLSV-02-100-0010 |
| QLSV-03-100 | Điểm danh bằng QR Động | Giảng viên, SV | FS-QLSV-03-100-0010 |
| QLSV-04-100 | Điểm & Khảo thí (Nhập điểm, Tự động xét Đạt/Trượt) | Giảng viên, Admin | FS-QLSV-04-100-0020 |
| QLSV-05-100 | Dịch vụ Sinh viên (Đơn từ, Hành chính, Hồ sơ) | SV, QN, GV | FS-QLSV-05-100-0010 |
| QLSV-06-100 | Thanh toán (Payment Gateway) | SV, Quản nhiệm | FS-QLSV-06-100-0010 |
| QLSV-07-100 | Đăng ký học lại/thi lại & Kỷ luật | SV, Quản nhiệm | FS-QLSV-07-100-0010 |
| QLSV-08-100 | Notification Center (Thông báo & Email) | Tất cả Users | FS-QLSV-08-100-0010 |

## **3.2. Danh Mục Màn Hình Giao Diện (Từ Mockup)**

### **3.2.1. Nhóm Admin (MH_Admin_Mockup)**

| **Mã MH** | **Tên màn hình** | **Vai trò** | **Module** |
| --- | --- | --- | --- |
| MH-00-1 | Tổng Quan Hệ Thống | Admin | Dashboard |
| MH-00-2 | Quản Lý Tài Khoản | Admin | QLSV-00 |
| MH-00-3 | Nhật Ký Hệ Thống (Audit Log) | Admin | Dashboard |
| MH-00-4 | Backup & Restore DB | Admin | Dashboard |

### **3.2.2. Nhóm Chung (MH_Chung_Mockup)**

| **Mã MH** | **Tên màn hình** | **Vai trò** | **Module** |
| --- | --- | --- | --- |
| MH-00-5 | Đăng Nhập Admin | Admin | QLSV-00 |
| MH-00-6 | Đăng Nhập Hệ Thống (GV/SV/QN) | Cán Bộ/GV/SV | QLSV-00 |

### **3.2.3. Nhóm Quản nhiệm (MH_QN_Mockup)**

| **Mã MH** | **Tên màn hình** | **Vai trò** | **Module** |
| --- | --- | --- | --- |
| MH-00-7 | Dashboard Báo Cáo | Cán bộ Quản nhiệm (QN) | Dashboard |
| MH-01-1 | Danh Sách Trúng Tuyển | Cán bộ Quản nhiệm (QN) | QLSV-01 |
| MH-01-2 | Tiếp Nhận Hồ Sơ Sinh Viên | Cán bộ Quản nhiệm (QN) | QLSV-01 |
| MH-01-3 | Cập Nhật Trạng Thái Học Tập | Cán bộ Quản nhiệm (QN) | QLSV-01 |
| MH-01-4 | Phân Bổ Sinh Viên Vào Lớp | Cán bộ Quản nhiệm (QN) | QLSV-01 |
| MH-01-5 | Danh Sách Lớp | Cán bộ Quản nhiệm (QN) | QLSV-01 |
| MH-01-8 | Hồ Sơ Sinh Viên Toàn Trường | Cán bộ Quản nhiệm (QN) | QLSV-01 |
| MH-02-1 | Quản Lý Danh Mục (Hub — GV, Chuyên ngành, Môn học) | Cán bộ Quản nhiệm (QN) | QLSV-02 |
| MH-02-1-1 | Quản Lý Giảng Viên (Chi tiết) | Cán bộ Quản nhiệm (QN) | QLSV-02 |
| MH-02-1-2 | Quản Lý Chuyên Ngành (Chi tiết) | Cán bộ Quản nhiệm (QN) | QLSV-02 |
| MH-02-1-3 | Quản Lý Môn Học (Chi tiết) | Cán bộ Quản nhiệm (QN) | QLSV-02 |
| MH-02-2 | Khung Chương Trình Học | Cán bộ Quản nhiệm (QN) | QLSV-02 |
| MH-02-3 | Xếp Thời Khóa Biểu | Cán bộ Quản nhiệm (QN) | QLSV-02 |
| MH-02-4 | Quản Lý Yêu Cầu Báo Nghỉ / Lịch Bù | Cán bộ Quản nhiệm (QN) | QLSV-02 |
| MH-05-1 | Hồ Sơ Cán Bộ Quản Nhiệm | Cán bộ Quản nhiệm (QN) | QLSV-05 |
| MH-05-2 | Phê Duyệt Đơn Từ Sinh Viên | Cán bộ Quản nhiệm (QN) | QLSV-05 |
| MH-06-1 | Lịch Sử Giao Dịch | Cán bộ Quản nhiệm (QN) | QLSV-06 |

### **3.2.4. Nhóm Giảng viên (MH_GV_Mockup)**

| **Mã MH** | **Tên màn hình** | **Vai trò** | **Module** |
| --- | --- | --- | --- |
| MH-00-8 | Tổng Quan Giảng Viên | Giảng viên | Dashboard |
| MH-02-5 | Lịch Giảng Dạy & Báo Nghỉ | Giảng viên | QLSV-02 |
| MH-03-1 | Điểm Danh Lớp Học (QR Động) | Giảng viên | QLSV-03 |
| MH-04-1 | Cập Nhật Điểm Quá Trình | Giảng viên | QLSV-04 |
| MH-05-3 | Quản Lý Hồ Sơ Giảng Viên | Giảng viên | QLSV-05 |

### **3.2.5. Nhóm Sinh viên (MH_SV_Mockup)**

| **Mã MH** | **Tên màn hình** | **Vai trò** | **Module** |
| --- | --- | --- | --- |
| MH-00-9 | Tổng Quan Học Tập (Dashboard SV) | Sinh viên | Dashboard |
| MH-02-6 | Thời Khóa Biểu | Sinh viên | QLSV-02 |
| MH-03-2 | Báo Cáo Điểm Danh | Sinh viên | QLSV-03 |
| MH-03-3 | Lịch Học Trong Ngày & QR Scanner (PWA) | Sinh viên | QLSV-03 |
| MH-04-1b | Chương Trình Đào Tạo | Sinh viên | QLSV-04 |
| MH-04-2 | Kết Quả Học Tập (Bảng điểm) | Sinh viên | QLSV-04 |
| MH-04-3 | Lịch Thi | Sinh viên | QLSV-04 |
| MH-05-4 | Quản Lý Hồ Sơ Cá Nhân | Sinh viên | QLSV-05 |
| MH-05-5 | Dịch Vụ Hành Chính Một Cửa | Sinh viên | QLSV-05 |
| MH-06-2 | Hóa Đơn & Thanh Toán | Sinh viên | QLSV-06 |

# **CHƯƠNG 4. ĐẶC TẢ LUỒNG NGHIỆP VỤ**

## **4.1. Quy trình Đăng nhập & Phân quyền**

| **Bước** | **Việc** | **Vai trò** | **Kết quả** |
| --- | --- | --- | --- |
| QT-00-1 | Người dùng nhập Username/Password tại **MH-00-5** hoặc **MH-00-6** | Tất cả | Xác thực |
| QT-00-2 | Hệ thống verify hash password (Bcrypt/Argon2). Check trạng thái tài khoản (Active/Locked/Disabled) | Hệ thống | Pass/Fail |
| QT-00-3 | Kiểm tra số lần sai liên tiếp. Nếu ≥ 5 → Khóa 15 phút (BR-049) | Hệ thống | Lockout |
| QT-00-4 | Cấp JWT Token + Refresh Token. Redirect theo Role | Hệ thống | Dashboard |
| QT-00-5 | (Tùy chọn) Đăng nhập bằng Google OAuth 2.0 — Chỉ tại **MH-00-6** | GV/SV | SSO |

## **4.2. Quy trình Tiếp nhận & Phân lớp Sinh viên**

| **Bước** | **Việc** | **Vai trò** | **Trạng thái** |
| --- | --- | --- | --- |
| QT-01-1 | QN xem danh sách trúng tuyển (từ nguồn ngoài) trên **MH-01-1** | Cán bộ Quản nhiệm (QN) | —   |
| QT-01-2 | QN tra cứu / nhập thủ công hồ sơ SV mới trên **MH-01-2** | Cán bộ Quản nhiệm (QN) | S0 (Initialized) |
| QT-01-3 | Hệ thống validate Unique (CCCD, Email). Lưu SV trạng thái S0 | Hệ thống | S0  |
| QT-01-4 | QN phân bổ SV vào lớp trên **MH-01-4**. Check MaxCapacity | Cán bộ Quản nhiệm (QN) | S0 → S1 (Active) |
| QT-01-5 | Hệ thống tự động tạo tài khoản, gửi email thông tin đăng nhập | Hệ thống | Tạo TT-00 |

## **4.3. Quy trình Xét điều kiện dự thi & Tổng kết điểm**

| **Bước** | **Việc** | **Vai trò** | **Trạng thái** |
| --- | --- | --- | --- |
| QT-04-1 | Hệ thống quét tỷ lệ vắng mặt: Nếu ≥ 20% → Chốt CẤM THI | Hệ thống | G0 → G3 (Fail) |
| QT-04-2 | Vắng < 20%: Tính Tổng điểm theo tỷ trọng thành phần | Hệ thống | G0 (In Progress) |
| QT-04-3 | Quét điều kiện liệt: FE < 4.0 HOẶC Tổng < 5.0 → Chốt THI LẠI | Hệ thống | G0 → G4 (Retake) |
| QT-04-4 | Xét ĐK học lại: Đang G4 mà thi lại FE vẫn trượt → Chốt HỌC LẠI | Hệ thống | G4 → G5 (Re-study) |
| QT-04-5 | SV thỏa mãn (Vắng < 20%, FE ≥ 4.0, Tổng ≥ 5.0) → Chốt ĐẠT | Hệ thống | G0/G4 → G1 (Passed) |

## **4.4. Quy trình Nộp đơn & Phê duyệt**

| **Bước** | **Việc** | **Vai trò** | **Trạng thái đơn** |
| --- | --- | --- | --- |
| QT-05-1 | SV chọn loại dịch vụ trên **MH-05-5** (Nghỉ học, Phúc khảo, Bảng điểm, Miễn giảm HP…) | SV  | —   |
| QT-05-2 | SV điền lý do, đính kèm file (nếu có), xác nhận gửi | SV  | Pending |
| QT-05-3 | Hệ thống kiểm tra phí dịch vụ, tạo hóa đơn nếu có phí | Hệ thống | Tạo TT-11 |
| QT-05-4 | QN xem đơn trên **MH-05-2**, filter theo trạng thái/loại đơn | QN  | —   |
| QT-05-5 | QN mở chi tiết, nhập phản hồi, chọn Phê duyệt/Từ chối | QN  | Approved/Rejected |
| QT-05-6 | Hệ thống gửi email kết quả cho SV (≤ 1 phút) | Hệ thống | Email sent |

## **4.5. Quy trình Thanh toán trực tuyến**

| **Bước** | **Việc** | **Vai trò** | **Trạng thái** |
| --- | --- | --- | --- |
| QT-06-1 | SV xem danh sách hóa đơn Unpaid trên **MH-06-2** | SV  | —   |
| QT-06-2 | SV chọn cổng thanh toán (VNPay/MoMo), hệ thống gen phiên 15p | Hệ thống | Pending |
| QT-06-3 | Redirect sang cổng thanh toán, SV thanh toán | SV  | —   |
| QT-06-4 | VNPay/MoMo gọi IPN Webhook. Hệ thống verify HMAC SHA512 | Hệ thống | —   |
| QT-06-5 | Khớp số tiền 100% → Hóa đơn Paid, Giao dịch Success | Hệ thống | Paid/Success |
| QT-06-6 | Background job hàng ngày quét hóa đơn quá DueDate → Overdue | Hệ thống | Overdue |
| QT-06-7 | Quản nhiệm tra soát trên **MH-06-1** nếu Webhook rớt | Cán bộ Quản nhiệm (QN) | Manual reconcile |

## **4.6. Luồng Ngoại lệ & Sự cố thường gặp**

| **Mã** | **Tình huống** | **Cách xử lý** |
| --- | --- | --- |
| NL-01 | **Gian lận QR:** Sinh viên dùng app ngoài quét hộ. | Chặn hoàn toàn. Token mã hóa (AES-256) chỉ app PWA giải mã được. Kết hợp check IP nội bộ (BR-016). |
| NL-02 | **Mất kết nối mạng:** Không quét được QR. | GV điểm danh thủ công qua cột “Điểm danh tay” trên **MH-03-1**. Bắt buộc nhập Lý do sửa vào ô input. Ghi Log giải trình. |
| NL-03 | **Payment rớt Webhook:** Tiền trừ nhưng hệ thống không gạch nợ. | Quản nhiệm sử dụng nút “Query Transaction” trên **MH-06-1** để gọi API vnp_Querydr của VNPay và đồng bộ lại. Ghi Audit Log. |
| NL-04 | **Quá sĩ số lớp:** Phân lớp vượt MaxCapacity. | Chặn gán vào lớp trên **MH-01-4**, đưa SV vào danh sách Waitlisted (S0). |
| NL-05 | **Trùng slot GV/Phòng khi xếp TKB.** | Chặn lưu TKB trên **MH-02-3**. Hiển thị ERR-QLSV-02 (Xung đột GV hoặc Phòng). |
| NL-06 | **SV bị đình chỉ (S5) cố tính đăng ký học lại.** | Chặn lệnh, hiển thị ERR-QLSV-06 (badge đỏ). |

# **CHƯƠNG 5. ĐẶC TẢ CHI TIẾT CHỨC NĂNG**

## **5.0. Nhóm 00-100 — Xác thực & Quản lý Tài khoản**

### **FS-QLSV-00-100-0010 — Đăng nhập & Phân quyền**

**① Mô tả & mục đích** Cung cấp cổng đăng nhập phân luồng theo vai trò (Admin riêng, GV/SV/QN chung), xác thực bảo mật, cấp JWT Token và điều hướng đến Dashboard phù hợp.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân: Tất cả người dùng.
- Tiền điều kiện: Tài khoản đã tồn tại trong hệ thống, trạng thái Active.
- Kích hoạt: Truy cập URL đăng nhập. Admin vào **MH-00-5**, các vai trò khác vào **MH-00-6**.

**③ Logic xử lý**

1.  Nhận username + password từ form đăng nhập.
2.  Truy vấn TT-00 theo username. Nếu không tồn tại → ERR-QLSV-07.
3.  Kiểm tra AccountStatus:
    - Locked → ERR-QLSV-08 (“Tài khoản bị khóa, vui lòng liên hệ Admin”).
    - Disabled → ERR-QLSV-09 (“Tài khoản bị vô hiệu hóa”).
4.  So sánh hash(password) với PasswordHash (Bcrypt/Argon2). Nếu sai → tăng FailedAttempts.
5.  Nếu FailedAttempts >= 5 → Khóa 15 phút (BR-049). Set LockedUntil = Now + 15m.
6.  Nếu pass → Reset FailedAttempts = 0. Cấp JWT Access Token (expire 30m) + Refresh Token (expire 7d).
7.  Redirect:
    - Admin → **MH-00-1** (Dashboard hệ thống)
    - QN → **MH-00-7** (Dashboard báo cáo)
    - GV → **MH-00-8** (Dashboard giảng viên)
    - SV → **MH-00-9** (Dashboard học tập)
8.  (MH-00-6 only) Đăng nhập Google OAuth 2.0: Xác thực qua Google → lấy email → match với email trong TT-00. Giới hạn domain (BR-050).

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** | **Ghi chú** |
| --- | --- | --- | --- | --- |
| FLD-ACC-USERNAME | String(50) | ✱   | Unique, Not blank, 4-50 ký tự | Mã số SV/GV hoặc username Admin |
| FLD-ACC-PASSWORD | String | ✱   | VLD-QLSV-06 (Min 8 ký tự, 1 hoa, 1 số, 1 đặc biệt) | Lưu trữ dạng hash, không bao giờ lưu bản rõ |
| FLD-ACC-ROLE | Enum | ✱   | Admin / QuanNhiem / GiangVien / SinhVien | —   |
| FLD-ACC-STATUS | Enum | ✱   | Active / Locked / Disabled | —   |
| FLD-ACC-FAILED-ATTEMPTS | Int | —   | 0-5 | Reset về 0 khi login thành công |
| FLD-ACC-LOCKED-UNTIL | DateTime | —   | Nullable | Set khi bị khóa do spam login |
| FLD-ACC-REMEMBER | Bool | —   | —   | Checkbox “Ghi nhớ đăng nhập” (MH-00-5, MH-00-6) |
| FLD-ACC-LAST-LOGIN | DateTime | —   | Auto-set | Thời gian đăng nhập gần nhất |

**⑤ Quy tắc nghiệp vụ áp dụng**

- **BR-048**: Mật khẩu phải ≥ 8 ký tự, chứa ít nhất 1 chữ hoa, 1 số, 1 ký tự đặc biệt.
- **BR-049**: Khóa tài khoản 15 phút sau 5 lần đăng nhập sai liên tiếp.
- **BR-050**: SSO Google chỉ chấp nhận email thuộc domain cho phép (@onenet.edu.vn).

**⑥ Hành vi màn hình**

- **MH-00-5** (Admin): Form đơn giản gồm Username, Password, checkbox Ghi nhớ, nút Đăng nhập. Có link “Quay lại Đăng nhập chung” → MH-00-6.
- **MH-00-6** (Chung): Form Username, Password, checkbox Ghi nhớ, nút Đăng nhập + nút “Đăng nhập bằng Google” (icon Google SVG). Dấu phân cách “hoặc” giữa 2 phương thức.
- Toggle hiển thị mật khẩu: Click icon eye-off → chuyển input type text/password.
- Nền login: Glassmorphism card trên background gradient + ảnh campus.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Thông báo** | **Loại** |
| --- | --- | --- | --- |
| ERR-QLSV-07 | Tài khoản không tồn tại | “Tên đăng nhập hoặc mật khẩu không đúng” | Inline form |
| ERR-QLSV-08 | Tài khoản bị Locked | “Tài khoản bị khóa tạm thời. Vui lòng thử lại sau 15 phút.” | Alert |
| ERR-QLSV-09 | Tài khoản Disabled (SV S3/S5) | “Tài khoản đã bị vô hiệu hóa. Liên hệ phòng Đào tạo.” | Alert |
| ERR-QLSV-10 | Email Google không thuộc domain cho phép | “Email không thuộc hệ thống. Vui lòng sử dụng email @onenet.edu.vn” | Alert |

**⑧ Hậu điều kiện & đầu ra**

- Người dùng được cấp JWT, redirect đúng Dashboard.

**⑨ Sự kiện phát sinh**

- EVT-LOGIN-SUCCESS: Ghi log IP, UserAgent, Timestamp.
- EVT-LOGIN-FAILED: Ghi log lần sai, IP.
- EVT-ACCOUNT-LOCKED: Ghi log lockout event.

**⑩ Truy vết & nghiệm thu**

- NT: UC-01.NT01, UC-01.NT02

### **FS-QLSV-00-100-0020 — Quản lý Tài khoản (Admin)**

**① Mô tả & mục đích** Admin CRUD tài khoản người dùng, reset mật khẩu, khóa/mở khóa, phân quyền — trên **MH-00-2**.

**② Tác nhân**: VT-00 Admin.

**③ Logic xử lý**

1.  Hiển thị danh sách tài khoản dạng bảng. Bộ lọc: Vai trò, Trạng thái, Tìm kiếm.
2.  Tạo mới: Nhập username, email, vai trò, set mật khẩu tạm. Validate VLD-QLSV-01, VLD-QLSV-06.
3.  Sửa: Cập nhật vai trò, trạng thái.
4.  Reset password: Gen mật khẩu tạm mới, gửi email.
5.  Xóa mềm: Chuyển trạng thái → Disabled (không xóa vật lý).

**④ Đặc tả trường dữ liệu** — Kế thừa bảng FLD-ACC từ FS-QLSV-00-100-0010.

Bổ sung:

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-ACC-EMAIL | Email | ✱   | Unique, Format email hợp lệ, VLD-QLSV-01 |
| FLD-ACC-CREATED-AT | DateTime | ✱   | Auto-set khi tạo |
| FLD-ACC-UPDATED-BY | String | —   | Ghi tên Admin thao tác |

**⑤ Quy tắc**: BR-048, BR-049.

**⑥ Hành vi MH-00-2**: Bảng danh sách + thanh filter + nút “Tạo tài khoản mới” + dropdown actions (Reset PW, Khóa, Mở khóa).

## **5.1. Nhóm 01-100 — Quản lý Sinh viên & Phân lớp**

### **FS-QLSV-01-100-0010 — Tiếp nhận hồ sơ & Phân lớp chuyên ngành**

**① Mô tả & mục đích** Số hóa danh sách sinh viên đầu vào (từ tuyển sinh), tra cứu/nhập thủ công hồ sơ, tự động cấp phát tài khoản và tự động chia lớp dựa trên MaxCapacity để tiết kiệm thời gian.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân: VT-01 Cán bộ Quản nhiệm (QN).
- Tiền điều kiện: Có danh sách trúng tuyển (TT-01 hoặc import file) trên **MH-01-1**.
- Kích hoạt:
    - Tra cứu mã trúng tuyển / họ tên trên **MH-01-2** (ô search input).
    - Hoặc bấm “Thêm SV thủ công” → unlock toàn bộ form nhập.
    - Thực hiện phân lớp trên **MH-01-4**.

**③ Logic xử lý**

1.  **Tra cứu**: QN nhập mã trúng tuyển hoặc Họ tên → Hệ thống query TT-01, auto-fill các trường disabled (Họ tên, Ngày sinh, CCCD, Chuyên ngành). QN bổ sung trường mở (SĐT, Email, Dân tộc, Địa chỉ).
2.  **Thêm thủ công**: Unlock tất cả trường → QN nhập đầy đủ. Validate VLD-QLSV-01 (Unique CCCD, Email).
3.  Bấm “Xác nhận nhập hồ sơ” → Lưu TT-01 trạng thái S0. Hiển thị Success Modal “Tiếp nhận thành công!”.
4.  **Phân lớp** (**MH-01-4**): QN chọn chuyên ngành → Hiển thị danh sách lớp khả dụng. Drag-drop hoặc chọn SV → gán lớp. Hệ thống check CurrentSize < MaxCapacity. Nếu đầy → Chặn, thông báo lỗi. Nếu OK → Update S0 → S1.
5.  **Cập nhật trạng thái** (**MH-01-3**): QN thay đổi trạng thái SV (S1→S2 Bảo lưu, S1→S3 Thôi học, S2→S1 Tái nhập…). Hệ thống thực hiện tác vụ phái sinh (gỡ khỏi lớp nếu S2/S3, chặn đăng nhập nếu S3).

**④ Đặc tả trường dữ liệu (MH-01-2 — Form tiếp nhận)**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** | **UI State** | **Ghi chú** |
| --- | --- | --- | --- | --- | --- |
| FLD-STUDENT-FULLNAME | String(100) | ✱   | Not blank, 2-100 ký tự, chỉ chữ cái + dấu tiếng Việt + khoảng trắng | Disabled (tra cứu), Enabled (thủ công) | Họ và Tên |
| FLD-STUDENT-CCCD | String(12) | ✱   | Unique (VLD-QLSV-01), Regex \[0-9\]{12}, title=“Số CCCD phải gồm đúng 12 chữ số” | Disabled (tra cứu), Enabled (thủ công) | Căn cước công dân |
| FLD-STUDENT-DOB | Date | ✱   | Not null, Tuổi 16-35 tại thời điểm nhập | Disabled (tra cứu), Enabled (thủ công) | Ngày sinh |
| FLD-STUDENT-PHONE | String(15) | ✱   | Regex \`(0\[3 | 5   | 7   |
| FLD-STUDENT-EMAIL | Email | ✱   | Unique (VLD-QLSV-01), Format email hợp lệ | Enabled | Email cá nhân |
| FLD-STUDENT-ETHNICITY | String(50) | —   | Tùy chọn, mặc định “Kinh” | Enabled | Dân tộc |
| FLD-STUDENT-ADDRESS | String(200) | —   | Tùy chọn | Enabled | Địa chỉ thường trú |
| FLD-STUDENT-MAJOR | FK(TT-05) | ✱   | Phải chọn 1 giá trị hợp lệ từ dropdown | Disabled (tra cứu), Enabled (thủ công) | Chuyên ngành đăng ký |
| FLD-STUDENT-ID | String(10) | ✱   | Unique (VLD-QLSV-01), Format \[A-Z\]{2}\[0-9\]{6} (VD: HE150001) | Auto-gen | Mã SV — tự sinh |
| FLD-STUDENT-STATUS | Enum | ✱   | S0, S1, S2, S3, S4, S5 | Read-only | Trạng thái học tập |

**⑤ Quy tắc nghiệp vụ áp dụng**

- **BR-001, BR-002**: Mã SV, CCCD, Email là duy nhất. Nếu trùng → ERR-QLSV-01.
- **BR-003**: Trạng thái S2/S3 → Gỡ khỏi lớp ngay, chặn đăng nhập (S3).
- **BR-004**: Lớp không vượt sĩ số MaxCapacity. Nếu vượt → NL-04.
- **BR-005b**: Bảo lưu S2 có thời hạn (mặc định 1 năm). Quá hạn → tự động S3.
- **BR-043**: Kỷ luật S5 có thời hạn. Hết hạn → quay về S1 (nếu không có quyết định S3).
- **BR-044**: Tốt nghiệp S4: Pass hết môn, hết nợ tài chính, không đang S5.

**⑥ Hành vi màn hình**

- **MH-01-2**: Thanh tìm kiếm trên cùng + nút “Thêm SV thủ công”. Form 3-cột (form-grid 3fr). Nút “Làm mới” reset form, nút “Xác nhận nhập hồ sơ” submit. Success Modal (modal icon check, title “Tiếp nhận thành công!”, desc “Hồ sơ sinh viên đã được lưu vào hệ thống và đang chờ xét duyệt.”).
- **MH-01-1**: Bảng danh sách trúng tuyển, phân theo chuyên ngành (Major Grid cards). Mỗi card hiện icon, tên chuyên ngành, số lượng SV. Click card → expand danh sách bảng tương ứng.
- **MH-01-4**: 2-panel layout: Bên trái danh sách SV (S0) chưa có lớp, bên phải danh sách lớp. Kéo thả hoặc nút gán.
- **MH-01-3**: Bảng SV + cột Trạng thái (dropdown select S0-S5). Nút xác nhận chuyển trạng thái.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Thông báo** | **Loại** |
| --- | --- | --- | --- |
| ERR-QLSV-01 | Trùng lặp Mã SV/CCCD/Email khi nhập | “Dữ liệu bị trùng. Vui lòng kiểm tra lại CCCD hoặc Email.” | Highlight field đỏ |
| ERR-QLSV-11 | Phân lớp vượt MaxCapacity | “Lớp \[X\] đã đầy. Sĩ số hiện tại: Y/Z.” | Toast warning |
| ERR-QLSV-12 | CCCD không đúng 12 số | “Số CCCD phải gồm đúng 12 chữ số” | Tooltip trên field |

**⑧ Hậu điều kiện & đầu ra**

- SV được tạo thành công ở trạng thái S0, được phân lớp → S1, tài khoản được tạo tự động.

**⑨ Sự kiện phát sinh**

- EVT-STUDENT-CREATED: Trigger tạo tài khoản, gửi email welcome.
- EVT-STUDENT-ASSIGNED-CLASS: Update sĩ số lớp.
- EVT-STUDENT-STATUS-CHANGED: Xử lý phái sinh (gỡ lớp, chặn login…).

**⑩ Truy vết & nghiệm thu**

- NT: UC-02.NT01, UC-04.NT01

## **5.2. Nhóm 02-100 — Đào tạo & Thời khóa biểu**

### **FS-QLSV-02-100-0010 — Quản lý Danh mục (GV, Chuyên ngành, Môn học)**

**① Mô tả & mục đích** Quản lý 3 loại danh mục cốt lõi: Giảng viên, Chuyên ngành, Môn học — phục vụ cho CTĐT và TKB.

**② Tác nhân · Kích hoạt**

- Tác nhân: VT-01 Cán bộ Quản nhiệm (QN).
- Kích hoạt: Chọn tab danh mục trên **MH-02-1** (3 Category Cards: Giảng viên / Chuyên ngành / Môn học).

**③ Logic xử lý**

1.  Hiển thị 3 Category Cards (với animation fade-slide-up). Click card → active + hiện Data Panel tương ứng.
2.  **Tab Giảng viên**: Bảng gồm Mã GV, Họ tên, Khoa/Bộ môn, Email, SĐT. Filter: Search text + Dropdown Khoa. CRUD qua Modal.
3.  **Tab Chuyên ngành**: Bảng gồm Mã CN, Tên, Mô tả. CRUD qua Modal.
4.  **Tab Môn học**: Bảng gồm Mã môn, Tên, Tín chỉ, Thuộc ngành (multi-badge). Filter: Search + Chuyên ngành + Tín chỉ. CRUD qua Modal.
5.  Xóa: Kiểm tra FK (Foreign Key). Nếu GV đang được dùng trong TKB → Chặn xóa, hiện Alert inline “Không thể xóa! Dữ liệu đang được sử dụng…”.

**④ Đặc tả trường dữ liệu**

**Bảng Giảng viên (TT-03):**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-GV-CODE | String(10) | ✱   | Unique, Format GV\[0-9\]{3} (VD: GV001) |
| FLD-GV-FULLNAME | String(100) | ✱   | Not blank, 2-100 ký tự |
| FLD-GV-DEPT | String(100) | ✱   | Dropdown: Công nghệ thông tin / Kinh tế / Ngôn ngữ Anh / … |
| FLD-GV-EMAIL | Email | —   | Format email, domain @onenet.edu.vn khuyến nghị |
| FLD-GV-PHONE | String(15) | —   | Regex SĐT VN |

**Bảng Chuyên ngành (TT-05):**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-MAJOR-CODE | String(5) | ✱   | Unique, chữ hoa (VD: SE, AI, IB) |
| FLD-MAJOR-NAME | String(100) | ✱   | Not blank |
| FLD-MAJOR-DESC | String(500) | —   | Mô tả tùy chọn |

**Bảng Môn học (TT-04):**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-SUBJECT-CODE | String(10) | ✱   | Unique, Format \[A-Z\]{3}\[0-9\]{3}\[a-z\]? (VD: PRF192, WDU203c) |
| FLD-SUBJECT-NAME | String(150) | ✱   | Not blank |
| FLD-SUBJECT-CREDITS | Int | ✱   | Range 1-6 |
| FLD-SUBJECT-MAJORS | FK(TT-05)\[\] | ✱   | Ít nhất 1 chuyên ngành, Multi-select (tags input) |
| FLD-SUBJECT-PREREQ | FK(TT-04)\[\] | —   | Môn tiên quyết, VLD-QLSV-07 (Chặn deadlock vòng lặp) |

**⑤ Quy tắc**: BR-006 (Mã môn unique), BR-007 (Không tạo vòng lặp môn tiên quyết).

**⑥ Hành vi MH-02-1**:

- 3 Category Cards grid. Card active: Viền gradient trên, background gradient, check indicator góc phải.
- Data Panel: Panel header (icon + title + nút “Thêm”) + Toolbar (Search + Filter select + nút Đặt lại) + Table.
- Alert inline (nền đỏ nhạt, icon alert-triangle) khi xóa FK fail.
- Toast thông báo thành công (slide-in từ phải, 3s auto-hide).

### **FS-QLSV-02-100-0020 — Khung Chương Trình Học (CTĐT)**

**① Mô tả**: Cấu hình danh sách môn học theo từng học kỳ cho mỗi chuyên ngành trên **MH-02-2**.

**② Tác nhân**: VT-01 Cán bộ Quản nhiệm (QN).

**③ Logic xử lý**

1.  QN chọn Chuyên ngành → Hiển thị grid CTĐT (chia theo học kỳ 1-9).
2.  Mỗi học kỳ hiển thị danh sách môn (kéo thả từ pool môn học).
3.  Tổng tín chỉ tự động tính. Validate: Môn tiên quyết phải nằm ở kỳ trước.

**④ Trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-CURR-MAJOR | FK(TT-05) | ✱   | Dropdown chuyên ngành |
| FLD-CURR-SEMESTER | Int | ✱   | 1-9 |
| FLD-CURR-SUBJECTS | FK(TT-04)\[\] | ✱   | Ít nhất 1 môn / kỳ |
| FLD-CURR-TOTAL-CREDITS | Int | —   | Auto-calc |

### **FS-QLSV-02-100-0030 — Xếp Thời khóa biểu**

**① Mô tả**: Auto-gen TKB tránh xung đột GV/phòng/slot trên **MH-02-3**.

**② Tác nhân**: VT-01 Cán bộ Quản nhiệm (QN).

**③ Logic xử lý**

1.  QN chọn Học kỳ, Chuyên ngành → Load danh sách lớp + môn học cần xếp.
2.  Hệ thống Auto-schedule:
    - Constraint: 1 GV không dạy 2 lớp cùng slot. 1 phòng không dùng cho 2 lớp cùng slot.
    - Slot = 1 buổi (07:30-09:50 / 10:00-12:20 / 12:50-15:10 / 15:20-17:40).
3.  Nếu có Conflict → Hiển thị danh sách xung đột, cho QN sửa tay.
4.  Lưu TKB (TT-06).

**④ Trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-TKB-CLASS | FK(TT-02) | ✱   | Lớp hợp lệ |
| FLD-TKB-SUBJECT | FK(TT-04) | ✱   | Môn thuộc CTĐT của lớp |
| FLD-TKB-LECTURER | FK(TT-03) | ✱   | GV phải thuộc Khoa phù hợp |
| FLD-TKB-SLOT | Enum | ✱   | Slot 1/2/3/4, kết hợp Thứ (Mon-Sat) |
| FLD-TKB-ROOM | String(20) | ✱   | Mã phòng, check unique per slot |
| FLD-TKB-SEMESTER | String(10) | ✱   | VD: “Fall 2026” |
| FLD-TKB-TOTAL-SLOTS | Int | ✱   | Tổng số buổi học (auto-calc từ tín chỉ) |

**⑤ Quy tắc**: BR-008, BR-009, BR-010 (0% conflict GV, phòng, slot).

**⑥ Hành vi MH-02-3**: Grid lịch dạng calendar (Thứ × Slot). Drag-drop môn vào ô. Ô conflict highlight đỏ.

### **FS-QLSV-02-100-0040 — Báo nghỉ / Lịch bù**

**① Mô tả**: GV yêu cầu nghỉ dạy + đề xuất lịch bù → QN duyệt. GV thao tác trên **MH-02-5**, QN quản lý trên **MH-02-4**.

**② Logic xử lý**

1.  GV trên **MH-02-5** chọn buổi dạy → Bấm “Báo nghỉ” → Chọn ngày bù + Nhập lý do.
2.  QN trên **MH-02-4** nhận danh sách yêu cầu (Pending). Duyệt/Từ chối.
3.  Nếu duyệt → TKB được update: Buổi gốc đánh dấu “Nghỉ”, thêm buổi bù vào TKB. Push notification cho SV.

**④ Trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-LEAVE-LECTURER | FK(TT-03) | ✱   | GV đang dạy buổi đó |
| FLD-LEAVE-ORIGINAL-DATE | Date | ✱   | Ngày buổi gốc |
| FLD-LEAVE-MAKEUP-DATE | Date | ✱   | Phải > ngày gốc, không trùng slot GV khác |
| FLD-LEAVE-REASON | String(500) | ✱   | Min 10 ký tự |
| FLD-LEAVE-STATUS | Enum | ✱   | Pending / Approved / Rejected |

### **FS-QLSV-02-100-0050 — Xem TKB (Sinh viên)**

**① Mô tả**: SV xem TKB cá nhân theo tuần/tháng trên **MH-02-6**. Dạng Calendar view.

**② Tác nhân**: VT-03 Sinh viên.

**③ Hành vi MH-02-6**: Calendar grid (Thứ × Slot). Mỗi ô hiện: Tên môn, Mã lớp, GV, Phòng. Buổi nghỉ/bù highlight khác màu.

## **5.3. Nhóm 03-100 — Điểm danh bằng QR Code Động**

### **FS-QLSV-03-100-0010 — Mở phiên QR & App Sinh viên quét mã**

**① Mô tả & mục đích** Chống gian lận điểm danh hộ bằng QR refresh liên tục và mã hóa PWA.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân: VT-02 Giảng viên (mở phiên trên **MH-03-1**), VT-03 Sinh viên (quét trên **MH-03-3**).
- Tiền điều kiện: GV có lớp trong slot hiện tại. SV thuộc lớp đó và trạng thái S1.
- Kích hoạt: GV chọn lớp/slot trên toolbar → Hệ thống tự mở phiên QR.

**③ Logic xử lý**

1.  Server sinh chuỗi Token = AES256(SessionID + Timestamp + ClassID).
2.  UI Giảng viên hiển thị mã QR dạng ảnh lớn (260×260px), dùng SignalR/WebSockets refresh mã sau mỗi 10 giây. Progress bar đếm ngược 10s bên dưới QR.
3.  SV mở PWA Camera trên **MH-03-3**, quét mã.
4.  Gửi Token lên API. Giải mã Token:
    - Check (Now - Timestamp) > 10s → Lỗi mã hết hạn (VLD-QLSV-03).
    - Check ClientIP in AllowedRange → Lỗi sai IP (nếu áp dụng BR-016).
5.  Pass → Cập nhật TT08.Status = Present. Push Event xuống UI Giảng viên (SignalR) để tô xanh dòng SV tương ứng (badge status-present + icon check-circle).
6.  Khi GV bấm “Đóng Phiên Điểm Danh QR”, tự động UPDATE tất cả SV còn status “Chưa quét” thành Absent.
7.  **Điểm danh thủ công**: GV có thể sửa tay qua cặp nút Present/Absent ở cột “Điểm danh tay”. Khi thay đổi, ô “Lý do sửa (Bắt buộc)” hiện ra (display:block + required). Badge hiện “(Sửa tay)”.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** | **Ghi chú** |
| --- | --- | --- | --- | --- |
| FLD-ATT-SESSION-ID | UUID | ✱   | Auto-gen | ID phiên điểm danh |
| FLD-ATT-CLASS-SLOT | String | ✱   | Format “PRJ301 - Lớp SE1501 (Slot 1: 07:30 - 09:50)” | Dropdown chọn lớp/slot |
| FLD-QR-TOKEN | String | ✱   | Mã hóa AES-256, expire 10s | Token QR |
| FLD-REC-MSSV | FK(TT-01) | ✱   | SV thuộc lớp | MSSV |
| FLD-REC-FULLNAME | String | ✱   | Hiển thị | Họ tên |
| FLD-REC-STATUS | Enum | ✱   | Present / Absent | Trạng thái QR |
| FLD-MANUAL-EDIT | Bool | —   | True nếu sửa tay | Cờ sửa thủ công |
| FLD-MANUAL-REASON | String(200) | ✱ (nếu sửa tay) | Min 5 ký tự, bắt buộc khi FLD-MANUAL-EDIT = true | Lý do sửa |
| FLD-ATT-SCANNED-COUNT | Int | —   | Auto-calc | Hiện “4/30” trên stats-box |
| FLD-ATT-TIMESTAMP | DateTime | ✱   | Auto-set | Thời gian quét |

**⑤ Quy tắc nghiệp vụ áp dụng**

- **BR-013**: QR Code làm mới mỗi 10 giây.
- **BR-014**: Chỉ app PWA nội bộ mới giải mã được Token.
- **BR-016**: Check IP nội bộ (tùy cấu hình).
- **BR-017**: Tự động chốt Fail (G3) khi Absent >= 20% tổng buổi.
- **BR-018**: Sửa tay bắt buộc ghi Log (Lý do, Who, When).

**⑥ Hành vi màn hình**

- **MH-03-1**: 2-column layout (attendance-layout grid 380px + 1fr).
    - Trái: Card QR (qr-section) — QR box 260×260, timer text “Mã tự động làm mới sau Xs”, progress bar 6px, stats-box “Đã quét: X/Y”, nút “Đóng Phiên Điểm Danh QR” (btn-primary full-width).
    - Phải: Card Manual (manual-section) — Bảng: MSSV, Họ tên, Trạng thái (QR) (badge), Điểm danh tay (cặp nút P/A), Lý do sửa (input hidden, hiện khi sửa tay). Nút “Lưu Thay Đổi”.
- **MH-03-3** (SV PWA): Danh sách lịch học trong ngày, mỗi item có nút “Quét QR Điểm danh” → Mở camera PWA. Overlay kết quả: Xanh lá (Thành công) / Đỏ (Thất bại).
- **MH-03-2** (SV): Báo cáo điểm danh cá nhân — Bảng theo môn, hiện số buổi Present/Absent, tỷ lệ %. Cảnh báo khi gần ngưỡng 20%.

**⑦ Xử lý ngoại lệ & thông báo lỗi**

| **Mã lỗi** | **Điều kiện** | **Thông báo** | **Loại** |
| --- | --- | --- | --- |
| ERR-QLSV-04 | Quét QR bằng App ngoài (Zalo/Camera thường) | “Mã QR không hợp lệ. Vui lòng sử dụng ứng dụng PWA chính thức.” | Overlay đỏ |
| ERR-QLSV-13 | QR Token hết hạn (>10s) | “Mã QR đã hết hạn. Vui lòng đợi mã mới.” | Overlay vàng |
| ERR-QLSV-14 | IP không thuộc dải cho phép | “Vui lòng kết nối WiFi trường để điểm danh.” | Alert |
| ERR-QLSV-15 | SV không thuộc lớp đang mở phiên | “Bạn không thuộc lớp này.” | Alert |

**⑧ Hậu điều kiện & đầu ra**

- Bản ghi TT-08 trạng thái rõ ràng (Present/Absent).

**⑨ Sự kiện phát sinh**

- EVT-ATTENDANCE-MARKED: Push realtime xuống UI GV.
- EVT-ATTENDANCE-SESSION-CLOSED: Batch update Absent cho SV chưa quét.
- EVT-STUDENT-ATTENDANCE-FAILED: Kích hoạt khi tỷ lệ vắng chạm 20% → Tự động chuyển G0 → G3.

**⑩ Truy vết & nghiệm thu**

- NT: UC-09.NT01, UC-09.NT02, UC-09.NT03

## **5.4. Nhóm 04-100 — Xét điều kiện điểm số tự động**

### **FS-QLSV-04-100-0010 — Nhập điểm quá trình (GV)**

**① Mô tả**: GV nhập/import điểm thành phần cho SV trên **MH-04-1**.

**② Tác nhân**: VT-02 Giảng viên.

**③ Logic xử lý**

1.  GV chọn Học kỳ + Môn + Lớp trên toolbar (3 select dropdowns).
2.  Bảng hiển thị danh sách SV: MSSV, Họ tên, các cột điểm thành phần (Quiz 1, Quiz 2, Assignment, PE…) theo tỷ trọng, cột Tổng TP (auto-calc).
3.  GV nhập điểm vào ô grade-input (input width 60px, text-align center). Real-time validate:
    - Giá trị ngoài dải 0.0-10.0 → Class error (viền đỏ, nền đỏ nhạt).
4.  SV bị G3 (Cấm thi): Toàn bộ dòng background #FEF2F2, border-left đỏ, input disabled, tên SV màu đỏ + note “(G3 - Cấm thi do vắng >= 20%)”.
5.  SV bị G4 (Thi lại): Dòng background #FFFBEB, border-left vàng, input disabled, tên SV màu vàng + note “(G4 - Thi lại)”.
6.  Nút “Import Điểm” → Upload Excel. Nút “Export” → Xuất Excel/CSV/PDF.
7.  Nút “Lưu bảng điểm” → Lưu batch.
8.  Sau khi QN “Chốt sổ” → Toàn bộ grid bị khóa cứng (disabled). BR-020.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** | **Ghi chú** |
| --- | --- | --- | --- | --- |
| FLD-GRADE-MSSV | FK(TT-01) | ✱   | SV thuộc lớp | —   |
| FLD-GRADE-QUIZ1 | Float | —   | 0.0-10.0, Step 0.1 | Tỷ trọng 10% |
| FLD-GRADE-QUIZ2 | Float | —   | 0.0-10.0, Step 0.1 | Tỷ trọng 10% |
| FLD-GRADE-ASM | Float | —   | 0.0-10.0, Step 0.1 | Assignment, tỷ trọng 20% |
| FLD-GRADE-PE | Float | —   | 0.0-10.0, Step 0.1 | Practical Exam, tỷ trọng 20% |
| FLD-GRADE-FE | Float | —   | 0.0-10.0, Step 0.1 | Final Exam, tỷ trọng 40% |
| FLD-GRADE-TOTAL-TP | Float | —   | Auto-calc, Round 1 decimal | Tổng thành phần (trước FE) |
| FLD-GRADE-TOTAL | Float | —   | Auto-calc, Min 0.0, Max 10.0, Step 0.1 | Tổng kết = Sum(Score × Weight) |
| FLD-GRADE-STATUS | Enum | ✱   | G0, G1, G3, G4, G5 | Auto-set bởi Rule Engine |
| FLD-GRADE-IS-LOCKED | Bool | ✱   | Cờ khóa bảng điểm | True sau khi chốt sổ |

### **FS-QLSV-04-100-0020 — Rule Engine xét G0 -> G1/G3/G4/G5**

**① Mô tả & mục đích** Loại bỏ cảm tính con người. Tự động tính điểm và chốt trạng thái qua Background job dựa trên công thức đào tạo.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân: Hệ thống (tự động), VT-01 Cán bộ Quản nhiệm (QN) (chốt sổ).
- Kích hoạt: Có đủ điểm FE và tiến hành “Chốt sổ”.

**③ Logic xử lý (Rule Engine)**

1.  Tính AbsentRatio = AbsentSlots / TotalSlots. Nếu >= 0.2 → UPDATE trạng thái G3. Stop.
2.  Tính Tổng điểm (áp dụng tỷ trọng TT-20) = Sum(Score \* Weight). Round 1 số thập phân (BR-024).
3.  Nếu FE < 4.0 HOẶC Tổng < 5.0:
    - Nếu hasRetaken (đã thi lại lần 1) → UPDATE G5.
    - Nếu chưa thi lại → UPDATE G4.
4.  Các trường hợp còn lại: UPDATE G1 (Passed).

**⑤ Quy tắc nghiệp vụ áp dụng**

- **BR-019**: Thang 10 điểm.
- **BR-020**: Sau “Chốt sổ”, GV không được sửa điểm trên **MH-04-1**.
- **BR-021, BR-022, BR-023**: Điều kiện liệt (FE < 4.0), thi lại (G4), học lại (G5).
- **BR-024**: Round 1 decimal.
- **BR-025b, BR-025c**: Giới hạn số lần thi lại (1 lần) / học lại.
- **BR-051**: Sửa sau chốt phải qua Admin và ghi Audit Log vĩnh viễn.

**⑥ Hành vi màn hình**

- **MH-04-1**: GV nhập điểm. Sau khi chốt → DataGrid disabled (Read-only).
- **MH-04-2** (SV): Bảng điểm cá nhân — Dòng G3 highlight đỏ, G4 highlight vàng, G5 highlight đỏ đậm. G1 highlight xanh.
- **MH-04-3** (SV): Lịch thi — Bảng gồm Môn, Ngày thi, Slot, Phòng, Hình thức.
- **MH-04-1b** (SV): Chương trình đào tạo — Xem CTĐT theo kỳ, trạng thái Pass/Fail/Đang học.

**⑦ Xử lý ngoại lệ**

| **Mã lỗi** | **Điều kiện** | **Thông báo** | **Loại** |
| --- | --- | --- | --- |
| VLD-QLSV-04 | Nhập điểm ngoài dải 0.0-10.0 | Viền ô input đỏ (class error), chặn lưu | Inline |
| VLD-QLSV-05 | Admin sửa điểm sau chốt mà không nhập Lý do (min 20 ký tự) | “Bắt buộc nhập lý do chỉnh sửa (tối thiểu 20 ký tự)” | Modal |
| ERR-QLSV-16 | GV cố lưu điểm khi bảng đã chốt sổ | “Bảng điểm đã được chốt. Liên hệ Admin nếu cần chỉnh sửa.” | Toast error |

**⑧⑨⑩**: EVT-GRADE-LOCKED, NT: UC-11.NT01, UC-11.NT02.

## **5.5. Nhóm 05-100 — Dịch vụ Sinh viên & Hành chính**

### **FS-QLSV-05-100-0010 — Dịch vụ hành chính một cửa (Nộp đơn trực tuyến)**

**① Mô tả & mục đích** Cổng thông tin hỗ trợ SV nộp đơn từ trực tuyến (Nghỉ học, Phúc khảo, Bảng điểm, Miễn giảm HP…), tra cứu lịch sử, đăng ký học lại/thi lại — tất cả trên **MH-05-5**.

**② Tác nhân**: VT-03 Sinh viên.

**③ Logic xử lý**

1.  **Dashboard chính** (**MH-05-5**):
    - **Section 1 “Nộp đơn từ trực tuyến”**: 5 card dịch vụ (Nghỉ học tạm thời, Phúc khảo điểm, Cấp bảng điểm, Miễn giảm HP, Đơn khác). Mỗi card truyền params (title, price, processingTime).
    - **Section 2 “Tra cứu & Đăng ký nghiệp vụ”**: 3 card (Lịch sử đơn từ, Đăng ký học lại \[G3/G5\], Đăng ký thi lại \[G4\]).
2.  **Click card dịch vụ** → Ẩn dashboard, hiện form service_form:
    - Auto-fill MSSV (disabled), Loại đơn (disabled).
    - Info bar: Số dư tài khoản, Giá dịch vụ, Hạn xử lý (ngày làm việc).
    - Textarea “Lý do/Nội dung chi tiết” (required).
    - Upload file đính kèm (drag-drop zone).
    - Nút “Xác nhận gửi đơn” + “Hủy bỏ”.
3.  Submit → Tạo TT-10 (trạng thái Pending). Nếu có phí → Tạo TT-11 (Unpaid). Toast “Đã nộp đơn thành công!”.
4.  **Lịch sử đơn từ** (service_history): Danh sách card timeline, mỗi đơn hiện icon, tên đơn, ngày nộp, phí, trạng thái (badge Đã duyệt/Đang xử lý/Từ chối), ngày duyệt/dự kiến.

**④ Đặc tả trường dữ liệu (TT-10 Đơn từ)**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** | **Ghi chú** |
| --- | --- | --- | --- | --- |
| FLD-REQ-ID | String(15) | ✱   | Auto-gen, Format REQ-YYMMDD-XXXX | Mã đơn |
| FLD-REQ-STUDENT | FK(TT-01) | ✱   | SV phải S1/S2 | —   |
| FLD-REQ-TYPE | Enum | ✱   | NghiHoc / BaoLuu / PhucKhao / BangDiem / MienGiam / Khac | Loại đơn |
| FLD-REQ-CONTENT | Text | ✱   | Min 10 ký tự, Max 2000 | Lý do/Nội dung |
| FLD-REQ-ATTACHMENT | File\[\] | —   | Max 5 files, mỗi file ≤ 10MB, Ext: pdf/docx/jpg/png | File đính kèm |
| FLD-REQ-SERVICE-FEE | Decimal | —   | ≥ 0 | Phí dịch vụ (0đ = miễn phí) |
| FLD-REQ-PROCESSING-DAYS | Int | —   | \> 0 | Hạn xử lý (ngày làm việc) |
| FLD-REQ-STATUS | Enum | ✱   | Pending / Approved / Rejected | —   |
| FLD-REQ-FEEDBACK | Text | —   | Nullable, nhập bởi QN | Phản hồi/ghi chú duyệt |
| FLD-REQ-SUBMITTED-AT | DateTime | ✱   | Auto-set | Ngày giờ nộp |
| FLD-REQ-REVIEWED-AT | DateTime | —   | Set khi QN duyệt | Ngày giờ duyệt |
| FLD-REQ-REVIEWED-BY | FK(TT-00) | —   | QN thao tác | —   |

### **FS-QLSV-05-100-0020 — Phê duyệt Đơn từ (Quản nhiệm)**

**① Mô tả**: QN xem, duyệt/từ chối đơn từ SV trên **MH-05-2**.

**② Tác nhân**: VT-01 Cán bộ Quản nhiệm (QN).

**③ Logic xử lý**

1.  Bảng danh sách đơn: Mã đơn, Ngày nộp, SV (MSSV + Họ tên), Lớp, Loại đơn, File đính kèm, Trạng thái (badge), Thao tác.
2.  Filter: Tìm kiếm (MSSV/Tên SV) + Loại đơn (dropdown) + Trạng thái (dropdown, mặc định “Chờ duyệt”).
3.  Bấm “Chi tiết” → Mở Modal xét duyệt:
    - Info Grid (2 cột): SV, Lớp, Loại đơn, Ngày gửi.
    - Content Box: Nội dung đơn + File đính kèm (clickable link).
    - Feedback Form: Textarea “Phản hồi / Ghi chú (sẽ gửi email cho SV)”.
    - Footer: Nút “Hủy” + “Từ chối” (btn-danger) + “Phê duyệt” (btn-success).
4.  Phê duyệt/Từ chối → Update TT-10 status. Gửi email thông báo SV (≤ 1 phút, UC-14.NT01).
5.  Toast thông báo kết quả (Xanh = duyệt, Đỏ = từ chối).

**⑥ Hành vi MH-05-2**: Bảng + filter bar trên. Modal overlay (650px) với info-grid nền xám, content-box, textarea feedback, footer action buttons.

### **FS-QLSV-05-100-0030 — Quản lý Hồ sơ cá nhân**

**① Mô tả**: Mỗi vai trò xem/sửa hồ sơ cá nhân:

- QN: **MH-05-1** (Hồ sơ cán bộ).
- GV: **MH-05-3** (Hồ sơ giảng viên — đổi mật khẩu, cập nhật SĐT/Email).
- SV: **MH-05-4** (Hồ sơ sinh viên — xem thông tin, đổi mật khẩu, cập nhật SĐT/ảnh đại diện).

**② Trường dữ liệu chung cho Đổi mật khẩu**

| **Trường** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-PROFILE-OLD-PW | String | ✱   | Phải khớp hash hiện tại |
| FLD-PROFILE-NEW-PW | String | ✱   | VLD-QLSV-06 (≥ 8, 1 hoa, 1 số, 1 đặc biệt) |
| FLD-PROFILE-CONFIRM-PW | String | ✱   | Phải = FLD-PROFILE-NEW-PW |

## **5.6. Nhóm 06-100 — Thanh toán (Payment Gateway)**

### **FS-QLSV-06-100-0010 — Tích hợp VNPay/MoMo & Tra soát**

**① Mô tả & mục đích** Gạch nợ tự động học phí, xử lý rớt mạng/mất webhook.

**② Tác nhân · Tiền điều kiện · Kích hoạt**

- Tác nhân: VT-03 Sinh viên (**MH-06-2**), VT-01 Cán bộ Quản nhiệm (QN) (**MH-06-1**), VNPay/MoMo.
- Kích hoạt: Nút thanh toán (icon VNPay/MoMo) tại **MH-06-2**.

**③ Logic xử lý**

1.  **MH-06-2** (SV):
    - Thống kê tài chính: 3 card (Tổng nợ cần nộp | Đã thanh toán kỳ này | Số dư Ví SV).
    - Bộ lọc: Tìm kiếm + Học kỳ (dropdown) + Trạng thái (dropdown) + Nút Lọc.
    - Bảng hóa đơn: Kỳ học, Nội dung thu, Số tiền, Hạn nộp, Trạng thái (badge), Thanh toán trực tuyến.
    - Hóa đơn Unpaid: Row highlight đỏ nhạt, hiện 2 nút thanh toán (VNPay logo + MoMo logo).
    - Hóa đơn Paid: Nút “Tải biên lai” (download icon).
2.  SV bấm nút cổng thanh toán → Gen mã phiên giao dịch (hạn 15p, BR-030). Redirect.
3.  VNPay/MoMo gọi IPN Webhook. Verify HMAC SHA512 (BR-031). Check số tiền khớp 100%.
4.  OK → Hóa đơn Paid, Giao dịch Success. Push notification cho SV.
5.  **MH-06-1** (Quản nhiệm):
    - Bảng lịch sử giao dịch: Mã GD, Ngày, SV, Nội dung, Số tiền, Trạng thái (Success/Failed/Pending), Nguồn (Webhook/Manual).
    - Nút “Truy vấn API” (Query Transaction) cho giao dịch Pending → Gọi vnp_Querydr.
    - Form gạch nợ thủ công: Bắt buộc nhập Lý do + Upload chứng từ. Ghi Audit Log (BR-035).
6.  Background job hàng ngày: Quét hóa đơn quá DueDate → Overdue (BR-046 → Chặn SV xem điểm/đăng ký).

**④ Đặc tả trường dữ liệu**

**Hóa đơn (TT-11):**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** | **Ghi chú** |
| --- | --- | --- | --- | --- |
| FLD-INV-ID | String(15) | ✱   | Auto-gen, Format INV-YYMM-XXXX | Mã hóa đơn |
| FLD-INV-STUDENT | FK(TT-01) | ✱   | —   | —   |
| FLD-INV-SEMESTER | String(10) | ✱   | VD: “FA26”, “SU26” | Kỳ học |
| FLD-INV-DESC | String(200) | ✱   | Not blank | Nội dung thu (VD: “Học phí chính khóa (15 TC)”) |
| FLD-INV-AMOUNT | Decimal | ✱   | \> 0, Số tiền khớp 100% với tính toán | Số tiền |
| FLD-INV-DUE-DATE | Date | ✱   | \> ngày tạo | Hạn nộp |
| FLD-INV-STATUS | Enum | ✱   | Unpaid / Paid / Overdue / Cancelled | —   |
| FLD-INV-PAID-DATE | DateTime | —   | Set khi thanh toán | Ngày nộp thực tế |

**Giao dịch (TT-12):**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** | **Ghi chú** |
| --- | --- | --- | --- | --- |
| FLD-TXN-ID | String(20) | ✱   | Auto-gen | Mã giao dịch nội bộ |
| FLD-TXN-INVOICE | FK(TT-11) | ✱   | —   | —   |
| FLD-TXN-GATEWAY | Enum | ✱   | VNPay / MoMo / Manual | Cổng thanh toán |
| FLD-TXN-AMOUNT | Decimal | ✱   | Khớp FLD-INV-AMOUNT | —   |
| FLD-TXN-STATUS | Enum | ✱   | Pending / Success / Failed | —   |
| FLD-TXN-GATEWAY-REF | String(50) | —   | Mã tham chiếu từ cổng TT | VNPay OrderID |
| FLD-TXN-CHECKSUM | String | —   | HMAC SHA512 | Chữ ký xác thực |
| FLD-TXN-SOURCE | Enum | —   | Webhook / ManualReconcile | Phân biệt tự động vs thủ công |
| FLD-TXN-MANUAL-REASON | Text | ✱ (nếu Manual) | Min 20 ký tự | Lý do gạch tay |
| FLD-TXN-CREATED-AT | DateTime | ✱   | Auto-set | —   |

**⑤ Quy tắc**

- **BR-030**: Session thanh toán 15 phút.
- **BR-031**: Khớp số tiền 100%.
- **BR-034**: Quản nhiệm có thể Query Transaction nếu Webhook rớt.
- **BR-035**: Gạch nợ thủ công phải lưu Log đầy đủ.
- **BR-046**: Hóa đơn Overdue → Chặn SV đăng ký/xem điểm.

**⑦ Xử lý ngoại lệ**

| **Mã lỗi** | **Điều kiện** | **Thông báo** | **Loại** |
| --- | --- | --- | --- |
| ERR-QLSV-05 | Checksum VNPay/MoMo trả về không khớp | “Giao dịch không xác thực được. Vui lòng liên hệ Quản nhiệm.” | Alert Admin |
| ERR-QLSV-17 | Phiên thanh toán hết hạn (> 15p) | “Phiên thanh toán đã hết hạn. Vui lòng thực hiện lại.” | Toast |
| ERR-QLSV-18 | SV có hóa đơn Overdue cố truy cập chức năng bị chặn | “Bạn có hóa đơn quá hạn. Vui lòng hoàn thành thanh toán để tiếp tục.” | Banner warning |

**⑩ Truy vết & nghiệm thu**: NT: UC-16.NT01, UC-16.NT02.

## **5.7. Nhóm 07-100 — Đăng ký Học lại / Thi lại & Kỷ luật**

### **FS-QLSV-07-100-0010 — Đăng ký Học lại (Re-study)**

**① Mô tả**: SV có môn G3/G5 đăng ký học lại trên Section “Đăng ký học lại” tại **MH-05-5**.

**② Tác nhân**: VT-03 Sinh viên.

**③ Logic xử lý**

1.  Hiển thị danh sách môn G3/G5 dạng card (nền đỏ nhạt, viền đỏ). Mỗi card: Mã môn (badge dashed), Tên môn, Lần học, Trạng thái NOT PASSED, Lệ phí dự kiến (= Tín chỉ × Đơn giá), Nút “Đăng ký ngay” (btn màu đỏ).
2.  Click “Đăng ký ngay” → Tạo TT-15 (ĐK Học lại). Tạo TT-11 (Hóa đơn lệ phí). Toast “Đã tạo đơn đăng ký học lại thành công! Vui lòng thanh toán hóa đơn.”
3.  Chặn SV S5 (Đình chỉ) → ERR-QLSV-06 (BR-038).

**④ Trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-RESTUDY-STUDENT | FK(TT-01) | ✱   | SV S1, không S5 |
| FLD-RESTUDY-SUBJECT | FK(TT-04) | ✱   | Môn trạng thái G3 hoặc G5 |
| FLD-RESTUDY-ATTEMPT | Int | ✱   | Lần học (≥ 2) |
| FLD-RESTUDY-FEE | Decimal | ✱   | \= Credits × UnitPrice |
| FLD-RESTUDY-STATUS | Enum | ✱   | Registered / InProgress / Completed |

### **FS-QLSV-07-100-0020 — Đăng ký Thi lại (Retake)**

**① Mô tả**: SV có môn G4 đăng ký thi lại Final Exam (1 lần) trên **MH-05-5**.

**② Logic xử lý**

1.  Danh sách môn G4 dạng card (nền vàng nhạt, viền vàng). Mỗi card: Mã môn, Tên môn, Lần học, Trạng thái “THIẾU ĐIỂM FE”, Lệ phí thi lại (Miễn phí lần 1, VD: “Miễn phí (Lần 1)”), Nút “Đăng ký thi” (btn màu vàng).
2.  Click → Tạo TT-15. Toast “Đăng ký thi lại thành công! Lịch thi sẽ được thông báo sau.”
3.  Giới hạn: Chỉ thi lại 1 lần (BR-025b). Nếu trượt lại → G5 (học lại).

**④ Trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-RETAKE-STUDENT | FK(TT-01) | ✱   | SV S1 |
| FLD-RETAKE-SUBJECT | FK(TT-04) | ✱   | Môn trạng thái G4 |
| FLD-RETAKE-FEE | Decimal | ✱   | Lần 1 = 0đ (miễn phí) |
| FLD-RETAKE-EXAM-DATE | DateTime | —   | Set bởi QN sau |

## **5.8. Nhóm 08-100 — Notification Center**

### **FS-QLSV-08-100-0010 — Hệ thống Thông báo & Email**

**① Mô tả**: Gửi thông báo in-app và email cho người dùng dựa trên sự kiện hệ thống.

**② Các sự kiện trigger thông báo**

| **Event** | **Đối tượng nhận** | **Kênh** | **Nội dung** |
| --- | --- | --- | --- |
| EVT-STUDENT-CREATED | SV mới | Email | Thông tin tài khoản đăng nhập |
| EVT-ATTENDANCE-WARNING | SV gần 20% vắng | In-app + Email | Cảnh báo vắng mặt |
| EVT-STUDENT-ATTENDANCE-FAILED | SV chạm 20% vắng | Email | Thông báo cấm thi |
| EVT-GRADE-LOCKED | SV  | In-app | Bảng điểm đã được công bố |
| EVT-REQUEST-APPROVED | SV  | Email + In-app | Đơn từ đã được duyệt |
| EVT-REQUEST-REJECTED | SV  | Email + In-app | Đơn từ bị từ chối + Lý do |
| EVT-PAYMENT-SUCCESS | SV  | In-app | Thanh toán thành công |
| EVT-INVOICE-OVERDUE | SV  | Email | Hóa đơn quá hạn, chặn chức năng |
| EVT-LEAVE-APPROVED | SV + GV | In-app | Lịch nghỉ/bù được duyệt |
| EVT-TKB-UPDATED | SV  | In-app | TKB có thay đổi |

**③ Trường dữ liệu (TT-18)**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-NOTIF-ID | UUID | ✱   | Auto-gen |
| FLD-NOTIF-USER | FK(TT-00) | ✱   | Người nhận |
| FLD-NOTIF-TYPE | Enum | ✱   | Info / Warning / Success / Danger |
| FLD-NOTIF-TITLE | String(100) | ✱   | Tiêu đề |
| FLD-NOTIF-BODY | Text | ✱   | Nội dung |
| FLD-NOTIF-READ | Bool | ✱   | Default false |
| FLD-NOTIF-CHANNEL | Enum | ✱   | InApp / Email / Both |
| FLD-NOTIF-CREATED-AT | DateTime | ✱   | Auto-set |

**④ Xử lý Email**: Background Queue (Hangfire/Quartz.NET). HTML Template. Retry 3 lần nếu SMTP fail. Log mọi email gửi ra.

# **CHƯƠNG 6. ĐẶC TẢ GIAO DIỆN CHÍNH**

| **Mã MH** | **Đặc tả UI & Hành vi** |
| --- | --- |
| **MH-00-5** | (Đăng nhập Admin) Glassmorphism card trên nền gradient + ảnh campus. Form: Username, Password (toggle show/hide), checkbox “Ghi nhớ đăng nhập”, nút “Đăng nhập”. Link quay lại MH-00-6. Header xanh primary. Footer copyright. |
| **MH-00-6** | (Đăng nhập Chung) Layout giống MH-00-5 nhưng thêm dấu phân cách “hoặc” + nút “Đăng nhập bằng Google” (nền trắng, icon Google SVG 4 màu). Redirect sang Dashboard GV/SV/QN tùy role. |
| **MH-01-2** | (Tiếp nhận hồ sơ) Card header: Search input + nút “Thêm SV thủ công”. Form-grid 3 cột: Họ tên, CCCD\*, Ngày sinh, SĐT, Email, Dân tộc, Địa chỉ, Chuyên ngành (disabled/enabled tùy mode). Nút “Làm mới” + “Xác nhận nhập hồ sơ”. Success Modal. |
| **MH-02-1** | (Quản lý Danh mục) 3 Category Cards grid (GV xanh, Chuyên ngành xanh lá, Môn học tím). Animation fadeSlideUp. Card active có gradient header, check indicator. Data Panel: Toolbar search + filter select + Table CRUD. Modal thêm/sửa. Alert inline FK. Toast success. |
| **MH-03-1** | (Mở QR Điểm Danh) 2-column: Trái QR box 260×260 + timer 10s + progress bar + stats “X/Y” + nút “Đóng phiên”. Phải: Bảng SV \[MSSV, Tên, Status(QR), ĐD tay (P/A buttons), Lý do sửa (input hiện khi sửa)\]. Real-time push qua SignalR. |
| **MH-03-3** | (Lịch Học - PWA Scan QR) Camera chiếm trọn, hiện overlay Thành công (xanh lá) / Thất bại (đỏ). Danh sách lịch học trong ngày phía trên. |
| **MH-04-1** | (Cập nhật điểm quá trình) Toolbar: 3 select (Kỳ, Môn, Lớp). Bảng: MSSV, Tên, các cột điểm (grade-input 60px), Tổng TP. Nút Import/Export/Lưu. Ô lỗi viền đỏ. Dòng G3 highlight đỏ (disabled). Dòng G4 highlight vàng (disabled). |
| **MH-05-2** | (Phê duyệt đơn từ) Filter: Search + Loại đơn + Trạng thái (mặc định Pending). Bảng: Mã đơn, Ngày nộp, SV (MSSV+Tên), Lớp, Loại đơn, File đính kèm (link), Trạng thái (badge warning/success/danger), nút “Chi tiết”. Modal xét duyệt: Info-grid + Content + Textarea feedback + Nút Từ chối (đỏ) / Phê duyệt (xanh). Toast kết quả. |
| **MH-05-5** | (Dịch vụ Hành chính) Dashboard 2 section: (1) 5 card dịch vụ nộp đơn, (2) 3 card tra cứu/đăng ký. Service views: Form nộp đơn (auto MSSV, textarea, file upload), Lịch sử (timeline cards), Học lại (cards đỏ + Đăng ký), Thi lại (cards vàng + Đăng ký). |
| **MH-06-1** | (Lịch sử giao dịch) Bảng giao dịch + filter. Nút “Truy vấn API” cho Pending. Form gạch nợ tay (Lý do + Upload chứng từ). Phân biệt Webhook vs Manual. |
| **MH-06-2** | (Hóa đơn & Thanh toán) 3 stat cards (Tổng nợ đỏ, Đã TT, Số dư ví). Bảng hóa đơn: Row Unpaid highlight đỏ nhạt + 2 nút thanh toán (VNPay/MoMo logo buttons). Row Paid: Nút tải biên lai. Filter: Search + Kỳ + Trạng thái. |
| **MH-01-8** | (Hồ sơ SV toàn trường) Grid card danh sách SV (auto-fill 300px). Mỗi card: Avatar, Tên, MSSV, Ngành, Khóa, Lớp, Trạng thái (badge). Click card → Modal chi tiết (max-width 1100px): Header (avatar 72px + tên + meta), Body gồm Info-grid 2 cột (Họ tên, CCCD, Ngày sinh, Email, SĐT, Dân tộc, Địa chỉ, Chuyên ngành, Lớp, Khóa), Bảng điểm (data-table), Timeline trạng thái (timeline-item). Filter: Tab ngành (pill tabs) + Search + Select sắp xếp + Select khóa + Select trạng thái. Nút "Xuất danh sách" + "Thêm hồ sơ". |
| **MH-02-1-1** | (QL Giảng viên chi tiết) Breadcrumb quay về MH-02-1. Bảng GV: Mã GV (code-badge), Họ tên, Khoa/Bộ môn, Email, SĐT, Thao tác (Sửa/Xóa). Toolbar: Search + Filter Khoa (dropdown) + Nút Đặt lại. Nút "Thêm giảng viên" (btn-primary). Modal thêm/sửa GV (620px). Alert inline FK khi xóa GV đang dùng trong TKB. Click row → Modal xem danh sách lớp GV đang dạy. |
| **MH-02-1-2** | (QL Chuyên ngành chi tiết) Breadcrumb quay về MH-02-1. Bảng CN: Mã CN (code-badge), Tên, Mô tả, Thao tác (Sửa/Xóa). Toolbar: Search + Nút Đặt lại. Nút "Thêm chuyên ngành" (btn-success). Modal thêm/sửa CN. Click row → Modal xem danh sách lớp thuộc ngành. |
| **MH-02-1-3** | (QL Môn học chi tiết) Breadcrumb quay về MH-02-1. Bảng Môn: Mã môn (code-badge), Tên, Tín chỉ, Thuộc ngành (multi-badge SE/AI/IB), Thao tác (Sửa/Xóa). Toolbar: Search + Filter chuyên ngành + Filter tín chỉ + Nút Đặt lại. Nút "Tạo môn học" (btn-purple). Modal thêm/sửa Môn (tags-input cho chuyên ngành). |

# **CHƯƠNG 7. MÁY TRẠNG THÁI HỒ SƠ**

## **7.1. Trạng thái Sinh viên (TT-01)**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp được** | **Tác vụ phái sinh** |
| --- | --- | --- | --- | --- |
| S0  | Mới (Initialized) | Vừa Import/Nhập thủ công | → S1 (Khi gán lớp) | Tạo TT-01, chờ phân lớp |
| S1  | Đang học (Active) | Có lớp, đang học | → S2, S3, S4, S5 | Full access hệ thống |
| S2  | Bảo lưu (Suspended) | Có QĐ tạm ngừng (duyệt đơn) | → S1 (Tái nhập), S3 (Quá hạn) | Gỡ khỏi lớp, giới hạn login, giữ lịch sử điểm |
| S3  | Thôi học (Dropped) | Nghỉ học vĩnh viễn | (Trạng thái cuối) | Gỡ khỏi lớp, disable tài khoản, archive dữ liệu |
| S4  | Tốt nghiệp (Graduated) | Pass hết môn, hết nợ, không S5 | (Trạng thái cuối) | Cấp bằng, archive dữ liệu, readonly account |
| S5  | Đình chỉ (Disciplined) | Vi phạm kỷ luật (QĐ) | → S1 (Hết hạn), S3 (QĐ kéo dài) | Chặn đăng ký học lại (BR-038), giới hạn login |

## **7.2. Trạng thái Bảng điểm Môn học (TT-09)**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp được** | **UI Indicator** |
| --- | --- | --- | --- | --- |
| G0  | In Progress | Đang theo học | → G1, G3, G4 | —   |
| G1  | Passed | Vắng<20%, FE≥4.0, Tổng≥5.0 | (Cuối môn) | Badge xanh lá |
| G3  | Fail (Cấm thi) | Vắng ≥ 20% | → G5 (ĐK học lại) | Row đỏ, text đỏ, disabled |
| G4  | Retake (Thi lại) | FE<4.0 hoặc Tổng<5.0 | → G1 (Đạt), G5 (Trượt) | Row vàng, text vàng, disabled |
| G5  | Re-study (Học lại) | Từ G3 hoặc trượt G4 | → G0 (ĐK học lại kỳ mới) | Badge đỏ đậm |

## **7.3. Trạng thái Đơn từ (TT-10)**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp** |
| --- | --- | --- | --- |
| Pending | Chờ duyệt | SV vừa nộp | → Approved, Rejected |
| Approved | Đã duyệt | QN phê duyệt | (Cuối) |
| Rejected | Từ chối | QN từ chối | (Cuối) |

## **7.4. Trạng thái Hóa đơn (TT-11)**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp** |
| --- | --- | --- | --- |
| Unpaid | Chưa nộp | Mới tạo | → Paid, Overdue, Cancelled |
| Paid | Đã nộp | Webhook/Manual thành công | (Cuối) |
| Overdue | Quá hạn | Background job detect DueDate < Now | → Paid (khi TT muộn) |
| Cancelled | Hủy | Admin/QN hủy | (Cuối) |

## **7.5. Trạng thái Giao dịch (TT-12)**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp** |
| --- | --- | --- | --- |
| Pending | Đang xử lý | Vừa tạo phiên | → Success, Failed |
| Success | Thành công | Webhook/Query confirm | (Cuối) |
| Failed | Thất bại | Hết hạn session / Checksum sai | (Cuối) |

# **CHƯƠNG 8. QUY TẮC NGHIỆP VỤ & CHỐT CHẶN CỨNG**

| **Quy tắc (BR)** | **Nội dung chốt chặn** | **Áp dụng tại** | **Vì sao chặn là đúng** |
| --- | --- | --- | --- |
| **BR-001/002** | Mã SV, CCCD, Email phải duy nhất | FS-QLSV-01-100 | Tránh nhầm lẫn dữ liệu. |
| **BR-003** | Bảo lưu/Thôi học bị gỡ khỏi lớp | Nhóm 01-100 | SV thôi học không được phép tồn tại trong TKB và điểm danh. |
| **BR-004** | Lớp không vượt sĩ số MaxCapacity | FS-QLSV-01-100 | Đảm bảo chất lượng đào tạo. |
| **BR-006** | Mã môn học unique toàn hệ thống | FS-QLSV-02-100 | Tránh trùng lặp CTĐT. |
| **BR-007** | Không tạo vòng lặp môn tiên quyết | FS-QLSV-02-100 | Deadlock logic CTĐT. |
| **BR-008/009/010** | 0% xung đột GV, Phòng, Slot khi xếp TKB | FS-QLSV-02-100 | Tính khả thi lịch học. |
| **BR-013** | QR Code refresh mỗi 10 giây | FS-QLSV-03-100 | Chống chụp hình/chia sẻ QR. |
| **BR-014** | Chỉ PWA nội bộ giải mã QR | FS-QLSV-03-100 | Chống quét bằng app ngoài. |
| **BR-016** | Validate IP nội bộ (tùy chọn) | FS-QLSV-03-100 | Chống điểm danh từ xa. |
| **BR-017** | Vắng ≥ 20% chốt Fail thẳng (G3) | FS-QLSV-03-100 | Tuân thủ quy chế đào tạo. |
| **BR-018** | Sửa điểm danh thủ công bắt buộc ghi Lý do | FS-QLSV-03-100 | Audit trail. |
| **BR-019** | Thang điểm 10 | FS-QLSV-04-100 | Chuẩn hóa. |
| **BR-020** | Sau “Chốt sổ”, GV không được sửa điểm | FS-QLSV-04-100 | Toàn vẹn bảng điểm đã công bố. |
| **BR-021** | FE < 4.0 → Không đạt | FS-QLSV-04-100 | Điều kiện liệt. |
| **BR-022** | Tổng < 5.0 → Không đạt | FS-QLSV-04-100 | Ngưỡng đạt. |
| **BR-024** | Round 1 số thập phân | FS-QLSV-04-100 | Thống nhất format điểm. |
| **BR-025b** | Thi lại tối đa 1 lần | FS-QLSV-07-100 | Công bằng. |
| **BR-030** | Session thanh toán 15 phút | FS-QLSV-06-100 | Chống treo phiên. |
| **BR-031** | Khớp số tiền 100% khi verify Webhook | FS-QLSV-06-100 | Chống giả mạo số tiền. |
| **BR-034** | Quản nhiệm query VNPay API khi Webhook rớt | FS-QLSV-06-100 | Đồng bộ dữ liệu. |
| **BR-035** | Gạch nợ thủ công phải lưu Log + Chứng từ | FS-QLSV-06-100 | Audit trail tài chính. |
| **BR-038** | Chặn ĐK học lại với SV S5 (Đình chỉ) | FS-QLSV-07-100 | Chấp hành kỷ luật. |
| **BR-044** | Tốt nghiệp: Pass hết, trả nợ, không S5 | Nhóm 01-100 | ĐK tiên quyết cấp bằng. |
| **BR-046** | Hóa đơn Overdue chặn xem điểm/đăng ký | FS-QLSV-06-100 | Ép hoàn thành nghĩa vụ tài chính. |
| **BR-048** | Mật khẩu ≥ 8 ký tự, 1 hoa, 1 số, 1 đặc biệt | FS-QLSV-00-100 | Bảo mật tối thiểu. |
| **BR-049** | Khóa 15p sau 5 lần sai password | FS-QLSV-00-100 | Chống brute force. |
| **BR-050** | SSO Google giới hạn domain email | FS-QLSV-00-100 | Chỉ user nội bộ. |
| **BR-051** | Mọi thay đổi dữ liệu lõi phải có Audit Log | Toàn hệ | Bằng chứng khi khiếu nại. |

# **CHƯƠNG 9. QUY TẮC KIỂM TRA DỮ LIỆU (VALIDATION)**

| **Mã** | **Quy tắc kiểm tra** | **Mức xử lý** | **UI Behavior** |
| --- | --- | --- | --- |
| VLD-QLSV-01 | Trùng lặp CCCD/Email/MSSV khi nhập/import | **CHẶN**, highlight dòng/field lỗi (viền đỏ) | ERR-QLSV-01 inline |
| VLD-QLSV-02 | Lớp học vượt quá sĩ số tối đa (MaxCapacity) | **CHẶN**, thông báo toast warning | ERR-QLSV-11 |
| VLD-QLSV-03 | Quét QR Code đã quá hạn 10s | **CHẶN**, báo “Mã hết hạn” | Overlay vàng trên camera |
| VLD-QLSV-04 | GV nhập điểm thành phần ngoài dải 0.0 - 10.0 | **CHẶN**, viền ô input đỏ (class error), chặn lưu | Real-time on-change |
| VLD-QLSV-05 | Admin sửa điểm sau chốt sổ mà không có Lý do | **CHẶN**, bắt buộc nhập (Min 20 ký tự) | Modal confirm |
| VLD-QLSV-06 | Mật khẩu tài khoản không đủ độ mạnh | **CHẶN**, yêu cầu (≥ 8, 1 hoa, 1 số, 1 đặc biệt) | Inline validation |
| VLD-QLSV-07 | Deadlock vòng lặp môn tiên quyết | **CHẶN** lưu cấu hình môn học | Toast error |
| VLD-QLSV-08 | CCCD không đúng 12 chữ số | **CHẶN**, pattern \[0-9\]{12} | Tooltip trên field |
| VLD-QLSV-09 | SĐT không đúng format VN | **CHẶN**, pattern \`(0\[3 | 5   |
| VLD-QLSV-10 | Email không đúng format | **CHẶN**, Regex email standard | Inline validation |
| VLD-QLSV-11 | Nội dung đơn từ quá ngắn | **CHẶN**, Min 10 ký tự | Inline validation |
| VLD-QLSV-12 | File đính kèm vượt kích thước/loại file | **CHẶN**, Max 10MB, chỉ pdf/docx/jpg/png | Alert |
| VLD-QLSV-13 | Lý do sửa điểm danh thủ công quá ngắn | **CHẶN**, Min 5 ký tự | Inline, required field |
| VLD-QLSV-14 | Ngày bù phải sau ngày nghỉ | **CHẶN** | Date picker constraint |
| VLD-QLSV-15 | Lý do gạch nợ thủ công quá ngắn | **CHẶN**, Min 20 ký tự | Inline validation |
| VLD-QLSV-16 | Tuổi SV phải từ 16-35 | **CHẶN** tại form nhập hồ sơ | Date picker constraint |
| VLD-QLSV-17 | Trùng lặp Username/Email khi CRUD tài khoản | **CHẶN**, highlight ô nhập liệu | Inline validation |
| VLD-QLSV-18 | Xóa tài khoản đang được gán lớp/TKB (FK) | **CHẶN** xóa | Modal/Alert thông báo |
| VLD-QLSV-19 | Xung đột slot lịch bù với TKB hiện tại | **CHẶN** gửi yêu cầu | Alert conflict time |
| VLD-QLSV-20 | Chuyển trạng thái SV không hợp lệ | **CHẶN** chuyển đổi sai quy tắc | Alert/Toast |
| VLD-QLSV-21 | Xóa danh mục GV/CN/MH đang được sử dụng (FK) | **CHẶN** xóa | Alert inline |
| VLD-QLSV-22 | Môn tiên quyết không ở học kỳ trước (CTĐT) | **CHẶN** kéo thả/lưu | Toast/Alert error |

# **CHƯƠNG 10. TÍCH HỢP & SỰ KIỆN**

## **10.1. Tích hợp bên ngoài**

| **Chiều tích hợp** | **Nội dung** | **Dữ liệu giao tiếp** | **Ghi chú** |
| --- | --- | --- | --- |
| **Hệ thống → VNPay** | Thanh toán học phí | URL Thanh toán (vnp_TxnRef, vnp_Amount, vnp_SecureHash HMAC SHA512) | IPN Webhook callback |
| **Hệ thống → MoMo** | Thanh toán học phí | URL Thanh toán (partnerCode, orderId, signature HMAC SHA256) | IPN Webhook callback |
| **Hệ thống → SMTP/Mailing Service** | Gửi Email (cảnh báo vắng, kết quả duyệt đơn, thông tin tài khoản…) | HTML Template, Email, Subject | Background Queue, Retry 3x |
| **Google/Microsoft → Hệ thống** | Đăng nhập SSO | OAuth 2.0 Authorization Code Flow, ID Token | Giới hạn domain @onenet.edu.vn |
| **Hệ thống ↔ Client (PWA)** | Real-time QR, Notification push | SignalR/WebSockets | Hub: AttendanceHub, NotificationHub |

## **10.2. Sự kiện hệ thống (Events)**

| **Event** | **Trigger khi** | **Subscriber** |
| --- | --- | --- |
| EVT-LOGIN-SUCCESS | Đăng nhập thành công | Audit Log |
| EVT-LOGIN-FAILED | Đăng nhập sai | Audit Log, Lockout Counter |
| EVT-ACCOUNT-LOCKED | Tài khoản bị khóa 15p | Audit Log |
| EVT-STUDENT-CREATED | SV mới được tạo | Account Service, Email Service |
| EVT-STUDENT-ASSIGNED-CLASS | SV được gán vào lớp | Class Counter Update |
| EVT-STUDENT-STATUS-CHANGED | Trạng thái SV thay đổi (S0→S1, S1→S2…) | Class Removal, Account Lock, Notification |
| EVT-ATTENDANCE-MARKED | SV quét QR thành công | SignalR push to GV UI |
| EVT-ATTENDANCE-SESSION-CLOSED | GV đóng phiên | Batch mark Absent |
| EVT-STUDENT-ATTENDANCE-FAILED | SV chạm 20% vắng | Grade Engine (G0→G3), Email warning |
| EVT-GRADE-LOCKED | QN chốt sổ điểm | Khóa DataGrid, Notification to SV |
| EVT-GRADE-MODIFIED-AFTER-LOCK | Admin sửa điểm sau chốt | Permanent Audit Log (Who/When/Old/New/Reason) |
| EVT-REQUEST-SUBMITTED | SV nộp đơn | Notification to QN |
| EVT-REQUEST-APPROVED | QN duyệt đơn | Email + Notification to SV |
| EVT-REQUEST-REJECTED | QN từ chối đơn | Email + Notification to SV |
| EVT-PAYMENT-SUCCESS | Webhook xác nhận thanh toán | Invoice update, Notification |
| EVT-PAYMENT-FAILED | Thanh toán thất bại | Log, Notification |
| EVT-INVOICE-OVERDUE | Background job detect quá hạn | Block SV functions, Email warning |
| EVT-LEAVE-REQUESTED | GV báo nghỉ | Notification to QN |
| EVT-LEAVE-APPROVED | QN duyệt lịch bù | TKB update, Notification to SV |

# **CHƯƠNG 11. DANH MỤC THÔNG BÁO LỖI (ERRORS)**

| **Mã lỗi** | **Điều kiện** | **Loại** | **Thông báo mẫu** |
| --- | --- | --- | --- |
| ERR-QLSV-01 | Trùng lặp Mã SV/CCCD/Email khi import/nhập | Chặn lưu | “Dữ liệu bị trùng. Vui lòng kiểm tra lại.” |
| ERR-QLSV-02 | Xếp TKB trùng Slot GV / Trùng phòng / Trùng lớp đã xếp | Chặn lưu TKB | “Xung đột lịch: GV/Phòng/Lớp [X] đã có lịch tại Slot [Y].” |
| ERR-QLSV-03 | Deadlock vòng lặp môn tiên quyết | Chặn lưu | “Phát hiện vòng lặp môn tiên quyết: \[A\] ↔ \[B\].” |
| ERR-QLSV-04 | SV quét QR bằng App ngoài (Zalo/Camera thường) | Chặn giải mã | “Mã QR không hợp lệ. Sử dụng PWA chính thức.” |
| ERR-QLSV-05 | Checksum VNPay/MoMo trả về không khớp | Cảnh báo Admin, Chặn gạch nợ | “Giao dịch không xác thực. Liên hệ Quản nhiệm.” |
| ERR-QLSV-06 | SV S5 (Đình chỉ) cố đăng ký học lại | Chặn lệnh, báo đỏ | “Tài khoản đang bị đình chỉ. Không thể đăng ký.” |
| ERR-QLSV-07 | Tài khoản không tồn tại khi đăng nhập | Inline form | “Tên đăng nhập hoặc mật khẩu không đúng.” |
| ERR-QLSV-08 | Tài khoản bị Locked (do spam login) | Alert | “Tài khoản bị khóa tạm thời. Thử lại sau 15 phút.” |
| ERR-QLSV-09 | Tài khoản Disabled (SV thôi học S3) | Alert | “Tài khoản đã bị vô hiệu hóa.” |
| ERR-QLSV-10 | Email Google không thuộc domain cho phép | Alert | “Email không thuộc hệ thống.” |
| ERR-QLSV-11 | Phân lớp vượt MaxCapacity | Toast warning | “Lớp \[X\] đã đầy. Sĩ số: Y/Z.” |
| ERR-QLSV-12 | CCCD không đúng 12 số | Tooltip | “Số CCCD phải gồm đúng 12 chữ số.” |
| ERR-QLSV-13 | QR Token hết hạn (>10s) | Overlay vàng | “Mã QR đã hết hạn. Đợi mã mới.” |
| ERR-QLSV-14 | IP không thuộc dải cho phép | Alert | “Vui lòng kết nối WiFi trường.” |
| ERR-QLSV-15 | SV quét QR nhưng không thuộc lớp | Alert | “Bạn không thuộc lớp này.” |
| ERR-QLSV-16 | GV cố lưu điểm khi bảng đã chốt | Toast error | “Bảng điểm đã chốt. Liên hệ Admin.” |
| ERR-QLSV-17 | Phiên thanh toán hết hạn | Toast | “Phiên thanh toán hết hạn. Thực hiện lại.” |
| ERR-QLSV-18 | SV có hóa đơn Overdue cố truy cập chức năng bị chặn | Banner | “Có hóa đơn quá hạn. Thanh toán để tiếp tục.” |
| ERR-QLSV-19 | Xóa GV/Môn/CN đang được sử dụng (FK constraint) | Alert inline | “Không thể xóa! Dữ liệu đang được sử dụng.” |
| ERR-QLSV-20 | File đính kèm vượt kích thước hoặc sai định dạng | Alert | “File không hợp lệ. Max 10MB, chỉ pdf/docx/jpg/png.” |

# **CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR ĐO ĐƯỢC)**

| **Mã** | **Nhóm** | **Yêu cầu** | **Cách đo kiểm / Ngưỡng** |
| --- | --- | --- | --- |
| NFR-01 | Hiệu năng | Đăng nhập & cấp Token | ≤ 1 giây (95th percentile) |
| NFR-02 | Hiệu năng | Import 1.000 bản ghi SV | ≤ 10 giây |
| NFR-03 | Hiệu năng | Xác thực QR Code | ≤ 2 giây (Test 200 SV quét đồng thời) |
| NFR-04 | Hiệu năng | Xếp TKB tự động 200 SV | ≤ 30 giây (0% Conflict) |
| NFR-05 | Hiệu năng | Load danh sách hóa đơn SV | ≤ 2 giây |
| NFR-06 | Hiệu năng | Tính điểm toàn bộ 200 SV | ≤ 30 giây |
| NFR-07 | Hiệu năng | Gửi email kết quả duyệt đơn | ≤ 1 phút (UC-14.NT01) |
| NFR-08 | Đồng thời | QR scan concurrent | 200 SV đồng thời quét QR |
| NFR-09 | Khả dụng | System uptime | ≥ 99.5% (Trừ maintenance window) |
| NFR-10 | Bảo mật | Hash mật khẩu một chiều | Bcrypt/Argon2 (Kiểm tra DB bản rõ = FAIL) |
| NFR-11 | Bảo mật | Chống Spam Login | Khóa 15p sau 5 lần sai (BR-049) |
| NFR-12 | Bảo mật | JWT Token | Access Token expire 30m, Refresh Token 7d |
| NFR-13 | Truy vết | Audit Trail | Log thao tác điểm (who/when/old/new) không thể xóa từ UI |
| NFR-14 | Vận hành | Backup Data | Daily backup, lưu 30 ngày, test restore hàng tháng |
| NFR-15 | Responsive | Giao diện | Hỗ trợ Desktop (1280px+) và PWA Mobile (360px+) |
| NFR-16 | SEO/A11y | Accessibility | Semantic HTML5, ARIA labels, keyboard navigation |

# **CHƯƠNG 13. MA TRẬN TRUY VẾT & NGHIỆM THU**

| **Mã NT** | **Tiêu chí nghiệm thu (Acceptance Criteria)** | **Nguồn truy vết (Đặc tả / BR / MH)** |
| --- | --- | --- |
| UC-01.NT01 | Đăng nhập thành công bằng username/password ≤ 1s. Token cấp đúng role. | FS-QLSV-00-100, BR-048/049, MH-00-5, MH-00-6 |
| UC-01.NT02 | Đăng nhập Google SSO thành công, chặn email ngoài domain. | FS-QLSV-00-100, BR-050, MH-00-6 |
| UC-02.NT01 | Nhập hồ sơ SV thành công: tạo đủ hồ sơ + tài khoản. Validate CCCD 12 số, Email unique. | FS-QLSV-01-100, BR-001, VLD-01/08/10, MH-01-2 |
| UC-04.NT01 | Phân lớp không vượt MaxCapacity, sĩ số đều. Chặn khi đầy. | FS-QLSV-01-100, BR-004, MH-01-4 |
| UC-05.NT01 | CRUD Danh mục (GV, CN, Môn học) thành công. Chặn xóa FK. | FS-QLSV-02-100, MH-02-1 |
| UC-07.NT01 | Xếp TKB tự động ra kết quả 0% Conflict phòng/GV ≤ 30s. | FS-QLSV-02-100, BR-008/009/010, MH-02-3 |
| UC-08.NT01 | GV báo nghỉ → QN duyệt → TKB update buổi bù. SV nhận thông báo. | FS-QLSV-02-100, MH-02-4, MH-02-5 |
| UC-09.NT01 | QR refresh mỗi 10s, quét thành công → Present real-time trên UI GV. | FS-QLSV-03-100, BR-013, MH-03-1, MH-03-3 |
| UC-09.NT02 | Quét QR bằng app ngoài bị chặn. QR hết hạn bị chặn. | FS-QLSV-03-100, BR-014, ERR-04/13 |
| UC-09.NT03 | Sửa điểm danh thủ công phải nhập lý do. Ghi Audit Log. | FS-QLSV-03-100, BR-018, MH-03-1 |
| UC-11.NT01 | Chuyển trạng thái G1/G3/G4/G5 đúng quy chế (% vắng, điểm FE, Tổng). | FS-QLSV-04-100, BR-017/021/022/024, MH-04-1 |
| UC-11.NT02 | Sau chốt sổ, GV không sửa được điểm. Admin sửa phải có Lý do + Audit Log. | FS-QLSV-04-100, BR-020/051, MH-04-1 |
| UC-12.NT01 | SV đăng ký học lại (G3/G5) thành công, tạo hóa đơn lệ phí. | FS-QLSV-07-100, MH-05-5 |
| UC-12.NT02 | Chặn tuyệt đối SV bị đình chỉ (S5) đăng ký học lại. | FS-QLSV-07-100, BR-038, ERR-06 |
| UC-13.NT01 | SV nộp đơn trực tuyến thành công (với file đính kèm). | FS-QLSV-05-100, MH-05-5 |
| UC-14.NT01 | QN duyệt/từ chối đơn → Email gửi cho SV ≤ 1 phút. | FS-QLSV-05-100, MH-05-2, NFR-07 |
| UC-16.NT01 | VNPay thành công → Paid tự động. Mất webhook → Quản nhiệm gạch tay có Log. | FS-QLSV-06-100, BR-031/035, MH-06-2, MH-06-1 |
| UC-16.NT02 | Webhook bị mất → Quản nhiệm Query Transaction trên MH-06-1 thành công. | FS-QLSV-06-100, BR-034, MH-06-1 |
| UC-17.NT01 | Hóa đơn quá hạn → Overdue → Chặn SV xem điểm/đăng ký. | FS-QLSV-06-100, BR-046 |

_Hết tài liệu FSD v3.0._





