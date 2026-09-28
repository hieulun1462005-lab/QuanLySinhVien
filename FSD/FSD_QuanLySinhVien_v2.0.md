**TÀI LIỆU ĐẶC TẢ CHỨC NĂNG**

**FUNCTIONAL SPECIFICATION DOCUMENT (FSD)**

**PHÂN HỆ QLSV — HỆ THỐNG QUẢN LÝ SINH VIÊN**

_Tự động hóa & Khách quan · Real-time & Đồng bộ · Truy vết toàn diện_

| **Thuộc tính** | **Nội dung** |
| --- | --- |
| Mã phân hệ | QLSV (Gồm QLSV-01 đến QLSV-06) |
| Tên phân hệ | Hệ thống Quản lý Sinh viên |
| Loại tài liệu | FSD — Đặc tả chức năng |
| Phạm vi | Đặc tả field-level các nhóm chức năng cốt lõi: Hồ sơ, Đào tạo, Điểm danh QR động, Quản lý Điểm & Khảo thí, Hành chính, Thanh toán. |
| Thực thể sở hữu | TT-01 Hồ sơ SV, TT-06 TKB, TT-07/08 Điểm danh, TT-09 Bảng điểm, TT-10 Đơn từ, TT-11 Hóa đơn, TT-12 Giao dịch, TT-15 ĐK Học lại, TT-18 Thông báo |
| Tài liệu nguồn | BRD-QLSV-v5.0 & Bộ Mockup Giao diện chuẩn (Cập nhật mới nhất) |
| Ranh giới chính | QLSV sở hữu TÀI KHOẢN, HỒ SƠ HỌC TẬP, QUY TRÌNH ĐÀO TẠO của Sinh viên. KHÔNG sở hữu dữ liệu tuyển sinh, không tính lương giảng viên. |
| Phiên bản | 3.0 (Cập nhật theo template chuẩn BRD v5.0 & Cấu trúc Mockup mới) |
| Ngày phát hành | 28/09/2026 |
| Đơn vị xây dựng | ONENET |

# **KIỂM SOÁT TÀI LIỆU**

| **Phiên bản** | **Ngày** | **Người thực hiện** | **Nội dung** |
| --- | --- | --- | --- |
| 1.0 | 18/09/2026 | Khảo sát BA | Khởi tạo tài liệu Draft ban đầu. |
| 2.0 | 21/09/2026 | Team Dev | Đặc tả kỹ thuật các luồng chức năng theo BRD v4.0. |
| 2.1 | 23/09/2026 | BA & Team Dev | Chuẩn hóa FSD theo khuôn 13 chương / mẫu 10 mục của Template chuẩn. Mapping lại toàn bộ mã định danh theo BRD v5.0. |
| 3.0 | 28/09/2026 | BA & Team Dev | Cập nhật toàn bộ FSD ánh xạ chính xác với bộ giao diện (Mockup) mới nhất và BRD v5.0. |

_Vị trí trong bộ tài liệu: FSD này là cầu nối giữa BRD (nghiệp vụ) và mã nguồn. Mọi ràng buộc (BR), mã lỗi (ERR), luồng ngoại lệ đều được dịch thành quy tắc xử lý phần mềm, đặc biệt tập trung vào máy trạng thái và các thuật toán lõi (QR động, xét điểm tự động)._

# **CHƯƠNG 1. GIỚI THIỆU**

## **1.1. Mục đích tài liệu**
Dựa trên BRD-QLSV-v5.0 và hệ thống giao diện Mockup, tài liệu FSD này đặc tả chi tiết cách hệ thống thực hiện các nghiệp vụ: quản lý hồ sơ sinh viên xuyên suốt, đào tạo và thời khóa biểu, điểm danh bằng QR Động (real-time), tự động xét điều kiện điểm số, dịch vụ sinh viên trực tuyến, và tích hợp thanh toán. 

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

# **CHƯƠNG 3. TỔNG QUAN CHỨC NĂNG & MÀN HÌNH**

## **3.1. Nhóm chức năng chính**

| **Nhóm** | **Tên nhóm** | **Vai trò** | **Đặc tả chi tiết tại** |
| --- | --- | --- | --- |
| QLSV-01-100 | Quản lý Sinh viên & Học tập (Tạo hồ sơ, Phân lớp) | Quản nhiệm | FS-QLSV-01-100-0010 |
| QLSV-02-100 | Đào tạo & Thời khóa biểu | Quản nhiệm | FS-QLSV-02-100-0010 |
| QLSV-03-100 | Điểm danh bằng QR Động | Giảng viên, SV | FS-QLSV-03-100-0010 |
| QLSV-04-100 | Điểm & Khảo thí (Nhập điểm, Tự động xét Đạt/Trượt) | Giảng viên, Admin | FS-QLSV-04-100-0020 |
| QLSV-05-100 | Dịch vụ Sinh viên (Đơn từ, Hành chính) | SV, Quản nhiệm | Xem BRD Chương 7 |
| QLSV-06-100 | Thanh toán (Payment Gateway) | SV, Kế toán | FS-QLSV-06-100-0010 |
| QLSV-07-100 | Đăng ký học lại & Kỷ luật | SV, Quản nhiệm | Xem BRD Chương 7 |
| QLSV-08-100 | Notification Center (Thông báo) | Tất cả Users | Xem BRD Chương 7 |

## **3.2. Danh Mục Màn Hình Giao Diện (Từ Mockup)**

| **Mã màn hình** | **Tên màn hình** | **Vai trò** | **Nhóm (Module)** |
| --- | --- | --- | --- |
| **MH-00-1** | Tổng Quan Hệ Thống (MH-00-1-TongQuanHeThong) | Admin | Dashboard |
| **MH-00-2** | Quản Lý Tài Khoản (MH-00-2-QuanLyTaiKhoan) | Admin | QLSV-01 |
| **MH-00-3** | Nhật Ký Hệ Thống (MH-00-3-NhatKyHeThong) | Admin | Dashboard |
| **MH-00-4** | Backup Restore DB (MH-00-4-BackupRestoreDB) | Admin | Dashboard |
| **MH-00-5** | Đăng Nhập Admin (MH-00-5-DangNhapAdmin) | Admin | QLSV-01 |
| **MH-00-6** | Đăng Nhập Hệ Thống (MH-00-6-DangNhapGiangVien) | Cán Bộ/GV/SV | QLSV-01 |
| **MH-00-7** | Dashboard Báo Cáo (MH-00-7-DashboardBaoCao) | Quản nhiệm | Dashboard |
| **MH-00-8** | Tổng Quan Giảng Viên (MH-00-8-TongQuanGiangVien) | Giảng viên | Dashboard |
| **MH-00-9** | Tổng Quan Học Tập (MH-00-9-TongQuanHocTap) | Sinh viên | Dashboard |
| **MH-01-1** | Danh Sách Trúng Tuyển (MH-01-1-DanhSachTrungTuyen) | Quản nhiệm | QLSV-01 |
| **MH-01-2** | Tiếp Nhận Hồ Sơ Sinh Viên (MH-01-2-TiepNhanHoSoSinhVien) | Quản nhiệm | QLSV-01 |
| **MH-01-3** | Cập Nhật Trạng Thái Học Tập (MH-01-3-CapNhatTrangThaiHocTap) | Quản nhiệm | QLSV-01 |
| **MH-01-4** | Phân Bổ Sinh Viên Vào Lớp (MH-01-4-PhanBoSinhVienVaoLop) | Quản nhiệm | QLSV-01 |
| **MH-02-1** | Quản Lý Danh Mục (MH-02-1-QuanLyDanhMuc) | Quản nhiệm | QLSV-02 |
| **MH-02-2** | Khung Chương Trình Học (MH-02-2-KhungChuongTrinhHoc) | Quản nhiệm | QLSV-02 |
| **MH-02-3** | Xếp Thời Khóa Biểu (MH-02-3-XepThoiKhoaBieu) | Quản nhiệm | QLSV-02 |
| **MH-02-4** | Quản Lý Yêu Cầu Báo Nghỉ Lịch Bù (MH-02-4-QuanLyYeuCauBaoNghiLichBu) | Quản nhiệm | QLSV-02 |
| **MH-02-5** | Lịch Giảng Dạy Báo Nghỉ (MH-02-5-LichGiangDayBaoNghi) | Giảng viên | QLSV-02 |
| **MH-02-6** | Thời Khóa Biểu (MH-02-6-ThoiKhoaBieu) | Sinh viên | QLSV-02 |
| **MH-03-1** | Điểm Danh Lớp Học (MH-03-1-DiemDanhLopHoc) | Giảng viên | QLSV-03 |
| **MH-03-2** | Báo Cáo Điểm Danh (MH-03-2-BaoCaoDiemDanh) | Sinh viên | QLSV-03 |
| **MH-03-3** | Lịch Học Trong Ngày (QR Scanner) (MH-03-3-LichHocTrongNgay) | Sinh viên | QLSV-03 |
| **MH-04-1** | Cập Nhật Điểm Quá Trình (MH-04-1-CapNhatDiemQuaTrinh) | Giảng viên | QLSV-04 |
| **MH-04-2** | Kết Quả Học Tập (MH-04-2-KetQuaHocTap) | Sinh viên | QLSV-04 |
| **MH-04-3** | Lịch Thi (MH-04-3-LichThi) | Sinh viên | QLSV-04 |
| **MH-05-1** | Hồ Sơ Cán Bộ Quản Nhiệm (MH-05-1-HoSoCanBoQuanNhiem) | Quản nhiệm | QLSV-05 |
| **MH-05-2** | Phê Duyệt Đơn Từ Sinh Viên (MH-05-2-PheDuyetDonTuSinhVien) | Quản nhiệm | QLSV-05 |
| **MH-05-3** | Quản Lý Hồ Sơ Giảng Viên (MH-05-3-QuanLyHoSoGiangVien) | Giảng viên | QLSV-05 |
| **MH-05-4** | Quản Lý Hồ Sơ Cá Nhân (MH-05-4-QuanLyHoSoCaNhan) | Sinh viên | QLSV-05 |
| **MH-05-5** | Dịch Vụ Hành Chính Một Cửa (MH-05-5-DichVuHanhChinhMotCua) | Sinh viên | QLSV-05 |
| **MH-06-1** | Lịch Sử Giao Dịch (MH-06-1-LichSuGiaoDich) | Quản nhiệm/Kế toán | QLSV-06 |
| **MH-06-2** | Hóa Đơn Và Thanh Toán (MH-06-2-HoaDonVaThanhToan) | Sinh viên | QLSV-06 |

# **CHƯƠNG 4. ĐẶC TẢ LUỒNG NGHIỆP VỤ**

## **4.1. Quy trình Xét điều kiện dự thi & Tổng kết điểm**

| **Bước** | **Việc** | **Vai trò** | **Trạng thái** |
| --- | --- | --- | --- |
| QT-04-1 | Hệ thống quét tỷ lệ vắng mặt: Nếu ≥ 20% → Chốt CẤM THI | Hệ thống | G0 → G3 (Fail) |
| QT-04-2 | Vắng < 20%: Tính Tổng điểm theo tỷ trọng thành phần | Hệ thống | G0 (In Progress) |
| QT-04-3 | Quét điều kiện liệt: FE < 4.0 HOẶC Tổng < 5.0 → Chốt THI LẠI | Hệ thống | G0 → G4 (Retake) |
| QT-04-4 | Xét ĐK học lại: Đang G4 mà thi lại FE vẫn trượt → Chốt HỌC LẠI | Hệ thống | G4 → G5 (Re-study) |
| QT-04-5 | SV thỏa mãn (Vắng < 20%, FE ≥ 4.0, Tổng ≥ 5.0) → Chốt ĐẠT | Hệ thống | G0/G4 → G1 (Passed) |

## **4.2. Luồng Ngoại lệ & Sự cố thường gặp**

| **Mã** | **Tình huống** | **Cách xử lý** |
| --- | --- | --- |
| NL-01 | **Gian lận QR:** Sinh viên dùng app ngoài quét hộ. | Chặn hoàn toàn. Token mã hóa (AES-256) chỉ app PWA giải mã được. Kết hợp check IP nội bộ (BR-016). |
| NL-02 | **Mất kết nối mạng:** Không quét được QR. | GV điểm danh thủ công qua màn hình **MH-03-1**. Bắt buộc ghi Log giải trình. |
| NL-03 | **Payment rớt Webhook:** Tiền trừ nhưng hệ thống không gạch nợ. | Kế toán sử dụng tính năng trên màn hình **MH-06-1** để tra soát API và gạch nợ. Ghi Audit Log. |
| NL-04 | **Quá sĩ số lớp:** Phân lớp vượt MaxCapacity. | Chặn gán vào lớp trên màn hình **MH-01-4**, đưa SV vào danh sách Waitlisted (S0). |

# **CHƯƠNG 5. ĐẶC TẢ CHI TIẾT CHỨC NĂNG**

## **5.1. Nhóm 01-100 — Quản lý Sinh viên & Phân lớp**
**FS-QLSV-01-100-0010 — Import hồ sơ & Phân lớp chuyên ngành**

**① Mô tả & mục đích**
Số hóa danh sách sinh viên đầu vào, tự động cấp phát tài khoản và tự động chia lớp dựa trên MaxCapacity để tiết kiệm thời gian.

**② Tác nhân · Tiền điều kiện · Kích hoạt**
- Tác nhân: VT-01 Quản nhiệm.
- Kích hoạt: Upload file Excel danh sách SV trên **MH-01-2**. Thực hiện phân lớp trên **MH-01-4**.

**③ Logic xử lý**
1. Đọc file Excel, validate Unique constraint (CCCD, Mã SV, Email).
2. Phát hiện lỗi → bôi đỏ dòng, bỏ qua dòng lỗi, lưu dòng đúng.
3. Chặn đăng nhập với tài khoản trạng thái S3; giới hạn (Limited) với S2.
4. Auto-assign lớp: Hệ thống lặp qua danh sách SV mới (S0), kiểm tra `CurrentSize < MaxCapacity` của từng lớp, đưa SV vào lớp khả dụng, update thành S1.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-STUDENT-ID | String | ✱ | Unique (VLD-QLSV-01), Format (HExxxxxx) |
| FLD-STUDENT-CCCD | String | ✱ | Unique (VLD-QLSV-01), 12 chữ số |
| FLD-STUDENT-STATUS | Enum | ✱ | S0, S1, S2, S3, S4, S5 |

**⑤ Quy tắc nghiệp vụ áp dụng**
- **BR-001, BR-002**: Mã SV, CCCD, Email là duy nhất.
- **BR-003, BR-004**: Trạng thái S2/S3 gỡ khỏi lớp; Lớp không vượt sĩ số.
- **BR-005b, BR-043**: Xử lý logic thời hạn bảo lưu và kỷ luật.

**⑥ Hành vi màn hình**
- Import thành công báo số lượng cụ thể, có preview các dòng bị lỗi để người dùng sửa.

**⑦ Xử lý ngoại lệ & thông báo lỗi**
- ERR-QLSV-01: Trùng lặp Mã SV/CCCD khi import (Chặn lưu).

**⑧ Hậu điều kiện & đầu ra**
- SV được tạo thành công ở trạng thái S0, cấp tài khoản S1.

**⑨ Sự kiện phát sinh**
- EVT-STUDENT-CREATED

**⑩ Truy vết & nghiệm thu**
- NT: UC-02.NT01, UC-04.NT01

---

## **5.2. Nhóm 03-100 — Điểm danh bằng QR Code Động**
**FS-QLSV-03-100-0010 — Mở phiên QR & App Sinh viên quét mã**

**① Mô tả & mục đích**
Chống gian lận điểm danh hộ bằng QR refresh liên tục và mã hóa PWA.

**② Tác nhân · Tiền điều kiện · Kích hoạt**
- Tác nhân: VT-02 Giảng viên (mở phiên trên **MH-03-1**), VT-03 Sinh viên (quét trên **MH-03-3**).
- Kích hoạt: Giảng viên ấn btnOpenSession.

**③ Logic xử lý**
1. Server sinh chuỗi Token = AES256(SessionID + Timestamp + ClassID).
2. UI Giảng viên hiển thị mã QR, dùng SignalR/WebSockets refresh mã sau mỗi 10 giây.
3. SV mở PWA Camera trên **MH-03-3**, quét mã.
4. Gửi Token lên API. Giải mã Token:
   - Check `(Now - Timestamp) > 10s` → Lỗi mã hết hạn.
   - Check `ClientIP in AllowedRange` → Lỗi sai IP (nếu áp dụng BR-016).
5. Pass → Cập nhật `TT08.Status = Present`. Push Event xuống UI Giảng viên để tô xanh dòng.
6. Khi đóng phiên, tự động UPDATE tất cả SV còn lại thành Absent.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-QR-TOKEN | String | ✱ | Mã hóa AES-256 |
| FLD-REC-STATUS | Enum | ✱ | Present / Absent |
| FLD-MANUAL-EDIT | Bool | — | True nếu sửa tay, bắt buộc ghi log |

**⑤ Quy tắc nghiệp vụ áp dụng**
- **BR-013, BR-014, BR-016**: QR động, App nội bộ, Validate IP.
- **BR-017**: Tự động chốt Fail (G3) khi Absent >= 20%.
- **BR-018**: Sửa tay bắt buộc ghi Log.

**⑥ Hành vi màn hình**
- **MH-03-1**: QR lớn chiếm 80%, có thanh progress bar 10s.
- **MH-03-3**: Camera chiếm trọn, hiện overlay Thành công/Thất bại.

**⑦ Xử lý ngoại lệ & thông báo lỗi**
- ERR-QLSV-04: Quét bằng Zalo/Camera thường (Mã hóa không giải được).

**⑧ Hậu điều kiện & đầu ra**
- Bản ghi TT-08 trạng thái rõ ràng.

**⑨ Sự kiện phát sinh**
- EVT-ATTENDANCE-MARKED

**⑩ Truy vết & nghiệm thu**
- NT: UC-09.NT01, UC-09.NT02, UC-09.NT03

---

## **5.3. Nhóm 04-100 — Xét điều kiện điểm số tự động**
**FS-QLSV-04-100-0020 — Rule Engine xét G0 -> G1/G3/G4/G5**

**① Mô tả & mục đích**
Loại bỏ cảm tính con người. Tự động tính điểm và chốt trạng thái qua Background job dựa trên công thức đào tạo FPT.

**② Tác nhân · Tiền điều kiện · Kích hoạt**
- Tác nhân: Hệ thống (tự động), VT-01 Quản nhiệm (chốt sổ).
- Kích hoạt: Có đủ điểm FE và tiến hành "Chốt sổ" (Thực hiện trên module nghiệp vụ).

**③ Logic xử lý (Rule Engine)**
1. Tính `AbsentRatio = AbsentSlots / TotalSlots`. Nếu `>= 0.2` → UPDATE trạng thái `G3`. Stop.
2. Tính Tổng điểm (áp dụng tỷ trọng TT-20) = `Sum(Score * Weight)`. Round 1 số thập phân (BR-024).
3. Nếu `FE < 4.0` HOẶC `Tổng < 5.0`:
   - Nếu `hasRetaken` (đã thi lại lần 1) → UPDATE `G5`.
   - Nếu chưa thi lại → UPDATE `G4`.
4. Các trường hợp còn lại: UPDATE `G1` (Passed).

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-GRADE-TOTAL | Float | — | Min 0.0, Max 10.0, Step 0.1 |
| FLD-GRADE-STATUS | Enum | ✱ | G0, G1, G3, G4, G5 |
| FLD-IS-LOCKED | Bool | ✱ | Cờ khóa bảng điểm |

**⑤ Quy tắc nghiệp vụ áp dụng**
- **BR-019, BR-020**: Thang 10, Chốt sổ cấm GV sửa điểm trên **MH-04-1**.
- **BR-021, BR-022, BR-023**: Điều kiện liệt, thi lại, học lại.
- **BR-025b, BR-025c**: Giới hạn số lần thi lại/học lại.
- **BR-051**: Sửa sau chốt phải qua Admin và ghi Audit Log vĩnh viễn.

**⑥ Hành vi màn hình**
- GV nhập điểm trên **MH-04-1**. Sau khi có xác nhận chốt, DataGrid của GV lập tức chuyển thành Read-only (Disabled).
- SV xem điểm qua **MH-04-2**. Các dòng G3, G4, G5 sẽ bị highlight/bôi đỏ cảnh báo.

**⑦ Xử lý ngoại lệ & thông báo lỗi**
- VLD-QLSV-04: Nhập điểm ngoài dải 0.0 - 10.0 (Chặn, viền đỏ).
- VLD-QLSV-05: Sửa điểm sau chốt thiếu Lý do (Chặn).

**⑧ Hậu điều kiện & đầu ra**
- TT-09 được chốt, GV không sửa được nữa.

**⑨ Sự kiện phát sinh**
- EVT-GRADE-LOCKED

**⑩ Truy vết & nghiệm thu**
- NT: UC-11.NT01, UC-11.NT02

---

## **5.4. Nhóm 06-100 — Thanh toán (Payment Gateway)**
**FS-QLSV-06-100-0010 — Tích hợp VNPay/MoMo & Tra soát**

**① Mô tả & mục đích**
Gạch nợ tự động học phí, xử lý rớt mạng/mất webhook.

**② Tác nhân · Tiền điều kiện · Kích hoạt**
- Tác nhân: VT-03 Sinh viên (**MH-06-2**), VT-04 Kế toán/Quản nhiệm (**MH-06-1**), VNPay.
- Kích hoạt: Nút "Thanh toán" tại **MH-06-2**.

**③ Logic xử lý**
1. SV chọn hóa đơn `Unpaid`. Gen mã phiên giao dịch (hạn 15p).
2. Điều hướng qua cổng thanh toán VNPay/MoMo.
3. VNPay gọi IPN Webhook về hệ thống.
4. Verify chữ ký `HMAC SHA512`. Nếu đúng, check số tiền (BR-031). Đổi hóa đơn sang `Paid`. Giao dịch sang `Success`.
5. Background job hàng ngày quét hóa đơn quá `DueDate`, chuyển thành `Overdue`.
6. Kế toán sử dụng **MH-06-1** để nhấn "Query Transaction", gọi API `vnp_Querydr` của VNPay để đồng bộ lại nếu Webhook rớt.

**④ Đặc tả trường dữ liệu**

| **Trường (Mã)** | **Kiểu** | **✱** | **Validate** |
| --- | --- | --- | --- |
| FLD-INV-AMOUNT | Decimal | ✱ | Số tiền khớp 100% |
| FLD-INV-STATUS | Enum | ✱ | Unpaid / Paid / Overdue / Cancelled |
| FLD-TXN-STATUS | Enum | ✱ | Pending / Success / Failed |

**⑤ Quy tắc nghiệp vụ áp dụng**
- **BR-030, BR-031**: Session 15p, Khớp tiền 100%.
- **BR-035**: Gạch nợ thủ công phải lưu Log.
- **BR-046**: Overdue chặn SV đăng ký/xem điểm.

**⑥ Hành vi màn hình**
- Báo cáo Giao dịch (**MH-06-1**) cho phép phân biệt rõ doanh thu đã gạch tự động qua Webhook so với gạch tay thủ công.

**⑦ Xử lý ngoại lệ & thông báo lỗi**
- ERR-QLSV-05: Checksum trả về sai (Nghi vấn giả mạo) → Chặn gạch nợ.

**⑧ Hậu điều kiện & đầu ra**
- Hóa đơn chuyển trạng thái an toàn.

**⑨ Sự kiện phát sinh**
- EVT-PAYMENT-SUCCESS

**⑩ Truy vết & nghiệm thu**
- NT: UC-16.NT01, UC-16.NT02

---

# **CHƯƠNG 6. ĐẶC TẢ GIAO DIỆN CHÍNH**

| **Mã MH** | **Đặc tả UI & Hành vi** |
| --- | --- |
| **MH-03-1** | (Mở QR Điểm Danh) Hiển thị QR Code kích thước lớn chiếm 80% màn chiếu, đếm ngược 10 giây bên dưới để refresh QR mới. Bảng danh sách bên cạnh Real-time cập nhật dòng xanh (Present) khi có SV quét thành công. |
| **MH-03-3** | (Lịch Học - PWA Scan QR) Tích hợp chức năng bật camera với vùng nhận diện định sẵn trên di động, hiện trạng thái “Thành công” nền xanh lá khi quét đúng mã QR của giảng viên. |
| **MH-04-1** | (Cập nhật điểm quá trình) Grid nhập điểm dành cho GV. Ô nhập điểm tự động validate < 0 hoặc > 10. Sau khi lớp được "Chốt sổ", toàn bộ Grid sẽ bị khóa cứng (Read-only). |
| **MH-06-1** | (Lịch sử giao dịch) Kế toán/Quản nhiệm xem danh sách giao dịch. Có nút "Truy vấn API" để chủ động gọi lệnh tra soát lên cổng thanh toán VNPay nếu trạng thái là Pending. Form gạch nợ tay yêu cầu nhập Log lý do đầy đủ. |

# **CHƯƠNG 7. MÁY TRẠNG THÁI HỒ SƠ**

## **7.1. Trạng thái Sinh viên (TT-01)**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp được** |
| --- | --- | --- | --- |
| S0 | Mới (Initialized) | Vừa Import | → S1 (Khi gán lớp) |
| S1 | Đang học (Active) | Có lớp, đang học | → S2, S3, S4, S5 |
| S2 | Bảo lưu (Suspended) | Có QĐ tạm ngừng | → S1 (Tái nhập), S3 |
| S3 | Thôi học (Dropped) | Nghỉ học vĩnh viễn | (Trạng thái cuối) |
| S4 | Tốt nghiệp | Pass hết, hết nợ | (Trạng thái cuối) |
| S5 | Đình chỉ | Vi phạm kỷ luật | → S1 (Hết hạn), S3 |

## **7.2. Trạng thái Bảng điểm Môn học (TT-09)**

| **Mã** | **Trạng thái** | **Điều kiện vào** | **Chuyển tiếp được** |
| --- | --- | --- | --- |
| G0 | In Progress | Đang theo học | → G1, G3, G4 |
| G1 | Passed | Vắng<20%, FE≥4.0, Tổng≥5.0 | (Cuối môn) |
| G3 | Fail (Cấm thi) | Vắng ≥ 20% | → G5 (ĐK học lại) |
| G4 | Retake (Thi lại) | FE<4.0 hoặc Tổng<5.0 | → G1 (Đạt), G5 (Trượt) |
| G5 | Re-study (Học lại) | Từ G3 hoặc trượt G4 | → G0 (ĐK học lại kỳ mới) |

# **CHƯƠNG 8. QUY TẮC NGHIỆP VỤ & CHỐT CHẶN CỨNG**

| **Quy tắc (BR)** | **Nội dung chốt chặn** | **Áp dụng tại** | **Vì sao chặn là đúng** |
| --- | --- | --- | --- |
| **BR-001/002** | Mã SV, CCCD, Email phải duy nhất | FS-QLSV-01-100 | Tránh nhầm lẫn dữ liệu. |
| **BR-003** | Bảo lưu/Thôi học bị gỡ khỏi lớp | Nhóm 01-100 | SV thôi học không được phép tồn tại trong TKB và điểm danh. |
| **BR-017** | Vắng ≥ 20% chốt Fail thẳng | FS-QLSV-03-100 | Tuân thủ tuyệt đối quy chế đào tạo FPT. |
| **BR-020** | Sau “Chốt sổ”, GV không được sửa | FS-QLSV-04-100 | Toàn vẹn bảng điểm cuối kỳ đã công bố. |
| **BR-038** | Chặn ĐK học lại với SV S5 | Nhóm 07-100 | Chấp hành quy chế kỷ luật nghiêm khắc. |
| **BR-044** | Tốt nghiệp: Pass hết, trả nợ, không S5 | Nhóm 01-100 | ĐK tiên quyết để nhận bằng cử nhân. |
| **BR-046** | Hóa đơn Overdue chặn xem điểm/đăng ký | FS-QLSV-06-100 | Ép buộc hoàn thành nghĩa vụ tài chính. |
| **BR-051** | Mọi thay đổi dữ liệu lõi phải có Audit Log | Toàn hệ | Vết dữ liệu là bằng chứng khi có khiếu nại. |

# **CHƯƠNG 9. QUY TẮC KIỂM TRA DỮ LIỆU (VALIDATION)**

| **Mã** | **Quy tắc kiểm tra** | **Mức xử lý** |
| --- | --- | --- |
| VLD-QLSV-01 | Trùng lặp CCCD/Email/MSSV khi import | **CHẶN**, highlight dòng lỗi |
| VLD-QLSV-02 | Lớp học vượt quá sĩ số tối đa (MaxCapacity) | **CHẶN**, đưa vào danh sách chờ (Waitlisted) |
| VLD-QLSV-03 | Quét QR Code đã quá hạn 10s | **CHẶN**, báo "Mã hết hạn" |
| VLD-QLSV-04 | GV sửa điểm thành phần ngoài dải 0.0 - 10.0 | **CHẶN**, viền ô màu đỏ không cho lưu |
| VLD-QLSV-05 | Admin sửa điểm sau chốt sổ mà không có Lý do | **CHẶN**, bắt buộc nhập (Min 20 ký tự) |
| VLD-QLSV-06 | Mật khẩu tài khoản không đủ độ mạnh (BR-048) | **CHẶN**, yêu cầu (≥ 8, 1 hoa, 1 số, 1 đặc biệt) |
| VLD-QLSV-07 | Deadlock vòng lặp môn tiên quyết | **CHẶN** lưu cấu hình môn học |

# **CHƯƠNG 10. TÍCH HỢP & SỰ KIỆN**

| **Chiều tích hợp** | **Nội dung** | **Dữ liệu giao tiếp** | **Ghi chú** |
| --- | --- | --- | --- |
| **Hệ thống → VNPay/MoMo** | Thanh toán học phí | URL Thanh toán (Checksum, Số tiền) | Hỗ trợ IPN Webhook |
| **Hệ thống → Mailing Service** | Gửi Email cảnh báo vắng | HTML Template, Email | Xử lý Background Queue |
| **Google/Microsoft → Hệ thống**| Đăng nhập SSO | OAuth 2.0 Token | Giới hạn miền @fpt.edu.vn |

### **Sự kiện hệ thống (Events)**
- `EVT-STUDENT-ATTENDANCE-FAILED`: Kích hoạt khi chạm mốc vắng 20%.
- `EVT-PAYMENT-SUCCESS`: Kích hoạt khi Webhook trả về thành công.
- `EVT-GRADE-LOCKED`: Khóa DataGrid khi QN chốt sổ điểm.

# **CHƯƠNG 11. DANH MỤC THÔNG BÁO LỖI (ERRORS)**

| **Mã lỗi** | **Điều kiện** | **Loại** |
| --- | --- | --- |
| ERR-QLSV-01 | Trùng lặp Mã SV/CCCD khi import danh sách | Chặn lưu |
| ERR-QLSV-02 | Xếp GV dạy 2 lớp trùng Slot / Trùng phòng | Chặn lưu TKB |
| ERR-QLSV-04 | SV quét QR Code bằng App ngoài (Zalo/Camera thường) | Chặn giải mã |
| ERR-QLSV-05 | Checksum VNPay trả về không khớp | Cảnh báo Admin, Chặn gạch nợ |
| ERR-QLSV-06 | Sinh viên S5 (Đình chỉ) cố tình đăng ký học | Chặn lệnh, báo đỏ |

# **CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR ĐO ĐƯỢC)**

| **Mã** | **Nhóm** | **Yêu cầu** | **Cách đo kiểm / Ngưỡng** |
| --- | --- | --- | --- |
| NFR-01 | Hiệu năng | Đăng nhập & cấp Token | ≤ 1 giây |
| NFR-02 | Hiệu năng | Import 1.000 bản ghi SV | ≤ 10 giây |
| NFR-03 | Hiệu năng | Xác thực QR Code | ≤ 2 giây (Test 200 SV quét đồng thời) |
| NFR-04 | Hiệu năng | Xếp TKB tự động 200 SV | ≤ 30 giây (0% Conflict) |
| NFR-06 | Hiệu năng | Tính điểm toàn bộ 200 SV | ≤ 30 giây |
| NFR-10 | Bảo mật | Hash mật khẩu một chiều | Bcrypt/Argon2 (Kiểm tra DB bản rõ) |
| NFR-11 | Bảo mật | Chống Spam Login | Khóa 15p sau 5 lần sai (BR-049) |
| NFR-13 | Truy vết | Audit Trail | Log thao tác điểm (who/when/old/new) không thể xóa từ UI |
| NFR-14 | Vận hành | Backup Data | Daily backup, lưu 30 ngày |

# **CHƯƠNG 13. MA TRẬN TRUY VẾT & NGHIỆM THU**

| **Mã NT** | **Tiêu chí nghiệm thu (Acceptance Criteria)** | **Nguồn truy vết (Đặc tả / BR)** |
| --- | --- | --- |
| UC-02.NT01 | Import file hợp lệ: tạo đủ hồ sơ + tài khoản ≤ 10s. | FS-QLSV-01-100, BR-001, VLD-01, MH-01-2 |
| UC-04.NT01 | Phân lớp không vượt MaxCapacity, sĩ số đều. | FS-QLSV-01-100, BR-004, MH-01-4 |
| UC-07.NT01 | Xếp TKB tự động ra kết quả 0% Conflict phòng/GV. | FS-QLSV-02-100, BR-008, BR-009, MH-02-3 |
| UC-09.NT01 | QR refresh mỗi 10s, quét thành công → Present real-time. | FS-QLSV-03-100, BR-013, MH-03-1, MH-03-3 |
| UC-11.NT01 | Chuyển trạng thái G1/G3/G4/G5 đúng quy chế, % vắng, điểm FE. | FS-QLSV-04-100, BR-021->025c, MH-04-1 |
| UC-12.NT02 | Chặn tuyệt đối SV bị đình chỉ (S5) đăng ký học lại. | Nhóm 07-100, BR-038 |
| UC-16.NT01 | VNPay thành công → Paid tự động. Mất webhook có gạch tay. | FS-QLSV-06-100, BR-031, BR-035, MH-06-2 |
| UC-16.NT02 | Webhook bị mất → Kế toán Query Transaction thành công. | FS-QLSV-06-100, BR-034, MH-06-1 |

_Hết tài liệu._