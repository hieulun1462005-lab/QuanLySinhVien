**TÀI LIỆU YÊU CẦU NGHIỆP VỤ — CHI TIẾT PHÂN HỆ**

**MODULE BUSINESS REQUIREMENTS DOCUMENT (BRD)**

**HỆ THỐNG QUẢN LÝ SINH VIÊN**

**STUDENT MANAGEMENT SYSTEM**

_Hệ thống quản lý đào tạo — Đại học FPT — Quy mô 1.000–1.500 sinh viên_

| **Thuộc tính** | **Nội dung** |
| --- | --- |
| Tên dự án | Xây dựng Hệ thống Quản Lý Sinh Viên (QLSV) |
| Loại tài liệu | Business Requirements Document — Chi tiết phân hệ |
| Mã tài liệu | BRD-QLSV-v5.0 |
| Phiên bản | 5.0 |
| Trạng thái | Chờ phê duyệt |
| Ngày phát hành | 23/09/2026 |
| Đơn vị xây dựng | ONENET |
| Mức độ mật | Nội bộ — Hạn chế |

---

# KIỂM SOÁT TÀI LIỆU

## Lịch sử phiên bản

| **Phiên bản** | **Ngày** | **Người thực hiện** | **Nội dung thay đổi** |
| --- | --- | --- | --- |
| 1.0 | 16/09/2026 | Khánh, Hiếu | Khởi tạo tài liệu Draft. |
| 2.0 | 16/09/2026 | Khánh, Hiếu | Sửa mâu thuẫn điểm số (Pass/Retake/Fail), thêm Data Dictionary, bổ sung quy trình Đăng nhập, Quản lý GV/Phòng, thêm NFR. |
| 3.0 | 17/09/2026 | Khánh, Hiếu | Thêm UC-12 (Đăng ký Học lại & Xếp lớp môn trượt), cơ chế Đình chỉ (S5), BR-036→BR-041, TT-15/TT-16, màn hình MH-04-4/MH-05-1/MH-05-2. |
| 3.1 | 17/09/2026 | Khánh, Hiếu | Soát lỗi toàn diện: Khắc phục mâu thuẫn nghiệp vụ (QR Code, BR-018), sửa lỗi cấu trúc Mục lục, bổ sung Tiêu chí Nghiệm thu, chuẩn hóa Data Dictionary & Ma trận truy vết. |
| 4.0 | 21/09/2026 | Khánh, Hiếu | Review toàn diện: Thống nhất KPI/NFR, bổ sung Glossary, thêm bảng Giảng viên (TT-17) & Notification (TT-18), bổ sung BR-042→BR-047, UC-14/UC-15, hoàn thiện Tiêu chí Nghiệm thu, sửa RBAC & State Machine, thêm DateOfBirth/Semester vào Data Dictionary, tách bảng PreRequisite & Grade Weight, làm rõ PWA cho QR. |
| 5.0 | 23/09/2026 | Khánh, Hiếu | Tái cấu trúc toàn diện theo template BRD chuẩn: chuẩn hóa mã định danh, sửa tham chiếu chéo UC/BR/NFR, đồng nhất bảng markdown, bổ sung BR-048→BR-051, đánh lại NFR liên tục, sửa ma trận truy vết & tiêu chí nghiệm thu, bổ sung mục Tài liệu tham chiếu. |

## Phê duyệt tài liệu

| **Vai trò** | **Họ tên / Đơn vị** | **Trách nhiệm** | **Ngày / Ký** |
| --- | --- | --- | --- |
| Người soạn | Khánh, Hiếu — BA / Developer | Biên soạn nội dung tài liệu |     |
| Người rà soát | Trưởng nhóm phát triển | Rà soát tính đúng đắn nghiệp vụ & kỹ thuật |     |
| Người phê duyệt | Ban lãnh đạo | Phê duyệt phạm vi & mục tiêu nghiệp vụ |     |

_Phạm vi tài liệu: Tài liệu BRD chi tiết phân hệ Quản lý Sinh viên, kế thừa nguyên tắc, quy ước mã định danh và template quy trình chuẩn._

---

# MỤC LỤC

[KIỂM SOÁT TÀI LIỆU](#kiểm-soát-tài-liệu)

[CHƯƠNG 0. QUY ƯỚC MÃ ĐỊNH DANH (BẮT BUỘC)](#chương-0-quy-ước-mã-định-danh-bắt-buộc)

[CHƯƠNG 1. GIỚI THIỆU TÀI LIỆU](#chương-1-giới-thiệu-tài-liệu)

- [1.1. Mục đích tài liệu](#11-mục-đích-tài-liệu)
- [1.2. Phạm vi tài liệu](#12-phạm-vi-tài-liệu)
- [1.3. Đối tượng sử dụng tài liệu](#13-đối-tượng-sử-dụng-tài-liệu)
- [1.4. Tài liệu tham chiếu](#14-tài-liệu-tham-chiếu)
- [1.5. Thuật ngữ và từ viết tắt](#15-thuật-ngữ-và-từ-viết-tắt)

[CHƯƠNG 2. BỐI CẢNH, MỤC TIÊU & QUY MÔ](#chương-2-bối-cảnh-mục-tiêu--quy-mô)

- [2.1. Các bên liên quan (Stakeholders)](#21-các-bên-liên-quan-stakeholders)
- [2.2. Mục tiêu & KPI](#22-mục-tiêu--kpi)
- [2.3. Quy mô triển khai](#23-quy-mô-triển-khai)
- [2.4. Giả định & Ràng buộc](#24-giả-định--ràng-buộc)
- [2.5. Rủi ro](#25-rủi-ro)

[CHƯƠNG 3. KIẾN TRÚC NGHIỆP VỤ](#chương-3-kiến-trúc-nghiệp-vụ)

[CHƯƠNG 4. DANH MỤC PHÂN HỆ & MÃ ĐỊNH DANH](#chương-4-danh-mục-phân-hệ--mã-định-danh)

[CHƯƠNG 5. NGUYÊN TẮC & QUY TẮC NGHIỆP VỤ BẮT BUỘC](#chương-5-nguyên-tắc--quy-tắc-nghiệp-vụ-bắt-buộc)

[CHƯƠNG 6. TÁC NHÂN, VAI TRÒ & THỰC THỂ NGHIỆP VỤ](#chương-6-tác-nhân-vai-trò--thực-thể-nghiệp-vụ)

[CHƯƠNG 7. QUY TRÌNH NGHIỆP VỤ ĐẦU–CUỐI](#chương-7-quy-trình-nghiệp-vụ-đầu–cuối)

[CHƯƠNG 8. BẢNG TRẠNG THÁI CÁC THỰC THỂ CHÍNH](#chương-8-bảng-trạng-thái-các-thực-thể-chính)

[CHƯƠNG 9. MA TRẬN PHÂN QUYỀN (RBAC)](#chương-9-ma-trận-phân-quyền-rbac)

[CHƯƠNG 10. DANH SÁCH MÀN HÌNH UI THEO PHÂN HỆ](#chương-10-danh-sách-màn-hình-ui-theo-phân-hệ)

[CHƯƠNG 11. TIÊU CHÍ NGHIỆM THU NGHIỆP VỤ](#chương-11-tiêu-chí-nghiệm-thu-nghiệp-vụ)

[CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR)](#chương-12-yêu-cầu-phi-chức-năng-nfr)

[CHƯƠNG 13. YÊU CẦU TÍCH HỢP](#chương-13-yêu-cầu-tích-hợp)

[CHƯƠNG 14. TUÂN THỦ PHÁP LÝ & QUY CHẾ](#chương-14-tuân-thủ-pháp-lý--quy-chế)

[CHƯƠNG 15. DANH MỤC DÙNG CHUNG](#chương-15-danh-mục-dùng-chung)

[CHƯƠNG 16. MA TRẬN TRUY VẾT & LỘ TRÌNH BRD](#chương-16-ma-trận-truy-vết--lộ-trình-brd)

---

# CHƯƠNG 0. QUY ƯỚC MÃ ĐỊNH DANH (BẮT BUỘC)

Mọi đối tượng trong tài liệu đều có mã định danh duy nhất, phục vụ truy vết xuyên suốt từ nghiệp vụ đến kiểm thử. Quy ước như sau:

| **Loại đối tượng** | **Cấu trúc mã** | **Ví dụ** | **Diễn giải** |
| --- | --- | --- | --- |
| Phân hệ | QLSV-&lt;số 2 chữ số&gt; | QLSV-01 | Quản lý Sinh viên |
| Nhóm chức năng (cấp 2) | QLSV-xx-N00 | QLSV-01-100 | Nhóm chức năng đầu tiên của QLSV-01 |
| Chức năng chi tiết (cấp 3) | QLSV-xx-N00-MMMM | QLSV-01-100-0010 | Chức năng chi tiết thứ 1 |
| Yêu cầu nghiệp vụ | YCNV-QLSV-xx-N00-MMMM | YCNV-QLSV-01-100-0010 | Yêu cầu nghiệp vụ tương ứng |
| Quy tắc nghiệp vụ | BR-&lt;3 số&gt; | BR-001 | Quy tắc bắt buộc chung |
| Quy trình (Use Case) | UC-&lt;2 số&gt; | UC-01 | Xác thực & Quản lý tài khoản |
| Tiêu chí nghiệm thu UC | &lt;mã UC&gt;.NT&lt;2 số&gt; | UC-01.NT01 | Tiêu chí nghiệm thu thứ 1 của UC-01 |
| Thực thể nghiệp vụ | TT-&lt;2 số&gt; | TT-01 | Hồ sơ Sinh viên |
| Vai trò / Tác nhân | VT-&lt;2 số&gt; | VT-01 | Quản nhiệm |
| Màn hình UI | MH-&lt;Module&gt;-&lt;số&gt; | MH-01-1 | Màn hình Import hồ sơ SV |
| Điểm tích hợp | TH-&lt;2 số&gt; | TH-01 | Tích hợp Payment Gateway |
| Yêu cầu phi chức năng | NFR-&lt;2 số&gt; | NFR-01 | Hiệu năng đăng nhập |

_Nguyên tắc đánh mã: Cấp 2 dùng bội số 100; cấp 3 dùng bội số 10. Không tái dùng mã đã hủy. Quy ước mã bất biến giữa các phiên bản tài liệu._

---

# CHƯƠNG 1. GIỚI THIỆU TÀI LIỆU

## 1.1. Mục đích tài liệu

Tài liệu Yêu cầu nghiệp vụ (BRD) mô tả toàn bộ nhu cầu nghiệp vụ, quy trình, quy tắc, dữ liệu và tiêu chí nghiệm thu cho **Hệ thống Quản Lý Sinh Viên** — một ứng dụng web (Progressive Web App) tập trung nhằm số hóa và tự động hóa các hoạt động quản lý đào tạo tại trường Đại học FPT. Tài liệu được biên soạn đủ chi tiết để suy ra các tài liệu cấp dưới:

- **FRD/SRS** – Đặc tả yêu cầu chức năng và phi chức năng chi tiết theo từng phân hệ.
- **Thiết kế UI/UX** – Danh sách màn hình, luồng thao tác theo vị trí tác nghiệp.
- **Thiết kế API & tích hợp** – Hợp đồng dịch vụ, sự kiện, tích hợp Payment Gateway & SSO.
- **Kịch bản kiểm thử (test case)** – Bắt nguồn từ luồng chính, luồng ngoại lệ và tiêu chí nghiệm thu.
- **Kế hoạch triển khai & nghiệm thu (UAT)** – Dựa trên tiêu chí nghiệm thu nghiệp vụ.

## 1.2. Phạm vi tài liệu

**Trong phạm vi (In-scope)**

- **Module Quản lý Sinh viên (QLSV-01):** Quản lý hồ sơ (CCCD, địa chỉ), theo dõi trạng thái học tập.
- **Module Chương trình đào tạo & Thời khóa biểu (QLSV-02):** Quản lý cây môn học, điều kiện tiên quyết, xếp lịch và đồng bộ TKB theo Slot chuẩn.
- **Module Điểm danh (QLSV-03):** Quét QR động (real-time) qua trình duyệt mobile (PWA) cho sinh viên và hệ thống tự động gửi Email cảnh báo vắng học.
- **Module Quản lý Điểm & Khảo thí (QLSV-04):** Nhập/tính điểm tổng kết, tự động xét điều kiện thi/PASS/FAIL/RETAKE theo Quy chế FPT.
- **Module Dịch vụ Sinh viên — Hành chính (QLSV-05):** Cổng nộp đơn từ trực tuyến, duyệt đơn và theo dõi trạng thái dành cho Quản nhiệm.
- **Module Thanh toán — Payment Gateway (QLSV-06):** Tích hợp Payment Gateway, tự động gạch nợ học phí và hỗ trợ kế toán đối soát.

**Ngoài phạm vi (Out-of-scope)**

- **Phân hệ Tuyển sinh:** Không quản lý data học sinh cấp 3, quy trình thi tuyển hay nhập học đầu vào.
- **Quản lý Nhân sự & Lương Giảng viên:** Hệ thống chỉ lưu thông tin giảng viên để xếp lớp, KHÔNG tính lương, chấm công hay quản lý hợp đồng giảng viên.
- **Quản lý Thư viện / Ký túc xá:** Không nằm trong hệ sinh thái của dự án này.
- **Ứng dụng Native Mobile (iOS/Android):** Hệ thống là Progressive Web App (PWA), không phát triển ứng dụng mobile riêng biệt.

## 1.3. Đối tượng sử dụng tài liệu

| **Đối tượng** | **Mục đích sử dụng** |
| --- | --- |
| Ban lãnh đạo / Người phê duyệt dự án | Xác nhận phạm vi, mục tiêu và tiêu chí nghiệm thu nghiệp vụ. |
| Quản nhiệm (Academic Staff) / Giảng viên | Rà soát tính đúng đắn của quy trình và thao tác nghiệp vụ. |
| Đội ngũ phát triển (Developer, Tester, DevOps) | Cơ sở xây dựng FRD/SRS, thiết kế kiến trúc, API, dữ liệu, phân quyền. |
| Kế toán / Bộ phận hành chính | Rà soát quy trình thanh toán, đối soát và báo cáo tài chính. |
| QA/QC & UAT | Cơ sở xây dựng test case và kịch bản nghiệm thu. |

## 1.4. Tài liệu tham chiếu

| **Mã** | **Văn bản / Tiêu chuẩn tham chiếu** | **Áp dụng** |
| --- | --- | --- |
| TL-01 | Quy chế đào tạo Đại học FPT (hiện hành) | Điểm liệt, vắng quá 20%, công thức tính điểm |
| TL-02 | Nghị định 13/2023/NĐ-CP về bảo vệ dữ liệu cá nhân | Bảo mật dữ liệu sinh viên |
| TL-03 | Quy định thanh toán điện tử VNPay/MoMo API | Tích hợp Payment Gateway |
| TL-04 | OAuth 2.0 / OpenID Connect Specification | Xác thực SSO Google/Microsoft |

_Lưu ý: Danh mục tham chiếu mang tính định hướng; khi triển khai phải rà soát phiên bản quy chế còn hiệu lực tại thời điểm nghiệm thu._

## 1.5. Thuật ngữ và từ viết tắt

| **Viết tắt** | **Diễn giải** |
| --- | --- |
| SV | Sinh viên |
| GV | Giảng viên |
| QN | Quản nhiệm (Academic Staff) |
| TKB | Thời khóa biểu |
| CTĐT | Chương trình đào tạo |
| Slot | Khung giờ học chuẩn FPT (VD: Slot 1 = 07:30–09:50) |
| Block | Đơn vị thời gian học (thường 5–7 tuần) trong 1 học kỳ |
| FE | Final Exam — Bài thi cuối kỳ |
| TP | Thành phần — Điểm quá trình (Quiz, Assignment, Lab) |
| QR Token | Chuỗi mã hóa động nhúng trong QR Code, refresh mỗi 10 giây |
| PWA | Progressive Web App — Ứng dụng web có thể cài đặt trên mobile và truy cập camera |
| IPN / Webhook | Instant Payment Notification — Cổng thanh toán gọi ngược về Server để thông báo kết quả |
| RBAC | Role-Based Access Control — Kiểm soát truy cập dựa trên vai trò |
| SSO | Single Sign-On — Đăng nhập một lần (Google/Microsoft) |
| CCCD | Căn Cước Công Dân |
| MSSV | Mã số sinh viên |
| BR | Business Rule — Quy tắc nghiệp vụ bắt buộc |
| UC | Use Case — Quy trình nghiệp vụ |
| NFR | Non-Functional Requirement — Yêu cầu phi chức năng |
| G0–G5 | Mã trạng thái môn học: In Progress / Passed / _(bỏ G2)_ / Fail / Retake / Re-study |
| S0–S5 | Mã trạng thái sinh viên: Initialized / Active / Suspended / Dropped / Graduated / Disciplinary |

---

# CHƯƠNG 2. BỐI CẢNH, MỤC TIÊU & QUY MÔ

## 2.1. Các bên liên quan (Stakeholders)

| **Nhóm** | **Vai trò** | **Quan tâm chính** |
| --- | --- | --- |
| Quản lý | Quản nhiệm (Academic Staff) | Quản lý hồ sơ SV, phân lớp, xếp TKB, duyệt đơn từ |
| Chuyên môn | Giảng viên | Điểm danh, nhập điểm, báo nghỉ/xếp lịch bù |
| Người dùng | Sinh viên | Xem TKB, quét QR điểm danh, xem điểm, nộp đơn, thanh toán |
| Tài chính | Kế toán | Đối soát giao dịch, tra soát, xuất báo cáo |
| Hệ thống | Admin | Quản trị hệ thống, cấp quyền, sửa điểm ngoại lệ |

## 2.2. Mục tiêu & KPI

| **Mã** | **Mục tiêu** | **KPI / Ngưỡng** |
| --- | --- | --- |
| G-01 | Tự động hóa & Trung tâm hóa Quản lý Sinh viên: Chuẩn hóa toàn bộ sơ yếu lý lịch (CCCD, địa chỉ, giới tính) và tự động theo dõi trạng thái học tập. | 100% hồ sơ SV được số hóa; Thời gian import 1.000 bản ghi ≤ 10 giây. |
| G-02 | Số hóa Chương trình học & Thời khóa biểu Real-time: Quản lý cây chương trình đào tạo, môn tiên quyết và tự động đồng bộ TKB theo hệ thống Slot chuẩn FPT. | Thuật toán xếp lịch tự động cho 200 SV hoàn tất ≤ 30 giây; 0% xung đột (Conflict). |
| G-03 | Hiện đại hóa Điểm danh & Cảnh báo chủ động: Tự động hóa điểm danh bằng QR Động, cảnh báo Email ngay khi SV chạm ngưỡng vắng 20%. | Xác thực QR ≤ 2 giây; Email cảnh báo gửi đi ≤ 2 phút sau chốt phiên. |
| G-04 | Minh bạch hóa Quản lý Điểm số & Xét điều kiện: Tự động tính điểm tổng kết theo tỷ trọng và ràng buộc điều kiện thi/đạt môn theo Quy chế FPT. | Tính điểm toàn bộ 200 SV ≤ 30 giây; Độ chính xác 100% theo công thức. |
| G-05 | Tối ưu hóa & Số hóa hành chính: Hỗ trợ SV nộp đơn từ trực tuyến, giảm thời gian xử lý giấy tờ. | 100% đơn từ được nộp trực tuyến; Email kết quả duyệt đơn ≤ 1 phút. |
| G-06 | Tích hợp Payment Gateway: Tự động gạch nợ và hỗ trợ kế toán đối soát. | Giao dịch mã hóa SSL/TLS; Export báo cáo 5.000 dòng ≤ 15 giây. |

## 2.3. Quy mô triển khai

| **Chỉ tiêu** | **Quy mô mục tiêu** |
| --- | --- |
| Sinh viên | 1.000 – 1.500 (chia 30–50 lớp chuyên ngành) |
| Giảng viên | 50 – 100 |
| Cán bộ Quản nhiệm & Admin | 5 – 10 |
| Tải trọng dữ liệu / học kỳ | 15.000–20.000 lượt điểm danh; 10.000 đầu điểm TP; 1.000–3.000 giao dịch thanh toán/đơn từ |

## 2.4. Giả định & Ràng buộc

| **Loại** | **Nội dung** |
| --- | --- |
| Giả định | Dữ liệu đầu vào (danh sách SV) được cung cấp dưới dạng Excel/CSV theo biểu mẫu chuẩn. |
| Giả định | Các khung giờ Slot chuẩn (Slot 1: 7h30–9h50, Slot 2…) đã được cấu hình tĩnh trong hệ thống. |
| Giả định | Trường cung cấp mạng WiFi ổn định cho việc quét QR điểm danh. |
| Giả định | Trình duyệt mobile của SV hỗ trợ WebRTC/Camera API (Chrome, Safari phiên bản hiện tại). |
| Ràng buộc | Hệ thống xây dựng trên nền tảng ASP.NET Core MVC, MS SQL Server, triển khai dạng PWA. |
| Ràng buộc | Tích hợp Payment Gateway phụ thuộc vào API bên thứ 3 (VNPay/MoMo). |
| Ràng buộc | Quy chế tính điểm tuân theo quy chế đào tạo của FPT hiện hành. |

## 2.5. Rủi ro

| **Mã** | **Rủi ro** | **Mức độ** | **Biện pháp giảm thiểu** |
| --- | --- | --- | --- |
| R-01 | Phụ thuộc vào dịch vụ bên thứ ba (Payment Gateway, Email) | Cao | Thiết kế linh hoạt, dễ dàng thay thế hoặc chuyển đổi dịch vụ. |
| R-02 | Tính toàn vẹn và độ tin cậy của dữ liệu người dùng | Trung bình | Áp dụng các quy trình kiểm tra chéo và phân quyền chặt chẽ. |
| R-03 | Rủi ro về hạ tầng mạng và kết nối hệ thống | Trung bình | Xây dựng quy trình xử lý ngoại lệ và thao tác thủ công dự phòng. |

---

# CHƯƠNG 3. KIẾN TRÚC NGHIỆP VỤ

## 3.1. Nguyên tắc thiết kế

Hệ thống được thiết kế theo kiến trúc **Modular Monolithic** kết hợp mô hình **MVC** (Model – View – Controller) nhằm đảm bảo tính đơn giản trong triển khai và vận hành, đồng thời phân tách rõ ràng các phân hệ nghiệp vụ.

| **Nguyên tắc** | **Diễn giải** |
| --- | --- |
| Sinh viên là trung tâm | Mọi dữ liệu phát sinh được liên kết vào một hồ sơ sinh viên thống nhất theo suốt vòng đời học tập. |
| Số hóa ngay từ đầu | Ưu tiên dữ liệu điện tử; điểm danh, bảng điểm, đơn từ đều quản lý trên hệ thống. |
| Không nhập liệu lặp lại | Thông tin đã có không yêu cầu nhập lại; kế thừa tự động giữa các bước/phân hệ. |
| Thao tác tối ưu theo vị trí | Màn hình và luồng được thiết kế theo vai trò (QN/GV/SV) để thao tác nhanh, ít bước, ít sai sót. |
| Quyết định dựa trên dữ liệu | Báo cáo và dashboard phục vụ quản trị điều hành. |

## 3.2. Kiến trúc phân lớp

| **Lớp** | **Tên lớp** | **Thành phần chính** |
| --- | --- | --- |
| L1 | Presentation | HTML/CSS/JS, Bootstrap, Razor Views, SignalR Client |
| L2 | Controller | ASP.NET Core MVC Controllers, API Endpoints |
| L3 | Business Logic | QLSV-01 (Sinh viên), QLSV-02 (Đào tạo), QLSV-03 (Điểm danh), QLSV-04 (Điểm số), QLSV-05 (Hành chính), QLSV-06 (Thanh toán), Background Services (Email, QR Refresh) |
| L4 | Data Access | Entity Framework Core + LINQ, Repositories |
| L5 | Database | MS SQL Server |
| L6 | External Integrations | VNPay/MoMo API, SMTP/SendGrid (Email), Google/Microsoft OAuth 2.0 (SSO) |

---

# CHƯƠNG 4. DANH MỤC PHÂN HỆ & MÃ ĐỊNH DANH

| **Mã phân hệ** | **Mnemonic** | **Phân hệ** | **Phạm vi chức năng cốt lõi** | **UC liên quan** |
| --- | --- | --- | --- | --- |
| QLSV-01 | STUDENT | Quản lý Sinh viên | Hồ sơ SV, trạng thái học tập, phân lớp chuyên ngành | UC-01, UC-02, UC-03, UC-04 |
| QLSV-02 | TRAINING | Đào tạo & Thời khóa biểu | Cây môn học, điều kiện tiên quyết, xếp TKB, điều chỉnh lịch | UC-05, UC-06, UC-07, UC-08 |
| QLSV-03 | ATTEND | Điểm danh (QR Code) | Quét QR động, chốt phiên, cảnh báo vắng | UC-09 |
| QLSV-04 | GRADE | Quản lý Điểm & Khảo thí | Điểm TP, tổng kết, xét dự thi/Pass/Fail/Retake/Re-study, đăng ký học lại | UC-10, UC-11, UC-12 |
| QLSV-05 | SERVICE | Dịch vụ Sinh viên (Hành chính) | Nộp đơn trực tuyến, duyệt đơn, quản lý Profile, báo cáo thống kê | UC-13, UC-14, UC-15 |
| QLSV-06 | PAYMENT | Thanh toán (Payment Gateway) | Tích hợp VNPay/MoMo, gạch nợ tự động, đối soát | UC-16 |

---

# CHƯƠNG 5. NGUYÊN TẮC & QUY TẮC NGHIỆP VỤ BẮT BUỘC

Các quy tắc nghiệp vụ (BR) áp dụng xuyên suốt toàn hệ thống, là ràng buộc bắt buộc cho mọi phân hệ và là cơ sở kiểm thử.

## 5.1. Quy tắc Module 1 — Quản lý Sinh viên

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-001 | Mã sinh viên (Student ID) phải là duy nhất trên toàn hệ thống (VD: HE191612). | UC-02 |
| BR-002 | Số CCCD và Email cá nhân không được phép trùng lặp giữa các tài khoản. | UC-02 |
| BR-003 | SV chuyển sang "Bảo lưu" hoặc "Thôi học" lập tức bị gỡ khỏi lớp hiện tại và chặn đăng nhập ứng dụng. | UC-03 |
| BR-004 | Sĩ số của một lớp chuyên ngành không được vượt quá số lượng thiết lập tối đa (VD: 30 SV/lớp). | UC-04 |
| BR-005 | Một SV không thể nằm trong 2 lớp chuyên ngành khác nhau trong cùng một học kỳ. | UC-04 |
| BR-005b | Thời hạn bảo lưu tối đa 2 học kỳ. Hết hạn mà không tái nhập → hệ thống tự chuyển S2 → S3 (Thôi học). | UC-03 |

## 5.2. Quy tắc Module 2 — Đào tạo & TKB

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-006 | Mã môn học (Subject Code) phải là duy nhất trên toàn hệ thống. | UC-06 |
| BR-007 | Không được phép thiết lập vòng lặp logic (Deadlock) đối với các môn tiên quyết (A→B, B→A). | UC-06 |
| BR-008 | Một Giảng viên không thể bị xếp dạy 2 lớp khác nhau trong cùng một Slot. | UC-07 |
| BR-009 | Một Phòng học không thể chứa 2 lớp học trong cùng một Slot. | UC-07 |
| BR-010 | Tổng số buổi học sinh ra phải bằng đúng tổng số Slot quy định của môn học đó. | UC-07 |
| BR-011 | GV chỉ được báo nghỉ trước thời điểm bắt đầu Slot học ít nhất 12 giờ. Quá hạn hệ thống sẽ chặn. Trường hợp bất khả kháng, QN có quyền tạo lệnh báo nghỉ thay GV. | UC-08 |
| BR-012 | Lịch học bù không được phép trùng (Conflict) với lịch học hiện tại của SV trong lớp đó. | UC-08 |

## 5.3. Quy tắc Module 3 — Điểm danh

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-013 | QR Code phải chứa token mã hóa động, thay đổi (refresh) tự động mỗi 10 giây. | UC-09 |
| BR-014 | QR Code chỉ thiết bị/App nằm trong hệ thống (PWA) mới giải mã được. | UC-09 |
| BR-015 | Mỗi tài khoản SV chỉ được ghi nhận "Present" 1 lần duy nhất trong 1 Slot. | UC-09 |
| BR-016 | Nếu áp dụng GPS/IP WiFi, hệ thống check IP phải trùng với mạng WiFi của trường. | UC-09 |
| BR-017 | Tỷ lệ vắng mặt (Absent) > 20% tổng số Slot → hệ thống tự động đánh **Cấm thi (G3)**. | UC-09, UC-11 |
| BR-018 | Chỉ GV phụ trách lớp, Quản nhiệm và Admin mới có quyền sửa trạng thái điểm danh thủ công. | UC-09 |

## 5.4. Quy tắc Module 4 — Điểm & Khảo thí

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-019 | Thang điểm tiêu chuẩn là hệ cơ số 10 (0.0 đến 10.0), làm tròn đến 1 chữ số thập phân. | UC-10 |
| BR-020 | Sau khi Quản nhiệm chốt sổ môn học, GV không được quyền tự ý sửa điểm quá trình. | UC-10 |
| BR-021 | Điều kiện Đạt (Pass) môn: (1) Vắng ≤ 20% VÀ (2) Final Exam ≥ 4.0 VÀ (3) Tổng điểm ≥ 5.0. | UC-11 |
| BR-022 | Điều kiện **Thi lại (Retake Exam)** — trạng thái G4: Vắng ≤ 20% NHƯNG (Final Exam < 4.0 HOẶC Tổng điểm < 5.0). SV chỉ cần thi lại bài Final Exam, giữ nguyên điểm quá trình. | UC-11 |
| BR-022b | Điều kiện **Học lại (Re-study)** — trạng thái G5: SV đã thi lại (G4) nhưng vẫn không đạt (FE < 4.0 HOẶC Tổng < 5.0 sau thi lại). SV phải đăng ký học lại toàn bộ môn từ đầu. | UC-11 |
| BR-023 | Điều kiện Cấm thi (Fail): Vắng > 20% tổng số Slot. SV chuyển sang trạng thái **Cấm thi (G3)**, phải đăng ký học lại (UC-12) → trạng thái G5 → G0. | UC-11 |
| BR-024 | Điểm trung bình môn được làm tròn đến 1 chữ số thập phân (VD: 4.95 → 5.0). | UC-11 |
| BR-025 | Sau khi chốt trạng thái Pass/Fail/Retake/Re-study, chỉ Admin có quyền sửa điểm (bắt buộc lưu Log giải trình). | UC-11 |
| BR-025b | Mỗi SV chỉ được thi lại Final Exam tối đa **1 lần** cho mỗi lần học môn. Nếu vẫn không đạt → chuyển G5 (Học lại toàn bộ). | UC-11 |
| BR-025c | SV học lại 1 môn tối đa **3 lần**. Nếu vẫn không đạt sau lần thứ 3 → Quản nhiệm xét buộc thôi học hoặc chuyển ngành. | UC-12 |

## 5.5. Quy tắc Module 5 — Dịch vụ Hành chính

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-026 | SV chỉ được nộp tối đa 3 đơn cùng loại ở trạng thái **Pending hoặc Processing** (tránh spam). | UC-14 |
| BR-027 | Đơn đặc thù (Phúc khảo) chỉ được nộp trong thời gian quy định (VD: 7 ngày sau công bố điểm). | UC-14 |
| BR-028 | Mọi thao tác đổi trạng thái đơn của Quản nhiệm đều phải được ghi Log (Who & When). | UC-14 |
| BR-029 | SV chỉ được "Hủy đơn" khi ở trạng thái "Pending". Đã chuyển "Processing" thì không được hủy. | UC-14 |

## 5.6. Quy tắc Module 6 — Thanh toán

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-030 | Mã giao dịch (Payment Session) chỉ có hiệu lực trong 15 phút. Quá hạn mã vô hiệu hóa. | UC-16 |
| BR-031 | Số tiền gửi sang Payment Gateway phải khớp chính xác 100% với số tiền trong Database. | UC-16 |
| BR-032 | Chỉ Kế toán/Admin mới được quyền xem dòng tiền và xuất báo cáo đối soát. | UC-15, UC-16 |
| BR-033 | Giao dịch thất bại (Failed) vẫn phải được lưu Database để tra soát khiếu nại. | UC-16 |
| BR-034 | Tính năng Query Transaction và gạch nợ thủ công chỉ dành cho Kế toán/Admin. | UC-16 |
| BR-035 | Mọi thao tác gạch nợ thủ công (Manual Sync) phải được ghi Log (ai thao tác, thời gian). | UC-16 |

## 5.7. Quy tắc — Học lại & Đình chỉ

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-036 | SV chỉ được đăng ký học lại các môn có trạng thái G3 hoặc G5. Môn ở G4 chỉ cần đăng ký thi lại FE, không cần học lại. | UC-12 |
| BR-037 | Mức phí học lại: Kỳ liền kề ngay sau kỳ trượt = **50%** đơn giá môn học; cách ≥ 1 kỳ = **100%** đơn giá. | UC-12 |
| BR-038 | SV đang trong trạng thái **Đình chỉ (S5)** bị chặn hoàn toàn việc đăng ký học lại. | UC-12 |
| BR-039 | SV **sau khi hết thời hạn đình chỉ** (từng ở S5) đăng ký học lại phải đóng phí = **150%** đơn giá (phạt kỷ luật). | UC-12 |
| BR-040 | Hệ thống tự động xếp SV học lại vào lớp khả dụng (CurrentSize < MaxCapacity). Lớp đầy → đưa vào Waitlisted. | UC-12 |
| BR-041 | Thời hạn đình chỉ học tập là 1 học kỳ. Hết hạn, hệ thống tự động chuyển S5 → S1 (Đang học). | UC-03, UC-12 |

## 5.8. Quy tắc bổ sung — Thanh toán, Tốt nghiệp & Thông báo

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-042 | Phí thi lại Final Exam (trạng thái G4) = **10%** đơn giá môn học, không phân biệt kỳ. | UC-12 |
| BR-043 | SV bị đình chỉ lần 2 (tái phạm) → hệ thống tự động chuyển S5 → S3 (Buộc thôi học). QN có quyền xét ngoại lệ (có Log). | UC-03 |
| BR-044 | Điều kiện Tốt nghiệp (S1 → S4): (1) Pass toàn bộ môn bắt buộc trong CTĐT, (2) Thanh toán hết nợ học phí, (3) Không đang bị đình chỉ (S5). | UC-03 |
| BR-045 | Hệ thống tự động chuyển hóa đơn Unpaid → Overdue khi vượt quá DueDate (Background Job chạy hàng ngày). | UC-16 |
| BR-046 | SV có hóa đơn Overdue bị chặn: (1) Không được đăng ký học lại, (2) Không được xem bảng điểm chính thức. | UC-12, UC-16 |
| BR-047 | Thông báo In-app (Notification) được lưu trữ tối đa **90 ngày**. Quá hạn hệ thống tự động xóa. | Toàn hệ |
| BR-048 | Mật khẩu phải ≥ 8 ký tự, chứa ít nhất 1 chữ hoa, 1 số, 1 ký tự đặc biệt. Không trùng 3 mật khẩu gần nhất. | UC-01, UC-13 |
| BR-049 | Tài khoản bị khóa tạm 15 phút sau 5 lần nhập sai mật khẩu liên tiếp. | UC-01 |
| BR-050 | SSO chỉ chấp nhận email thuộc tên miền nhà trường (VD: *@fpt.edu.vn). Email cá nhân bị từ chối. | UC-01 |
| BR-051 | Mọi thao tác tạo/sửa/xóa dữ liệu quan trọng (điểm, trạng thái, gạch nợ) phải ghi audit log không thể chỉnh sửa (who-when-what-old/new). | Toàn hệ |

---

# CHƯƠNG 6. TÁC NHÂN, VAI TRÒ & THỰC THỂ NGHIỆP VỤ

## 6.1. Từ điển Vai trò

| **Mã** | **Vai trò** | **Vị trí tác nghiệp** | **Trách nhiệm chính** |
| --- | --- | --- | --- |
| VT-01 | Quản nhiệm (Academic Staff) | Back-office | Quản trị hồ sơ SV, phân lớp, xếp TKB, thiết lập CTĐT, duyệt đơn từ, duyệt lịch bù, chốt sổ điểm. |
| VT-02 | Giảng viên (Lecturer) | Phòng học/Online | Mở phiên điểm danh, nhập điểm, báo nghỉ/đề xuất lịch bù, sửa điểm danh thủ công. |
| VT-03 | Sinh viên (Student) | Mobile/Desktop | Quét QR điểm danh, xem TKB, xem điểm, nộp đơn từ, thanh toán lệ phí, theo dõi trạng thái đơn. |
| VT-04 | Kế toán (Accountant) | Back-office | Xem dòng tiền, xuất báo cáo đối soát, tra soát giao dịch lỗi, gạch nợ thủ công. |
| VT-05 | Admin hệ thống | Back-office | Toàn quyền hệ thống: sửa điểm sau chốt sổ (có Log), quản lý cấu hình, CRUD Giảng viên & Phòng học, tạo tài khoản thủ công. |
| VT-06 | Hệ thống (System) | Tự động | Tự động: tính điểm, gạch nợ, gửi Email cảnh báo, chốt phiên điểm danh, chuyển Overdue. |
| VT-07 | Payment Gateway | Bên ngoài | Bên thứ 3 (VNPay/MoMo) xử lý thanh toán, gửi Webhook/IPN. |

## 6.2. Danh mục Thực thể Nghiệp vụ

| **Mã** | **Thực thể** | **Mô tả** | **Phân hệ** |
| --- | --- | --- | --- |
| TT-01 | Hồ sơ Sinh viên (Student Profile) | MSSV, CCCD, Email, SĐT, giới tính, ngày sinh, địa chỉ, trạng thái học tập | QLSV-01 |
| TT-02 | Tài khoản Người dùng (User Account) | Thông tin đăng nhập, vai trò (Role), trạng thái kích hoạt | QLSV-01 |
| TT-03 | Lớp chuyên ngành (Class) | Mã lớp, chuyên ngành, học kỳ, sĩ số tối đa, danh sách SV | QLSV-01 |
| TT-04 | Môn học (Subject) | Mã môn, tên, số tín chỉ, thời lượng Slot, học kỳ | QLSV-02 |
| TT-05 | Chương trình đào tạo (Curriculum) | Cây môn học theo khóa, ràng buộc tiên quyết/song hành | QLSV-02 |
| TT-06 | Thời khóa biểu (Schedule) | Lịch học theo Slot, phòng, GV, lớp, trạng thái buổi học | QLSV-02 |
| TT-07 | Phiên điểm danh (Attendance Session) | Mã phiên, Slot, lớp, trạng thái (Opening/Closed), QR Token | QLSV-03 |
| TT-08 | Bản ghi điểm danh (Attendance Record) | SV, phiên, trạng thái (Present/Absent), timestamp | QLSV-03 |
| TT-09 | Bảng điểm (Grade Record) | SV, môn, điểm TP (Quiz/Assign/Lab/FE), tỷ trọng, tổng điểm, trạng thái G0–G5 | QLSV-04 |
| TT-10 | Đơn từ (Service Request) | Mã yêu cầu, loại đơn, SV, trạng thái, file đính kèm, ghi chú, timeline xử lý | QLSV-05 |
| TT-11 | Hóa đơn (Invoice) | Mã hóa đơn, SV, số tiền, trạng thái (Unpaid/Paid/Overdue/Cancelled), ngày đến hạn | QLSV-06 |
| TT-12 | Giao dịch thanh toán (Transaction) | Mã giao dịch, thời gian, phương thức, trạng thái, Webhook response | QLSV-06 |
| TT-13 | Phòng học (Room) | Mã phòng, sức chứa, loại phòng, trạng thái sử dụng | QLSV-02 |
| TT-14 | Activity Log | Ghi lại mọi thao tác quan trọng (import, sửa điểm, duyệt đơn, gạch nợ thủ công) | Toàn hệ |
| TT-15 | Đăng ký Học lại (Retake Registration) | SV, môn, kỳ gốc trượt, kỳ đăng ký lại, mức phí, trạng thái xếp lớp | QLSV-04 |
| TT-16 | Hồ sơ Kỷ luật (Disciplinary Record) | Lý do đình chỉ, ngày bắt đầu, ngày kết thúc, trạng thái (Active/Expired) | QLSV-01 |
| TT-17 | Hồ sơ Giảng viên (Lecturer Profile) | Mã GV, họ tên, chuyên môn, email, SĐT, trạng thái hoạt động | QLSV-02 |
| TT-18 | Thông báo (Notification) | Nội dung, loại, người nhận, trạng thái đã đọc, thời điểm, TTL 90 ngày | Toàn hệ |
| TT-19 | Môn tiên quyết (Subject PreRequisite) | Bảng trung gian quản lý quan hệ tiên quyết giữa các môn học | QLSV-02 |
| TT-20 | Cấu hình tỷ trọng điểm (Grade Weight Config) | Tỷ trọng từng đầu điểm thành phần theo môn học | QLSV-04 |

---

# CHƯƠNG 7. QUY TRÌNH NGHIỆP VỤ ĐẦU–CUỐI

## 7.1. Sơ đồ quy trình tổng thể

**A. Luồng nghiệp vụ tổng thể liên kết các quy trình lõi:**

1\. Thiết lập & Đầu vào: Quản lý Danh mục (UC-05) → Tiếp nhận hồ sơ SV (UC-02) → Phân bổ lớp (UC-04).

2\. Kế hoạch đào tạo: Khung chương trình (UC-06) → Xếp TKB (UC-07) → Rẽ nhánh: Điều chỉnh lịch học (UC-08).

3\. Quá trình học tập: Điểm danh QR (UC-09) → Cập nhật điểm quá trình (UC-10).

4\. Khảo thí & Kết quả: Xét dự thi & Tổng kết điểm (UC-11) → Rẽ nhánh:
   - Đạt (Passed): Tiếp tục học / Tốt nghiệp (UC-03).
   - Trượt (Fail/Retake/Re-study): Đăng ký Học lại & Xếp lớp (UC-12).

5\. Dịch vụ & Tài chính: Nộp đơn từ (UC-14) → Thanh toán trực tuyến (UC-16).

6\. Xuyên suốt & Hỗ trợ: Xác thực hệ thống (UC-01), Quản lý Profile (UC-13), Báo cáo thống kê (UC-15).

**B. Bảng tổng hợp quy trình theo Module**

| **Mã** | **Quy trình** | **Điểm bắt đầu** | **Điểm kết thúc** | **Module** |
| --- | --- | --- | --- | --- |
| UC-01 | Xác thực & Quản lý tài khoản | Mở ứng dụng / Truy cập Login | Đăng nhập thành công, vào Dashboard | QLSV-01 |
| UC-02 | Tiếp nhận hồ sơ sinh viên mới | Có danh sách SV đầu kỳ | Hồ sơ lưu DB, tài khoản được tạo | QLSV-01 |
| UC-03 | Cập nhật trạng thái học tập | Có quyết định (Bảo lưu, Thôi học...) | Trạng thái thay đổi, cập nhật quyền | QLSV-01 |
| UC-04 | Phân bổ SV vào lớp chuyên ngành | SV mới cần xếp lớp đầu khóa | SV được gán lớp (Sĩ số cập nhật) | QLSV-01 |
| UC-05 | Quản lý Danh mục (Master Data) | Có thay đổi nhân sự / Phòng học | Dữ liệu được cập nhật an toàn | QLSV-02 |
| UC-06 | Thiết lập khung chương trình | Xây dựng CTĐT / Khóa mới | Môn học & điều kiện tiên quyết lưu DB | QLSV-02 |
| UC-07 | Đồng bộ Thời khóa biểu | Bắt đầu học kỳ / block mới | Lịch học (TKB) hiển thị cho GV/SV | QLSV-02 |
| UC-08 | Điều chỉnh lịch học (Báo nghỉ/Bù) | GV có sự cố đột xuất | TKB chuyển MakeUp, sinh lịch bù | QLSV-02 |
| UC-09 | Điểm danh bằng QR động | Bắt đầu Slot học | Chốt Present / Absent toàn lớp | QLSV-03 |
| UC-10 | Cập nhật điểm quá trình | GV hoàn tất chấm bài (Quiz/Lab...) | Bảng điểm quá trình được lưu | QLSV-04 |
| UC-11 | Xét điều kiện dự thi & Tổng kết | Hoàn tất nhập điểm FE | Chốt trạng thái môn (G1, G3, G4, G5) | QLSV-04 |
| UC-12 | Đăng ký Học lại & Xếp lớp | Kỳ mới, SV có môn trượt (G3/G4/G5) | Sinh Hóa đơn / Được xếp lớp | QLSV-04 |
| UC-13 | Quản lý Profile & Đổi mật khẩu | Người dùng có nhu cầu đổi TT/MK | Thông tin / Mật khẩu được cập nhật | QLSV-05 |
| UC-14 | Nộp đơn từ & Xét duyệt | SV nộp đơn xin hỗ trợ / khiếu nại | Đơn chuyển Approved / Rejected | QLSV-05 |
| UC-15 | Xem Báo cáo & Thống kê | Cán bộ / Lãnh đạo cần số liệu | Báo cáo hiển thị / Xuất file Excel | QLSV-05 |
| UC-16 | Thanh toán trực tuyến (Gateway) | Hóa đơn mới phát sinh (Unpaid) | Hóa đơn chuyển Paid, đối soát xong | QLSV-06 |

---

## 7.2. Đặc tả chi tiết từng Quy trình

### UC-01 — Xác thực & Quản lý tài khoản (Đăng nhập)

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-01 |
| **Tên quy trình** | Xác thực & Quản lý tài khoản (Đăng nhập) |
| **Phân hệ liên quan** | QLSV-01 |
| **Tác nhân** | Tất cả Người dùng (VT-01 → VT-05) |
| **Điều kiện bắt đầu** | Tài khoản đã được tạo và kích hoạt (IsActive = True). |
| **Dữ liệu đầu vào** | Username/Email, Password (hoặc SSO Token). |
| **Luồng chính** | 1. Người dùng nhập Username/Email và Password. 2. Hệ thống xác thực thông tin tài khoản. 3. Hệ thống tạo và trả về JWT Token. 4. Chuyển hướng người dùng vào Dashboard tương ứng với Role. |
| **Luồng ngoại lệ** | 1a. Quên mật khẩu: Nhập Email → Nhận link OTP → Đặt lại mật khẩu. 2a. Sai thông tin: Hệ thống báo lỗi "Tài khoản hoặc mật khẩu không chính xác". 2b. Sai mật khẩu 5 lần liên tiếp: Tài khoản bị khóa tạm thời trong 15 phút (BR-049). |
| **Dữ liệu đầu ra** | JWT Token, Dashboard theo vai trò. |
| **Quy tắc nghiệp vụ** | BR-048, BR-049, BR-050. |
| **Tiêu chí nghiệm thu** | UC-01.NT01: Đăng nhập thành công ≤ 1 giây, chuyển đúng Dashboard theo Role. UC-01.NT02: Khóa tài khoản sau 5 lần sai, tự mở sau 15 phút. UC-01.NT03: SSO chỉ chấp nhận email @fpt.edu.vn. |

---

### UC-02 — Tiếp nhận hồ sơ sinh viên mới (Import danh sách)

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-02 |
| **Tên quy trình** | Tiếp nhận hồ sơ sinh viên mới (Import danh sách) |
| **Phân hệ liên quan** | QLSV-01 |
| **Tác nhân** | VT-01 Quản nhiệm |
| **Điều kiện bắt đầu** | Bắt đầu học kỳ mới, có danh sách SV cần đưa vào hệ thống. Tệp Excel/CSV đã chuẩn bị theo biểu mẫu. |
| **Dữ liệu đầu vào** | Tệp Excel/CSV chứa danh sách SV (MSSV, họ tên, CCCD, email, SĐT, ngày sinh, giới tính, địa chỉ). |
| **Luồng chính** | 1. QN truy cập "Quản lý Sinh viên" → "Import hồ sơ". 2. QN tải lên tệp Excel/CSV. 3. Hệ thống validate các trường bắt buộc (BR-001, BR-002). 4. Hệ thống lưu hồ sơ hợp lệ và tự động tạo tài khoản đăng nhập. 5. Hiển thị thông báo "Import thành công" kèm số lượng bản ghi. |
| **Luồng ngoại lệ** | 1a. Thêm mới thủ công: QN chọn "Thêm mới sinh viên" → Điền form → Lưu → tiếp tục bước 3. 3a. Dữ liệu trùng/lỗi: Bôi đỏ các dòng lỗi, yêu cầu tải lại. |
| **Dữ liệu đầu ra** | Hồ sơ SV (TT-01), Tài khoản (TT-02), Activity Log (TT-14). |
| **Quy tắc nghiệp vụ** | BR-001, BR-002. |
| **Tiêu chí nghiệm thu** | UC-02.NT01: Import 200 bản ghi hợp lệ: tạo đủ hồ sơ + tài khoản ≤ 10 giây. UC-02.NT02: File có dòng lỗi (trùng CCCD): bôi đỏ dòng lỗi, vẫn lưu dòng hợp lệ. |

---

### UC-03 — Cập nhật trạng thái học tập

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-03 |
| **Tên quy trình** | Cập nhật trạng thái học tập |
| **Phân hệ liên quan** | QLSV-01 |
| **Tác nhân** | VT-01 Quản nhiệm |
| **Điều kiện bắt đầu** | Có quyết định chính thức cho phép thay đổi trạng thái sinh viên. |
| **Dữ liệu đầu vào** | Mã SV, trạng thái mới, lý do thay đổi. |
| **Luồng chính** | 1. QN tìm kiếm hồ sơ SV. 2. Chọn "Cập nhật trạng thái". 3. Lựa chọn trạng thái mới (VD: Bảo lưu) và nhập lý do. 4. Xác nhận thay đổi. 5. Hệ thống cập nhật DB, tự động điều chỉnh quyền truy cập tương ứng. |
| **Luồng ngoại lệ** | 3a. SV đang nợ phí: Cảnh báo nợ phí và chặn cập nhật sang "Bảo lưu" / "Thôi học". |
| **Dữ liệu đầu ra** | Trạng thái SV cập nhật (TT-01), Activity Log (TT-14). |
| **Quy tắc nghiệp vụ** | BR-003, BR-005b, BR-041, BR-043, BR-044. |
| **Tiêu chí nghiệm thu** | UC-03.NT01: Trạng thái SV thay đổi real-time, quyền truy cập điều chỉnh tức thì. UC-03.NT02: SV Bảo lưu/Thôi học bị gỡ khỏi lớp hiện tại. |

---

### UC-04 — Phân bổ sinh viên vào lớp chuyên ngành

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-04 |
| **Tên quy trình** | Phân bổ sinh viên vào lớp chuyên ngành |
| **Phân hệ liên quan** | QLSV-01 |
| **Tác nhân** | VT-01 Quản nhiệm |
| **Điều kiện bắt đầu** | SV (trạng thái S0) cần được gán lớp. Danh sách lớp đã tạo. |
| **Dữ liệu đầu vào** | Danh sách SV, danh sách lớp chuyên ngành. |
| **Luồng chính** | 1. QN chọn "Phân lớp tự động". 2. Hệ thống chia đều SV vào các lớp khả dụng. 3. QN xem trước Draft, nhấn "Xác nhận". 4. Hệ thống gán SV, chuyển trạng thái S0 → S1, cập nhật sĩ số. |
| **Luồng ngoại lệ** | 1a. Phân lớp thủ công: QN kéo-thả SV vào lớp cụ thể. 2a. Lớp đầy: Cảnh báo vượt MaxCapacity, yêu cầu mở thêm lớp. |
| **Dữ liệu đầu ra** | SV gắn lớp (TT-03), trạng thái S1 (TT-01). |
| **Quy tắc nghiệp vụ** | BR-004, BR-005. |
| **Tiêu chí nghiệm thu** | UC-04.NT01: Phân lớp tự động 200 SV vào 8 lớp: sĩ số đều, không vượt MaxCapacity. |

---

### UC-05 — Quản lý Danh mục (Giảng viên, Phòng học)

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-05 |
| **Tên quy trình** | Quản lý Danh mục Hệ thống (Master Data) |
| **Phân hệ liên quan** | QLSV-02 |
| **Tác nhân** | VT-05 Admin hệ thống |
| **Điều kiện bắt đầu** | Có thay đổi nhân sự giảng viên hoặc cơ sở vật chất. |
| **Dữ liệu đầu vào** | Thông tin GV (TT-17), Phòng học (TT-13). |
| **Luồng chính** | 1. Admin vào màn hình Quản lý danh mục. 2. Chọn Thêm/Sửa/Xóa. 3. Cập nhật dữ liệu vào Form. 4. Hệ thống kiểm tra ràng buộc toàn vẹn và lưu DB. |
| **Luồng ngoại lệ** | 4a. Vi phạm FK Constraint: Xóa phòng đang xếp TKB hoặc GV đang có lịch dạy → Chặn Xóa, báo lỗi "Dữ liệu đang được sử dụng". |
| **Dữ liệu đầu ra** | Danh mục GV (TT-17), Phòng (TT-13) cập nhật. |
| **Quy tắc nghiệp vụ** | Referential Integrity chuẩn. |
| **Tiêu chí nghiệm thu** | UC-05.NT01: CRUD Giảng viên & Phòng hoàn tất đúng, chặn xóa khi có ràng buộc. |

---

### UC-06 — Thiết lập khung chương trình môn học

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-06 |
| **Tên quy trình** | Thiết lập khung chương trình môn học |
| **Phân hệ liên quan** | QLSV-02 |
| **Tác nhân** | VT-01 Quản nhiệm |
| **Điều kiện bắt đầu** | Xây dựng CTĐT khóa mới hoặc có môn học mới được phê duyệt. |
| **Dữ liệu đầu vào** | Mã môn, tên, số tín chỉ, tổng Slot, danh sách môn tiên quyết. |
| **Luồng chính** | 1. QN truy cập "Đào tạo" → "Thêm mới" môn học. 2. Nhập thông tin môn học. 3. Thiết lập môn tiên quyết (nếu có). 4. Nhấn "Lưu". 5. Hệ thống kiểm tra tính hợp lệ và lưu DB. |
| **Luồng ngoại lệ** | 2a. Trùng mã môn: Báo lỗi "Mã môn học đã tồn tại". 3a. Vòng lặp tiên quyết: Phát hiện Deadlock → Chặn lưu, báo lỗi. |
| **Dữ liệu đầu ra** | Môn học (TT-04), Tiên quyết (TT-19), CTĐT (TT-05). |
| **Quy tắc nghiệp vụ** | BR-006, BR-007. |
| **Tiêu chí nghiệm thu** | UC-06.NT01: Thêm môn thành công, phát hiện Deadlock tiên quyết ≤ 2 giây. |

---

### UC-07 — Đồng bộ Thời khóa biểu (Auto-Scheduling)

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-07 |
| **Tên quy trình** | Đồng bộ Thời khóa biểu (Auto-Scheduling) |
| **Phân hệ liên quan** | QLSV-02 |
| **Tác nhân** | VT-01 Quản nhiệm |
| **Điều kiện bắt đầu** | Dữ liệu Lớp, Môn, GV, Phòng học đã đầy đủ. |
| **Dữ liệu đầu vào** | Học kỳ, danh sách Lớp, Môn, GV, Phòng. |
| **Luồng chính** | 1. QN vào TKB, chọn "Xếp lịch tự động". 2. Cấu hình Học kỳ, Lớp, Môn. 3. Khởi chạy thuật toán. 4. Hệ thống tạo bản Draft trên Calendar. 5. QN rà soát và nhấn "Đồng bộ TKB". 6. Hệ thống lưu DB và Push lịch lên Dashboard. |
| **Luồng ngoại lệ** | 1a. Xếp lịch thủ công: QN kéo thả Slot trên giao diện Calendar. 4a. Xung đột tài nguyên: Thiếu phòng hoặc trùng GV → Hiển thị danh sách lớp không thể xếp. |
| **Dữ liệu đầu ra** | TKB hoàn chỉnh (TT-06). |
| **Quy tắc nghiệp vụ** | BR-008, BR-009, BR-010. |
| **Tiêu chí nghiệm thu** | UC-07.NT01: Xếp TKB tự động 200 SV ≤ 30 giây, 0% Conflict GV/Phòng. |

---

### UC-08 — Điều chỉnh lịch học (Báo nghỉ & Lịch bù)

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-08 |
| **Tên quy trình** | Điều chỉnh lịch học (Báo nghỉ & Lịch bù) |
| **Phân hệ liên quan** | QLSV-02 |
| **Tác nhân** | VT-02 Giảng viên, VT-01 Quản nhiệm |
| **Điều kiện bắt đầu** | GV có sự cố đột xuất, cách thời điểm báo nghỉ ít nhất 12 giờ. |
| **Dữ liệu đầu vào** | Slot cần nghỉ, lý do, Ngày/Slot bù đề xuất. |
| **Luồng chính** | 1. GV chọn Slot → "Báo nghỉ". 2. GV điền lý do và Ngày/Slot bù. 3. Gửi yêu cầu duyệt đến QN. 4. QN duyệt. 5. Hệ thống đổi TKB, sinh Slot học bù mới. 6. Gửi Email/Noti cho SV bị ảnh hưởng. |
| **Luồng ngoại lệ** | 1a. Báo nghỉ quá hạn (< 12 giờ): Hệ thống chặn, QN có thể tạo thay. 4a. QN từ chối: Trả lại GV chọn lịch bù khác. |
| **Dữ liệu đầu ra** | TKB cập nhật (Cancelled + MakeUp), Notification (TT-18). |
| **Quy tắc nghiệp vụ** | BR-011, BR-012. |
| **Tiêu chí nghiệm thu** | UC-08.NT01: Email/Push thông báo hoàn tất ≤ 1 phút sau QN duyệt. UC-08.NT02: Chặn báo nghỉ < 12 giờ trước Slot. |

---

### UC-09 — Điểm danh bằng QR động

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-09 |
| **Tên quy trình** | Mở phiên & Điểm danh bằng QR động |
| **Phân hệ liên quan** | QLSV-03 |
| **Tác nhân** | VT-02 Giảng viên, VT-03 Sinh viên, VT-06 Hệ thống |
| **Điều kiện bắt đầu** | Bắt đầu giờ học, GV ở lớp có kết nối màn hình chiếu. SV có PWA. |
| **Dữ liệu đầu vào** | Slot, Lớp, QR Token. |
| **Luồng chính** | 1. GV chọn "Mở điểm danh". 2. Hệ thống sinh QR động (Token mã hóa), refresh mỗi 10 giây. 3. SV quét QR bằng PWA. 4. App gửi Token lên Server → ghi "Present". 5. GV đóng phiên → Hệ thống đánh "Absent" cho SV chưa quét. 6. Hệ thống kiểm tra tỷ lệ vắng tổng cộng, nếu ≥ 20% → G3. |
| **Luồng ngoại lệ** | 5a. Sửa điểm danh thủ công: SV hỏng điện thoại → GV sửa "Present" thủ công, ghi Log. 3a. App bên ngoài quét (Zalo/Camera): Không giải mã được. 3b. QR hết hạn (>10 giây): Báo lỗi "Mã hết hạn". |
| **Dữ liệu đầu ra** | Phiên điểm danh (TT-07), Bản ghi điểm danh (TT-08). |
| **Quy tắc nghiệp vụ** | BR-013, BR-014, BR-015, BR-016, BR-017, BR-018. |
| **Tiêu chí nghiệm thu** | UC-09.NT01: QR refresh mỗi 10 giây, SV quét thành công → Present real-time. UC-09.NT02: App bên ngoài không giải mã được QR. UC-09.NT03: Xác thực QR ≤ 2 giây. |

---

### UC-10 — Cập nhật điểm quá trình

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-10 |
| **Tên quy trình** | Cập nhật điểm quá trình |
| **Phân hệ liên quan** | QLSV-04 |
| **Tác nhân** | VT-02 Giảng viên |
| **Điều kiện bắt đầu** | Môn đang In Progress (G0), QN chưa chốt sổ. |
| **Dữ liệu đầu vào** | SV, Môn, Điểm TP (Quiz/Assignment/Lab). |
| **Luồng chính** | 1. GV truy cập lớp → Tab "Quản lý điểm". 2. Nhập điểm vào DataGrid (Excel-like). 3. Validate: 0.0 đến 10.0. 4. GV nhấn "Lưu bảng điểm". 5. Hệ thống lưu DB. |
| **Luồng ngoại lệ** | 3a. Điểm ngoài dải / sai định dạng: Ô đỏ, chặn "Lưu" đến khi sửa. |
| **Dữ liệu đầu ra** | Bảng điểm quá trình (TT-09). |
| **Quy tắc nghiệp vụ** | BR-019, BR-020. |
| **Tiêu chí nghiệm thu** | UC-10.NT01: Nhập điểm ngoài dải bị chặn, highlight đỏ. UC-10.NT02: GV không sửa được điểm sau chốt sổ. |

---

### UC-11 — Xét điều kiện dự thi & Tổng kết điểm

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-11 |
| **Tên quy trình** | Xét điều kiện dự thi & Tổng kết Pass/Fail/Retake/Re-study |
| **Phân hệ liên quan** | QLSV-04 |
| **Tác nhân** | VT-06 Hệ thống (tự động), VT-01 Quản nhiệm, VT-05 Admin |
| **Điều kiện bắt đầu** | Điểm FE đã nhập hoàn tất, QN nhấn "Chốt sổ". |
| **Dữ liệu đầu vào** | Bảng điểm TP + FE, % vắng, cấu hình tỷ trọng (TT-20). |
| **Luồng chính** | 1. Hệ thống quét % vắng: > 20% → G3 (Fail/Cấm thi). 2. Tính Tổng điểm theo tỷ trọng (TT-20). 3. FE < 4.0 HOẶC Tổng < 5.0 → G4 (Retake); nếu đã ở G4 → G5 (Re-study). 4. Thỏa mãn tất cả → G1 (Passed). 5. Cập nhật Transcript. |
| **Luồng ngoại lệ** | 5a. Admin sửa điểm sau chốt sổ: Nhập điểm mới → Bắt buộc lý do → Cập nhật trạng thái → Ghi audit log. |
| **Dữ liệu đầu ra** | Bảng điểm chốt (TT-09), Activity Log (TT-14). |
| **Quy tắc nghiệp vụ** | BR-021, BR-022, BR-022b, BR-023, BR-024, BR-025, BR-025b. |
| **Tiêu chí nghiệm thu** | UC-11.NT01: Tính điểm 200 SV đúng 100% theo tỷ trọng (TT-20), ≤ 30 giây. UC-11.NT02: Vắng > 20% → tự động G3. FE < 4.0 → tự động G4. |

---

### UC-12 — Đăng ký Học lại & Xếp lớp Môn trượt

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-12 |
| **Tên quy trình** | Đăng ký Học lại & Xếp lớp Môn trượt |
| **Phân hệ liên quan** | QLSV-04 |
| **Tác nhân** | VT-03 Sinh viên, VT-01 Quản nhiệm, VT-06 Hệ thống |
| **Điều kiện bắt đầu** | Kỳ mới mở đăng ký, SV trạng thái S1 hoặc vừa hết đình chỉ, có ≥ 1 môn G3/G4/G5. |
| **Dữ liệu đầu vào** | Danh sách môn trượt, số kỳ trôi qua, hồ sơ kỷ luật. |
| **Luồng chính** | **Luồng A — Thi lại (G4):** 1. SV xem danh sách môn G4. 2. Đăng ký thi lại FE. 3. Hệ thống sinh hóa đơn thi lại (10% đơn giá — BR-042). 4. SV thanh toán (UC-16). 5. Xếp lịch thi lại. **Luồng B — Học lại (G3/G5):** 1. SV xem danh sách môn G3/G5. 2. Chọn môn đăng ký học lại. 3. Tính phí: 50% (kỳ liền kề) / 100% (cách ≥ 1 kỳ) — BR-037. 4. Sinh hóa đơn → SV thanh toán (UC-16). 5. Xếp SV vào lớp khả dụng. |
| **Luồng ngoại lệ** | 3a. SV vừa hết đình chỉ (S5 → S1): Phí 150% (BR-039). 3b. SV đang đình chỉ (S5): Chặn đăng ký (BR-038). 5a. Lớp đầy: Đưa vào Waitlisted (BR-040). |
| **Dữ liệu đầu ra** | Đăng ký học lại (TT-15), Hóa đơn (TT-11). |
| **Quy tắc nghiệp vụ** | BR-025c, BR-036, BR-037, BR-038, BR-039, BR-040, BR-041, BR-042, BR-046. |
| **Tiêu chí nghiệm thu** | UC-12.NT01: SV đăng ký học lại G3: phí đúng 50%/100% theo BR-037. UC-12.NT02: SV đình chỉ (S5) → chặn đăng ký, thông báo đúng. |

---

### UC-13 — Quản lý Profile & Đổi mật khẩu

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-13 |
| **Tên quy trình** | Quản lý Profile & Đổi mật khẩu |
| **Phân hệ liên quan** | QLSV-05 |
| **Tác nhân** | Tất cả Người dùng, VT-05 Admin |
| **Điều kiện bắt đầu** | Tài khoản đã đăng nhập. |
| **Dữ liệu đầu vào** | SĐT, ảnh đại diện, mật khẩu cũ/mới. |
| **Luồng chính** | 1. Truy cập Profile. 2. Chỉnh sửa SĐT/ảnh hoặc nhấn "Đổi mật khẩu". 3. Nhập MK cũ + MK mới (2 lần). 4. Hệ thống validate và lưu. |
| **Luồng ngoại lệ** | 2a. Admin reset MK cho user khác → Sinh MK tạm → Gửi Email. 3a. MK cũ sai → Báo lỗi. 3b. MK mới không đủ độ mạnh → Báo lỗi. |
| **Dữ liệu đầu ra** | Thông tin cập nhật (TT-02). |
| **Quy tắc nghiệp vụ** | BR-048. |
| **Tiêu chí nghiệm thu** | UC-13.NT01: Đổi MK thành công với MK đủ mạnh. UC-13.NT02: Chặn MK trùng 3 lần gần nhất. |

---

### UC-14 — Nộp đơn từ & Xét duyệt

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-14 |
| **Tên quy trình** | Nộp đơn từ & Xét duyệt |
| **Phân hệ liên quan** | QLSV-05 |
| **Tác nhân** | VT-03 Sinh viên, VT-01 Quản nhiệm |
| **Điều kiện bắt đầu** | SV đăng nhập, trạng thái S1. |
| **Dữ liệu đầu vào** | Loại đơn, nội dung, file đính kèm. |
| **Luồng chính** | 1. SV chọn loại đơn, điền nội dung, đính kèm file. 2. Bấm nộp → Trạng thái "Pending". 3. QN nhận Noti, kiểm tra đơn. 4. QN duyệt (Approved/Rejected) + Ghi chú. 5. Hệ thống gửi Email kết quả cho SV. |
| **Luồng ngoại lệ** | 2a. Đơn có lệ phí (Phúc khảo): SV thanh toán trước (UC-16). 1a. Vượt 3 đơn chưa xử lý: Chặn nộp thêm (BR-026). 3a. SV hủy đơn Pending → "Cancelled". |
| **Dữ liệu đầu ra** | Đơn từ (TT-10), Email thông báo, Activity Log (TT-14). |
| **Quy tắc nghiệp vụ** | BR-026, BR-027, BR-028, BR-029. |
| **Tiêu chí nghiệm thu** | UC-14.NT01: Nộp/duyệt đơn thành công, Email kết quả ≤ 1 phút. UC-14.NT02: Chặn nộp khi > 3 đơn cùng loại chưa xử lý. |

---

### UC-15 — Xem Báo cáo & Thống kê

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-15 |
| **Tên quy trình** | Xem Báo cáo & Thống kê |
| **Phân hệ liên quan** | QLSV-05 |
| **Tác nhân** | VT-01 Quản nhiệm, VT-04 Kế toán, VT-05 Admin |
| **Điều kiện bắt đầu** | Tài khoản đăng nhập có quyền xem báo cáo. |
| **Dữ liệu đầu vào** | Loại báo cáo, bộ lọc (Học kỳ, Lớp, Môn). |
| **Luồng chính** | 1. Truy cập Dashboard Báo cáo. 2. Chọn loại (Học tập / Tài chính / Điểm danh) + bộ lọc. 3. Hệ thống truy xuất và hiển thị. 4. Xuất Excel/PDF nếu cần. |
| **Luồng ngoại lệ** | 3a. Không có dữ liệu: Hiển thị "Không có dữ liệu cho bộ lọc đã chọn". |
| **Dữ liệu đầu ra** | Báo cáo trên Dashboard, file Excel/PDF. |
| **Quy tắc nghiệp vụ** | BR-032 (Chỉ Kế toán/Admin xem dòng tiền). |
| **Tiêu chí nghiệm thu** | UC-15.NT01: Tải báo cáo ≤ 5 giây. Xuất Excel 5.000 dòng ≤ 15 giây. |

---

### UC-16 — Thanh toán trực tuyến (Payment Gateway)

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Mã quy trình** | UC-16 |
| **Tên quy trình** | Thanh toán trực tuyến (Payment Gateway) |
| **Phân hệ liên quan** | QLSV-06 |
| **Tác nhân** | VT-03 Sinh viên, VT-04 Kế toán, VT-07 Payment Gateway |
| **Điều kiện bắt đầu** | Hóa đơn trạng thái "Unpaid" hoặc "Overdue". Payment Gateway hoạt động. |
| **Dữ liệu đầu vào** | Hóa đơn, phương thức thanh toán. |
| **Luồng chính** | 1. SV mở danh sách hóa đơn, chọn phương thức. 2. Hệ thống sinh URL + mã phiên giao dịch → chuyển hướng sang Gateway. 3. SV thanh toán thành công. 4. Gateway gửi IPN/Webhook về Server. 5. Server xác thực Checksum (HMAC SHA512), gạch nợ → "Paid". |
| **Luồng ngoại lệ** | 4a. Mất Webhook: Kế toán "Query Transaction" thủ công → Gạch nợ bổ sung. 3a. Giao dịch thất bại/Quá hạn: Hóa đơn giữ "Unpaid", Transaction → "Failed". 5a. Checksum sai/Số tiền không khớp: Từ chối gạch nợ, cảnh báo Admin. |
| **Dữ liệu đầu ra** | Hóa đơn "Paid" (TT-11), Giao dịch (TT-12), Activity Log (TT-14). |
| **Quy tắc nghiệp vụ** | BR-030, BR-031, BR-032, BR-033, BR-034, BR-035, BR-045. |
| **Tiêu chí nghiệm thu** | UC-16.NT01: VNPay/MoMo thành công → Paid + Success. UC-16.NT02: Webhook bị mất → Query Transaction thủ công → gạch nợ bổ sung. |

---

# CHƯƠNG 8. BẢNG TRẠNG THÁI CÁC THỰC THỂ CHÍNH

## 8.1. Trạng thái Sinh viên (TT-01)

| **Mã** | **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- | --- |
| S0 | Khởi thủy (Initialized) | SV vừa import, chưa có lớp | → S1 (Khi được gán lớp — UC-04) |
| S1 | Đang học (Active) | SV đang theo học chính thức | → S2, S3, S4, S5 |
| S2 | Bảo lưu (Suspended) | SV tạm ngừng học tập (tối đa 2 kỳ — BR-005b) | → S1 (Tái nhập), → S3 (Hết hạn bảo lưu mà không tái nhập) |
| S3 | Thôi học (Dropped) | SV nghỉ học vĩnh viễn | (Trạng thái cuối) |
| S4 | Tốt nghiệp (Graduated) | SV hoàn thành chương trình (BR-044) | (Trạng thái cuối) |
| S5 | Đình chỉ (Disciplinary) | SV bị đình chỉ do vi phạm, chặn mọi đăng ký | → S1 (Hết hạn — BR-041), → S3 (Đình chỉ lần 2 — BR-043) |

## 8.2. Trạng thái Tài khoản Người dùng (TT-02)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Active | Đang hoạt động, đăng nhập bình thường | → Locked (Sai MK 5 lần), → Inactive, → Limited |
| Locked | Bị khóa tạm 15 phút (BR-049) | → Active (Sau 15 phút tự mở) |
| Limited | Quyền hạn chế (SV Bảo lưu — BR-003): chỉ xem, nộp đơn tái nhập, thanh toán nợ | → Active (Khi tái nhập) |
| Inactive | Bị khóa vĩnh viễn (SV Thôi học) | → Active (Trường hợp đặc biệt) |

## 8.3. Trạng thái Thời khóa biểu / Slot học (TT-06)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Normal | Lịch học bình thường theo TKB chuẩn | → Cancelled (Khi GV báo nghỉ) |
| Cancelled | Bị hủy do GV báo nghỉ | (Trạng thái cuối) |
| MakeUp | Slot học bù được tạo sau báo nghỉ | (Trạng thái cuối) |

## 8.4. Trạng thái Phiên điểm danh (TT-07)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Opening | Phiên đang mở, QR động đang chạy | → Closed (Hết giờ/Đóng phiên thủ công) |
| Closed | Phiên đã chốt, không nhận quét QR nữa | (Trạng thái cuối) |

## 8.5. Trạng thái Bản ghi điểm danh (TT-08)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Present | Sinh viên có mặt (quét QR hoặc GV sửa tay) | → Absent (Nếu QN/GV sửa lại) |
| Absent | Sinh viên vắng mặt (chưa quét khi phiên đóng) | → Present (Nếu QN/GV sửa tay) |

## 8.6. Trạng thái Môn học của SV / Bảng điểm (TT-09)

| **Mã** | **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- | --- |
| G0 | Đang học (In Progress) | SV đang theo học môn này | → G1, G3, G4 |
| G1 | Đạt (Passed) | Thỏa mãn (Vắng ≤ 20%, FE ≥ 4.0, Tổng ≥ 5.0) | (Trạng thái cuối) |
| G3 | Cấm thi (Fail) | Vắng > 20% tổng Slot. SV phải đăng ký học lại (UC-12) | → G5 (Khi SV đăng ký học lại) |
| G4 | Thi lại (Retake Exam) | FE < 4.0 HOẶC Tổng < 5.0 (Vắng ≤ 20%). Thi lại FE 1 lần (BR-025b), giữ điểm TP | → G1 (Thi lại đạt) / G5 (Thi lại trượt) |
| G5 | Học lại (Re-study) | Từ G3 hoặc G4 trượt. Học lại toàn bộ. Tối đa 3 lần (BR-025c) | → G0 (Đăng ký học lại → vào lớp mới) |

_Ghi chú: Trạng thái G2 (Reserved) đã được loại bỏ từ v4.0 vì không có use case sử dụng._

## 8.7. Trạng thái Đơn từ (TT-10)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Pending | SV vừa nộp, chờ QN tiếp nhận | → Processing, Approved, Rejected, Cancelled |
| Processing | QN đang xử lý (hoặc chờ thanh toán) | → Approved, Rejected |
| Approved | QN đã duyệt | (Trạng thái cuối) |
| Rejected | QN từ chối | (Trạng thái cuối) |
| Cancelled | SV tự thu hồi đơn (chỉ khi Pending — BR-029) | (Trạng thái cuối) |

## 8.8. Trạng thái Hóa đơn (TT-11)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Unpaid | Chưa thanh toán | → Paid, → Overdue (Tự động khi quá DueDate — BR-045), → Cancelled |
| Paid | Đã thanh toán (Gateway xác nhận) | (Trạng thái cuối) |
| Overdue | Quá hạn, SV bị chặn đăng ký/xem điểm (BR-046) | → Paid (Nộp bù), → Cancelled |
| Cancelled | Hóa đơn bị hủy (VD: rút đơn) | (Trạng thái cuối) |

## 8.9. Trạng thái Giao dịch thanh toán (TT-12)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Pending | Đã tạo URL sang Gateway, đang chờ Webhook | → Success, → Failed |
| Success | Thanh toán thành công | (Trạng thái cuối) |
| Failed | Hủy giao dịch, quá hạn, lỗi số tiền/checksum | (Trạng thái cuối) |

## 8.10. Trạng thái Đăng ký Học lại (TT-15)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Pending | Chờ SV thanh toán hóa đơn học lại | → Paid, → Cancelled |
| Paid | Đã thanh toán, chờ xếp lớp | → Assigned, → Waitlisted |
| Assigned | Đã được xếp vào lớp học lại | (Trạng thái cuối) |
| Waitlisted | Lớp đầy, chờ mở bổ sung hoặc QN xếp tay | → Assigned |
| Cancelled | SV hủy đăng ký (trước thanh toán) | (Trạng thái cuối) |

## 8.11. Trạng thái Hồ sơ Kỷ luật (TT-16)

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Active | Đang trong thời gian đình chỉ | → Expired (Tự động khi hết hạn — BR-041) |
| Expired | Hết hạn, SV được phép đăng ký lại (phí 150% — BR-039) | (Trạng thái cuối) |

---

# CHƯƠNG 9. MA TRẬN PHÂN QUYỀN (RBAC)

| **Chức năng \ Vai trò** | **VT-01 (QN)** | **VT-02 (GV)** | **VT-03 (SV)** | **VT-04 (Kế toán)** | **VT-05 (Admin)** |
| --- | --- | --- | --- | --- | --- |
| Quản lý GV & Phòng | — | — | — | — | C/R/U/D |
| Import hồ sơ SV | C/R/U/D | — | — | — | R |
| Cập nhật trạng thái SV | R/U | — | — | — | R/U |
| Phân lớp chuyên ngành | C/R/U | — | R | — | R |
| Thiết lập môn học & CTĐT | C/R/U/D | R | R | — | R |
| Xếp Thời khóa biểu | C/R/U/D | R | R | — | R |
| Báo nghỉ & Xếp lịch bù | C/R/U (duyệt) | C/R (đề xuất) | R | — | R |
| Mở phiên điểm danh | — | C/R/U | — | — | R |
| Quét QR điểm danh | — | — | X | — | — |
| Sửa điểm danh thủ công | U | U | — | — | R |
| Nhập điểm quá trình | — | C/R/U | R | — | R |
| Chốt sổ điểm | R/U | — | — | — | R |
| Sửa điểm sau chốt sổ | — | — | — | — | U (Log) |
| Duyệt/Từ chối đơn từ | R/U | — | R (của mình) | — | R |
| Thanh toán trực tuyến | — | — | X | — | — |
| Đối soát & Tra soát | — | — | — | R/U | R |
| Quản lý Hóa đơn | R | — | R (của mình) | C/R/U | C/R/U/D |
| Đăng ký học lại | R/U (xếp lớp) | — | C/R/U (của mình) | — | R |
| Quản lý kỷ luật / Đình chỉ | C/R/U | — | R (của mình) | — | C/R/U/D |
| Xem Activity Log | — | — | — | R (tài chính) | R |
| Xem Báo cáo thống kê | R (học tập) | R (của mình) | — | R (tài chính) | R |
| Đổi mật khẩu / Profile | U (của mình) | U (của mình) | U (của mình) | U (của mình) | U (tất cả) |

_Ghi chú: C = Create, R = Read, U = Update, D = Delete, X = Execute, — = Không có quyền._

---

# CHƯƠNG 10. DANH SÁCH MÀN HÌNH UI THEO PHÂN HỆ

## 10.1. Dashboard Chung

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **UC** |
| --- | --- | --- | --- | --- |
| MH-00-1 | Dashboard Quản nhiệm / Admin | VT-01, VT-05 | Thống kê tổng số SV, đơn chờ duyệt, trạng thái hệ thống | Tất cả |
| MH-00-2 | Dashboard Giảng viên | VT-02 | Lịch dạy trong ngày/tuần, thông báo lớp học | Tất cả |
| MH-00-3 | Dashboard Sinh viên | VT-03 | TKB hôm nay, thông báo khẩn, tình trạng đơn từ | Tất cả |

## 10.2. Module 1: Quản lý Sinh viên (QLSV-01)

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **UC** |
| --- | --- | --- | --- | --- |
| MH-01-1 | Import hồ sơ Sinh viên | VT-01 | Import Excel/CSV, tạo tài khoản tự động | UC-02 |
| MH-01-2 | Danh sách & Hồ sơ chi tiết | VT-01 | Tìm kiếm, xem, chỉnh sửa, cập nhật trạng thái | UC-02, UC-03 |
| MH-01-3 | Phân lớp chuyên ngành | VT-01 | Phân lớp tự động/thủ công | UC-04 |

## 10.3. Module 2: Đào tạo & TKB (QLSV-02)

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **UC** |
| --- | --- | --- | --- | --- |
| MH-02-1 | Quản lý Môn học & CTĐT | VT-01 | Cấu hình cây CTĐT, thiết lập tiên quyết | UC-06 |
| MH-02-2 | Xếp Thời khóa biểu | VT-01 | Xếp lịch tự động/thủ công, kiểm tra Conflict | UC-07 |
| MH-02-3 | Quản lý lịch báo nghỉ/bù | VT-01 | Duyệt lịch báo nghỉ, xếp lịch bù | UC-08 |
| MH-02-4 | TKB cá nhân Giảng viên | VT-02 | Xem lịch dạy, báo nghỉ, đề xuất lịch bù | UC-07, UC-08 |
| MH-02-5 | TKB cá nhân Sinh viên | VT-03 | Xem lịch học theo tuần/tháng | UC-07 |
| MH-02-6 | Quản lý Giảng viên & Phòng | VT-05 | CRUD Giảng viên, Phòng học | UC-05 |

## 10.4. Module 3: Điểm danh (QLSV-03)

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **UC** |
| --- | --- | --- | --- | --- |
| MH-03-1 | Mở phiên Điểm danh (QR) | VT-02 | Mở/đóng phiên, hiển thị QR toàn màn hình | UC-09 |
| MH-03-2 | Quét QR Điểm danh | VT-03 | PWA quét QR qua camera để ghi nhận có mặt | UC-09 |
| MH-03-3 | Danh sách điểm danh lớp | VT-01, VT-02 | Xem Present/Absent, sửa thủ công (có Log) | UC-09 |

## 10.5. Module 4: Quản lý Điểm & Khảo thí (QLSV-04)

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **UC** |
| --- | --- | --- | --- | --- |
| MH-04-1 | Nhập/Import điểm | VT-02 | Grid nhập điểm TP, import từ Excel | UC-10 |
| MH-04-2 | Chốt sổ điểm | VT-01 | Xem bảng điểm tổng hợp, thực hiện chốt sổ | UC-11 |
| MH-04-3 | Bảng điểm cá nhân | VT-03 | Xem điểm chi tiết, tổng kết, trạng thái G0–G5 | UC-10, UC-11 |
| MH-04-4 | Quản lý Đăng ký học lại | VT-01, VT-03 | Đăng ký học lại/thi lại (SV) và quản lý xếp lớp (QN) | UC-12 |

## 10.6. Module 5: Dịch vụ Hành chính (QLSV-05)

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **UC** |
| --- | --- | --- | --- | --- |
| MH-05-1 | Nộp đơn từ trực tuyến | VT-03 | Điền form, upload minh chứng, theo dõi timeline | UC-14 |
| MH-05-2 | Duyệt đơn từ | VT-01 | Xem danh sách đơn chờ, Approve/Reject + ghi chú | UC-14 |
| MH-05-3 | Quản lý Profile & Đổi MK | Tất cả | Cập nhật SĐT, ảnh, đổi mật khẩu | UC-13 |
| MH-05-4 | Báo cáo & Thống kê | VT-01, VT-04, VT-05 | Dashboard báo cáo, xuất Excel/PDF | UC-15 |

## 10.7. Module 6: Thanh toán (QLSV-06)

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **UC** |
| --- | --- | --- | --- | --- |
| MH-06-1 | Hóa đơn & Thanh toán | VT-03 | Xem hóa đơn, chọn gateway, thanh toán | UC-16 |
| MH-06-2 | Dashboard Tài chính | VT-04, VT-05 | Doanh thu, tra soát giao dịch, xuất báo cáo đối soát | UC-15, UC-16 |
| MH-06-3 | Tra soát & Gạch nợ | VT-04 | Query Transaction, gạch nợ thủ công (khi mất Webhook) | UC-16 |

---

# CHƯƠNG 11. TIÊU CHÍ NGHIỆM THU NGHIỆP VỤ

## 11.1. Tiêu chí nghiệm thu theo Quy trình

| **Mã** | **Tiêu chí nghiệm thu** | **UC liên quan** | **Phương pháp kiểm chứng** |
| --- | --- | --- | --- |
| UC-01.NT01 | Đăng nhập thành công với tài khoản hợp lệ, chuyển đúng Dashboard theo Role | UC-01 | Test thủ công + Automated UI Test |
| UC-01.NT02 | Khóa tài khoản sau 5 lần sai mật khẩu, tự mở sau 15 phút | UC-01 | Test thủ công |
| UC-01.NT03 | SSO chỉ chấp nhận email @fpt.edu.vn | UC-01 | Test thủ công |
| UC-02.NT01 | Import 200 bản ghi hợp lệ: tạo đủ hồ sơ + tài khoản ≤ 10 giây | UC-02 | Automated Test + đo thời gian |
| UC-02.NT02 | File có dòng lỗi (trùng CCCD): bôi đỏ dòng lỗi, vẫn lưu dòng hợp lệ | UC-02 | Test thủ công |
| UC-04.NT01 | Phân lớp tự động 200 SV vào 8 lớp: sĩ số đều, không vượt MaxCapacity | UC-04 | Automated Test |
| UC-07.NT01 | Xếp TKB tự động 200 SV ≤ 30 giây, 0% Conflict GV/Phòng | UC-07 | Automated Test + đo thời gian |
| UC-09.NT01 | QR Code refresh mỗi 10 giây, SV quét thành công → Present real-time | UC-09 | Test thủ công trên mobile browser |
| UC-09.NT02 | SV quét QR bằng app bên ngoài (Zalo/Camera) → không giải mã được | UC-09 | Test thủ công |
| UC-11.NT01 | Tính điểm 200 SV: đúng 100% theo tỷ trọng (TT-20), ≤ 30 giây | UC-11 | Automated Test + so khớp Excel |
| UC-11.NT02 | SV vắng > 20% → tự động G3. SV FE < 4.0 → tự động G4 | UC-11 | Automated Test |
| UC-12.NT01 | SV đăng ký học lại G3: phí đúng 50%/100% theo BR-037 | UC-12 | Automated Test |
| UC-12.NT02 | SV đang đình chỉ (S5) → chặn đăng ký, hiển thị thông báo đúng | UC-12 | Test thủ công |
| UC-16.NT01 | Thanh toán VNPay/MoMo thành công → hóa đơn Paid, giao dịch Success | UC-16 | Test thủ công trên Sandbox |
| UC-16.NT02 | Webhook bị mất → Kế toán Query Transaction thủ công → gạch nợ bổ sung | UC-16 | Test thủ công |

## 11.2. Điều kiện hoàn thành (Definition of Done) & UAT

- Mỗi quy trình UC-xx PASS toàn bộ tiêu chí UC-xx.NTxx bắt buộc.
- Không tồn tại lỗi mức Blocker/Critical; lỗi Major có kế hoạch xử lý được chấp thuận.
- Người dùng nghiệp vụ đại diện mỗi vai trò ký xác nhận UAT.
- Tài liệu vận hành, phân quyền và hướng dẫn sử dụng được bàn giao.

---

# CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR)

| **Mã** | **Nhóm** | **Yêu cầu** | **Ngưỡng đo được** |
| --- | --- | --- | --- |
| NFR-01 | Hiệu năng | Thời gian đăng nhập & cấp Token | ≤ 1 giây |
| NFR-02 | Hiệu năng | Import 1.000 bản ghi SV | ≤ 10 giây |
| NFR-03 | Hiệu năng | Xác thực QR điểm danh | ≤ 2 giây |
| NFR-04 | Hiệu năng | Thuật toán Auto-scheduling (200 SV) | ≤ 30 giây, 0% Conflict |
| NFR-05 | Hiệu năng | Kiểm tra vòng lặp tiên quyết | ≤ 2 giây |
| NFR-06 | Hiệu năng | Tính điểm toàn bộ 200 SV | ≤ 30 giây |
| NFR-07 | Hiệu năng | Tải báo cáo Dashboard | ≤ 5 giây |
| NFR-08 | Hiệu năng | Xuất Excel 5.000 dòng | ≤ 15 giây |
| NFR-09 | Bảo mật | Giao tiếp Payment Gateway | Mã hóa SSL/TLS |
| NFR-10 | Bảo mật | Mật khẩu người dùng | Hash một chiều (Argon2/Bcrypt) |
| NFR-11 | Bảo mật | Chống Spam Login | Khóa 15 phút sau 5 lần sai |
| NFR-12 | Vận hành | Đồng thời (Concurrent Users) | Hỗ trợ 200 SV điểm danh cùng lúc |
| NFR-13 | Vận hành | Logging (Audit Trail) | Ghi Log 100% thao tác sửa điểm/thanh toán |
| NFR-14 | Vận hành | Backup Data | Daily backup, lưu trữ 30 ngày |
| NFR-15 | Vận hành | SLA Uptime | 99.5% thời gian hoạt động |
| NFR-16 | Vận hành | Email thông báo (duyệt đơn, cảnh báo vắng) | ≤ 1–2 phút sau sự kiện |
| NFR-17 | Trải nghiệm | Giao diện responsive | Tương thích Chrome, Safari, Edge; PWA trên mobile |
| NFR-18 | Trải nghiệm | Nhập liệu bảng điểm | Hỗ trợ Tab/Enter liên tục trên DataGrid |

---

# CHƯƠNG 13. YÊU CẦU TÍCH HỢP

| **Mã** | **Hệ thống / Dịch vụ** | **Giao thức** | **Chiều dữ liệu** |
| --- | --- | --- | --- |
| TH-01 | Payment Gateway (VNPay / MoMo) | REST API + Webhook/IPN | Tạo Payment URL → Nhận kết quả giao dịch |
| TH-02 | Dịch vụ gửi Email (SendGrid / SMTP) | SMTP / REST API | Gửi Email cảnh báo, duyệt đơn, hóa đơn |
| TH-03 | Xác thực SSO (Google / Microsoft OAuth 2.0) | OAuth 2.0 / OpenID Connect | Xác thực → Cấp Token |

### 13.1. Tích hợp Cổng thanh toán (TH-01)

- **Đối tác:** VNPay hoặc MoMo API.
- **Giao thức:** REST API (Tạo Payment URL) và Webhook/IPN (Nhận kết quả giao dịch).
- **Bảo mật:** Dữ liệu ký chữ ký điện tử (Checksum / HMAC SHA512) bằng Secret Key. Kiểm tra IP Whitelist từ Gateway.
- **Dự phòng:** Background Job Query Transaction cho hóa đơn "Pending" quá 15 phút (đề phòng mất Webhook).

### 13.2. Tích hợp Dịch vụ Gửi Email (TH-02)

- **Dịch vụ:** SendGrid API, Amazon SES, hoặc SMTP nội bộ.
- **Kỹ thuật:** Đẩy tác vụ gửi Email vào Message Queue (Background Worker) để xử lý bất đồng bộ. Hỗ trợ Template HTML động.

### 13.3. Tích hợp Xác thực SSO (TH-03)

- **Công nghệ:** Google OAuth 2.0 hoặc Microsoft Entra ID.
- **Ràng buộc:** Chỉ chấp nhận email thuộc tên miền nhà trường (VD: *@fpt.edu.vn). Email cá nhân (@gmail.com) bị từ chối (BR-050).

---

# CHƯƠNG 14. TUÂN THỦ PHÁP LÝ & QUY CHẾ

| **Khía cạnh** | **Yêu cầu tuân thủ** |
| --- | --- |
| Quy chế đào tạo | Logic điểm liệt (FE < 4.0), vắng quá 20%, công thức tính trung bình tổng phải tuân thủ nghiêm ngặt Quy chế Đào tạo FPT hiện hành. |
| Bảo mật dữ liệu | Mật khẩu bắt buộc mã hóa một chiều (Argon2/Bcrypt). Không lưu trữ thông tin thẻ ngân hàng — chỉ lưu mã tham chiếu giao dịch. Tuân thủ NĐ 13/2023 về bảo vệ dữ liệu cá nhân. |
| Lưu vết (Audit Trail) | Toàn bộ thao tác can thiệp điểm số sau chốt, gạch nợ thủ công phải lưu vết vĩnh viễn (Ai, Khi nào, IP, Giá trị cũ/mới) — BR-051. |

---

# CHƯƠNG 15. DANH MỤC DÙNG CHUNG

Danh mục dùng chung (Master Data) bao gồm dữ liệu tham chiếu ít biến động, cấu hình sẵn để sử dụng thống nhất trên toàn hệ thống.

| **Nhóm danh mục** | **Nội dung** |
| --- | --- |
| Thời gian học (Slot & Block) | Slot học chuẩn (Slot 1: 07:30–09:50, Slot 2: 10:00–12:20, Slot 3: 12:50–15:10…); Block học tập (Block 1, Block 2) cấu thành học kỳ. |
| Tổ chức & Đào tạo | Ngành học (Major), Khoa/Bộ môn (Department), Học kỳ (Semester: Spring/Summer/Fall + năm). |
| Hành chính & Cơ sở vật chất | Địa giới hành chính (Tỉnh/Huyện/Xã), Loại phòng học (Theory/Lab/Hội trường). |
| Trạng thái & Phân loại | Trạng thái học tập (S0–S5), Trạng thái môn học (G0–G5), Loại đơn từ (Phúc khảo, Chuyển lớp, Xin nghỉ, Cấp bảng điểm…). |
| Hệ thống | Vai trò (VT-01 → VT-07), nhóm quyền, mẫu Email. |

---

# CHƯƠNG 16. MA TRẬN TRUY VẾT & LỘ TRÌNH BRD

## 16.1. Ma trận truy vết Yêu cầu

| **Mục tiêu** | **Phân hệ** | **UC** | **BR** | **NFR** | **Màn hình** |
| --- | --- | --- | --- | --- | --- |
| G-01: Tự động hóa QL Sinh viên | QLSV-01 | UC-01, UC-02, UC-03, UC-04 | BR-001→005b | NFR-01, NFR-02 | MH-01-1→3 |
| G-02: Số hóa CTĐT & TKB | QLSV-02 | UC-05, UC-06, UC-07, UC-08 | BR-006→012 | NFR-04, NFR-05 | MH-02-1→6 |
| G-03: Hiện đại hóa điểm danh | QLSV-03 | UC-09 | BR-013→018 | NFR-03, NFR-12 | MH-03-1→3 |
| G-04: Minh bạch QL Điểm | QLSV-04 | UC-10, UC-11, UC-12 | BR-019→025c, BR-036→042 | NFR-06, NFR-13 | MH-04-1→4 |
| G-05: Số hóa hành chính | QLSV-05 | UC-13, UC-14, UC-15 | BR-026→029, BR-048 | NFR-07, NFR-16 | MH-05-1→4 |
| G-06: Tích hợp Payment | QLSV-06 | UC-16 | BR-030→035, BR-045→046 | NFR-08, NFR-09 | MH-06-1→3 |
| Xuyên suốt: Bảo mật & Audit | Toàn hệ | UC-01 | BR-047→051 | NFR-10→15 | — |

## 16.2. Kết luận

Tài liệu này thiết lập khung nghiệp vụ chi tiết đầy đủ cho Hệ thống Quản Lý Sinh Viên: mã định danh chuẩn hóa, 16 quy trình nghiệp vụ đầu–cuối theo template, bảng trạng thái các thực thể chính, ma trận phân quyền theo vai trò, danh sách màn hình theo phân hệ, tiêu chí nghiệm thu và yêu cầu phi chức năng có ngưỡng đo cụ thể. Đây là cơ sở vững chắc để suy ra các tài liệu FRD/SRS, thiết kế UI/UX, API, test case và kế hoạch triển khai.

---

**Trạng thái tài liệu:** Chờ phê duyệt — Phiên bản 5.0

**Ngày cập nhật:** 23/09/2026

**Người cập nhật:** Hiếu, Khánh

_Hết tài liệu._
