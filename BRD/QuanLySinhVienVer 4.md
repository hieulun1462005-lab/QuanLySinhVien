**TÀI LIỆU YÊU CẦU NGHIỆP VỤ — CHI TIẾT PHÂN HỆ**

MODULE BUSINESS REQUIREMENTS DOCUMENT

&nbsp;

&nbsp;

&nbsp;

**Tài Liệu Mô Tả Yêu Cầu Nghiệp Vụ**

Quản lý sinh viên

&nbsp;

&nbsp;

&nbsp;

Ngày 15 tháng 9 năm 2026

&nbsp;

&nbsp;

_Tài liệu yêu cầu nghiệp vụ cho Hệ thống Quản Lý Sinh Viên_

|     |     |
| --- | --- |
| **Mã tài liệu** | BRD-QLSV-v3.1 |
| **Tài liệu nguồn** | Tài Liệu Mô Tả Yêu Cầu Nghiệp Vụ — Quản lý Sinh viên v3.1 |
| **Phiên bản** | 4.0 |
| **Ngày ban hành** | 21/09/2026 |
| **Người soạn** | Khánh, Hiếu |
| **Phân loại** | Nội bộ — Hạn chế |
| **Trạng thái** | Chờ phê duyệt |

**PHÊ DUYỆT TÀI LIỆU**

| **Vai trò** | **Người soạn** | **Người rà soát** | **Người phê duyệt** |
| --- | --- | --- | --- |
| Chức danh | BA / Developer | Trưởng nhóm phát triển | Ban lãnh đạo |
| Họ tên | Khánh, Hiếu | \[Để trống\] | \[Để trống\] |
| Ký / Ngày | 16/09/2026 |     |     |

**LỊCH SỬ THAY ĐỔI**

| **Phiên bản** | **Ngày** | **Người thay đổi** | **Mô tả thay đổi** |
| --- | --- | --- | --- |
| 1.0 | 16/09/2026 | Khánh, Hiếu | Khởi tạo tài liệu Draft |
| 2.0 | 16/09/2026 | Khánh, Hiếu | Cập nhật theo review: Sửa mâu thuẫn điểm số (Pass/Retake/Fail), thêm Data Dictionary, bổ sung quy trình Đăng nhập, Quản lý GV/Phòng, thêm NFR. |
| 3.0 | 17/09/2026 | Khánh, Hiếu | Thêm QT-13 (Đăng ký Học lại & Xếp lớp môn trượt), cơ chế Đình chỉ (S5), BR-036→BR-041, TT-15/TT-16, màn hình MH-SV-08/MH-QN-10/MH-QN-11. |
| 3.1 | 17/09/2026 | Khánh, Hiếu | Soát lỗi toàn diện: Khắc phục mâu thuẫn nghiệp vụ (QR Code, BR-018), sửa lỗi cấu trúc Mục lục, bổ sung Tiêu chí Nghiệm thu, chuẩn hóa Data Dictionary & Ma trận truy vết. |
| 4.0 | 21/09/2026 | Khánh, Hiếu | Review toàn diện: Thống nhất KPI/NFR, bổ sung Glossary, thêm bảng Giảng viên (TT-17) & Notification (TT-18), bổ sung BR-042→BR-051, QT-14/QT-15, hoàn thiện Tiêu chí Nghiệm thu, sửa RBAC & State Machine, thêm DateOfBirth/Semester vào Data Dictionary, tách bảng PreRequisite & Grade Weight, làm rõ PWA cho QR. |

**MỤC LỤC**

[CHƯƠNG 0. QUY ƯỚC MÃ ĐỊNH DANH (BẮT BUỘC)](#chương-0-quy-ước-mã-định-danh-bắt-buộc)

[CHƯƠNG 1. GIỚI THIỆU](#chương-1-giới-thiệu)

[CHƯƠNG 2. BỐI CẢNH, MỤC TIÊU & RỦI RO](#chương-2-bối-cảnh-mục-tiêu--rủi-ro)

[CHƯƠNG 3. KIẾN TRÚC NGHIỆP VỤ](#chương-3-kiến-trúc-nghiệp-vụ)

[CHƯƠNG 4. DANH MỤC PHÂN HỆ & MÃ ĐỊNH DANH](#chương-4-danh-mục-phân-hệ--mã-định-danh)

[CHƯƠNG 5. NGUYÊN TẮC & QUY TẮC NGHIỆP VỤ BẮT BUỘC](#Xe042652ab1242ad3019483e8b18280f402be4c0)

[CHƯƠNG 6. TÁC NHÂN, VAI TRÒ & THỰC THỂ NGHIỆP VỤ](#X34aa5d7ae9f15b51d75c26490090782bd4ee9bb)

[CHƯƠNG 7. QUY TRÌNH NGHIỆP VỤ ĐẦU–CUỐI](#chương-7-quy-trình-nghiệp-vụ-đầucuối)

[CHƯƠNG 8. BẢNG TRẠNG THÁI CÁC THỰC THỂ CHÍNH (ĐẦY ĐỦ)](#X9ade1f2cb9072bbfa604745cddd1253e0691315)

[CHƯƠNG 9. MA TRẬN PHÂN QUYỀN (RBAC)](#chương-9-ma-trận-phân-quyền-rbac)

[CHƯƠNG 10. DANH SÁCH MÀN HÌNH UI THEO VỊ TRÍ TÁC NGHIỆP](#X8b40d10d0c7b2758966136191d020c3e69e9488)

[CHƯƠNG 11. TIÊU CHÍ NGHIỆM THU NGHIỆP VỤ](#chương-11-tiêu-chí-nghiệm-thu-nghiệp-vụ)

[CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR)](#chương-12-yêu-cầu-phi-chức-năng-nfr)

[CHƯƠNG 13. YÊU CẦU TÍCH HỢP](#chương-13-yêu-cầu-tích-hợp)

[CHƯƠNG 14. TUÂN THỦ PHÁP LÝ & QUY CHẾ](#chương-14-tuân-thủ-pháp-lý--quy-chế)

[CHƯƠNG 15. DANH MỤC DÙNG CHUNG](#chương-15-danh-mục-dùng-chung)

[CHƯƠNG 16. MA TRẬN TRUY VẾT & LỘ TRÌNH BRD](#chương-16-ma-trận-truy-vết--lộ-trình-brd)

# **CHƯƠNG 0. QUY ƯỚC MÃ ĐỊNH DANH (BẮT BUỘC)**

| **Loại đối tượng** | **Quy ước mã** | **Ví dụ** |
| --- | --- | --- |
| Phân hệ | QLSV-xx | QLSV-01 |
| Nhóm chức năng (cấp 2) | QLSV-xx-N00 | QLSV-01-100 |
| Chức năng/chi tiết (cấp 3) | QLSV-xx-N00-MMMM | QLSV-01-100-0010 |
| Yêu cầu nghiệp vụ | YCNV-QLSV-xx-N00-MMMM | YCNV-QLSV-01-100-0010 |
| Quy tắc bắt buộc chung | BR-&lt;3 số&gt; | BR-001 |
| Quy trình | QT-xx (–QT-xx-xxx) | QT-01 |
| Nghiệm thu theo QT | &lt;mã QT&gt;.NTxx | QT-01.NT01 |
| Thực thể | TT-&lt;2 số&gt; | TT-01 |
| Vai trò | VT-&lt;2 số&gt; | VT-01 |
| Màn hình | MH-\[VỊ TRÍ\]-\[số\] | MH-SV-01 |
| Use Case | UC-QLSV-&lt;Phân hệ&gt;.&lt;Số&gt; | UC-QLSV-01.1 |

**Ghi chú:** &lt;HỆ&gt; = QLSV (Quản Lý Sinh Viên). Cấp 2 là bội số 100; cấp 3 là bội số

10\. Không tái dùng mã đã hủy.

# **  
CHƯƠNG 1. GIỚI THIỆU**

## **1.1. Mục đích tài liệu**

Tài liệu BRD này mô tả toàn bộ yêu cầu nghiệp vụ chi tiết cho **Hệ thống Quản Lý Sinh Viên** — một ứng dụng web (Progressive Web App) tập trung nhằm số hóa và tự động hóa các hoạt động quản lý đào tạo tại trường Đại học FPT. Tài liệu phục vụ làm cơ sở cho đội ngũ phát triển, kiểm thử và các bên liên quan (Stakeholders) trong suốt vòng đời dự án.

## **1.2. Phạm vi**

### TRONG PHẠM VI (In-Scope)

1.  **Module Quản lý Sinh viên & Học tập (QLSV-01):** Quản lý hồ sơ (CCCD, địa chỉ), theo dõi trạng thái học tập.
2.  **Module Chương trình đào tạo & Thời khóa biểu (QLSV-02):** Quản lý cây môn học, điều kiện tiên quyết, xếp lịch và đồng bộ TKB theo Slot chuẩn.
3.  **Module Điểm danh (QLSV-03):** Quét QR động (real-time) qua trình duyệt mobile (PWA) cho sinh viên và hệ thống tự động gửi Email cảnh báo vắng học.
4.  **Module Quản lý Điểm & Khảo thí (QLSV-04):** Nhập/tính điểm tổng kết, tự động xét điều kiện thi/PASS/FAIL/RETAKE theo Quy chế FPT.
5.  **Module Dịch vụ Sinh viên — Hành chính (QLSV-05):** Cổng nộp đơn từ trực tuyến, duyệt đơn và theo dõi trạng thái dành cho Quản nhiệm.
6.  **Module Thanh toán — Payment Gateway (QLSV-06):** Tích hợp Payment Gateway, tự động gạch nợ học phí và hỗ trợ kế toán đối soát.

###   
NGOÀI PHẠM VI (Out-of-Scope)

1.  **Phân hệ Tuyển sinh:** Không quản lý data học sinh cấp 3, quy trình thi tuyển hay nhập học đầu vào.
2.  **Quản lý Nhân sự & Lương Giảng viên:** Hệ thống chỉ lưu thông tin giảng viên để xếp lớp, KHÔNG tính lương, chấm công hay quản lý hợp đồng giảng viên.
3.  **Quản lý Thư viện / Ký túc xá:** Không nằm trong hệ sinh thái của dự án này.
4.  **Ứng dụng Native Mobile (iOS/Android):** Hệ thống là Progressive Web App (PWA), không phát triển ứng dụng mobile riêng biệt.

## **  
1.3. Đối tượng sử dụng tài liệu**

- Ban lãnh đạo / Người phê duyệt dự án
- Quản nhiệm (Academic Staff) / Giảng viên
- Đội ngũ phát triển phần mềm (Developer, Tester, DevOps)
- Kế toán / Bộ phận hành chính

## **  
1.4. Bảng thuật ngữ (Glossary)**

| **Thuật ngữ** | **Giải thích** |
| --- | --- |
| SV  | Sinh viên |
| GV  | Giảng viên |
| QN  | Quản nhiệm (Academic Staff) |
| TKB | Thời khóa biểu |
| CTĐT | Chương trình đào tạo |
| Slot | Khung giờ học chuẩn FPT (VD: Slot 1 = 07:30–09:50) |
| Block | Đơn vị thời gian học (thường 5–7 tuần) trong 1 học kỳ |
| FE  | Final Exam — Bài thi cuối kỳ |
| TP  | Thành phần — Điểm quá trình (Quiz, Assignment, Lab) |
| QR Token | Chuỗi mã hóa động nhúng trong QR Code, refresh mỗi 10 giây |
| PWA | Progressive Web App — Ứng dụng web có thể cài đặt trên mobile và truy cập camera |
| IPN / Webhook | Instant Payment Notification — Cổng thanh toán gọi ngược về Server để thông báo kết quả |
| RBAC | Role-Based Access Control — Kiểm soát truy cập dựa trên vai trò |
| SSO | Single Sign-On — Đăng nhập một lần (Google/Microsoft) |
| CCCD | Căn Cước Công Dân |
| MSSV | Mã số sinh viên |
| BR  | Business Rule — Quy tắc nghiệp vụ bắt buộc |
| QT  | Quy trình nghiệp vụ |
| NFR | Non-Functional Requirement — Yêu cầu phi chức năng |
| G0–G5 | Các mã trạng thái môn học (In Progress / Passed / Reserved / Fail / Retake / Re-study) |
| S0–S5 | Các mã trạng thái sinh viên (Initialized / Active / Suspended / Dropped / Graduated / Disciplinary) |

# **CHƯƠNG 2. BỐI CẢNH, MỤC TIÊU & RỦI RO**

## **2.1. Stakeholders**

| **Vai trò** | **Mô tả** |
| --- | --- |
| Quản nhiệm (Academic Staff) | Quản lý hồ sơ SV, phân lớp, xếp TKB, duyệt đơn từ |
| Giảng viên | Điểm danh, nhập điểm, báo nghỉ/xếp lịch bù |
| Sinh viên | Xem TKB, quét QR điểm danh, xem điểm, nộp đơn, thanh toán |
| Kế toán | Kế toán: Đối soát giao dịch, tra soát. |
| Admin | Admin: Quản trị hệ thống, cấp quyền |

## **  
2.2. Mục tiêu & KPI**

| **Mã** | **Mục tiêu** | **KPI / Ngưỡng** |
| --- | --- | --- |
| G-01 | Tự động hóa & Trung tâm hóa Quản lý Sinh viên: Chuẩn hóa toàn bộ sơ yếu lý lịch (CCCD, địa chỉ, giới tính) và tự động theo dõi trạng thái học tập | 100% hồ sơ SV được số hóa; Thời gian import 1.000 bản ghi ≤ 10 giây |
| G-02 | Số hóa Chương trình học & Thời khóa biểu Real-time: Quản lý cây chương trình đào tạo, môn tiên quyết và tự động đồng bộ TKB theo hệ thống Slot chuẩn FPT | Thuật toán xếp lịch tự động cho 200 SV hoàn tất ≤ 30 giây; 0% xung đột (Conflict) |
| G-03 | Hiện đại hóa Điểm danh & Cảnh báo chủ động: Tự động hóa quá trình điểm danh bằng QR Động, kích hoạt cảnh báo Email ngay khi SV chạm ngưỡng vắng 20% | Xác thực QR ≤ 2 giây; Email cảnh báo gửi đi ≤ 2 phút sau chốt phiên |
| G-04 | Minh bạch hóa Quản lý Điểm số & Xét điều kiện: Tự động tính điểm tổng kết theo tỷ trọng và ràng buộc điều kiện thi/đạt môn theo Quy chế FPT | Tính điểm toàn bộ 200 SV ≤ 30s ; Độ chính xác 100% theo công thức |
| G-05 | Tối ưu hóa & Số hóa hành chính: Hỗ trợ SV nộp đơn từ trực tuyến, giảm thời gian xử lý giấy tờ | 100% đơn từ được nộp trực tuyến; Email kết quả duyệt đơn ≤ 1 phút |
| G-06 | Tích hợp Payment Gateway, tự động gạch nợ và hỗ trợ kế toán đối soát | Giao dịch mã hóa SSL/TLS; Export báo cáo 5.000 dòng ≤ 15 giây |

## **2.3. Quy mô**

**Đối tượng & Số lượng người dùng:**

- **Sinh viên:** 150 – 200 sinh viên (chia 5–8 lớp chuyên ngành).
- **Giảng viên:** 10 – 15 giảng viên.
- **Cán bộ Quản nhiệm & Kế toán/Admin:** 1–3 cán bộ.

**Tải trọng dữ liệu (Data Load):**

- Tối đa 200 hồ sơ sinh viên cố định.
- Khoảng 1.500 – 2.000 lượt điểm danh, 1.000 đầu điểm thành phần và 100 – 300 giao dịch thanh toán/đơn từ mỗi học kỳ.

## **2.4. Giả định & Ràng buộc**

| **Loại** | **Nội dung** |
| --- | --- |
| Giả định | Dữ liệu đầu vào (danh sách SV) được cung cấp dưới dạng Excel/CSV theo biểu mẫu chuẩn |
| Giả định | Các khung giờ Slot chuẩn (Slot 1: 7h30-9h50, Slot 2…) đã được cấu hình tĩnh trong hệ thống |
| Giả định | Trường cung cấp mạng WiFi ổn định cho việc quét QR điểm danh |
| Giả định | Trình duyệt mobile của SV hỗ trợ WebRTC/Camera API (Chrome, Safari phiên bản hiện tại) |
| Ràng buộc | Hệ thống xây dựng trên nền tảng ASP.NET Core MVC, MS SQL Server, triển khai dạng PWA |
| Ràng buộc | Tích hợp Payment Gateway phụ thuộc vào API bên thứ 3 (VNPay/MoMo) |
| Ràng buộc | Quy chế tính điểm tuân theo quy chế đào tạo của FPT |

## **2.5. Rủi ro**

| **Mã** | **Rủi ro** | **Mức độ** | **Biện pháp giảm thiểu** |
| --- | --- | --- | --- |
| R-01 | API Payment Gateway thay đổi hoặc ngừng hoạt động | Cao | Thiết kế Adapter Pattern, dễ chuyển đổi gateway |
| R-02 | Gian lận điểm danh (chụp ảnh QR gửi ra ngoài lớp) | Trung bình | QR động refresh 10s, kiểm tra IP WiFi trường |
| R-03 | Mất kết nối mạng khi SV đang quét QR | Trung bình | Cho phép GV điểm danh thủ công (Manual Attendance) |
| R-04 | Webhook/IPN từ Payment Gateway bị mất do lỗi mạng | Cao | Cơ chế Retry + Query API tra soát thủ công |

# **CHƯƠNG 3. KIẾN TRÚC NGHIỆP VỤ**

## **3.1. Nguyên tắc thiết kế**

Hệ thống được xây dựng theo kiến trúc **Modular Monolithic** kết hợp mô hình **MVC (Model - View - Controller)**:

- **Modular Monolithic:** Phù hợp quy mô dự án, tập trung mã nguồn, dễ triển khai, tối ưu chi phí vận hành mà vẫn đảm bảo phân tách rõ ràng giữa các phân hệ.
- **MVC:** Phân tách rõ ràng giữa Xử lý giao diện (View), Điều hướng luồng (Controller) và Tương tác dữ liệu (Model).

## **3.2. Technology Stack**

| **Lớp kiến trúc (Layer)** | **Công nghệ / Nền tảng** | **Vai trò** |
| --- | --- | --- |
| Backend & Logic | C# / ASP.NET Core MVC | Bộ não xử lý nghiệp vụ, thuật toán tính điểm, xếp lịch Slot |
| Tương tác Dữ liệu (ORM) | Entity Framework Core (EF Core) + LINQ | Ánh xạ CSDL thành Object, Code-First Migration |
| Cơ sở dữ liệu | MS SQL Server | Toàn vẹn dữ liệu cho ràng buộc nghiệp vụ chặt chẽ |
| Frontend (Giao diện) | HTML/CSS/JS, Bootstrap, Razor Views | Web Responsive, render dữ liệu động từ Server |
| Real-time | SignalR (WebSockets) | Đẩy trạng thái điểm danh “Present” real-time lên màn hình GV |
| QR Code | QRCoder Library | Sinh mã QR động Base64 + Token mã hóa, refresh 10s |
| Thanh toán | VNPay API / MoMo API | Tạo URL thanh toán, Webhook Endpoint nhận IPN |
| Email | MailKit / SendGrid SMTP | Gửi Email cảnh báo vắng, biên lai giao dịch (Background Task) |
| Xác thực & Phân quyền | ASP.NET Core Identity | Role-based Access Control (Admin, GV, SV) |
| Hosting | IIS / Microsoft Azure | Triển khai và vận hành hệ thống |

## **3.3. Sơ đồ kiến trúc phân lớp**

PRESENTATION LAYER  
(HTML/CSS/JS, Bootstrap, Razor Views, SignalR Client)

CONTROLLER LAYER

(ASP.NET Core MVC Controllers, API Endpoints)

BUSINESS LOGIC LAYER

|     |     |     |     |
| --- | --- | --- | --- |
| QLSV-01<br><br>Sinh viên | QLSV-02<br><br>Đào tạo | QLSV-03<br><br>Điểm danh | QLSV-04<br><br>Điểm số |
| QLSV-05<br><br>Hành chính | QLSV-06<br><br>Thanh toán | Background Services<br><br>(Email, QR Refresh) |     |

DATA ACCESS LAYER

(Entity Framework Core + LINQ, Repositories)

DATABASE LAYER

(MS SQL Server)

EXTERNAL INTEGRATIONS

|     |     |
| --- | --- |
| VNPay | SMTP (Email) |

# **CHƯƠNG 4. DANH MỤC PHÂN HỆ & MÃ ĐỊNH DANH**

| **Mã phân hệ** | **Mnemonic** | **Phân hệ** | **BRD chi tiết** |
| --- | --- | --- | --- |
| QLSV-01 | STUDENT | Quản lý Sinh viên & Học tập | BRD-QLSV-01-v2.0 |
| QLSV-02 | TRAINING | Đào tạo & Thời khóa biểu | BRD-QLSV-02-v2.0 |
| QLSV-03 | ATTEND | Điểm danh (QR Code) | BRD-QLSV-03-v2.0 |
| QLSV-04 | GRADE | Quản lý Điểm & Khảo thí | BRD-QLSV-04-v2.0 |
| QLSV-05 | SERVICE | Dịch vụ Sinh viên (Hành chính) | BRD-QLSV-05-v2.0 |
| QLSV-06 | PAYMENT | Thanh toán (Payment Gateway) | BRD-QLSV-06-v2.0 |

# **CHƯƠNG 5. NGUYÊN TẮC & QUY TẮC NGHIỆP VỤ BẮT BUỘC**

## **5.1. Quy tắc Module 1 — Quản lý Sinh viên**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-001 | Mã sinh viên (Student ID) phải là duy nhất trên toàn hệ thống (VD: HE191612). | UC-QLSV-01.1 |
| BR-002 | Số CCCD và Email cá nhân không được phép trùng lặp giữa các tài khoản. | UC-QLSV-01.1 |
| BR-003 | SV chuyển sang “Bảo lưu” hoặc “Thôi học” lập tức bị gỡ khỏi lớp hiện tại và chặn đăng nhập ứng dụng. | UC-QLSV-01.2 |
| BR-004 | Sĩ số của một lớp chuyên ngành không được vượt quá số lượng thiết lập tối đa (VD: 30 SV/lớp). | UC-QLSV-01.3 |
| BR-005 | Một SV không thể nằm trong 2 lớp chuyên ngành khác nhau trong cùng một học kỳ. | UC-QLSV-01.3 |

## **5.2. Quy tắc Module 2 — Đào tạo & TKB**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-006 | Mã môn học (Subject Code) phải là duy nhất trên toàn hệ thống. | UC-QLSV-02.1 |
| BR-007 | Không được phép thiết lập vòng lặp logic (Deadlock) đối với các môn tiên quyết (A→B, B→A). | UC-QLSV-02.1 |
| BR-008 | Một Giảng viên không thể bị xếp dạy 2 lớp khác nhau trong cùng một Slot. | UC-QLSV-02.2 |
| BR-009 | Một Phòng học không thể chứa 2 lớp học trong cùng một Slot. | UC-QLSV-02.2 |
| BR-010 | Tổng số buổi học sinh ra phải bằng đúng tổng số Slot quy định của môn học đó. | UC-QLSV-02.2 |
| BR-011 | GV chỉ được báo nghỉ trước thời điểm bắt đầu Slot học ít nhất 12 giờ. Quá hạn hệ thống sẽ chặn. Trường hợp bất khả kháng, Quản nhiệm có quyền tạo lệnh báo nghỉ thay GV. | UC-QLSV-02.3 |
| BR-012 | Lịch học bù không được phép trùng (Conflict) với lịch học hiện tại của SV trong lớp đó. | UC-QLSV-02.3 |

## **5.3. Quy tắc Module 3 — Điểm danh**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-013 | QR Code phải chứa token mã hóa động, thay đổi (refresh) tự động 10giây/lần. | UC-QLSV-03.1 |
| BR-014 | QR Code chỉ thiết bị nằm trong hệ thống mới giải mã được. | UC-QLSV-03.1 |
| BR-015 | Mỗi tài khoản SV chỉ được ghi nhận “Present” 1 lần duy nhất trong 1 Slot. | UC-QLSV-03.2 |
| BR-016 | Nếu áp dụng GPS/IP WiFi, hệ thống check IP phải trùng với mạng WiFi của trường. | UC-QLSV-03.2 |
| BR-017 | Tỷ lệ vắng mặt (Absent) >= 20% tổng số Slot → hệ thống tự động đánh **Cấm thi (G3)**. | UC-QLSV-03.3 |
| BR-018 | Chỉ GV phụ trách lớp, Quản nhiệm và Admin mới có quyền sửa trạng thái điểm danh thủ công. | UC-QLSV-03.3 |

## **5.4. Quy tắc Module 4 — Điểm & Khảo thí**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-019 | Thang điểm tiêu chuẩn là hệ cơ số 10 (0.0 đến 10.0), làm tròn đến 1 chữ số thập phân. | UC-QLSV-04.1 |
| BR-020 | Sau khi Quản nhiệm chốt sổ môn học, GV không được quyền tự ý sửa điểm quá trình. | UC-QLSV-04.1 |
| BR-021 | Điều kiện Đạt (Pass) môn: (1) Vắng &lt; 20% VÀ (2) Final Exam &gt;= 4.0 VÀ (3) Tổng điểm >= 5.0. | UC-QLSV-04.2 |
| BR-022 | Điều kiện **Thi lại (Retake Exam)** — trạng thái G4: Vắng < 20% NHƯNG (Final Exam < 4.0 HOẶC Tổng điểm < 5.0). SV chỉ cần thi lại bài Final Exam, giữ nguyên điểm quá trình. | UC-QLSV-04.2 |
| BR-022b | Điều kiện **Học lại (Re-study)** — trạng thái G5: SV đã thi lại (G4) nhưng vẫn không đạt (FE < 4.0 HOẶC Tổng < 5.0 sau thi lại). SV phải đăng ký học lại toàn bộ môn từ đầu (vào lớp mới, làm lại bài, thi lại). | UC-QLSV-04.2 |
| BR-023 | Điều kiện Cấm thi (Fail): Vắng >= 20% tổng số Slot của môn học. SV chuyển sang trạng thái **Cấm thi (G3)**. SV phải chủ động đăng ký học lại (QT-13) để chuyển vào trạng thái G5 rồi G0. | UC-QLSV-04.2 |
| BR-024 | Điểm trung bình môn được làm tròn đến 1 chữ số thập phân (VD: 4.95 → 5.0). | UC-QLSV-04.3 |
| BR-025 | Sau khi chốt trạng thái Pass/Fail/Retake/Re-study, chỉ Admin có quyền sửa điểm (bắt buộc lưu Log giải trình). | UC-QLSV-04.3 |
| BR-025b | Mỗi SV chỉ được thi lại Final Exam tối đa **1 lần** cho mỗi lần học môn. Nếu vẫn không đạt → chuyển G5 (Học lại toàn bộ). | UC-QLSV-04.2 |
| BR-025c | SV học lại1 môn tối đa **3 lần**. Nếu vẫn không đạt sau lần thứ 3 → Quản nhiệm xét buộc thôi học hoặc chuyển ngành. | UC-QLSV-04.2 |

## **5.5. Quy tắc Module 5 — Dịch vụ Hành chính**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-026 | SV chỉ được nộp tối đa 3 đơn cùng loại ở trạng thái **Pending hoặc Processing** (tránh spam). Nếu các đơn cũ đã ở Approved/Rejected/Cancelled thì không tính. | UC-QLSV-05.1 |
| BR-027 | Đơn đặc thù (Phúc khảo) chỉ được nộp trong thời gian quy định (VD: 7 ngày sau công bố điểm). | UC-QLSV-05.1 |
| BR-028 | Mọi thao tác đổi trạng thái đơn của Quản nhiệm đều phải được ghi Log (Who & When). | UC-QLSV-05.2 |
| BR-029 | SV chỉ được “Hủy đơn” khi ở trạng thái “Pending”. Đã chuyển “Processing” thì không được hủy. | UC-QLSV-05.3 |

## **5.6. Quy tắc Module 6 — Thanh toán**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-030 | Mã giao dịch (Payment Session) chỉ có hiệu lực trong 15 phút. Quá hạn mã vô hiệu hóa. | UC-QLSV-06.1 |
| BR-031 | Số tiền gửi sang Payment Gateway phải khớp chính xác 100% với số tiền trong Database. | UC-QLSV-06.1 |
| BR-032 | Chỉ Kế toán/Admin mới được quyền xem dòng tiền và xuất báo cáo đối soát. | UC-QLSV-06.2 |
| BR-033 | Giao dịch thất bại (Failed) vẫn phải được lưu Database để tra soát khiếu nại. | UC-QLSV-06.2 |
| BR-034 | Tính năng Query Transaction và gạch nợ thủ công chỉ dành cho Kế toán/Admin. | UC-QLSV-06.3 |
| BR-035 | Mọi thao tác gạch nợ thủ công (Manual Sync) phải được ghi Log (ai thao tác, thời gian). | UC-QLSV-06.3 |

## **5.7. Quy tắc Module — Học lại & Đình chỉ**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-036 | SV chỉ được đăng ký học lại các môn có trạng thái Cấm thi (G3) hoặc Học lại (G5). Môn ở trạng thái Thi lại (G4) chỉ cần đăng ký thi lại FE, không cần học lại. | QT-13 |
| BR-037 | Mức phí học lại: Kỳ liền kề ngay sau kỳ trượt = **50%** đơn giá môn học; cách ≥ 1 kỳ = **100%** đơn giá môn học. | QT-13 |
| BR-038 | SV đang trong trạng thái **Đình chỉ (S5)** bị chặn hoàn toàn việc đăng ký học lại. Hệ thống hiển thị thông báo: “Tài khoản đang trong thời gian đình chỉ học tập 1 học kỳ”. | QT-13 |
| BR-039 | SV **sau khi hết thời hạn đình chỉ** (từng ở S5) đăng ký học lại phải đóng phí = **150%** đơn giá môn học (phạt kỷ luật). | QT-13 |
| BR-040 | Hệ thống tự động xếp SV học lại vào lớp chuyên ngành khả dụng (CurrentSize < MaxCapacity). Nếu lớp đầy → đưa SV vào danh sách chờ (Waitlisted) và thông báo Quản nhiệm xếp lớp bổ sung. | QT-13 |
| BR-041 | Thời hạn đình chỉ học tập là 1 học kỳ. Hết hạn, hệ thống tự động chuyển trạng thái SV từ S5 → S1 (Đang học). | QT-13 |

## **5.8. Quy tắc bổ sung — Thanh toán, Tốt nghiệp & Thông báo**

| **Mã** | **Quy tắc bắt buộc** | **Áp dụng** |
| --- | --- | --- |
| BR-042 | Phí thi lại Final Exam (trạng thái G4) = **20%** đơn giá môn học, không phân biệt kỳ liền kề hay cách kỳ. | QT-13 |
| BR-043 | SV bị đình chỉ lần 2 (tái phạm) → hệ thống tự động chuyển trạng thái S5 → S3 (Buộc thôi học). Quản nhiệm có quyền xét ngoại lệ (có Log). | QT-02 |
| BR-044 | Điều kiện Tốt nghiệp (S1 → S4): (1) Pass toàn bộ môn bắt buộc trong CTĐT, (2) Thanh toán hết nợ học phí và lệ phí, (3) Không đang bị đình chỉ (S5). | QT-02 |
| BR-045 | Hệ thống tự động chuyển hóa đơn Unpaid → Overdue khi vượt quá DueDate (Background Job chạy hàng ngày). | QT-11 |
| BR-046 | SV có hóa đơn Overdue bị chặn: (1) Không được đăng ký học lại, (2) Không được xem bảng điểm chính thức. Hệ thống hiển thị cảnh báo nợ phí. | QT-11, QT-13 |
| BR-047 | Thông báo In-app (Notification) được lưu trữ tối đa **90 ngày**. Quá hạn hệ thống tự động xóa. Người dùng có thể đánh dấu “Đã đọc”. | QT-15 |

# **CHƯƠNG 6. TÁC NHÂN, VAI TRÒ & THỰC THỂ NGHIỆP VỤ**

## **6.1. Từ điển Vai trò**

| **Mã** | **Vai trò** | **Mô tả** |
| --- | --- | --- |
| VT-01 | Quản nhiệm (Academic Staff) | Quản trị hồ sơ SV, phân lớp, xếp TKB, thiết lập chương trình đào tạo, duyệt đơn từ, duyệt lịch bù. |
| VT-02 | Giảng viên (Lecturer) | Mở phiên điểm danh, nhập điểm, báo nghỉ/đề xuất lịch bù, sửa điểm danh thủ công |
| VT-03 | Sinh viên (Student) | Quét QR điểm danh, xem TKB, xem điểm, nộp đơn từ, thanh toán lệ phí, theo dõi trạng thái đơn |
| VT-04 | Kế toán (Accountant) | Xem dòng tiền, xuất báo cáo đối soát, tra soát giao dịch lỗi, gạch nợ thủ công |
| VT-05 | Admin hệ thống | Toàn quyền hệ thống: sửa điểm sau chốt sổ (có Log), quản lý cấu hình, tạo tài khoản thủ công, CRUD Giảng viên & Phòng học. |
| VT-06 | Hệ thống (System) | Tự động xử lý: tính điểm, gạch nợ, gửi Email cảnh báo, chốt phiên điểm danh |
| VT-07 | Payment Gateway (VNPay/MoMo) | Bên thứ 3 xử lý thanh toán, gửi Webhook/IPN |

## **6.2. Danh mục Thực thể Nghiệp vụ**

| **Mã** | **Thực thể** | **Mô tả** |
| --- | --- | --- |
| TT-01 | Hồ sơ Sinh viên (Student Profile) | Chứa thông tin cá nhân (MSSV, CCCD, Email, SĐT, giới tính, địa chỉ), trạng thái học tập |
| TT-02 | Tài khoản Người dùng (User Account) | Thông tin đăng nhập, vai trò (Role), trạng thái kích hoạt |
| TT-03 | Lớp chuyên ngành (Class) | Mã lớp, chuyên ngành, học kỳ, sĩ số tối đa, danh sách SV |
| TT-04 | Môn học (Subject) | Mã môn, tên, số tín chỉ, thời lượng Slot, học kỳ, danh sách môn tiên quyết |
| TT-05 | Chương trình đào tạo (Curriculum) | Cây môn học theo khóa, ràng buộc tiên quyết/song hành |
| TT-06 | Thời khóa biểu (Schedule) | Lịch học theo Slot, phòng, GV, lớp, trạng thái buổi học |
| TT-07 | Phiên điểm danh (Attendance Session) | Mã phiên, Slot, lớp, trạng thái (Opening/Closed), QR Token |
| TT-08 | Bản ghi điểm danh (Attendance Record) | SV, phiên, trạng thái (Present/Absent), timestamp |
| TT-09 | Bảng điểm (Grade Record) | SV, môn, điểm thành phần (Quiz/Assign/Lab/FE), tỷ trọng, tổng điểm, trạng thái Pass/Fail/Retake |
| TT-10 | Đơn từ (Service Request) | Mã yêu cầu, loại đơn, SV, trạng thái, file đính kèm, ghi chú, timeline xử lý |
| TT-11 | Hóa đơn (Invoice) | Mã hóa đơn, SV, số tiền, trạng thái (Unpaid/Paid/Failed), mã giao dịch ngân hàng |
| TT-12 | Giao dịch thanh toán (Transaction) | Mã giao dịch, thời gian, phương thức, trạng thái, Webhook response |
| TT-13 | Phòng học (Room) | Mã phòng, sức chứa, trạng thái sử dụng |
| TT-14 | Activity Log | Ghi lại mọi thao tác quan trọng (import, sửa điểm, duyệt đơn, gạch nợ thủ công) |
| TT-15 | Đăng ký Học lại (Retake Registration) | Lưu thông tin SV đăng ký học lại: môn, kỳ gốc trượt, kỳ đăng ký lại, mức phí, trạng thái xếp lớp |
| TT-16 | Hồ sơ Kỷ luật (Disciplinary Record) | Lưu lý do đình chỉ, ngày bắt đầu, ngày kết thúc, trạng thái (Active/Expired) |
| TT-17 | Hồ sơ Giảng viên (Lecturer Profile) | Mã GV, họ tên, chuyên môn, email, SĐT, trạng thái hoạt động |
| TT-18 | Thông báo (Notification) | Nội dung thông báo, loại, người nhận, trạng thái đã đọc, thời điểm |
| TT-19 | Môn tiên quyết (Subject PreRequisite) | Bảng trung gian quản lý quan hệ tiên quyết giữa các môn học |
| TT-20 | Cấu hình tỷ trọng điểm (Grade Weight Config) | Tỷ trọng từng đầu điểm thành phần theo môn học |

## **6.3. Đặc tả Dữ liệu (Data Dictionary)**

### **Bảng: Hồ sơ Sinh viên (TT-01 - Student Profile)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| StudentID | String | Có  | PK. Mã định danh duy nhất (VD: HE191612) |
| CCCD | String | Có  | Unique, 12 ký tự số (^\[0-9\]{12}$) |
| FullName | String | Có  | Max 100 ký tự |
| DateOfBirth | Date | Có  | Ngày sinh (phải >= 16 tuổi tại thời điểm nhập học) |
| Email | String | Có  | Unique, định dạng Email chuẩn (@fpt.edu.vn) |
| PhoneNumber | String | Không | 10 ký tự số (^\[0-9\]{10}$) |
| Address | String | Không | Max 255 ký tự |
| Gender | Enum | Có  | Male, Female, Other |
| AvatarUrl | String | Không | Đường dẫn ảnh đại diện (.jpg, .png, tối đa 2MB) |
| Status | Enum | Có  | Trạng thái học tập: S0 (Mới), S1 (Đang học), S2 (Bảo lưu), S3 (Thôi học), S4 (Tốt nghiệp), S5 (Đình chỉ) |
| SuspendedUntil | Date | Không | Ngày hết hạn bảo lưu (null nếu không bảo lưu). Hệ thống kiểm tra theo BR-005b |
| ClassID | String | Không | FK -> TT-03 (Lớp chuyên ngành) |

### **Bảng: Tài khoản Người dùng (TT-02 - User Account)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| UserID | String | Có  | PK. Mã tài khoản duy nhất (Guid / String) |
| ProfileID | String | Không | FK -> Liên kết tới TT-01 (StudentID) hoặc Mã Giảng viên |
| Username | String | Có  | Unique. Tên đăng nhập (Email / MSSV / Mã GV) |
| PasswordHash | String | Có  | Mật khẩu mã hóa Bcrypt/Argon2 |
| Role | Enum | Có  | Admin, AcademicStaff, Lecturer, Student, Accountant |
| IsActive | Boolean | Có  | Default: True. False nếu tài khoản bị khóa/bảo lưu |
| FailedLoginCount | Int | Có  | Đếm số lần đăng nhập sai liên tiếp (Max 5) |
| LockoutEnd | DateTime | Không | Thời điểm hết hạn khóa tài khoản |
| CreatedAt | DateTime | Có  | Thời điểm tạo tài khoản |
| LastLoginAt | DateTime | Không | Thời điểm đăng nhập gần nhất |

### **Bảng: Lớp chuyên ngành (TT-03 - Class)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| ClassID | String | Có  | PK. Mã lớp (VD: SE1801) |
| MajorName | String | Có  | Tên chuyên ngành (VD: Kỹ thuật phần mềm) |
| MaxCapacity | Int | Có  | Sĩ số tối đa (Default: 30) |
| CurrentSize | Int | Có  | Sĩ số hiện tại |
| Semester | String | Có  | Học kỳ (VD: Fall2026) |

### **Bảng: Môn học (TT-04 - Subject)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| SubjectCode | String | Có  | PK. Unique (VD: PRF192, PRN211) |
| Name | String | Có  | Tên môn học (Max 100 ký tự) |
| Credits | Int | Có  | Số tín chỉ (> 0) |
| TotalSlots | Int | Có  | Tổng số Slot bài học (> 0, VD: 30 slots) |
| UnitPrice | Decimal | Có  | Đơn giá môn học (VNĐ), dùng để tính phí học lại/thi lại theo BR-037/BR-039/BR-042 |

### **Bảng: Chương trình đào tạo (TT-05 - Curriculum)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| CurriculumID | String | Có  | PK. Mã chương trình (VD: CURR-SE-2026) |
| MajorCode | String | Có  | Mã ngành (VD: SE, IA, GD) |
| SubjectCode | String | Có  | FK -> TT-04 |
| TermIndex | Int | Có  | Học kỳ khuyến nghị (1 -> 9) |
| IsMandatory | Boolean | Có  | Bắt buộc hay tự chọn |

### **Bảng: Thời khóa biểu (TT-06 - Schedule)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| ScheduleID | Int | Có  | PK. Identity Auto-increment |
| ClassID | String | Có  | FK -> TT-03 |
| SubjectCode | String | Có  | FK -> TT-04 |
| LecturerID | String | Có  | FK -> TT-17 (Hồ sơ Giảng viên) |
| RoomID | String | Có  | FK -> TT-13 (Phòng học) |
| SlotIndex | Int | Có  | Slot học trong ngày (1 -> 6) |
| Date | Date | Có  | Ngày học |
| Semester | String | Có  | Học kỳ (VD: Fall2026) — hỗ trợ query TKB theo kỳ |
| Status | Enum | Có  | Normal, Cancelled, MakeUp |

### **Bảng: Phiên điểm danh (TT-07 - Attendance Session)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| SessionID | Int | Có  | PK. Identity Auto-increment |
| ScheduleID | Int | Có  | FK -> TT-06 |
| OpenTime | DateTime | Có  | Thời điểm mở phiên điểm danh |
| CloseTime | DateTime | Có  | Thời điểm đóng phiên điểm danh |
| Status | Enum | Có  | Opening, Closed |
| DynamicQRToken | String | Có  | Token động mã hóa sinh từ server, refresh 10s |

### **Bảng: Bản ghi điểm danh (TT-08 - Attendance Record)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| RecordID | Int | Có  | PK. Identity Auto-increment |
| SessionID | Int | Có  | FK -> TT-07 |
| StudentID | String | Có  | FK -> TT-01 |
| Status | Enum | Có  | Present, Absent |
| ScannedAt | DateTime | Không | Thời điểm sinh viên quét mã thành công |
| IsManualEdit | Boolean | Có  | True nếu do Giảng viên/Quản nhiệm sửa thủ công |

### **Bảng: Bảng điểm (TT-09 - Grade Record)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| GradeID | Int | Có  | PK. Identity Auto-increment |
| StudentID | String | Có  | FK -> TT-01 |
| SubjectCode | String | Có  | FK -> TT-04 |
| ClassID | String | Có  | FK -> TT-03 (Lớp học, phân biệt các lần học khác nhau) |
| Semester | String | Có  | Học kỳ ghi điểm (VD: Fall2026) — phân biệt lần học |
| QuizScore | Float | Không | 0.0 -> 10.0 (Tỷ trọng theo TT-20 Grade Weight Config) |
| AssignmentScore | Float | Không | 0.0 -> 10.0 (Tỷ trọng theo TT-20) |
| LabScore | Float | Không | 0.0 -> 10.0 (Tỷ trọng theo TT-20) |
| FinalExamScore | Float | Không | 0.0 -> 10.0 (Tỷ trọng theo TT-20) |
| RetakeFEScore | Float | Không | 0.0 -> 10.0 (Điểm thi lại Final Exam, tối đa 1 lần theo BR-025b) |
| TotalScore | Float | Không | Σ(Điểm TP × Tỷ trọng từ TT-20), làm tròn 1 chữ số |
| AttemptCount | Int | Có  | Số lần học môn này (1 = lần đầu, 2 = học lại lần 1… tối đa 3 theo BR-025c) |
| Status | Enum | Có  | In Progress (G0), Passed (G1), Fail/Cấm thi (G3), Retake (G4), Re-study (G5) |

### **Bảng: Đơn từ (TT-10 - Service Request)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| RequestID | Int | Có  | PK. Identity Auto-increment |
| StudentID | String | Có  | FK -> TT-01 |
| RequestType | Enum | Có  | Phúc khảo, Chuyển lớp, Xin nghỉ học, Khác |
| Content | String | Có  | Nội dung chi tiết đơn |
| AttachmentUrl | String | Không | Đường dẫn file đính kèm (.pdf, .jpg) |
| Status | Enum | Có  | Pending, Processing, Approved, Rejected, Cancelled |
| CreatedAt | DateTime | Có  | Thời điểm tạo đơn |
| ProcessedBy | String | Không | Người duyệt (Quản nhiệm) |

### **Bảng: Hóa đơn (TT-11 - Invoice)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| InvoiceID | String | Có  | PK. Mã hóa đơn (VD: INV-2026-0001) |
| StudentID | String | Có  | FK -> TT-01 |
| Amount | Decimal | Có  | Số tiền cần thanh toán (> 0) |
| Description | String | Có  | Nội dung khoản thu (Học phí kỳ 1, Lệ phí phúc khảo…) |
| DueDate | DateTime | Có  | Hạn chót thanh toán |
| Status | Enum | Có  | Unpaid, Paid, Cancelled, Overdue |

### **Bảng: Giao dịch thanh toán (TT-12 - Transaction)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| TransactionID | String | Có  | PK. Mã giao dịch hệ thống |
| InvoiceID | String | Có  | FK -> TT-11 |
| PaymentGateway | Enum | Có  | VNPay, MoMo |
| GatewayTransNo | String | Không | Mã giao dịch phía Ngân hàng / Ví trả về |
| Amount | Decimal | Có  | Số tiền giao dịch |
| Status | Enum | Có  | Pending, Success, Failed |
| TransTime | DateTime | Có  | Thời gian thực hiện giao dịch |

### **Bảng: Phòng học (TT-13 - Room)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| RoomID | String | Có  | PK. Mã phòng (VD: Alpha-101, Beta-203) |
| Capacity | Int | Có  | Sức chứa tối đa (VD: 30, 40) |
| RoomType | Enum | Có  | Theory (Lý thuyết), Lab (Thực hành) |
| IsActive | Boolean | Có  | True (Đang sử dụng), False (Bảo trì) |

### **Bảng: Nhật ký thao tác (TT-14 - Activity Log)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| LogID | Int | Có  | PK. Identity Auto-increment |
| UserID | String | Có  | Mã người thực hiện thao tác |
| Action | String | Có  | Hành động (Sửa điểm, Duyệt đơn, Gạch nợ, Lockout) |
| TargetEntity | String | Có  | Thực thể bị tác động (TT-09, TT-11…) |
| OldValue | String | Không | Giá trị trước khi sửa (JSON / Text) |
| NewValue | String | Không | Giá trị sau khi sửa (JSON / Text) |
| Timestamp | DateTime | Có  | Thời điểm ghi log |
| IPAddress | String | Không | IP người dùng |

### **Bảng: Đăng ký Học lại (TT-15 - Retake Registration)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| RetakeID | Int | Có  | PK. Identity Auto-increment |
| StudentID | String | Có  | FK -> TT-01 |
| SubjectCode | String | Có  | FK -> TT-04 |
| OriginalSemester | String | Có  | Học kỳ SV trượt môn (VD: Fall2026) |
| RetakeSemester | String | Có  | Học kỳ SV đăng ký học lại (VD: Spring2027) |
| OriginalGradeStatus | Enum | Có  | G3 (Fail/Cấm thi) hoặc G5 (Re-study/Học lại) |
| FeePercentage | Int | Có  | 50, 100, hoặc 150 (%) - Theo BR-037/BR-039 |
| FeeAmount | Decimal | Có  | \= FeePercentage × UnitPrice môn học |
| InvoiceID | String | Không | FK -> TT-11 (Hóa đơn học lại) |
| AssignedClassID | String | Không | FK -> TT-03 (Lớp được xếp vào) |
| Status | Enum | Có  | Pending (chờ thanh toán), Paid (đã TT), Assigned (đã xếp lớp), Waitlisted (chờ mở lớp), Cancelled (hủy) |
| CreatedAt | DateTime | Có  | Thời điểm đăng ký |

### **Bảng: Hồ sơ Kỷ luật (TT-16 - Disciplinary Record)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| DisciplinaryID | Int | Có  | PK. Identity Auto-increment |
| StudentID | String | Có  | FK -> TT-01 |
| Reason | String | Có  | Lý do đình chỉ (Max 500 ký tự) |
| StartDate | DateTime | Có  | Ngày bắt đầu đình chỉ |
| EndDate | DateTime | Có  | Ngày kết thúc đình chỉ |
| SuspensionSemesters | Int | Có  | Số kỳ đình chỉ (Default: 1) |
| Status | Enum | Có  | Active (đang đình chỉ), Expired (hết hạn) |
| CreatedBy | String | Có  | Người tạo (Quản nhiệm / Admin) |
| CreatedAt | DateTime | Có  | Thời điểm ghi nhận |

### **Bảng: Hồ sơ Giảng viên (TT-17 - Lecturer Profile)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| LecturerID | String | Có  | PK. Mã giảng viên duy nhất (VD: GV001, GV002) |
| FullName | String | Có  | Họ tên đầy đủ (Max 100 ký tự) |
| Email | String | Có  | Unique, định dạng Email chuẩn (@fpt.edu.vn) |
| PhoneNumber | String | Không | 10 ký tự số |
| Department | String | Có  | Khoa/Bộ môn (VD: CNTT, QTKD) |
| Specialization | String | Không | Chuyên môn chính (VD: Lập trình Java, Mạng máy tính) |
| IsActive | Boolean | Có  | True (Đang giảng dạy), False (Nghỉ việc / Tạm nghỉ) |
| CreatedAt | DateTime | Có  | Thời điểm tạo hồ sơ |

### **Bảng: Thông báo (TT-18 - Notification)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| NotificationID | Int | Có  | PK. Identity Auto-increment |
| RecipientUserID | String | Có  | FK -> TT-02 (Người nhận) |
| Title | String | Có  | Tiêu đề thông báo (Max 200 ký tự) |
| Content | String | Có  | Nội dung chi tiết thông báo |
| NotificationType | Enum | Có  | Schedule (Lịch học), Grade (Điểm), Attendance (Điểm danh), Request (Đơn từ), Payment (Thanh toán), System (Hệ thống) |
| IsRead | Boolean | Có  | Default: False. True khi người dùng đánh dấu đã đọc |
| RelatedEntityType | String | Không | Loại thực thể liên quan (TT-06, TT-09, TT-10…) |
| RelatedEntityID | String | Không | ID của thực thể liên quan |
| CreatedAt | DateTime | Có  | Thời điểm tạo thông báo |
| ExpiresAt | DateTime | Có  | Thời điểm hết hạn (CreatedAt + 90 ngày theo BR-047) |

### **Bảng: Môn tiên quyết (TT-19 - Subject PreRequisite)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| SubjectCode | String | Có  | FK -> TT-04. Môn học chính |
| PreReqSubjectCode | String | Có  | FK -> TT-04. Môn tiên quyết phải Pass trước |
|     |     |     | Composite PK: (SubjectCode, PreReqSubjectCode). Hệ thống phải kiểm tra vòng lặp (BR-007) khi thêm mới |

### **Bảng: Cấu hình tỷ trọng điểm (TT-20 - Grade Weight Config)**

| **Trường** | **Kiểu dữ liệu** | **Bắt buộc** | **Đặc tả / Ràng buộc** |
| --- | --- | --- | --- |
| ConfigID | Int | Có  | PK. Identity Auto-increment |
| SubjectCode | String | Có  | FK -> TT-04 |
| ComponentName | String | Có  | Tên đầu điểm: Quiz, Assignment, Lab, FinalExam |
| WeightPercent | Int | Có  | Tỷ trọng (%) (VD: 10, 20, 50). Tổng các WeightPercent của 1 SubjectCode phải = 100% |
|     |     |     | Unique: (SubjectCode, ComponentName) |

# **CHƯƠNG 7. QUY TRÌNH NGHIỆP VỤ ĐẦU–CUỐI (USE CASE SPECIFICATION)**

## **QT-00 — Xác thực & Quản lý tài khoản (Đăng nhập)**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Xác thực & Quản lý tài khoản (Đăng nhập) |
| **Description** | Người dùng đăng nhập vào hệ thống để truy cập các tính năng theo phân quyền Role-Based Access Control. |
| **Actor(s)** | Tất cả Người dùng (All Users) |
| **Priority** | Must Have |
| **Trigger** | Người dùng mở ứng dụng và truy cập trang Login. |
| **Precondition(s)** | Tài khoản đã được tạo và kích hoạt (IsActive = True). |
| **Post-Condition(s)** | Đăng nhập thành công, nhận JWT Token, chuyển hướng tới Dashboard tương ứng. |
| **Basic Flow** | 1.Người dùng nhập Username/Email và Password.  <br><br>2.Hệ thống xác thực thông tin tài khoản.  <br><br>3.Hệ thống tạo và trả về JWT Token.  <br><br>4.Chuyển hướng người dùng vào Dashboard tương ứng. |
| **Alternative Flow** | 1a. Quên mật khẩu: Nhập Email -> Nhận link OTP -> Đặt lại mật khẩu. |
| **Exception Flow** | 2a. Sai thông tin: Hệ thống báo lỗi “Tài khoản hoặc mật khẩu không chính xác”.  <br><br/>2b. Sai mật khẩu 5 lần liên tiếp: Tài khoản bị khóa tạm thời trong 15 phút. |
| **Business Rules** | Không có BR nghiệp vụ đặc thù, tuân thủ logic bảo mật chuẩn. |
| **Non-functional Requirements** | NFR-01 (Thời gian login ≤ 1s), NFR-16 (Hash mật khẩu một chiều), NFR-17 (Khóa tài khoản sau 5 lần sai). |

## **QT-01 — Tiếp nhận hồ sơ sinh viên mới (Import danh sách)**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Tiếp nhận hồ sơ sinh viên mới (Import danh sách) |
| **Description** | Là Quản nhiệm hệ thống, tôi muốn nhập danh sách hồ sơ sinh viên đầu vào để hệ thống tạo mới dữ liệu và cấp tài khoản đăng nhập. |
| **Actor(s)** | Quản nhiệm (Academic Staff) |
| **Priority** | Must Have |
| **Trigger** | Bắt đầu học kỳ mới, có danh sách sinh viên cần đưa vào hệ thống quản lý. |
| **Precondition(s)** | • Tài khoản Quản nhiệm đã được phân quyền quản lý dữ liệu sinh viên  <br><br/>• Tệp dữ liệu hồ sơ (Excel/CSV) đã được chuẩn bị theo đúng biểu mẫu của hệ thống. |
| **Post-Condition(s)** | • Hồ sơ sinh viên được lưu trữ thành công vào Cơ sở dữ liệu.  <br><br/>• Hệ thống tự động tạo tài khoản đăng nhập cho các sinh viên mới.  <br><br/>• Hệ thống ghi nhận hoạt động Import vào Activity Log. |
| **Basic Flow** | 1.Quản nhiệm truy cập vào phân hệ “Quản lý Sinh viên”, chọn tính năng “Import hồ sơ”.  <br><br/>2\. Quản nhiệm tải lên tệp dữ liệu Excel/CSV đã chuẩn bị.  <br><br/>3\. Hệ thống quét dữ liệu và kiểm tra tính hợp lệ của các trường thông tin bắt buộc (CCCD, SĐT, Email).  <br><br/>4\. Hệ thống lưu trữ hồ sơ hợp lệ vào Database và tự động khởi tạo tài khoản đăng nhập.  <br><br/>5\. Hệ thống hiển thị thông báo “Import thành công” kèm theo số lượng bản ghi đã thêm. |
| **Alternative Flow** | 1a. Thêm mới hồ sơ thủ công (Single Record):<br><br>\*1a1. Quản nhiệm chọn lệnh “Thêm mới sinh viên”.  <br><br>\*1a2. Quản nhiệm điền thông tin vào Form đăng ký trên hệ thống.  <br><br>\*1a3. Quản nhiệm bấm “Lưu”.<br><br>Use Case tiếp tục bước 3. |
| **Exception Flow** | 3a. Dữ liệu trong tệp bị trùng lặp hoặc sai định dạng:  <br><br/>\*3a1. Hệ thống phát hiện CCCD, Email hoặc Mã SV đã tồn tại.  <br><br/>\*3a2. Hệ thống hiển thị thông báo lỗi “Import thất bại”, bôi đỏ các dòng chứa dữ liệu lỗi và yêu cầu tải lại.<br><br>Use Case dừng lại. |
| **Business Rules** | BR-001: Mỗi hồ sơ sinh viên phải có một Mã sinh viên (Student ID) duy nhất trên toàn hệ thống.  <br><br/>BR-002: CCCD và Email cá nhân không được phép trùng lặp giữa các tài khoản. |
| **Non-functional Requirements** | NFR-01: Thời gian xử lý file import chứa 1.000 bản ghi không được vượt quá 10 giây. |

## **QT-02 — Cập nhật trạng thái học tập**

<div class="joplin-table-wrapper"><table><thead><tr><th><p><strong>Thuộc tính</strong></p></th><th><p><strong>Mô tả chi tiết</strong></p></th></tr></thead><tbody><tr><td><p><strong>Use Case Name</strong></p></td><td><p>Cập nhật trạng thái học tập<br></p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Quản nhiệm cập nhật trạng thái học tập của sinh viên (Bảo lưu, Thôi học, Tốt nghiệp) khi có quyết định chính thức từ nhà trường.<br></p></td></tr><tr><td><p><strong>Actor(s)</strong></p></td><td><p>Quản nhiệm (Academic Staff)<br></p></td></tr><tr><td><p><strong>Priority</strong></p></td><td><p>Must Have<br></p></td></tr><tr><td><p><strong>Trigger</strong></p></td><td><p>Có quyết định chính thức cho phép thay đổi trạng thái sinh viên.<br></p></td></tr><tr><td><p><strong>Precondition(s)</strong></p></td><td><p>Hồ sơ sinh viên đã tồn tại và hệ thống đã ghi nhận sinh viên này.<br></p></td></tr><tr><td><p><strong>Post-Condition(s)</strong></p></td><td><p>Trạng thái sinh viên được cập nhật, quyền truy cập và dữ liệu liên quan được điều chỉnh.<br></p></td></tr><tr><td><p><strong>Basic Flow</strong></p></td><td><ol><li>Quản nhiệm tìm kiếm hồ sơ sinh viên cần thao tác.<br></li><li>Chọn chức năng “Cập nhật trạng thái”.<br></li><li>Lựa chọn trạng thái mới (VD: Bảo lưu) và nhập lý do<br></li><li>Xác nhận thay đổi.<br></li><li>Hệ thống cập nhật Database, tự động thu hồi/khóa quyền liên quan tương ứng với trạng thái mới.<br></li></ol></td></tr><tr><td><p><strong>Alternative Flow</strong></p></td><td><p>Không có.<br></p></td></tr><tr><td><p><strong>Exception Flow</strong></p></td><td><p>3a. Sinh viên đang nợ phí: Hệ thống hiển thị cảnh báo nợ phí và chặn việc cập nhật trạng thái sang “Bảo lưu” hoặc “Thôi học”.<br></p></td></tr><tr><td><p><strong>Business Rules</strong></p></td><td><p>BR-003: SV chuyển sang “Bảo lưu” hoặc “Thôi học” lập tức bị gỡ khỏi lớp hiện tại và chặn đăng nhập ứng dụng.<br></p></td></tr><tr><td><p><strong>Non-functional Requirements</strong></p></td><td><p>Tính đồng bộ dữ liệu Real-time (Trạng thái có hiệu lực tức thì).<br></p></td></tr></tbody></table></div>

## **QT-03 — Phân bổ sinh viên vào lớp chuyên ngành**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Phân bổ sinh viên vào lớp chuyên ngành |
| **Description** | Quản nhiệm chia danh sách sinh viên mới nhập học vào các lớp chuyên ngành cố định để chuẩn bị xếp lịch. |
| **Actor(s)** | Quản nhiệm (Academic Staff) |
| **Priority** | Must Have |
| **Trigger** | Chuẩn bị học kỳ mới, có danh sách SV (trạng thái S0) cần được gán lớp. |
| **Precondition(s)** | Danh sách lớp chuyên ngành đã được tạo, danh sách SV mới đã được Import. |
| **Post-Condition(s)** | SV được gán vào lớp, chuyển sang trạng thái S1 (Đang học), sĩ số lớp cập nhật chính xác. |
| **Basic Flow** | 1.Quản nhiệm chọn tính năng “Phân lớp tự động”.  <br><br/>2\. Hệ thống áp dụng thuật toán chia đều sinh viên vào các lớp khả dụng.  <br><br/>3\. Quản nhiệm xem trước danh sách dự thảo (Draft) và nhấn “Xác nhận”.  <br><br/>4\. Hệ thống gán SV vào các lớp tương ứng và cập nhật trạng thái sĩ số. |
| **Alternative Flow** | 1a. Phân lớp thủ công: Quản nhiệm tự chọn từng nhóm SV và gán trực tiếp vào một lớp cụ thể. |
| **Exception Flow** | 2a. Lớp đầy: Vượt quá sĩ số tối đa quy định, hệ thống cảnh báo đỏ và yêu cầu Quản nhiệm mở thêm lớp mới. |
| **Business Rules** | BR-004: Sĩ số của một lớp không được vượt quá số lượng thiết lập tối đa (VD: 30 SV/lớp).  <br><br/>BR-005: Một SV không thể nằm trong 2 lớp chuyên ngành khác nhau trong cùng học kỳ. |
| **Non-functional Requirements** | Tối ưu hóa UI để xử lý danh sách hàng trăm sinh viên mượt mà. |

## **QT-04 — Thiết lập khung chương trình môn học**

<div class="joplin-table-wrapper"><table><thead><tr><th><p><strong>Thuộc tính</strong></p></th><th><p><strong>Mô tả chi tiết</strong></p></th></tr></thead><tbody><tr><td><p><strong>Use Case Name</strong></p></td><td><p>Thiết lập khung chương trình môn học<br></p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Quản nhiệm tạo mới thông tin môn học và thiết lập các điều kiện tiên quyết (Pre-requisites) của chương trình đào tạo.<br></p></td></tr><tr><td><p><strong>Actor(s)</strong></p></td><td><p>Quản nhiệm (Academic Staff)<br></p></td></tr><tr><td><p><strong>Priority</strong></p></td><td><p>Must Have<br></p></td></tr><tr><td><p><strong>Trigger</strong></p></td><td><p>Xây dựng chương trình đào tạo khóa mới hoặc có môn học mới được phê duyệt.<br></p></td></tr><tr><td><p><strong>Precondition(s)</strong></p></td><td><p>QN có quyền cấu hình hệ thống môn học.<br></p></td></tr><tr><td><p><strong>Post-Condition(s)</strong></p></td><td><p>Dữ liệu môn học và điều kiện ràng buộc được lưu trữ an toàn.<br></p></td></tr><tr><td><p><strong>Basic Flow</strong></p></td><td><ol><li>Quản nhiệm truy cập “Đào tạo” -&gt; “Thêm mới” môn học.<br><br>2. Nhập thông tin môn học (Mã môn, Tên, Tín chỉ, Tổng Slot).<br><br>3. Thiết lập môn tiên quyết (nếu có).<br><br>4. Nhấn “Lưu”.<br><br>5. Hệ thống kiểm tra tính hợp lệ và lưu vào Database.<br></li></ol></td></tr><tr><td><p><strong>Alternative Flow</strong></p></td><td><p>Không có.<br></p></td></tr><tr><td><p><strong>Exception Flow</strong></p></td><td><p>2a. Trùng mã môn: Hệ thống báo lỗi “Mã môn học đã tồn tại”.<br><br>3a. Vòng lặp tiên quyết: Hệ thống phát hiện Deadlock (Ví dụ: A cần B, B cần A) -&gt; Chặn lưu và báo lỗi.<br></p></td></tr><tr><td><p><strong>Business Rules</strong></p></td><td><p>BR-006: Mã môn học phải là duy nhất.<br><br>BR-007: Không được phép thiết lập vòng lặp logic (Deadlock) đối với môn tiên quyết.<br></p></td></tr><tr><td><p><strong>Non-functional Requirements</strong></p></td><td><p>Thuật toán kiểm tra vòng lặp tiên quyết phản hồi ≤ 2 giây.<br></p></td></tr></tbody></table></div>

## **QT-05 — Đồng bộ Thời khóa biểu**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Đồng bộ Thời khóa biểu (Auto-Scheduling) |
| **Description** | Sử dụng thuật toán tự động để phân bổ Slots học, Giảng viên, Phòng học cho các Lớp mà không gây xung đột (Conflict). |
| **Actor(s)** | Quản nhiệm (Academic Staff) |
| **Priority** | Must Have |
| **Trigger** | Gần bắt đầu kỳ/block học mới, cần tạo lịch học chi tiết. |
| **Precondition(s)** | Dữ liệu Lớp, Môn, Giảng viên, Phòng học đã đầy đủ. |
| **Post-Condition(s)** | Thời khóa biểu hoàn chỉnh được chốt và tự động hiển thị lên Dashboard của Giảng viên & Sinh viên. |
| **Basic Flow** | 1.QN vào màn hình TKB, chọn “Xếp lịch tự động”.  <br><br/>2\. Cấu hình Học kỳ, Chọn các Lớp, Chọn Môn.  <br><br/>3\. Khởi chạy thuật toán xếp lịch.  <br><br/>4\. Hệ thống phân bổ tối ưu và tạo bản Draft hiển thị trên Calendar.  <br><br/>5\. QN rà soát sơ bộ và nhấn “Đồng bộ TKB”.  <br><br/>6\. Hệ thống lưu Database và Push lịch học lên Dashboard các bên. |
| **Alternative Flow** | 1a. Xếp lịch thủ công: QN thao tác kéo thả từng Slot gán cho Lớp, Phòng và GV trên giao diện Calendar. |
| **Exception Flow** | 4a. Xung đột tài nguyên: Thiếu Phòng hoặc trùng GV -> Thuật toán dừng lại, hiển thị danh sách các Lớp không thể xếp lịch để xử lý thủ công. |
| **Business Rules** | BR-008: Một GV không thể bị xếp dạy 2 lớp khác nhau trong cùng 1 Slot.  <br><br/>BR-009: Một Phòng không thể chứa 2 lớp học cùng lúc.  <br><br/>BR-010: Tổng số buổi sinh ra phải bằng đúng tổng Slot quy định. |
| **Non-functional Requirements** | NFR-04: Thời gian chạy thuật toán auto-scheduling cho 200 SV ≤ 30 giây; Đảm bảo 0% Conflict tài nguyên. |

## **QT-06 — Điều chỉnh lịch học (Báo nghỉ & Lịch bù)**

<div class="joplin-table-wrapper"><table><thead><tr><th><p><strong>Thuộc tính</strong></p></th><th><p><strong>Mô tả chi tiết</strong></p></th></tr></thead><tbody><tr><td><p><strong>Use Case Name</strong></p></td><td><p>Điều chỉnh lịch học (Báo nghỉ &amp; Lịch bù)<br></p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Giảng viên báo nghỉ khi có việc đột xuất và đề xuất lịch dạy bù, Quản nhiệm tiến hành xét duyệt.<br></p></td></tr><tr><td><p><strong>Actor(s)</strong></p></td><td><p>Giảng viên, Quản nhiệm<br></p></td></tr><tr><td><p><strong>Priority</strong></p></td><td><p>Must Have<br></p></td></tr><tr><td><p><strong>Trigger</strong></p></td><td><p>Giảng viên có sự cố đột xuất không thể đứng lớp theo TKB.<br></p></td></tr><tr><td><p><strong>Precondition(s)</strong></p></td><td><p>Lịch học chưa diễn ra, cách thời điểm báo nghỉ ít nhất 12 giờ.<br></p></td></tr><tr><td><p><strong>Post-Condition(s)</strong></p></td><td><p>TKB cập nhật trạng thái “MakeUp” (Bù), tự động gửi thông báo cho Sinh viên lớp đó.<br></p></td></tr><tr><td><p><strong>Basic Flow</strong></p></td><td><ol><li>Giảng viên truy cập TKB, chọn Slot học sắp tới, nhấn “Báo nghỉ”.<br><br>2. GV điền lý do và chỉ định Ngày/Slot bù đề xuất.<br><br>3. Gửi yêu cầu duyệt đến Quản nhiệm.<br><br>4.Quản nhiệm vào trung tâm xử lý, xem xét và bấm “Duyệt”.<br><br>5. Hệ thống chốt đổi TKB, sinh ra Slot học bù mới.1. Hệ thống gửi Email/Noti cho tất cả sinh viên bị ảnh hưởng.<br></li></ol></td></tr><tr><td><p><strong>Alternative Flow</strong></p></td><td><p>4a. Quản nhiệm “Từ chối” đề xuất lịch bù (do trùng sự kiện trường) -&gt; Trả lại cho GV chọn lại lịch.<br></p></td></tr><tr><td><p><strong>Exception Flow</strong></p></td><td><p>1a. Báo nghỉ quá hạn: Nếu thời điểm hiện tại cách giờ học &lt; 12h, nút “Báo nghỉ” vô hiệu hóa, GV phải liên hệ trực tiếp.2a. Lịch bù trùng TKB Sinh viên: Hệ thống cảnh báo Conflict ngay khi GV chọn.<br></p></td></tr><tr><td><p><strong>Business Rules</strong></p></td><td><p>BR-011: GV chỉ được báo nghỉ trước Slot học tối thiểu 12 giờ.BR-012: Lịch học bù không được phép Conflict với lịch hiện tại của Sinh viên.<br></p></td></tr><tr><td><p><strong>Non-functional Requirements</strong></p></td><td><p>Push Notification và gửi Email cảnh báo hoàn tất ≤ 1 phút sau khi QN duyệt.<br></p></td></tr></tbody></table></div>

## **QT-07 — Điểm danh bằng QR động**

<div class="joplin-table-wrapper"><table><thead><tr><th><p><strong>Thuộc tính</strong></p></th><th><p><strong>Mô tả chi tiết</strong></p></th></tr></thead><tbody><tr><td><p><strong>Use Case Name</strong></p></td><td><p>Mở phiên &amp; Điểm danh bằng QR động<br></p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Giảng viên mở mã QR điểm danh Real-time trên bảng, Sinh viên dùng App của nhà trường để quét mã xác thực sự có mặt.<br></p></td></tr><tr><td><p><strong>Actor(s)</strong></p></td><td><p>Giảng viên, Sinh viên, Hệ thống<br></p></td></tr><tr><td><p><strong>Priority</strong></p></td><td><p>Must Have<br></p></td></tr><tr><td><p><strong>Trigger</strong></p></td><td><p>Bắt đầu giờ học, GV yêu cầu sinh viên điểm danh.<br></p></td></tr><tr><td><p><strong>Precondition(s)</strong></p></td><td><p>GV phải ở trong lớp học, có kết nối màn hình chiếu. Sinh viên có cài đặt App nội bộ.<br></p></td></tr><tr><td><p><strong>Post-Condition(s)</strong></p></td><td><p>Trạng thái “Present/Absent” của toàn lớp được ghi nhận. Hệ thống tự gửi cảnh báo nếu sinh viên vi phạm quy chế nghỉ học.<br></p></td></tr><tr><td><p><strong>Basic Flow</strong></p></td><td><ol><li>GV chọn “Mở điểm danh” trên hệ thống.<br><br>2. Hệ thống sinh mã QR động (chứa Token mã hóa) chiếu lên màn hình, tự động refresh mỗi 10s.<br><br>3. Sinh viên mở App nội bộ trên điện thoại, quét QR.<br><br>4. App gửi Token giải mã lên Server, ghi nhận trạng thái “Present” cho SV tương ứng.<br><br>5. Khi hoàn tất, GV đóng phiên. Hệ thống đánh “Absent” cho toàn bộ SV chưa quét QR.<br><br>6. Hệ thống kiểm tra tỷ lệ vắng mặt tổng cộng, nếu &gt;= 20% tự động đánh rớt môn.<br></li></ol></td></tr><tr><td><p><strong>Alternative Flow</strong></p></td><td><p>5a. Sửa điểm danh thủ công: SV hỏng điện thoại, GV vào danh sách lớp chọn tên SV và cập nhật “Present” thủ công, ghi Log.<br></p></td></tr><tr><td><p><strong>Exception Flow</strong></p></td><td><p>3a. Dùng App bên ngoài quét (Zalo/Camera): Không mở được link, hiển thị chuỗi mã hóa vô nghĩa.3b. Mã QR đã cũ (hết 10s): App báo lỗi “Mã hết hạn, vui lòng quét mã mới trên bảng”.<br></p></td></tr><tr><td><p><strong>Business Rules</strong></p></td><td><p>BR-013: QR Code động refresh mỗi 10s.<br><br>BR-014: Chỉ thiết bị/App nằm trong hệ thống mới giải mã được QR.<br><br>BR-015: 1 SV chỉ được ghi nhận “Present” 1 lần trong Slot.<br><br>BR-016: Xác thực IP mạng WiFi trường (Tùy chọn).BR-017: Vắng &gt;= 20% tự động đánh Fail (FE).<br><br>BR-018: Chỉ GV phụ trách, Quản nhiệm và Admin được sửa điểm danh thủ công.<br></p></td></tr><tr><td><p><strong>Non-functional Requirements</strong></p></td><td><p>Thời gian phản hồi quét QR ≤ 2 giây. Hỗ trợ kết nối đồng thời tốt theo NFR-18.NFR-19: Ghi Log Audit nếu sửa tay.<br></p></td></tr></tbody></table></div>

## **QT-08 — Cập nhật điểm quá trình**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Cập nhật điểm quá trình |
| **Description** | Giảng viên nhập điểm các đầu điểm thành phần (Quiz, Assignment, Lab) cho sinh viên trên giao diện quản lý điểm. |
| **Actor(s)** | Giảng viên (Lecturer) |
| **Priority** | Must Have |
| **Trigger** | GV hoàn tất việc chấm bài kiểm tra/bài tập của sinh viên. |
| **Precondition(s)** | Môn học đang trong trạng thái “In Progress”, Quản nhiệm chưa chốt sổ môn học. |
| **Post-Condition(s)** | Bảng điểm quá trình được cập nhật thành công vào hệ thống. |
| **Basic Flow** | 1.GV truy cập lớp học, chọn Tab “Quản lý điểm”.  <br><br/>2\. Nhập trực tiếp điểm thành phần vào các ô tương ứng trên DataGrid (Giao diện Excel-like).  <br><br/>3\. Hệ thống kiểm tra (Validate) dữ liệu trực tiếp: Điểm phải từ 0.0 đến 10.0.  <br><br/>4\. GV nhấn “Lưu bảng điểm”.  <br><br/>5\. Hệ thống lưu thay đổi xuống Database. |
| **Alternative Flow** | Không có. |
| **Exception Flow** | 3a. Điểm vượt ngoài dải hoặc sai định dạng: Ô nhập liệu chuyển sang màu đỏ, chặn tính năng “Lưu bảng điểm” cho đến khi sửa xong. |
| **Business Rules** | BR-019: Thang điểm chuẩn là 0.0 - 10.0, làm tròn 1 chữ số thập phân.  <br><br/>BR-020: Sau khi QN chốt sổ môn, GV bị tước quyền tự sửa điểm. |
| **Non-functional Requirements** | Giao diện tối ưu để hỗ trợ phím Tab/Enter nhập liệu nhanh liên tục. |

## **QT-09 — Xét điều kiện dự thi & Tổng kết điểm**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Xét điều kiện dự thi & Tổng kết Pass/Fail/Retake/Re-study |
| **Description** | Hệ thống tự động tổng hợp toàn bộ điểm số, đánh giá tỷ lệ vắng và đưa ra phán quyết đậu/trượt cuối môn. |
| **Actor(s)** | Hệ thống (Tự động), Quản nhiệm, Admin |
| **Priority** | Must Have |
| **Trigger** | Điểm Final Exam được nhập hoàn tất và QN nhấn nút “Chốt sổ”. |
| **Precondition(s)** | Đã nhập đầy đủ các đầu điểm quá trình và điểm thi cuối kỳ. |
| **Post-Condition(s)** | Trạng thái môn học của Sinh viên chuyển sang Passed (G1), Fail (G3), Retake (G4) hoặc Re-study (G5). |
| **Basic Flow** | 1.Hệ thống tự động quét lại % Vắng mặt: Nếu >= 20% -> Chốt FAIL (G3), SV chuyển thẳng sang Học lại (G5).  <br><br/>2\. Với SV có tỷ lệ vắng < 20%, hệ thống tính Tổng điểm môn học theo công thức tỷ trọng (Ví dụ: Quiz 10% + FE 50%…).  <br><br/>3\. Hệ thống quét điều kiện liệt: Nếu FE &lt; 4.0 HOẶC Tổng điểm < 5.0 -&gt; Chốt RETAKE (G4), cho phép **thi lại bài Final Exam** (giữ nguyên điểm quá trình).  <br><br/>3b. Nếu SV đang ở G4 (đã thi lại) mà vẫn không đạt -> Chốt RE-STUDY (G5), yêu cầu **học lại toàn bộ** môn từ đầu.  <br><br/>4\. Các SV thỏa mãn (Vắng &lt; 20%, FE &gt;= 4.0, Tổng >= 5.0) -> Chốt PASSED (G1).  <br><br/>5\. Cập nhật Bảng điểm chính thức (Transcript). |
| **Alternative Flow** | 5a. Admin sửa điểm sau chốt sổ: Admin nhập điểm mới -> Hệ thống bắt buộc nhập Lý do giải trình -> Cập nhật lại Trạng thái (G1/G3/G4/G5) -> Ghi log (Audit Trail). |
| **Exception Flow** | Không có. Mọi tình huống đều được cover bởi Business Rules. |
| **Business Rules** | BR-021: Điều kiện Đạt (Pass) môn.  <br><br/>BR-022: Điều kiện Thi lại (Retake Exam).  <br><br/>BR-022b: Điều kiện Học lại (Re-study) khi thi lại vẫn trượt.  <br><br/>BR-023: Điều kiện Cấm thi/Fail → chuyển thẳng G5.  <br><br/>BR-024: Điểm TB được làm tròn 1 chữ số.BR-025: Quyền sửa điểm sau chốt sổ chỉ dành cho Admin kèm Log. |
| **Non-functional Requirements** | NFR-07: Tính điểm toàn bộ 200 SV ≤ 1 phút. NFR-19: Ghi Log Audit 100%. |

## **QT-10 — Nộp đơn từ & Xét duyệt (Dịch vụ hành chính)**

<div class="joplin-table-wrapper"><table><thead><tr><th><p><strong>Thuộc tính</strong></p></th><th><p><strong>Mô tả chi tiết</strong></p></th></tr></thead><tbody><tr><td><p><strong>Use Case Name</strong></p></td><td><p>Nộp đơn từ &amp; Xét duyệt<br></p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Sinh viên nộp đơn từ trực tuyến (Phúc khảo, Chuyển lớp, Đơn xin nghỉ), Quản nhiệm tiếp nhận và xử lý.<br></p></td></tr><tr><td><p><strong>Actor(s)</strong></p></td><td><p>Sinh viên, Quản nhiệm<br></p></td></tr><tr><td><p><strong>Priority</strong></p></td><td><p>Should Have<br></p></td></tr><tr><td><p><strong>Trigger</strong></p></td><td><p>Sinh viên có nhu cầu giải quyết thủ tục hành chính liên quan tới học vụ.<br></p></td></tr><tr><td><p><strong>Precondition(s)</strong></p></td><td><p>Sinh viên đăng nhập vào hệ thống bình thường (Trạng thái S1).<br></p></td></tr><tr><td><p><strong>Post-Condition(s)</strong></p></td><td><p>Đơn được chuyển trạng thái sang Approved/Rejected, Sinh viên nhận được Email thông báo kết quả.<br></p></td></tr><tr><td><p><strong>Basic Flow</strong></p></td><td><ol><li>SV truy cập Cổng Dịch vụ, chọn Loại đơn và điền nội dung, đính kèm File chứng minh.<br><br>2. SV bấm nộp. Trạng thái đơn là “Pending”.<br><br>3. QN nhận Noti, vào kiểm tra Đơn.<br><br>4. QN thực hiện thay đổi trạng thái sang “Approved” (Duyệt) hoặc “Rejected” (Từ chối) kèm Ghi chú.<br><br>5. Hệ thống gửi Email chứa kết quả cho SV.<br></li></ol></td></tr><tr><td><p><strong>Alternative Flow</strong></p></td><td><p>2a. Đơn có lệ phí (VD Phúc khảo): SV phải thanh toán qua Payment Gateway, khi thanh toán thành công Đơn mới được chuyển cho QN xử lý.<br></p></td></tr><tr><td><p><strong>Exception Flow</strong></p></td><td><p>1a. Vượt quá số lượng đơn cho phép (Spam): Hệ thống hiển thị cảnh báo không cho nộp thêm.<br><br>3a. Hủy đơn: SV tự thu hồi đơn đang Pending, trạng thái đổi thành “Cancelled”, dừng xử lý.<br></p></td></tr><tr><td><p><strong>Business Rules</strong></p></td><td><p>BR-026: Tối đa 3 đơn cùng loại chưa xử lý.<br><br>BR-027: Tuân thủ hạn chót nộp đơn đặc thù (VD Phúc khảo trong 7 ngày).<br><br>BR-028: Mọi thao tác duyệt đơn của QN đều phải lưu Log (Who &amp; When).<br><br>BR-029: Chỉ được “Hủy đơn” khi đang Pending.<br></p></td></tr><tr><td><p><strong>Non-functional Requirements</strong></p></td><td><p>Email tự động gửi kết quả duyệt trong vòng 1 phút theo SLA hệ thống.<br></p></td></tr></tbody></table></div>

## **QT-11 — Thanh toán trực tuyến (Payment Gateway)**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Thanh toán trực tuyến (Payment Gateway) |
| **Description** | Sinh viên thanh toán các khoản phí phát sinh (Học phí, Lệ phí đơn từ) thông qua VNPay hoặc MoMo. |
| **Actor(s)** | Sinh viên, Kế toán, Payment Gateway |
| **Priority** | Should Have |
| **Trigger** | Hệ thống xuất hóa đơn mới (Unpaid), sinh viên chủ động chọn thanh toán. |
| **Precondition(s)** | Hóa đơn có trạng thái “Unpaid”. Payment Gateway đang hoạt động. |
| **Post-Condition(s)** | Hóa đơn chuyển trạng thái “Paid”, giao dịch được đối soát. |
| **Basic Flow** | 1\. SV mở danh sách Hóa đơn nợ, chọn phương thức thanh toán.  <br><br/>2\. Hệ thống sinh URL chứa mã phiên giao dịch và chuyển hướngtrình duyệt sang cổng thanh toán đối tác (VNPay/MoMo).  <br><br/>3\. SV thanh toán thành công tại Gateway.  <br><br/>4\. Gateway gọi IPN/Webhook trả kết quả về Server của Trường.  <br><br/>5\. Server xác thực Chữ ký điện tử (Checksum), gạch nợ tự động chuyển hóa đơn sang “Paid”. |
| **Alternative Flow** | 4a. Mất IPN/Webhook: Mạng lỗi khiến Webhook không về, Kế toán vào Dashboard bấm lệnh “Query Transaction” thủ công -> Hệ thống gọi API sang Gateway lấy kết quả chốt -> Gạch nợ bổ sung. |
| **Exception Flow** | 3a. Giao dịch thất bại/Quá hạn: Hóa đơn vẫn giữ nguyên “Unpaid”, Transaction chuyển “Failed”.  <br><br/>5a. Checksum sai lệch/Số tiền không khớp: Hệ thống từ chối gạch nợ, cảnh báo Admin kiểm tra gian lận. |
| **Business Rules** | BR-030: Mã Payment Session hiệu lực trong 15 phút.  <br><br/>BR-031: Dữ liệu số tiền gửi đi và nhận về phải khớp 100%.  <br><br/>BR-032: Tính năng đối soát chỉ dành cho Kế toán/Admin.  <br><br/>BR-033: Giao dịch thất bại vẫn phải lưu DB.  <br><br/>BR-034, BR-035: Tính năng Query/Gạch nợ thủ công phải lưu Log thao tác. |
| **Non-functional Requirements** | NFR-15: Giao tiếp SSL/TLS mã hóa hoàn toàn. Export báo cáo đối soát 5.000 dòng ≤ 15 giây. |

## **  
QT-12 — Quản lý Danh mục (Giảng viên, Phòng học)**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Quản lý Danh mục Hệ thống (Master Data) |
| **Description** | Admin thực hiện các thao tác Thêm, Sửa, Xóa để duy trì cơ sở dữ liệu Giảng viên và Phòng học. |
| **Actor(s)** | Admin Hệ thống |
| **Priority** | Must Have |
| **Trigger** | Có thay đổi nhân sự giảng viên hoặc cơ sở vật chất. |
| **Precondition(s)** | Tài khoản Admin đang đăng nhập. |
| **Post-Condition(s)** | Danh mục hệ thống được cập nhật an toàn. |
| **Basic Flow** | 1\. Admin vào màn hình Quản lý danh mục tương ứng.  <br><br/>2\. Chọn hành động Thêm/Sửa/Xóa.  <br><br/>3\. Cập nhật dữ liệu vào Form biểu mẫu.  <br><br/>4\. Hệ thống kiểm tra ràng buộc toàn vẹn dữ liệu và lưu DB. |
| **Alternative Flow** | Không có. |
| **Exception Flow** | 4a. Vi phạm ràng buộc dữ liệu (FK Constraint): Xóa phòng đang được xếp TKB hoặc Giảng viên đang có lịch dạy -> Hệ thống chặn lệnh Xóa và báo lỗi “Dữ liệu đang được sử dụng”. |
| **Business Rules** | Quy tắc kiểm tra tính toàn vẹn (Referential Integrity) của Cơ sở dữ liệu chuẩn. |
| **Non-functional Requirements** | Cung cấp trải nghiệm CRUD mượt mà và trực quan. |

## **QT-13 — Đăng ký Học lại & Xếp lớp Môn trượt**

| **Thuộc tính** | **Mô tả chi tiết** |
| --- | --- |
| **Use Case Name** | Đăng ký Học lại & Xếp lớp Môn trượt |
| **Mã QT** | QT-13 |
| **Description** | SV có môn trạng thái Cấm thi (G3) hoặc Học lại (G5) đăng ký học lại toàn bộ môn từ đầu; SV có môn trạng thái Thi lại (G4) đăng ký thi lại bài Final Exam. Hệ thống tính phí theo quy chế và xếp vào lớp chuyên ngành khả dụng (nếu học lại). |
| **Actor(s)** | Sinh viên, Quản nhiệm, Hệ thống |
| **Priority** | Must Have |
| **Trigger** | Kỳ mới mở đăng ký, SV có môn trượt cần thi lại hoặc học lại. |
| **Precondition(s)** | • SV đang ở trạng thái S1 (Đang học) hoặc vừa hết hạn đình chỉ (S5 → S1)  <br><br/>.• Có ít nhất 1 môn trạng thái G3, G4, hoặc G5. |
| **Post-Condition(s)** | • Nếu G4 (Thi lại): Hóa đơn thi lại được sinh, SV chỉ thi lại FE (giữ điểm quá trình).  <br><br/>• Nếu G3/G5 (Học lại): Hóa đơn học lại được sinh, SV được xếp vào lớp mới để học lại toàn bộ. |
| **Basic Flow** | **Luồng A — Thi lại (G4):  <br><br/>**1\. SV xem danh sách môn G4 (Thi lại).  <br><br/>2\. SV đăng ký thi lại bài Final Exam.  <br><br/>3\. Hệ thống sinh Hóa đơn thi lại (Unpaid) với phí thi lại. SV thanhtoán qua QT-11.  <br><br/>4\. Sau thanh toán, SV được xếp vào lịch thi lại FE.  <br><br/>**Luồng B — Học lại (G3/G5):  <br><br/>**\*1. SV xem danh sách môn G3 (Cấm thi) hoặc G5 (Học lại).<br><br>\*2. SV chọn môn đăng ký học lại cho kỳ tới.<br><br>\*3. Hệ thống kiểm tra số học kỳ trôi qua từ thời điểm trượt: — Kỳ liền kề ngay sau: Phí = **50%** đơn giá môn. — Cách ≥ 1 kỳ: Phí = **100%** đơn giá môn.<br><br>\*4. Hệ thống sinh Hóa đơn học lại (Unpaid). SV thanh toán qua Payment Gateway hoặc Ví FAP (QT-11).<br><br>\*5. Sau khi thanh toán thành công, hệ thống tìm lớp chuyên ngành khả dụng (CurrentSize < MaxCapacity) trong kỳ mới và xếp SV vào lớp. |
| **Alternative Flow** | 3a. **SV vừa hết thời hạn đình chỉ (từng ở S5):\*** Hệ thống phát hiện hồ sơ kỷ luật Expired→ Áp dụng phí = **150%** đơn giá môn (phạt kỷ luật).Use Case tiếp tục bước 4. |
| **Exception Flow** | 3b. **SV đang bị Đình chỉ (S5):** Hệ thống phát hiện trạng thái kỷ luật Active → Chặn đăng ký, hiển thị thông báo: “Tài khoản đang trong thời gian đình chỉ học tập 1 học kỳ”. Use Case dừng.<br><br>5a. **Lớp học lại đã hết chỗ:** Hệ thống cảnh báo lớp đầy, đưa SV vào danh sách chờ (Waitlisted) và thông báo Quản nhiệm xếp lớp bổ sung hoặc xếp tay. |
| **Business Rules** | BR-036: Chỉ môn G3/G5 (Học lại) hoặc G4 (Thi lại).<br><br>BR-037: Phí học lại 50%/100% theo kỳ.<br><br>BR-038: Chặn SV đang đình chỉ (S5).<br><br>BR-039: Phí 150% sau đình chỉ. BR-040: Xếp lớp tự động hoặc Waitlist.<br><br>BR-041: Tự động gỡ đình chỉ sau 1 kỳ. |
| **Non-functional Requirements** | Thời gian kiểm tra điều kiện & tính phí ≤ 2 giây. Email thông báo kết quả xếp lớp ≤ 1 phút. |

## **QT-14 — Xem Báo cáo & Thống kê**

<div class="joplin-table-wrapper"><table><thead><tr><th><p><strong>Thuộc tính</strong></p></th><th><p><strong>Mô tả chi tiết</strong></p></th></tr></thead><tbody><tr><td><p><strong>Use Case Name</strong></p></td><td><p>Xem Báo cáo &amp; Thống kê</p><p></p></td></tr><tr><td><p><strong>Mã QT</strong></p></td><td><p>QT-14</p><p></p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Quản nhiệm, Kế toán và Admin xem các báo cáo tổng hợp: tỷ lệ Pass/Fail theo môn/kỳ, thống kê vắng mặt, số SV đình chỉ, doanh thu học phí.</p><p></p></td></tr><tr><td><p><strong>Actor(s)</strong></p></td><td><p>Quản nhiệm, Kế toán, Admin</p><p></p></td></tr><tr><td><p><strong>Priority</strong></p></td><td><p>Should Have</p><p></p></td></tr><tr><td><p><strong>Trigger</strong></p></td><td><p>Người dùng muốn xem thống kê tổng hợp phục vụ quản lý điều hành.</p><p></p></td></tr><tr><td><p><strong>Precondition(s)</strong></p></td><td><p>Tài khoản đã đăng nhập và có quyền xem báo cáo (VT-01, VT-04, VT-05).</p><p></p></td></tr><tr><td><p><strong>Post-Condition(s)</strong></p></td><td><p>Báo cáo được hiển thị trên Dashboard hoặc xuất ra file Excel/PDF.</p><p></p></td></tr><tr><td><p><strong>Basic Flow</strong></p></td><td><ol><li>Người dùng truy cập màn hình Báo cáo (MH-AD-04).</li></ol><p></p><p>2. Chọn loại báo cáo (Học tập / Tài chính / Điểm danh) và bộ lọc (Học kỳ, Lớp, Môn học).</p><p></p><p>3. Hệ thống trựy xuất dữ liệu và hiển thị báo cáo.</p><p></p><p>4. Người dùng có thể xuất Excel/PDF nếu cần.</p><p></p></td></tr><tr><td><p><strong>Alternative Flow</strong></p></td><td><p>Không có.</p><p></p></td></tr><tr><td><p><strong>Exception Flow</strong></p></td><td><p>3a. Không có dữ liệu: Hệ thống hiển thị thông báo “Không có dữ liệu cho bộ lọc đã chọn”.</p><p></p></td></tr><tr><td><p><strong>Business Rules</strong></p></td><td><p>BR-032: Chỉ Kế toán/Admin xem dòng tiền. Quản nhiệm chỉ xem báo cáo học tập.</p><p></p></td></tr><tr><td><p><strong>Non-functional Requirements</strong></p></td><td><p>Thời gian tải báo cáo ≤ 5 giây. Xuất Excel 5.000 dòng ≤ 15 giây.</p><p></p></td></tr></tbody></table></div>

## **QT-15 — Quản lý Profile & Đổi mật khẩu**

<div class="joplin-table-wrapper"><table><thead><tr><th><p><strong>Thuộc tính</strong></p></th><th><p><strong>Mô tả chi tiết</strong></p></th></tr></thead><tbody><tr><td><p><strong>Use Case Name</strong></p></td><td><p>Quản lý Profile &amp; Đổi mật khẩu</p><p></p></td></tr><tr><td><p><strong>Mã QT</strong></p></td><td><p>QT-15</p><p></p></td></tr><tr><td><p><strong>Description</strong></p></td><td><p>Người dùng tự cập nhật thông tin cá nhân (SĐT, ảnh đại diện) và đổi mật khẩu. Admin có thể reset mật khẩu cho người dùng khác.</p><p></p></td></tr><tr><td><p><strong>Actor(s)</strong></p></td><td><p>Tất cả Người dùng, Admin</p><p></p></td></tr><tr><td><p><strong>Priority</strong></p></td><td><p>Should Have</p><p></p></td></tr><tr><td><p><strong>Trigger</strong></p></td><td><p>Người dùng muốn thay đổi thông tin cá nhân hoặc mật khẩu.</p><p></p></td></tr><tr><td><p><strong>Precondition(s)</strong></p></td><td><p>Tài khoản đã đăng nhập.</p><p></p></td></tr><tr><td><p><strong>Post-Condition(s)</strong></p></td><td><p>Thông tin cá nhân / mật khẩu được cập nhật thành công.</p></td></tr><tr><td><p><strong>Basic Flow</strong></p></td><td><ol><li>Người dùng truy cập màn hình Profile (MH-ALL-03).</li></ol><p></p><p>2. Chỉnh sửa thông tin (SĐT, ảnh đại diện) hoặc nhấn “Đổi mật khẩu”.</p><p></p><p>3. Nếu đổi MK: Nhập mật khẩu cũ, mật khẩu mới (2 lần).</p><p></p><p>4. Hệ thống validate và lưu thay đổi.</p><p></p></td></tr><tr><td><p><strong>Alternative Flow</strong></p></td><td><p>2a. Admin reset mật khẩu cho user khác: Nhập UserID → Hệ thống sinh mật khẩu tạm → Gửi Email cho user.<br></p></td></tr><tr><td><p><strong>Exception Flow</strong></p></td><td><p>3a. Mật khẩu cũ sai: Hệ thống báo lỗi, không cho đổi.3b. Mật khẩu mới không đủ độ mạnh (&lt; 8 ký tự, thiếu số/chữ hoa): Hệ thống báo lỗi.</p><p></p></td></tr><tr><td><p><strong>Business Rules</strong></p></td><td><p>Mật khẩu mới phải ≥ 8 ký tự, chứa ít nhất 1 chữ hoa, 1 số, 1 ký tự đặc biệt. Không trùng 3 mật khẩu gần nhất.</p><p></p></td></tr><tr><td><p><strong>Non-functional Requirements</strong></p></td><td><p>NFR-16: Hash mậtL khẩu một chiều.</p><p></p></td></tr></tbody></table></div>

# **CHƯƠNG 8. BẢNG TRẠNG THÁI CÁC THỰC THỂ CHÍNH (ĐẦY ĐỦ)**

## **8.1. Trạng thái Sinh viên (TT-01)**

| Mã  | Trạng thái | Ý nghĩa | Chuyển từ → tới |
| --- | --- | --- | --- |
| S0  | Khởi thủy (Initialized) | SV vừa import, chưa có lớp | → S1 (Khi được gán lớp QT-03) |
| S1  | Đang học (Active) | SV đang theo học chính thức | → S2, S3, S4, S5 |
| S2  | Bảo lưu (Suspended) | SV tạm ngừng học tập (tối đa 2 kỳ theo BR-005b) | → S1 (Tái nhập), → S3 (Hết hạn bảo lưu mà không tái nhập — BR-005b) |
| S3  | Thôi học (Dropped) | SV nghỉ học vĩnh viễn | (Trạng thái cuối) |
| S4  | Tốt nghiệp (Graduated) | SV hoàn thành chương trình (theo BR-044) | (Trạng thái cuối) |
| S5  | Đình chỉ (Disciplinary Suspension) | SV bị đình chỉ do vi phạm quy chế, chặn mọi đăng ký | → S1 (Hết hạn đình chỉ — BR-041), → S3 (Đình chỉ lần 2 — BR-043) |

## **8.2. Trạng thái Tài khoản Người dùng (TT-02)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Active | Đang hoạt động, có thể đăng nhập bình thường | → Locked (Sai MK 5 lần), → Inactive, → Limited |
| Locked | Bị khóa tạm thời (15 phút do sai mật khẩu) | → Active (Sau 15 phút hệ thống tự mở) |
| Limited | Quyền hạn chế (SV Bảo lưu — BR-003): chỉ xem thông tin, nộp đơn tái nhập, thanh toán nợ | → Active (Khi QN mở lại quyền / SV tái nhập) |
| Inactive | Bị khóa vĩnh viễn (SV Thôi học) | → Active (Khi QN mở lại quyền — trường hợp đặc biệt) |

## **8.3. Trạng thái Thời khóa biểu / Slot học (TT-06)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Normal | Lịch học bình thường theo TKB chuẩn | → Cancelled (Khi GV báo nghỉ) |
| Cancelled | Bị hủy do GV báo nghỉ đột xuất | (Trạng thái cuối của Slot này) |
| MakeUp | Slot học bù được tạo ra sau khi báo nghỉ | (Trạng thái cuối của Slot này) |

## **8.4. Trạng thái Phiên điểm danh (TT-07)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Opening | Phiên đang mở, QR động đang chạy | → Closed (Hết giờ/Đóng phiên thủ công) |
| Closed | Phiên đã chốt, không nhận quét QR nữa | (Trạng thái cuối) |

## **8.5. Trạng thái Bản ghi điểm danh (TT-08)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Present | Sinh viên có mặt (đã quét QR hoặc GV sửa tay) | → Absent (Nếu QN/GV sửa lại) |
| Absent | Sinh viên vắng mặt (chưa quét khi phiên đóng) | → Present (Nếu QN/GV sửa tay) |

## **8.6. Trạng thái Môn học của SV / Bảng điểm (TT-09)**

| **Mã** | **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- | --- |
| G0  | Đang học (In Progress) | SV đang theo học môn này | → G1, G3, G4 |
| G1  | Đạt (Passed) | Thỏa mãn (Vắng<20%, FE≥4.0, Tổng≥5.0) | (Kết thúc môn) |
| G3  | Cấm thi (Fail) | Vắng ≥ 20% tổng Slot. SV phải chủ động đăng ký học lại (QT-13) | → G5 (Khi SV đăng ký học lại qua QT-13) |
| G4  | Thi lại (Retake Exam) | FE < 4.0 HOẶC Tổng < 5.0 (Vắng < 20%). Chỉ thi lại bài FE 1 lần (BR-025b), giữ điểm quá trình | → G1 (Nếu thi lại đạt) / G5 (Nếu thi lại vẫn trượt) |
| G5  | Học lại (Re-study) | Cấm thi (từ G3) hoặc thi lại vẫn trượt (từ G4). Phải học lại toàn bộ môn từ đầu. Tối đa 3 lần (BR-025c) | → G0 (Đăng ký học lại QT-13 → vào lớp mới) |

**Ghi chú:** Trạng thái G2 (Reserved) đã được loại bỏ trong v4.0 vì không có use case nào sử dụng. Nếu cần mở rộng trạng thái trong tương lai, sẽ bổ sung kèm BR và QT tương ứng.

## **8.7. Trạng thái Đơn từ (TT-10)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Pending | SV vừa nộp đơn, chờ QN tiếp nhận | → Processing, Approved, Rejected, Cancelled |
| Processing | QN đang xử lý (hoặc Đơn đang chờ thanh toán) | → Approved, Rejected |
| Approved | QN đã duyệt đơn | (Trạng thái cuối) |
| Rejected | QN từ chối đơn | (Trạng thái cuối) |
| Cancelled | SV tự thu hồi đơn | (Trạng thái cuối) |

## **8.8. Trạng thái Hóa đơn (TT-11)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Unpaid | Chưa thanh toán | → Paid, → Overdue (Hệ thống tự động chuyển khi quá DueDate — BR-045), Cancelled |
| Paid | Đã thanh toán thành công (Gateway xác nhận) | (Trạng thái cuối) |
| Overdue | Quá hạn thanh toán. SV bị chặn đăng ký học lại và xem bảng điểm (BR-046) | → Paid (Nếu nộp bù), Cancelled |
| Cancelled | Hóa đơn bị hủy bỏ (Ví dụ: Rút đơn) | (Trạng thái cuối) |

## **8.9. Trạng thái Giao dịch thanh toán (TT-12)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Pending | Đã tạo URL sang Gateway, đang chờ Webhook | → Success, Failed |
| Success | Sinh viên thanh toán thành công | (Trạng thái cuối) |
| Failed | Hủy giao dịch, quá hạn 15p, lỗi số tiền/checksum | (Trạng thái cuối) |

## **8.10. Trạng thái Đăng ký Học lại (TT-15)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Pending | Chờ SV thanh toán hóa đơn học lại | → Paid, Cancelled |
| Paid | Đã thanh toán, chờ xếp lớp | → Assigned, Waitlisted |
| Assigned | Đã được xếp vào lớp học lại | (Trạng thái cuối) |
| Waitlisted | Lớp đầy, chờ mở lớp bổ sung hoặc Quản nhiệm xếp tay | → Assigned |
| Cancelled | SV hủy đăng ký (trước khi thanh toán) | (Trạng thái cuối) |

## **8.11. Trạng thái Hồ sơ Kỷ luật (TT-16)**

| **Trạng thái** | **Ý nghĩa** | **Chuyển từ → tới** |
| --- | --- | --- |
| Active | Đang trong thời gian đình chỉ | → Expired (Hệ thống tự động chuyển khi hết hạn) |
| Expired | Hết hạn đình chỉ, SV được phép đăng ký lại (phí 150%) | (Trạng thái cuối) |

# **CHƯƠNG 9. MA TRẬN PHÂN QUYỀN (RBAC)**

| **Chức năng \\ Vai trò** | **VT-01 (Quản nhiệm)** | **VT-02 (Giảng viên)** | **VT-03 (Sinh viên)** | **VT-04 (Kế toán)** | **VT-05 (Admin)** |
| --- | --- | --- | --- | --- | --- |
| Quản lý GV & Phòng | —   | —   | —   | —   | C/R/U/D |
| Import hồ sơ SV | C/R/U/D | —   | —   | —   | R   |
| Cập nhật trạng thái SV | R/U | —   | —   | —   | R/U |
| Phân lớp chuyên ngành | C/R/U | —   | R   | —   | R   |
| Thiết lập môn học & CTĐT | C/R/U/D | R   | R   | —   | R   |
| Xếp Thời khóa biểu | C/R/U/D | R   | R   | —   | R   |
| Báo nghỉ & Xếp lịch bù | C/R/U | C/R | R   | —   | R   |
| Mở phiên điểm danh | —   | C/R/U | —   | —   | R   |
| Quét QR điểm danh | —   | —   | X   | —   | —   |
| Sửa điểm danh thủ công | U   | U   | —   | —   | R   |
| Nhập điểm quá trình | —   | C/R/U | R   | —   | R   |
| Chốt sổ điểm | R/U | —   | —   | —   | R   |
| Sửa điểm sau chốt sổ | —   | —   | —   | —   | U (Log) |
| Duyệt/Từ chối đơn từ | R/U | —   | R (của mình) | —   | R   |
| Thanh toán trực tuyến | —   | —   | X   | —   | —   |
| Đối soát & Tra soát | —   | —   | —   | R/U | R   |
| Quản lý Hóa đơn | R   | —   | R (của mình) | C/R/U | C/R/U/D |
| Đăng ký học lại | R/U | —   | C/R/U (của mình) | —   | R   |
| Quản lý kỷ luật / Đình chỉ | C/R/U | —   | R (của mình) | —   | C/R/U/D |
| Xem Activity Log | —   | —   | —   | R (tài chính) | R   |
| Xem Báo cáo thống kê | R   | R (của mình) | —   | R   | R   |
| Đổi mật khẩu / Profile | U (của mình) | U (của mình) | U (của mình) | U (của mình) | U (tất cả) |

**Ghi chú: C = Create, R = Read, U = Update, D = Delete (Xóa/Toàn quyền), X = Execute, — = Không có quyền**

# **CHƯƠNG 10. DANH SÁCH MÀN HÌNH UI THEO VỊ TRÍ TÁC NGHIỆP**

## **10.1. Vị trí: Quản nhiệm (Academic Staff)**

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT/PH** |
| --- | --- | --- | --- | --- |
| MH-QN-01 | Dashboard Quản nhiệm | VT-01 | Tổng quan: SV, đơn chờ, lịch dạy | QLSV-01~06 |
| MH-QN-02 | Import hồ sơ Sinh viên | VT-01 | Upload Excel/CSV, validate, tạo tài khoản | QT-01 |
| MH-QN-03 | Danh sách Sinh viên | VT-01 | Tìm kiếm, xem, sửa hồ sơ, cập nhật trạng thái | QT-01, QT-02 |
| MH-QN-04 | Phân lớp chuyên ngành | VT-01 | Phân lớp tự động/thủ công, xem trước, xác nhận | QT-03 |
| MH-QN-05 | Quản lý Môn học | VT-01 | CRUD môn học, thiết lập tiên quyết, import Excel | QT-04 |
| MH-QN-06 | Xếp Thời khóa biểu | VT-01 | Xếp tự động/thủ công, xem Draft, đồng bộ | QT-05 |
| MH-QN-07 | Duyệt lịch nghỉ/bù | VT-01 | Xem yêu cầu, Duyệt/Từ chối | QT-06 |
| MH-QN-08 | Duyệt đơn từ Sinh viên | VT-01 | Danh sách đơn chờ, xem chi tiết, Duyệt/Từ chối/Yêu cầu bổ sung | QT-10 |
| MH-QN-09 | Chốt sổ điểm | VT-01 | Xem bảng điểm lớp, chốt sổ | QT-09 |
| MH-QN-10 | Quản lý Đăng ký Học lại | VT-01 | Xem danh sách SV đăng ký học lại, xếp lớp thủ công cho SV Waitlisted | QT-13 |
| MH-QN-11 | Quản lý Kỷ luật | VT-01 | Tạo/Xem hồ sơ đình chỉ, theo dõi thời hạn, chuyển trạng thái S5 | QT-13 |

## **10.2. Vị trí: Giảng viên (Lecturer)**

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT/PH** |
| --- | --- | --- | --- | --- |
| MH-GV-01 | Dashboard Giảng viên | VT-02 | Lịch dạy trong ngày/tuần, thống kê nhanh | QLSV-02~04 |
| MH-GV-02 | TKB cá nhân Giảng viên | VT-02 | Xem lịch, chọn Slot báo nghỉ | QT-05, QT-06 |
| MH-GV-03 | Mở phiên Điểm danh (QR) | VT-02 | Mở phiên, hiển thị QR full-screen, đóng phiên | QT-07 |
| MH-GV-04 | Danh sách điểm danh lớp | VT-02 | Xem Present/Absent, sửa thủ công | QT-07 |
| MH-GV-05 | Nhập/Import điểm | VT-02 | Grid nhập điểm, import Excel, lưu | QT-08 |
| MH-GV-06 | Form báo nghỉ & đề xuất bù | VT-02 | Chọn Slot nghỉ, nhập lý do, chọn Slot bù | QT-06 |

## **10.3. Vị trí: Sinh viên (Student)**

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT/PH** |
| --- | --- | --- | --- | --- |
| MH-SV-01 | Dashboard Sinh viên | VT-03 | Tổng quan: TKB hôm nay, thông báo, đơn chờ | QLSV-01~06 |
| MH-SV-02 | TKB cá nhân Sinh viên | VT-03 | Xem lịch học theo tuần/tháng | QT-05 |
| MH-SV-03 | Quét QR Điểm danh (PWA Camera) | VT-03 | Mở camera trình duyệt mobile (WebRTC), quét QR, xác thực, kết quả | QT-07 |
| MH-SV-04 | Bảng điểm cá nhân | VT-03 | Xem điểm TP, FE, tổng, trạng thái Pass/Fail | QT-08, QT-09 |
| MH-SV-05 | Nộp đơn từ trực tuyến | VT-03 | Chọn loại đơn, điền form, đính kèm, nộp | QT-10 |
| MH-SV-06 | Lịch sử & Timeline đơn từ | VT-03 | Danh sách đơn, Timeline xử lý, hủy đơn | QT-10 |
| MH-SV-07 | Hóa đơn & Thanh toán | VT-03 | Xem hóa đơn, chọn gateway, thanh toán | QT-11 |
| MH-SV-08 | Đăng ký Học lại | VT-03 | Xem môn trượt (G3/G4/G5), chọn đăng ký, xem phí, thanh toán học lại | QT-13 |
| MH-SV-09 | Đổi mật khẩu & Profile | VT-03 | Đổi mật khẩu, cập nhật SĐT, ảnh đại diện | QT-15 |

## **10.4. Vị trí: Kế toán (Accountant)**

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT/PH** |
| --- | --- | --- | --- | --- |
| MH-KT-01 | Dashboard Kế toán | VT-04 | Tổng quan doanh thu, giao dịch mới | QLSV-06 |
| MH-KT-02 | Đối soát giao dịch | VT-04 | Lọc theo ngày/trạng thái, xuất Excel | QT-11 |
| MH-KT-03 | Tra soát giao dịch lỗi | VT-04 | Nhập Order ID, Query API, gạch nợ thủ công | QT-11 |

## **10.5. Màn hình chung (All) & Admin**

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** |
| --- | --- | --- | --- |
| MH-ALL-01 | Đăng nhập & Quên MK | All | Login (Username/Password + SSO Google/Microsoft), gửi OTP lấy lại mật khẩu |
| MH-ALL-02 | Notification Center | All | Chuông thông báo In-app, đánh dấu đã đọc, xem chi tiết (TT-18) |
| MH-ALL-03 | Đổi mật khẩu & Profile | All | Đổi mật khẩu, cập nhật thông tin cá nhân (SĐT, ảnh) |
| MH-AD-01 | Quản lý Giảng viên | VT-05 | CRUD thông tin Giảng viên (TT-17) |
| MH-AD-02 | Quản lý Phòng học | VT-05 | CRUD thông tin Phòng học |
| MH-AD-03 | Xem Activity Log | VT-05 | Tra cứu, lọc nhật ký thao tác hệ thống (TT-14) |
| MH-AD-04 | Báo cáo & Thống kê | VT-01, VT-05 | Xem tỷ lệ Pass/Fail, thống kê vắng, doanh thu kỳ |

# **CHƯƠNG 11. TIÊU CHÍ NGHIỆM THU NGHIỆP VỤ**

| **Mã** | **Tiêu chí nghiệm thu** | **QT liên quan** | **Phương pháp kiểm chứng** |
| --- | --- | --- | --- |
| QT-00.NT01 | Đăng nhập thành công với tài khoản hợp lệ, chuyển đúng Dashboard theo Role | QT-00 | Test thủ công + Automated UI Test |
| QT-00.NT02 | Khóa tài khoản sau 5 lần sai mật khẩu, tự mở sau 15 phút | QT-00 | Test thủ công |
| QT-00.NT03 | Đăng nhập SSO Google/Microsoft chỉ chấp nhận email @fpt.edu.vn | QT-00 | Test thủ công |
| QT-01.NT01 | Import file 200 bản ghi hợp lệ: tạo đủ hồ sơ + tài khoản trong ≤ 10 giây | QT-01 | Automated Test + đo thời gian |
| QT-01.NT02 | Import file có dòng lỗi (trùng CCCD): bôi đỏ dòng lỗi, không lưu dòng lỗi, vẫn lưu dòng hợp lệ | QT-01 | Test thủ công |
| QT-03.NT01 | Phân lớp tự động 200 SV vào 8 lớp: sĩ số đều nhau, không vượt MaxCapacity | QT-03 | Automated Test |
| QT-05.NT01 | Xếp TKB tự động cho 200 SV: hoàn tất ≤ 30 giây, 0% Conflict GV/Phòng | QT-05 | Automated Test + đo thời gian |
| QT-07.NT01 | QR Code refresh mỗi 10s, SV quét thành công → hiển thị Present real-time | QT-07 | Test thủ công trên mobile browser |
| QT-07.NT02 | SV quét QR bằng app bên ngoài (Zalo/Camera) → không giải mã được | QT-07 | Test thủ công |
| QT-09.NT01 | Tính điểm 200 SV: kết quả đúng 100% theo công thức tỷ trọng (TT-20), hoàn tất ≤ 30 giây | QT-09 | Automated Test + so khớp Excel |
| QT-09.NT02 | SV vắng ≥ 20% → tự động chốt G3 (Cấm thi). SV FE < 4.0 → chốt G4 (Thi lại) | QT-09 | Automated Test |
| QT-11.NT01 | Thanh toán VNPay/MoMo thành công → hóa đơn chuyển Paid, giao dịch Success | QT-11 | Test thủ công trên môi trường Sandbox |
| QT-11.NT02 | Webhook bị mất → Kế toán Query Transaction thủ công → gạch nợ bổ sung | QT-11 | Test thủ công |
| QT-13.NT01 | SV đăng ký học lại môn G3: phí đúng 50%/100% theo BR-037, hóa đơn sinh đúng | QT-13 | Automated Test |
| QT-13.NT02 | SV đang đình chỉ (S5) → chặn đăng ký, hiển thị thông báo đúng | QT-13 | Test thủ công |

# **CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR)**

| **Nhóm** | **Mã NFR** | **Yêu cầu** | **Ngưỡng đo được** |
| --- | --- | --- | --- |
| **Hiệu năng** | NFR-01 | Thời gian đăng nhập & cấp Token | ≤ 1 giây |
| NFR-04 | Thuật toán Auto-scheduling (200 SV) | ≤ 30 giây |     |
| NFR-07 | Tính điểm toàn bộ 200 SV | ≤ 30 giây |     |
| **Bảo mật** | NFR-15 | Giao tiếp Payment Gateway | Mã hóa SSL/TLS |
| NFR-16 | Mật khẩu người dùng | Hash một chiều (Argon2/Bcrypt) |     |
| NFR-17 | Chống Spam Login | Khóa 15p sau 5 lần sai |     |
| **Vận hành** | NFR-18 | Đồng thời (Concurrent Users) | Hỗ trợ 200 SV điểm danh cùng lúc |
| NFR-19 | Logging (Audit Trail) | Ghi Log 100% thao tác sửa điểm/thanh toán |     |
| NFR-20 | Backup Data | Daily backup, lưu trữ 30 ngày |     |
| NFR-21 | SLA Uptime | 99.5% thời gian hoạt động |     |

# **CHƯƠNG 13. YÊU CẦU TÍCH HỢP (INTEGRATION)**

Hệ thống Quản lý Sinh viên không hoạt động độc lập mà cần giao tiếp với các dịch vụ bên ngoài để hoàn thiện quy trình nghiệp vụ:

## **13.1. Tích hợp Cổng thanh toán (Payment Gateway)**

Hỗ trợ luồng nghiệp vụ thanh toán học phí, lệ phí đơn từ.

- **Đối tác:** VNPay hoặc MoMo API.
- **Giao thức:** REST API (Tạo Payment URL) và Webhook/IPN (Nhận kết quả giao dịch).
- **Yêu cầu bảo mật:**
    - Dữ liệu gửi đi và nhận về phải được ký chữ ký điện tử (Checksum / HMAC SHA512) bằng Secret Key riêng tư.
    - Phải kiểm tra IP Whitelist từ phía VNPay/MoMo gửi tới Webhook để tránh giả mạo kết quả gạch nợ.
- **Cơ chế dự phòng:** Có Background Job chạy ngầm để Query Transaction API những hóa đơn “Pending” quá 15 phút (Đề phòng rớt mạng mất Webhook).

## **13.2. Tích hợp Dịch vụ Gửi Email (Mailing Service)**

Gửi thông báo duyệt đơn, hóa đơn điện tử, và Cảnh báo vắng học tự động (khi sát mốc 20%).

- **Dịch vụ:** SendGrid API, Amazon SES, hoặc máy chủ SMTP nội bộ của nhà trường.
- **Yêu cầu kỹ thuật:** Đẩy tác vụ gửi Email vào Hàng đợi (Background Worker / Message Queue) để xử lý bất đồng bộ, không làm treo giao diện người dùng. Có hỗ trợ Template HTML động.

## **13.3. Tích hợp Xác thực (Single Sign-On)**

- **Công nghệ:** Google OAuth 2.0 hoặc Microsoft Entra ID (SSO).
- **Ràng buộc:** Chỉ cấp quyền truy cập cho những Email thuộc tên miền của trường (Ví dụ: \*@fpt.edu.vn). Các Email cá nhân (@gmail.com) sẽ bị từ chối.

# **CHƯƠNG 14. TUÂN THỦ PHÁP LÝ & QUY CHẾ**

- **Quy chế Đào tạo:** Logic điểm liệt (Final Exam < 4.0), vắng quá 20%, công thức tính trung bình tổng phải tuân thủ nghiêm ngặt Quy chế Đào tạo FPT hiện hành.
- **Bảo mật Dữ liệu (Data Privacy):** Mật khẩu bắt buộc mã hóa một chiều (Argon2/Bcrypt). Không lưu trữ thông tin thẻ ngân hàng của Sinh viên trên hệ thống (chỉ lưu mã tham chiếu giao dịch).
- **Lưu vết (Audit Trail):** Toàn bộ thao tác can thiệp điểm số sau khi chốt, hoặc gạch nợ thủ công phải lưu vết vĩnh viễn (Ai làm, Khi nào, IP nào, Giá trị cũ/mới) để truy cứu trách nhiệm pháp lý.

# **CHƯƠNG 15. DANH MỤC DÙNG CHUNG**

Các danh mục Master Data ít biến động, được sử dụng làm nguồn dữ liệu (Lookup Data) cho toàn hệ thống:

- **Danh mục Slot học:** Slot 1 (07:30 - 09:50), Slot 2 (10:00 - 12:20),…
- **Danh mục Tỉnh/Thành phố:** Hỗ trợ nhập liệu địa chỉ thường trú chuẩn xác.
- **Danh mục Ngành học:** Cấu hình sẵn các mã ngành (SE, IA, GD…)
- **Danh mục Trạng thái Core:** Các mảng Status enum chuẩn (Đạt, Trượt, Chờ xử lý…).

# **CHƯƠNG 16. MA TRẬN TRUY VẾT & LỘ TRÌNH BRD**

## **16.1. Ma trận truy vết Yêu cầu**

| **Use Case** | **Quy trình** | **Quy tắc (BR)** | **NFR** | **Màn hình** |
| --- | --- | --- | --- | --- |
| UC-QLSV-00.1 | QT-00 | —   | NFR-01, 16, 17 | MH-ALL-01, MH-ALL-03 |
| UC-QLSV-01.1 | QT-01 | BR-001, 002 | NFR-01 | MH-QN-02, 03 |
| UC-QLSV-01.2 | QT-02 | BR-003, 005b, 044 | —   | MH-QN-03 |
| UC-QLSV-01.3 | QT-03 | BR-004, 005 | —   | MH-QN-04 |
| UC-QLSV-02.1 | QT-04 | BR-006, 007 | —   | MH-QN-05 |
| UC-QLSV-02.2 | QT-05 | BR-008, 009, 010 | NFR-04 | MH-QN-06, MH-GV-02, MH-SV-02 |
| UC-QLSV-02.3 | QT-06 | BR-011, 012 | —   | MH-QN-07, MH-GV-06 |
| UC-QLSV-03.1 | QT-07 | BR-013, 014, 015, 016, 017, 018 | NFR-18, NFR-19 | MH-GV-03, 04, MH-SV-03 |
| UC-QLSV-04.1 | QT-08 | BR-019, 020 | —   | MH-GV-05, MH-SV-04 |
| UC-QLSV-04.2 | QT-09 | BR-021, 022, 022b, 023, 024, 025, 025b, 025c | NFR-07, NFR-19 | MH-QN-09, MH-SV-04 |
| UC-QLSV-05.1 | QT-10 | BR-026, 027, 028, 029 | —   | MH-QN-08, MH-SV-05, 06 |
| UC-QLSV-06.1 | QT-11 | BR-030, 031, 032, 033, 034, 035, 045, 046 | NFR-15, NFR-19 | MH-SV-07, MH-KT-02, 03 |
| UC-QLSV-07.1 | QT-12 | —   | NFR-19 | MH-AD-01, 02 |
| UC-QLSV-01.4 | QT-13 | BR-036, 037, 038, 039, 040, 041, 042, 043 | NFR-01, NFR-19 | MH-SV-08, MH-QN-10, MH-QN-11 |
| UC-QLSV-08.1 | QT-14 | BR-032 | —   | MH-AD-04 |
| UC-QLSV-00.2 | QT-15 | —   | NFR-16 | MH-ALL-03 |

**Trạng thái tài liệu:** Chờ phê duyệt — Phiên bản 4.0

**Ngày cập nhật:** 21/09/2026

**Người cập nhật: Hiếu, Khánh, AI Assistant**

_Hết tài liệu._