**TÀI LIỆU YÊU CẦU NGHIỆP VỤ**

**BUSINESS REQUIREMENTS DOCUMENT (BRD)**

**HỆ THỐNG THÔNG TIN BỆNH VIỆN**

**HOSPITAL INFORMATION SYSTEM (HIS)**

**TÀI LIỆU NỀN TẢNG (MASTER BRD)**

_Bệnh viện đa khoa quy mô 1.500 giường – 1.500÷3.000 lượt khám/ngày_

| **Thuộc tính** | **Nội dung** |
| --- | --- |
| Tên dự án | Xây dựng Hệ thống Thông tin Bệnh viện (HIS) |
| Loại tài liệu | Business Requirements Document – Tài liệu nền tảng |
| Phiên bản | 2.0 |
| Trạng thái | Dự thảo trình duyệt |
| Ngày phát hành | 17/07/2026 |
| Đơn vị xây dựng | ONENET |
| Mức độ mật | Nội bộ – Sử dụng cho mục đích dự án |

# KIỂM SOÁT TÀI LIỆU

## Lịch sử phiên bản

| **Phiên bản** | **Ngày** | **Người thực hiện** | **Nội dung thay đổi** |
| --- | --- | --- | --- |
| 1.0 | 08/06/2026 | ONENET – BA Team | Khởi tạo BRD: tổng quan, kiến trúc nghiệp vụ, danh mục nghiệp vụ, FRS sơ bộ. |
| 1.1 | 12/06/2026 | ONENET – BA Team | Bổ sung kiến trúc dữ liệu, giải pháp, bảo mật, workflow. |
| 2.0 | 17/07/2026 | ONENET – BA Team | Tái cấu trúc thành Tài liệu nền tảng: chuẩn hóa mã định danh, đặc tả 16 quy trình đầu–cuối theo template, bảng trạng thái, ma trận RBAC, danh sách màn hình theo vị trí tác nghiệp, tiêu chí nghiệm thu nghiệp vụ, ma trận truy vết. |

## Phê duyệt tài liệu

| **Vai trò** | **Họ tên / Đơn vị** | **Trách nhiệm** | **Ngày / Ký** |
| --- | --- | --- | --- |
| Chủ đầu tư / Chủ nhiệm dự án | Ban Giám đốc bệnh viện | Phê duyệt phạm vi & mục tiêu nghiệp vụ |     |
| Trưởng phòng KHTH | Phòng Kế hoạch tổng hợp | Xác nhận quy trình chuyên môn |     |
| Trưởng phòng CNTT | Phòng Công nghệ thông tin | Xác nhận khả thi kỹ thuật & tích hợp |     |
| Giám đốc dự án (NCC) | ONENET | Chịu trách nhiệm nội dung tài liệu |     |

_Phạm vi tài liệu: Tài liệu nền tảng này là khung chuẩn dùng chung. Mỗi phân hệ (mã PH-xx) sẽ có một tài liệu BRD chi tiết riêng, kế thừa nguyên tắc, quy ước mã định danh, tác nhân, bảng trạng thái và template quy trình được định nghĩa tại đây._

[KIỂM SOÁT TÀI LIỆU 2](#_Toc235187006)

[Lịch sử phiên bản 2](#_Toc235187007)

[Phê duyệt tài liệu 2](#_Toc235187008)

[CHƯƠNG 1. GIỚI THIỆU TÀI LIỆU 5](#_Toc235187009)

[1.1. Mục đích tài liệu 5](#_Toc235187010)

[1.2. Phạm vi tài liệu 5](#_Toc235187011)

[1.3. Đối tượng sử dụng tài liệu 5](#_Toc235187012)

[1.4. Tài liệu tham chiếu 5](#_Toc235187013)

[1.5. Thuật ngữ và từ viết tắt 6](#_Toc235187014)

[1.6. Quy ước mã định danh (ID conventions) 6](#_Toc235187015)

[CHƯƠNG 2. BỐI CẢNH, MỤC TIÊU VÀ QUY MÔ 6](#_Toc235187016)

[2.1. Bối cảnh dự án 6](#_Toc235187017)

[2.2. Mục tiêu dự án 7](#_Toc235187018)

[2.3. Quy mô triển khai 7](#_Toc235187019)

[2.4. Các bên liên quan (Stakeholders) 7](#_Toc235187020)

[2.5. Giả định và ràng buộc 7](#_Toc235187021)

[2.6. Tiêu chí thành công của dự án 7](#_Toc235187022)

[CHƯƠNG 3. KIẾN TRÚC NGHIỆP VỤ TỔNG THỂ 8](#_Toc235187023)

[3.1. Nguyên tắc thiết kế nghiệp vụ 8](#_Toc235187024)

[3.2. Kiến trúc phân lớp nghiệp vụ 8](#_Toc235187025)

[3.3. Bản đồ năng lực nghiệp vụ (Capability Map) 8](#_Toc235187026)

[3.4. Mô hình vòng đời người bệnh 8](#_Toc235187027)

[CHƯƠNG 4. DANH MỤC PHÂN HỆ VÀ MÃ ĐỊNH DANH 9](#_Toc235187028)

[CHƯƠNG 5. NGUYÊN TẮC VÀ QUY TẮC NGHIỆP VỤ BẮT BUỘC 9](#_Toc235187029)

[CHƯƠNG 6. TÁC NHÂN, VAI TRÒ VÀ THỰC THỂ NGHIỆP VỤ 10](#_Toc235187030)

[6.1. Từ điển tác nhân / vai trò 10](#_Toc235187031)

[6.2. Danh mục thực thể nghiệp vụ chính 11](#_Toc235187032)

[CHƯƠNG 7. QUY TRÌNH NGHIỆP VỤ ĐẦU–CUỐI 12](#_Toc235187033)

[7.1. Sơ đồ quy trình tổng thể 12](#_Toc235187034)

[7.2. QT-01 — Đăng ký & Tiếp nhận người bệnh 13](#_Toc235187035)

[7.3. QT-02 — Tiếp nhận & xử trí Cấp cứu 13](#_Toc235187036)

[7.4. QT-03 — Khám bệnh ngoại trú 14](#_Toc235187037)

[7.5. QT-04 — Chỉ định & thực hiện cận lâm sàng 15](#_Toc235187038)

[7.6. QT-05 — Kê đơn & cấp phát thuốc/VTYT ngoại trú 15](#_Toc235187039)

[7.7. QT-06 — Chỉ định nhập viện & tiếp nhận nhập khoa 16](#_Toc235187040)

[7.8. QT-07 — Điều trị nội trú & chăm sóc 17](#_Toc235187041)

[7.9. QT-08 — Phẫu thuật – thủ thuật 18](#_Toc235187042)

[7.10. QT-09 — Chuyển khoa / chuyển viện 18](#_Toc235187043)

[7.11. QT-10 — Ra viện & tổng kết bệnh án 19](#_Toc235187044)

[7.12. QT-11 — Viện phí & thanh toán 20](#_Toc235187045)

[7.13. QT-12 — Quyết toán BHYT (XML) 20](#_Toc235187046)

[7.14. QT-13 — Bệnh án điện tử & ký số 21](#_Toc235187047)

[7.15. QT-14 — Kho Dược/VTYT/Hóa chất & cấp phát 21](#_Toc235187048)

[7.16. QT-15 — Ngân hàng máu 22](#_Toc235187049)

[7.17. QT-16 — Nhà thuốc bán lẻ 23](#_Toc235187050)

[CHƯƠNG 8. BẢNG TRẠNG THÁI CÁC THỰC THỂ CHÍNH 24](#_Toc235187051)

[8.1. TT-02 — Lượt tiếp nhận / khám 24](#_Toc235187052)

[8.2. TT-03 — Chỉ định cận lâm sàng / DVKT 24](#_Toc235187053)

[8.3. TT-05 — Đơn thuốc / Y lệnh thuốc 24](#_Toc235187054)

[8.4. TT-06 — Bệnh án nội trú 24](#_Toc235187055)

[8.5. TT-07 — Giường bệnh 25](#_Toc235187056)

[8.6. TT-09 — Phiếu thu / Hóa đơn 25](#_Toc235187057)

[8.7. TT-10 — Hồ sơ quyết toán BHYT 25](#_Toc235187058)

[8.8. TT-08 — Phiếu phẫu thuật – thủ thuật 25](#_Toc235187059)

[8.9. TT-11 — Tài liệu EMR (ký số) 25](#_Toc235187060)

[8.10. TT-13 — Đơn vị máu (Ngân hàng máu) 26](#_Toc235187061)

[CHƯƠNG 9. MA TRẬN PHÂN QUYỀN THEO VAI TRÒ (RBAC) 27](#_Toc235187062)

[CHƯƠNG 10. DANH SÁCH MÀN HÌNH UI THEO VỊ TRÍ TÁC NGHIỆP 28](#_Toc235187063)

[10.1. Quầy tiếp đón & Cổng/Kiosk 28](#_Toc235187064)

[10.2. Phòng khám & Cấp cứu 28](#_Toc235187065)

[10.3. Điều dưỡng & Nội trú 28](#_Toc235187066)

[10.4. Cận lâm sàng & Phòng mổ 28](#_Toc235187067)

[10.5. Dược, Kho, Nhà thuốc, Ngân hàng máu, Dinh dưỡng 29](#_Toc235187068)

[10.6. Viện phí, BHYT, Điều hành, Quản trị 29](#_Toc235187069)

[CHƯƠNG 11. TIÊU CHÍ NGHIỆM THU NGHIỆP VỤ 30](#_Toc235187070)

[11.1. Tiêu chí nghiệm thu tổng thể 30](#_Toc235187071)

[11.2. Điều kiện hoàn thành (Definition of Done) & UAT 30](#_Toc235187072)

[11.3. Ma trận truy vết quy trình – tiêu chí nghiệm thu 30](#_Toc235187073)

[CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR) 32](#_Toc235187074)

[CHƯƠNG 13. YÊU CẦU TÍCH HỢP 32](#_Toc235187075)

[CHƯƠNG 14. TUÂN THỦ PHÁP LÝ & CHUẨN 32](#_Toc235187076)

[CHƯƠNG 15. DANH MỤC DÙNG CHUNG 32](#_Toc235187077)

[CHƯƠNG 16. MA TRẬN TRUY VẾT & LỘ TRÌNH BRD THEO PHÂN HỆ 33](#_Toc235187078)

[16.1. Ma trận truy vết yêu cầu 33](#_Toc235187079)

[16.2. Lộ trình phân rã BRD chi tiết theo phân hệ 33](#_Toc235187080)

[16.3. Cấu trúc chuẩn của BRD chi tiết theo phân hệ 33](#_Toc235187081)

[16.4. Kết luận 34](#_Toc235187082)

# CHƯƠNG 1. GIỚI THIỆU TÀI LIỆU

## 1.1. Mục đích tài liệu

Tài liệu Yêu cầu nghiệp vụ (BRD) mô tả toàn diện nhu cầu nghiệp vụ, quy trình, quy tắc, dữ liệu và tiêu chí nghiệm thu cho Hệ thống Thông tin Bệnh viện (HIS). Tài liệu được biên soạn theo định hướng AI-Ready, đủ chi tiết để suy ra các tài liệu cấp dưới:

- FRD/SRS – Đặc tả yêu cầu chức năng và phi chức năng chi tiết theo từng phân hệ.
- Thiết kế UI/UX – Danh sách màn hình, luồng thao tác theo vị trí tác nghiệp.
- Thiết kế API & tích hợp – Hợp đồng dịch vụ, sự kiện, chuẩn HL7/FHIR/DICOM.
- Kịch bản kiểm thử (test case) – Bắt nguồn từ luồng chính, luồng ngoại lệ và tiêu chí nghiệm thu.
- Kế hoạch triển khai & nghiệm thu (UAT) – Dựa trên tiêu chí nghiệm thu nghiệp vụ.

## 1.2. Phạm vi tài liệu

**Trong phạm vi (In-scope)**

- Toàn bộ quy trình khám chữa bệnh từ tiếp nhận/cấp cứu đến ra viện và quyết toán.
- Các phân hệ lâm sàng, cận lâm sàng, dược – vật tư – kho, ngân hàng máu, nhà thuốc, viện phí – BHYT, bệnh án điện tử, điều hành và tích hợp.
- Yêu cầu nghiệp vụ, quy tắc nghiệp vụ, bảng trạng thái, ma trận phân quyền, danh sách màn hình, tiêu chí nghiệm thu ở mức nền tảng dùng chung.

**Ngoài phạm vi (Out-of-scope) của tài liệu nền tảng**

- Đặc tả chi tiết cấp trường dữ liệu, quy tắc validate từng ô nhập của mỗi màn hình (thuộc BRD chi tiết theo phân hệ).
- Thiết kế cơ sở dữ liệu vật lý, sơ đồ lớp, mã nguồn.
- Quy trình quản trị nội bộ không liên quan trực tiếp KCB (nhân sự, tài sản, kế toán tổng hợp) – chỉ nêu điểm tích hợp.

## 1.3. Đối tượng sử dụng tài liệu

| **Đối tượng** | **Mục đích sử dụng** |
| --- | --- |
| Ban lãnh đạo, Phòng KHTH | Xác nhận phạm vi, mục tiêu và tiêu chí nghiệm thu nghiệp vụ. |
| Business Analyst | Cơ sở xây dựng BRD chi tiết theo phân hệ, FRD/SRS. |
| Kiến trúc sư giải pháp / Dev | Cơ sở thiết kế kiến trúc, API, dữ liệu, phân quyền. |
| QA/QC & UAT | Cơ sở xây dựng test case và kịch bản nghiệm thu. |
| Người dùng nghiệp vụ (bác sĩ, điều dưỡng, dược, thu ngân…) | Rà soát tính đúng đắn của quy trình và thao tác. |

## 1.4. Tài liệu tham chiếu

| **Mã** | **Văn bản / Tiêu chuẩn tham chiếu** | **Áp dụng** |
| --- | --- | --- |
| TL-01 | Luật Khám bệnh, chữa bệnh số 15/2023/QH15 | Quy trình chuyên môn, quyền người bệnh |
| TL-02 | Thông tư 32/2023/TT-BYT hướng dẫn Luật KBCB | Hồ sơ, quy trình KCB |
| TL-03 | Thông tư 46/2018/TT-BYT về bệnh án điện tử | EMR, lưu trữ, ký số |
| TL-04 | Nghị định 130/2018/NĐ-CP về chữ ký số | Ký số bệnh án, hóa đơn |
| TL-05 | Quy định danh mục dùng chung của BHXH VN & cổng giám định BHYT | Danh mục, quyết toán XML |
| TL-06 | Nghị định 123/2020/NĐ-CP & TT78 về hóa đơn điện tử | Hóa đơn điện tử viện phí, nhà thuốc |
| TL-07 | Các tiêu chuẩn HL7 v2.x, FHIR R4, DICOM | Tích hợp LIS/RIS/PACS |
| TL-08 | Nghị định 13/2023/NĐ-CP về bảo vệ dữ liệu cá nhân | Bảo mật dữ liệu y tế |

_Lưu ý pháp lý: Danh mục tham chiếu mang tính định hướng; khi triển khai phải rà soát phiên bản văn bản còn hiệu lực tại thời điểm nghiệm thu._

## 1.5. Thuật ngữ và từ viết tắt

| **Viết tắt** | **Diễn giải** |
| --- | --- |
| HIS | Hospital Information System – Hệ thống thông tin bệnh viện |
| EMR | Electronic Medical Record – Bệnh án điện tử |
| CPOE | Computerized Physician Order Entry – Ra y lệnh điện tử |
| eMAR | Electronic Medication Administration Record – Thực hiện thuốc điện tử |
| LIS / RIS / PACS | Hệ thống xét nghiệm / chẩn đoán hình ảnh / lưu trữ – truyền tải hình ảnh |
| CLS | Cận lâm sàng (xét nghiệm, CĐHA, thăm dò chức năng, nội soi, GPB) |
| PTTT | Phẫu thuật – thủ thuật |
| VTYT / HC | Vật tư y tế / Hóa chất |
| BHYT / BHXH | Bảo hiểm y tế / Bảo hiểm xã hội |
| HĐĐT | Hóa đơn điện tử |
| DVKT | Dịch vụ kỹ thuật |
| ICD-10 | Phân loại bệnh tật quốc tế phiên bản 10 |
| STT | Số thứ tự (hàng đợi) |
| RBAC / ABAC | Phân quyền theo vai trò / theo thuộc tính |
| UAT | User Acceptance Test – Kiểm thử chấp nhận người dùng |

## 1.6. Quy ước mã định danh (ID conventions)

Mọi đối tượng trong tài liệu đều có mã định danh duy nhất, phục vụ truy vết xuyên suốt từ nghiệp vụ đến kiểm thử. Quy ước như sau:

| **Loại đối tượng** | **Cấu trúc mã** | **Ví dụ** | **Diễn giải** |
| --- | --- | --- | --- |
| Phân hệ | PH-&lt;số 2 chữ số&gt; | PH-03 | Khám bệnh ngoại trú |
| Yêu cầu nghiệp vụ | YCNV-&lt;mã PH&gt;-&lt;số 3 chữ số&gt; | YCNV-PH03-010 | Yêu cầu chức năng khám ngoại trú thứ 10 |
| Quy tắc nghiệp vụ | BR-&lt;số 3 chữ số&gt; | BR-004 | Không nhập liệu lặp lại |
| Quy trình nghiệp vụ | QT-&lt;số 2 chữ số&gt; | QT-04 | Chỉ định & thực hiện CLS |
| Tiêu chí nghiệm thu QT | &lt;mã QT&gt;.NT&lt;số 2 chữ số&gt; | QT-04.NT02 | Tiêu chí nghiệm thu thứ 2 của QT-04 |
| Vai trò / tác nhân | VT-&lt;số 2 chữ số&gt; | VT-04 | Bác sĩ khám |
| Thực thể nghiệp vụ | TT-&lt;số 2 chữ số&gt; | TT-02 | Lượt khám / lượt tiếp nhận |
| Trạng thái | &lt;mã TT&gt;-S&lt;số&gt; | TT02-S03 | Trạng thái 'Đang khám' |
| Màn hình UI | MH-&lt;khu vực&gt;-&lt;số 2 chữ số&gt; | MH-PK-02 | Màn hình khám bệnh (khu Phòng khám) |
| Điểm tích hợp | TH-&lt;số 2 chữ số&gt; | TH-01 | Tích hợp LIS |
| Yêu cầu phi chức năng | NFR-&lt;số 2 chữ số&gt; | NFR-03 | Hiệu năng |

_Nguyên tắc đánh mã: Quy ước mã là bất biến giữa tài liệu nền tảng và các BRD chi tiết. Khi phân rã một phân hệ, mã YCNV-&lt;PH&gt;-xxx được kế thừa và mở rộng, không đánh lại số._

# CHƯƠNG 2. BỐI CẢNH, MỤC TIÊU VÀ QUY MÔ

## 2.1. Bối cảnh dự án

Trong bối cảnh chuyển đổi số ngành Y tế và lộ trình triển khai bệnh án điện tử của Bộ Y tế, bệnh viện cần một hệ thống HIS thế hệ mới nhằm số hóa xuyên suốt quy trình khám chữa bệnh, thay thế hồ sơ giấy, chuẩn hóa chuyên môn và nâng cao năng lực quản trị – điều hành dựa trên dữ liệu.

## 2.2. Mục tiêu dự án

| **Nhóm mục tiêu** | **Nội dung** |
| --- | --- |
| Nghiệp vụ | Tin học hóa 100% quy trình KCB; quản lý xuyên suốt vòng đời người bệnh; chuẩn hóa chuyên môn; giảm thời gian chờ; giảm sai sót; tăng phối hợp liên khoa/liên viện. |
| Quản trị | Điều hành thời gian thực; theo dõi KPI; quản lý doanh thu – chi phí – nguồn lực; hỗ trợ ra quyết định dựa trên dữ liệu. |
| Công nghệ | Nền tảng web; kiến trúc mở, microservices; tuân thủ HL7/FHIR/DICOM; sẵn sàng mở rộng; vận hành 24/7; bảo mật & an toàn dữ liệu. |

## 2.3. Quy mô triển khai

| **Chỉ tiêu** | **Quy mô mục tiêu** |
| --- | --- |
| Số giường bệnh | ≈ 1.500 |
| Lượt khám ngoại trú/ngày | 1.500 – 3.000 |
| Người bệnh nội trú/ngày | ≈ 1.200 – 1.500 |
| Tổng người dùng hệ thống | 1.000 – 3.000 |
| Người dùng đồng thời | Tối thiểu 500 |
| Hồ sơ bệnh án phát sinh/năm | \> 1.000.000 |

## 2.4. Các bên liên quan (Stakeholders)

| **Nhóm** | **Bên liên quan** | **Quan tâm chính** |
| --- | --- | --- |
| Lãnh đạo | Ban Giám đốc, Trưởng khoa/phòng | Hiệu quả điều hành, KPI, tuân thủ, doanh thu |
| Quản lý | KHTH, CNTT, TCKT, Điều dưỡng, QLCL | Quy trình chuẩn, khả thi kỹ thuật, chất lượng |
| Chuyên môn | Tiếp đón, thu ngân, bác sĩ, điều dưỡng, PTV, KTV, dược sĩ, thủ kho | Thao tác nhanh, chính xác, ít sai sót |
| Bên ngoài | Người bệnh & người nhà, BHXH, Bộ Y tế, NCC giải pháp | Trải nghiệm, quyền lợi BHYT, liên thông dữ liệu |

## 2.5. Giả định và ràng buộc

| **Loại** | **Nội dung** |
| --- | --- |
| Giả định | Hạ tầng mạng, máy chủ, thiết bị đầu cuối và đường truyền đáp ứng yêu cầu; các hệ thống LIS/RIS/PACS/BHXH cung cấp giao diện tích hợp theo chuẩn. |
| Ràng buộc | Tuân thủ quy định pháp luật hiện hành; vận hành song song với hồ sơ giấy trong giai đoạn chuyển tiếp; không gián đoạn hoạt động KCB khi triển khai. |

## 2.6. Tiêu chí thành công của dự án

| **Khía cạnh** | **Tiêu chí** |
| --- | --- |
| Nghiệp vụ | 100% quy trình KCB được số hóa; 100% dữ liệu lâm sàng quản lý tập trung; giảm ≥30% thời gian chờ khám; giảm ≥90% hồ sơ giấy. |
| Vận hành | Sẵn sàng 24/7, uptime ≥99,95%; ≥500 người dùng đồng thời; thời gian phản hồi tác vụ thường <1s, báo cáo <5s. |
| Pháp lý | Tuân thủ Luật KBCB, TT32/2023, quy định EMR, quy định BHXH; liên thông dữ liệu y tế quốc gia. |

# CHƯƠNG 3. KIẾN TRÚC NGHIỆP VỤ TỔNG THỂ

## 3.1. Nguyên tắc thiết kế nghiệp vụ

| **Nguyên tắc** | **Diễn giải** |
| --- | --- |
| Người bệnh là trung tâm | Mọi dữ liệu phát sinh được liên kết vào một hồ sơ người bệnh thống nhất theo suốt vòng đời. |
| Số hóa ngay từ đầu | Ưu tiên dữ liệu điện tử; thông tin KCB được lưu trữ điện tử và ký số theo quy định. |
| Nền tảng tích hợp | HIS là trung tâm kết nối EMR, LIS, RIS/PACS, Dược, Billing, BHYT, Dashboard qua chuẩn mở. |
| Quyết định dựa trên dữ liệu | Dữ liệu là tài sản; chuẩn hóa, tập trung, khai thác phục vụ quản trị điều hành. |
| Thao tác tối ưu theo vị trí | Màn hình và luồng được thiết kế theo vị trí tác nghiệp để thao tác nhanh, ít bước, ít sai sót. |

## 3.2. Kiến trúc phân lớp nghiệp vụ

Hệ thống được tổ chức theo bảy lớp nghiệp vụ, HIS là nền tảng trung tâm:

| **Lớp** | **Tên lớp** | **Thành phần chính** |
| --- | --- | --- |
| L1  | Tương tác người bệnh | Patient Portal, Mobile App, Kiosk, Tổng đài, Đặt lịch trực tuyến |
| L2  | Nghiệp vụ lâm sàng | HIS, EMR, CPOE, eMAR, Nursing |
| L3  | Cận lâm sàng | LIS, RIS, PACS, Nội soi, Thăm dò chức năng, GPB |
| L4  | Viện phí – tài chính | Billing, BHYT, e-Payment, Hóa đơn điện tử, Công nợ |
| L5  | Dược – vật tư – hậu cần | Kho Dược/VTYT/HC, Nhà thuốc, Ngân hàng máu, Dinh dưỡng |
| L6  | Quản trị – điều hành | Executive/KPI/Quality Dashboard, Báo cáo thống kê |
| L7  | Dữ liệu & tích hợp | API Gateway, HL7/FHIR, DICOM, ESB, Data Warehouse, Data Lake |

## 3.3. Bản đồ năng lực nghiệp vụ (Capability Map)

Bản đồ năng lực gom nhóm chức năng nghiệp vụ cốt lõi, làm cơ sở phân rã phân hệ và yêu cầu chức năng:

| **Nhóm năng lực** | **Năng lực nghiệp vụ** |
| --- | --- |
| Trước khám | Đặt lịch · Đăng ký (online/quầy/kiosk) · Quản lý hàng đợi · Định danh người bệnh |
| Khám & cấp cứu | Tiếp nhận · Khám ngoại trú · Cấp cứu · Khám sức khỏe · Khám theo yêu cầu |
| Cận lâm sàng | Chỉ định · Lấy mẫu/tiếp nhận · Thực hiện · Trả kết quả · Duyệt kết quả |
| Điều trị | Nội trú · Ban ngày · Hồi sức · PTTT · Chuyển khoa/viện · Chăm sóc điều dưỡng |
| Hỗ trợ điều trị | Dược lâm sàng · Kho & cấp phát · Nhà thuốc · Ngân hàng máu · Dinh dưỡng · KSNK |
| Viện phí | Tạm ứng · Thu phí · Hóa đơn điện tử · Công nợ · Thanh toán không tiền mặt |
| Bảo hiểm | Duyệt tuyến/BHYT · Kiểm tra cổng · Quyết toán XML |
| Bệnh án điện tử | Lập – ký số – khóa – lưu trữ – phân quyền khai thác EMR |
| Điều hành | Dashboard · KPI · Báo cáo thống kê y tế · Phân tích dữ liệu |
| Nền tảng | Danh mục dùng chung · Phân quyền · Nhật ký/audit · Tích hợp |

## 3.4. Mô hình vòng đời người bệnh

Vòng đời người bệnh trải dài từ tiếp nhận đến kết thúc điều trị, được quản lý xuyên suốt trên một mã người bệnh và một mã lượt điều trị:

1\. Đăng ký / Tiếp nhận (thường quy hoặc cấp cứu).

2\. Khám bệnh và chẩn đoán sơ bộ.

3\. Chỉ định và thực hiện cận lâm sàng.

4\. Kết luận: kê đơn điều trị ngoại trú HOẶC chỉ định nhập viện.

5\. Điều trị nội trú, chăm sóc, PTTT (nếu có).

6\. Ra viện / chuyển viện / tử vong.

7\. Tổng kết bệnh án, viện phí, quyết toán BHYT.

8\. Ký số, khóa và lưu trữ bệnh án điện tử.

# CHƯƠNG 4. DANH MỤC PHÂN HỆ VÀ MÃ ĐỊNH DANH

Đây là chỉ mục nền tảng của toàn hệ thống. Mỗi phân hệ (HIS-xx) sẽ được phân rã thành một tài liệu BRD chi tiết riêng, kế thừa mã định danh, quy trình và tiêu chí nghiệm thu từ tài liệu này.

| **Mã** | **Phân hệ** | **Phạm vi chức năng cốt lõi** | **QT liên quan** |
| --- | --- | --- | --- |
| HIS-01 | Quản lý thông tin người bệnh | ID, thông tin hành chính, tiền sử, lịch sử KCB | QT-01 |
| HIS-02 | Hàng đợi & Lịch hẹn | Đặt lịch, hàng đợi, điều phối STT | QT-01, QT-03 |
| HIS-03 | Tiếp nhận & Đăng ký khám | Kiosk/quầy/online, định danh, gọi số, phân buồng | QT-01 |
| HIS-04 | Khám bệnh | Hỏi bệnh, khám, chẩn đoán ICD, chỉ định, kê đơn, xử trí | QT-03 |
| HIS-05 | Cấp cứu | Tiếp nhận cấp cứu, phân loại (triage), xử trí, chuyển viện/nhập viện | QT-02 |
| HIS-06 | Điều trị (ban ngày, nội trú, ngoại trú) | Nhập khoa, bệnh án, buồng giường, y lệnh, tổng kết ra viện | QT-06, QT-07, QT-10 |
| HIS-07 | Điều dưỡng & Chăm sóc | Sinh hiệu, thực hiện y lệnh (eMAR), phiếu chăm sóc | QT-07 |
| HIS-08 | Chỉ định & Y lệnh (CPOE) | Chỉ định, ra y lệnh thuốc, xét nghiệm, CĐHA/ DVKT… | QT-03, QT-04, QT-07 |
| HIS-09 | Phẫu thuật – Thủ thuật | Chỉ định, hội chẩn, lịch mổ, tường trình, gây mê hồi sức | QT-08 |
| HIS-10 | Dược lâm sàng & Kê đơn | Kê đơn, duyệt đơn BHYT, cảnh báo | QT-05 |
| HIS-11 | Kho Dược/VTYT/HC & Cấp phát | Danh mục, thầu, nhập/xuất, kiểm kê, tổng hợp lĩnh, bù tủ trực | QT-14 |
| HIS-12 | Nhà thuốc bệnh viện | Nhập NCC, bán lẻ, HĐĐT, công nợ NCC | QT-16 |
| HIS-13 | Ngân hàng máu | Người hiến/nhận, xét nghiệm sàng lọc, kho máu, phát – truyền máu | QT-15 |
| HIS-14 | Dinh dưỡng | Sàng lọc, hội chẩn, chỉ định – cấp phát suất ăn | QT-07 |
| HIS-15 | Kiểm soát nhiễm khuẩn | Giám sát nhiễm khuẩn, báo cáo sự cố, kháng sinh | QT-07 |
| HIS-16 | Viện phí & Thanh toán | Tạm ứng, thu phí, HĐĐT, thanh toán không tiền mặt, công nợ | QT-11 |
| HIS-17 | BHYT & Quyết toán | Duyệt tuyến, kiểm tra cổng, quản lý & gửi XML quyết toán | QT-12 |
| HIS-18 | Tạo lập bệnh án điện tử | Tạo – Cập nhật – Theo dõi – Đóng – Chuyển bệnh án | QT-13 |
| HIS-19 | Báo cáo thống kê | Tạo lập và quản lý báo cáo thống kê | Toàn hệ |
| HIS-20 | Danh mục dùng chung & QTHT | Danh mục chuẩn, người dùng, vai trò, phân quyền, nhật ký | Toàn hệ |
| HIS-21 | CDSS – Hệ thống hỗ trợ ra quyết định lâm sàng | Hỗ trợ bác sĩ ra quyết định tốt hơn. Giảm biến cố y khoa. Chuẩn hóa điều trị theo phác đồ. Tăng chất lượng khám chữa bệnh | Toàn hệ |
| HIS-22 | Tích hợp | API Gateway, HL7/FHIR, DICOM, BHXH, HĐĐT, CA, ESB | Toàn hệ |

# CHƯƠNG 5. NGUYÊN TẮC VÀ QUY TẮC NGHIỆP VỤ BẮT BUỘC

Các quy tắc nghiệp vụ (BR) áp dụng xuyên suốt toàn hệ thống, là ràng buộc bắt buộc cho mọi phân hệ và là cơ sở kiểm thử.

| **Mã** | **Quy tắc nghiệp vụ** | **Diễn giải & tác động** |
| --- | --- | --- |
| BR-001 | Một người bệnh – một hồ sơ | Mỗi người bệnh có duy nhất một mã (patient ID); hỗ trợ phát hiện & gộp hồ sơ trùng. |
| BR-002 | Một lượt điều trị – một mã lượt | Mọi dữ liệu KCB gắn với một mã lượt (encounter); ngoại trú, nội trú, cấp cứu phân biệt bằng loại lượt. |
| BR-003 | Dữ liệu dùng chung toàn viện | Danh mục và dữ liệu nền dùng chung, không nhân bản cục bộ theo khoa/phòng. |
| BR-004 | Không nhập liệu lặp lại | Thông tin đã có không yêu cầu nhập lại; kế thừa tự động giữa các bước/phân hệ. |
| BR-005 | EMR là hồ sơ pháp lý gốc | Sau khi ký số & khóa, EMR có giá trị pháp lý; mọi sửa đổi phải qua bản đính chính (amendment) có truy vết. |
| BR-006 | Ký số thay chữ ký tay | Tài liệu lâm sàng, hóa đơn được ký số hợp lệ theo NĐ130; không chấp nhận sửa sau ký. |
| BR-007 | Truy vết & kiểm toán | Mọi thao tác tạo/sửa/xóa/xem hồ sơ nhạy cảm được ghi log không thể chỉnh sửa (who-when-what). |
| BR-008 | Sử dụng danh mục chuẩn | Chẩn đoán theo ICD-10; thuốc/DVKT/VTYT ánh xạ danh mục dùng chung BHXH & Bộ Y tế. |
| BR-009 | Ghi nhận chi phí realtime | Mỗi dịch vụ/thuốc/VTYT phát sinh được ghi nhận chi phí tức thời vào lượt điều trị. |
| BR-010 | Chặn chi khi hết tạm ứng | Hệ thống cảnh báo/kiểm soát khi chi phí vượt tạm ứng hoặc trần thanh toán (theo cấu hình). |
| BR-011 | Kiểm tra an toàn dùng thuốc | Cảnh báo tương tác thuốc, trùng hoạt chất, dị ứng, liều bất thường khi kê đơn/thực hiện thuốc. |
| BR-012 | Kiểm soát tồn kho & lô/hạn | Xuất kho theo FEFO; chặn xuất quá tồn; cảnh báo cận date/hết hạn. |
| BR-013 | An toàn truyền máu | Bắt buộc định nhóm, phản ứng chéo, đối chiếu người bệnh – đơn vị máu trước truyền. |
| BR-014 | Tích hợp mở theo chuẩn | Tích hợp qua API/HL7/FHIR/DICOM; không phụ thuộc giao diện đóng. |
| BR-015 | Bảo mật & tối thiểu quyền | Truy cập theo vai trò và phạm vi (least privilege); dữ liệu nhạy cảm được mã hóa. |
| BR-016 | Toàn vẹn quyết toán BHYT | Dữ liệu XML quyết toán khớp với dữ liệu lâm sàng & viện phí; chặn gửi khi thiếu dữ liệu bắt buộc. |

# CHƯƠNG 6. TÁC NHÂN, VAI TRÒ VÀ THỰC THỂ NGHIỆP VỤ

## 6.1. Từ điển tác nhân / vai trò

Danh mục vai trò chuẩn (VT), dùng thống nhất cho ma trận phân quyền (Chương 9) và các đặc tả quy trình.

| **Mã** | **Vai trò** | **Vị trí tác nghiệp** | **Trách nhiệm chính** |
| --- | --- | --- | --- |
| VT-01 | Nhân viên tiếp đón | Quầy tiếp đón/Kiosk | Đăng ký, định danh, phân buồng, gọi số |
| VT-02 | NV Tổng đài / Đặt lịch | Tổng đài | Đặt lịch, xác nhận, nhắc hẹn |
| VT-03 | Thu ngân | Quầy thu ngân | Tạm ứng, thu phí, HĐĐT, hoàn/điều chỉnh |
| VT-04 | Bác sĩ khám | Phòng khám | Hỏi–khám, chẩn đoán, chỉ định, kê đơn, xử trí |
| VT-05 | Bác sĩ điều trị nội trú | Khoa nội trú | Bệnh án, y lệnh, theo dõi, tổng kết ra viện |
| VT-06 | Bác sĩ cấp cứu | Khoa cấp cứu | Phân loại, xử trí cấp cứu, chỉ định khẩn |
| VT-07 | Phẫu thuật viên | Phòng mổ | Thực hiện & tường trình PTTT |
| VT-08 | Bác sĩ gây mê hồi sức | Phòng mổ/Hồi tỉnh | Khám tiền mê, gây mê, hồi sức |
| VT-09 | Điều dưỡng | Khoa/Phòng khám | Sinh hiệu, thực hiện y lệnh (eMAR), chăm sóc |
| VT-10 | Điều dưỡng trưởng | Khoa | Phân công, duyệt chăm sóc, tổng hợp lĩnh thuốc |
| VT-11 | KTV Xét nghiệm | Khoa XN | Nhận mẫu, chạy máy, nhập/duyệt kết quả |
| VT-12 | KTV Chẩn đoán hình ảnh | Khoa CĐHA | Chụp, xử lý ảnh, đẩy PACS |
| VT-13 | Bác sĩ CĐHA | Khoa CĐHA | Đọc & ký kết quả hình ảnh |
| VT-14 | Dược sĩ lâm sàng | Khoa Dược | Duyệt đơn, cảnh báo, tư vấn dùng thuốc |
| VT-15 | Dược sĩ cấp phát | Kho lẻ/tủ trực | Cấp phát thuốc/VTYT nội trú & ngoại trú |
| VT-16 | Thủ kho | Kho Dược/VTYT | Nhập/xuất/kiểm kê, quản lý lô–hạn |
| VT-17 | Dược sĩ nhà thuốc | Nhà thuốc BV | Bán lẻ, phát hành HĐĐT, công nợ NCC |
| VT-18 | KTV Ngân hàng máu | Ngân hàng máu | Tiếp nhận, sàng lọc, phát – truyền máu |
| VT-19 | NV Dinh dưỡng | Khoa Dinh dưỡng | Sàng lọc, chỉ định & cấp suất ăn |
| VT-20 | Giám định BHYT nội bộ | Phòng KHTH/BHYT | Duyệt tuyến, kiểm tra & gửi XML quyết toán |
| VT-21 | Kế toán viện phí | Phòng TCKT | Tổng hợp doanh thu, công nợ, đối soát |
| VT-22 | Trưởng khoa | Khoa | Duyệt chuyên môn, hội chẩn, giám sát KPI khoa |
| VT-23 | Ban Giám đốc | Ban GĐ | Điều hành, phê duyệt, giám sát KPI toàn viện |
| VT-24 | Phòng KHTH | KHTH | Quản lý quy trình, thống kê, báo cáo Bộ Y tế |
| VT-25 | Quản trị hệ thống | CNTT | Quản trị người dùng, phân quyền, vận hành |
| VT-26 | Quản trị danh mục | CNTT/KHTH | Cấu hình danh mục dùng chung, ánh xạ BHXH |
| VT-27 | Người bệnh / Người nhà | Cổng/Kiosk/App | Đăng ký, tra cứu, thanh toán, phản hồi |

## 6.2. Danh mục thực thể nghiệp vụ chính

Các thực thể (TT) cốt lõi làm cơ sở cho mô hình dữ liệu và bảng trạng thái (Chương 8).

| **Mã** | **Thực thể** | **Mô tả** | **Chủ sở hữu dữ liệu** |
| --- | --- | --- | --- |
| TT-01 | Người bệnh | Hồ sơ định danh, hành chính, BHYT, tiền sử | PH-01/PH-21 |
| TT-02 | Lượt tiếp nhận/khám | Encounter ngoại trú/nội trú/cấp cứu | PH-01/PH-03/PH-05 |
| TT-03 | Chỉ định CLS/DVKT | Order xét nghiệm/CĐHA/DVKT | PH-07 |
| TT-04 | Kết quả cận lâm sàng | Kết quả XN/CĐHA/TDCN | PH-08/PH-09 |
| TT-05 | Đơn thuốc / Y lệnh thuốc | Đơn ngoại trú & y lệnh nội trú | PH-11 |
| TT-06 | Bệnh án nội trú | Hồ sơ điều trị nội trú | PH-05 |
| TT-07 | Giường bệnh | Tài nguyên buồng/giường | PH-05 |
| TT-08 | Phiếu PTTT | Hồ sơ phẫu thuật – thủ thuật | PH-10 |
| TT-09 | Phiếu thu / Hóa đơn | Chứng từ viện phí & HĐĐT | PH-17 |
| TT-10 | Hồ sơ quyết toán BHYT | Bộ dữ liệu XML gửi cổng BHXH | PH-18 |
| TT-11 | Tài liệu EMR | Tài liệu lâm sàng ký số | PH-19 |
| TT-12 | Phiếu kho / Chứng từ kho | Nhập/xuất/điều chuyển/kiểm kê | PH-12 |
| TT-13 | Đơn vị máu | Túi máu & chế phẩm | PH-14 |

# CHƯƠNG 7. QUY TRÌNH NGHIỆP VỤ ĐẦU–CUỐI

Chương này đặc tả 16 quy trình lõi theo template chuẩn: mã, tác nhân, điều kiện bắt đầu, luồng chính, luồng ngoại lệ, dữ liệu đầu vào, dữ liệu đầu ra, quy tắc nghiệp vụ và tiêu chí nghiệm thu. Đây là khung dùng chung; BRD chi tiết theo phân hệ sẽ phân rã từng bước thành thao tác cấp trường.

## 7.1. Sơ đồ quy trình tổng thể

Luồng khám chữa bệnh tổng thể liên kết các quy trình lõi:

1\. Tiếp nhận thường quy (QT-01) hoặc Cấp cứu (QT-02).

2\. Khám ngoại trú (QT-03) → Chỉ định & thực hiện CLS (QT-04).

3\. Rẽ nhánh: Kê đơn & cấp phát ngoại trú (QT-05) HOẶC Nhập viện (QT-06).

4\. Điều trị nội trú & chăm sóc (QT-07); có thể PTTT (QT-08), chuyển khoa/viện (QT-09).

5\. Ra viện & tổng kết bệnh án (QT-10).

6\. Viện phí & thanh toán (QT-11) → Quyết toán BHYT (QT-12).

7\. Bệnh án điện tử & ký số (QT-13) xuyên suốt.

8\. Các quy trình hậu cần hỗ trợ: Kho & cấp phát (QT-14), Ngân hàng máu (QT-15), Nhà thuốc (QT-16).

| **Mã** | **Quy trình** | **Điểm bắt đầu** | **Điểm kết thúc** |
| --- | --- | --- | --- |
| QT-01 | Đăng ký & Tiếp nhận người bệnh | Người bệnh đến/đặt lịch | Có lượt khám, vào hàng đợi |
| QT-02 | Tiếp nhận & xử trí Cấp cứu | Người bệnh cấp cứu đến | Ổn định: nhập viện/chuyển/về |
| QT-03 | Khám bệnh ngoại trú | Được gọi vào khám | Kết luận khám, hướng xử trí |
| QT-04 | Chỉ định & thực hiện CLS | Bác sĩ ra chỉ định | Trả kết quả vào hồ sơ |
| QT-05 | Kê đơn & cấp phát thuốc/VTYT ngoại trú | Bác sĩ kê đơn | Người bệnh nhận thuốc |
| QT-06 | Chỉ định nhập viện & tiếp nhận nhập khoa | Chỉ định nhập viện | Bệnh án nội trú mở, có giường |
| QT-07 | Điều trị nội trú & chăm sóc | Nhập khoa | Đủ điều kiện ra viện |
| QT-08 | Phẫu thuật – thủ thuật | Chỉ định PTTT | Hoàn tất PTTT, hồi tỉnh |
| QT-09 | Chuyển khoa / chuyển viện | Yêu cầu chuyển | Bàn giao thành công |
| QT-10 | Ra viện & tổng kết bệnh án | Quyết định ra viện | BA khóa, thanh toán |
| QT-11 | Viện phí & thanh toán | Phát sinh chi phí | Tất toán, phát hành HĐĐT |
| QT-12 | Quyết toán BHYT (XML) | Kết thúc đợt điều trị | Gửi & đối soát cổng BHXH |
| QT-13 | Bệnh án điện tử & ký số | Hoàn tất tài liệu lâm sàng | Ký số, khóa, lưu trữ |
| QT-14 | Kho Dược/VTYT/HC & cấp phát | Nhu cầu nhập/lĩnh | Xuất/cấp phát, cập nhật tồn |
| QT-15 | Ngân hàng máu | Nhu cầu máu / tiếp nhận đơn vị máu | Truyền máu an toàn |
| QT-16 | Nhà thuốc bán lẻ | Khách mua/đơn ngoại trú | Bán, phát hành HĐĐT |

## 7.2. QT-01 — Đăng ký & Tiếp nhận người bệnh

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-01</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Đăng ký &amp; Tiếp nhận người bệnh (ngoại trú thường quy)</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-01</p><p>PH-02</p><p>PH-23</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-27 Người bệnh/Người nhà</li><li>VT-01 Nhân viên tiếp đón</li><li>VT-03 Thu ngân</li><li>VT-04 Bác sĩ khám (nhận điều phối)</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Người bệnh đến viện hoặc đã đặt lịch trực tuyến</li><li>Hệ thống danh mục &amp; lịch làm việc đã cấu hình</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>CCCD/định danh, thẻ BHYT, mã đặt lịch (nếu có)</li><li>Lý do khám, đối tượng (BHYT/dịch vụ/yêu cầu)</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Người bệnh lấy số tại kiosk hoặc quầy; hệ thống cấp STT theo loại dịch vụ.</p><p>2. Tra cứu/định danh: tìm hồ sơ theo CCCD/mã BN/BHYT; nếu chưa có, tạo hồ sơ mới (BR-001).</p><p>3. Kiểm tra thẻ BHYT trực tuyến (thông tuyến, hạn thẻ, mức hưởng).</p><p>4. Chọn phòng khám/chuyên khoa; hệ thống tạo lượt khám (TT-02) và đưa vào hàng đợi (BR-002).</p><p>5. Thu công khám/tạm ứng (nếu đối tượng dịch vụ) — chuyển QT-11.</p><p>6. In phiếu STT/phiếu khám; điều phối người bệnh tới phòng khám.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Thẻ BHYT không hợp lệ/hết hạn → cảnh báo, chuyển đối tượng thu phí hoặc hướng dẫn bổ sung</li><li>Phát hiện hồ sơ trùng → gắn cờ nghi trùng, chuyển nghiệp vụ gộp hồ sơ (BR-001)</li><li>Sai chuyên khoa/phòng khám → cho phép điều chuyển lượt sang phòng khác, giữ STT ưu tiên</li><li>Người bệnh không đến (no-show) lịch hẹn → tự động hủy/hoãn slot, giải phóng hàng đợi</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Hồ sơ người bệnh (TT-01)</li><li>Lượt khám ở trạng thái 'Chờ khám' (TT-02)</li><li>Phiếu STT/biên lai (nếu thu phí)</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-001</li><li>BR-002</li><li>BR-003</li><li>BR-004</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-01.NT01: Tạo/định danh người bệnh và sinh mã BN duy nhất trong ≤ thời gian mục tiêu.</li><li>QT-01.NT02: Kiểm tra BHYT trực tuyến trả kết quả và lưu vào lượt khám.</li><li>QT-01.NT03: Lượt khám xuất hiện đúng hàng đợi phòng khám đã chọn.</li><li>QT-01.NT04: In được phiếu STT/phiếu khám; số liệu khớp lượt vừa tạo.</li></ul></td></tr></tbody></table></div>

## 7.3. QT-02 — Tiếp nhận & xử trí Cấp cứu

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-02</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Tiếp nhận &amp; xử trí Cấp cứu</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-04</p><p>PH-01</p><p>PH-07</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-27 Người bệnh/Người nhà</li><li>VT-06 Bác sĩ cấp cứu</li><li>VT-09 Điều dưỡng</li><li>VT-01 Tiếp đón</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Người bệnh vào khoa cấp cứu (có thể chưa đủ giấy tờ)</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Thông tin tối thiểu (họ tên/ước lượng tuổi/giới), tình trạng cấp cứu</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Tiếp nhận nhanh: tạo lượt cấp cứu tạm với định danh tối thiểu (bổ sung sau).</p><p>2. Phân loại mức độ ưu tiên (triage) theo thang cấp cứu; gắn màu ưu tiên.</p><p>3. Bác sĩ xử trí cấp cứu; ra y lệnh khẩn (thuốc/CLS) không chờ thanh toán (BR-009, BR-010 nới lỏng).</p><p>4. Ghi nhận diễn biến, can thiệp, thuốc/VTYT sử dụng theo thời gian thực.</p><p>5. Quyết định hướng: nhập viện (QT-06), chuyển viện (QT-09), lưu theo dõi hoặc cho về.</p><p>6. Bổ sung định danh/BHYT &amp; hoàn tất thủ tục hành chính khi ổn định.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Người bệnh không xác định danh tính → dùng mã tạm 'vô danh', gắn ảnh/đặc điểm, hợp nhất khi có thông tin</li><li>Cấp cứu hàng loạt (thảm họa) → kích hoạt chế độ tiếp nhận nhanh, triage hàng loạt</li><li>Tử vong tại cấp cứu → chuyển quy trình xử lý tử vong, khóa hồ sơ theo quy định</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Lượt cấp cứu &amp; bệnh án cấp cứu</li><li>Y lệnh khẩn đã thực hiện</li><li>Quyết định hướng điều trị</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-002</li><li>BR-007</li><li>BR-009</li><li>BR-011</li><li>BR-013</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-02.NT01: Tạo lượt cấp cứu với định danh tối thiểu trong vài thao tác, không chặn bởi thủ tục thu phí.</li><li>QT-02.NT02: Ghi nhận triage và diễn biến theo mốc thời gian.</li><li>QT-02.NT03: Y lệnh khẩn thực hiện được ngay và vẫn được ghi nhận chi phí đầy đủ để hậu kiểm.</li><li>QT-02.NT04: Chuyển tiếp nhập viện/chuyển viện kế thừa toàn bộ dữ liệu cấp cứu.</li></ul></td></tr></tbody></table></div>

## 7.4. QT-03 — Khám bệnh ngoại trú

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-03</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Khám bệnh ngoại trú</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-03</p><p>PH-07</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-04 Bác sĩ khám</li><li>VT-09 Điều dưỡng phòng khám</li><li>VT-27 Người bệnh</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Lượt khám ở trạng thái 'Chờ khám' trong hàng đợi phòng khám</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Lượt khám, tiền sử, kết quả CLS cũ (nếu có), lý do đến khám</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Gọi người bệnh theo STT; xác nhận đúng người – đúng lượt.</p><p>2. Điều dưỡng đo sinh hiệu, khai thác lý do khám (tùy mô hình).</p><p>3. Bác sĩ hỏi bệnh, khám lâm sàng, ghi nhận triệu chứng.</p><p>4. Chẩn đoán sơ bộ theo ICD-10 (BR-008).</p><p>5. Chỉ định CLS/DVKT nếu cần → QT-04; đọc kết quả khi có.</p><p>6. Kết luận: chẩn đoán xác định; kê đơn (QT-05) hoặc chỉ định nhập viện (QT-06) hoặc hẹn tái khám.</p><p>7. Hoàn tất phiếu khám, ký số (QT-13).</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Cần hội chẩn/chuyển chuyên khoa → tạo yêu cầu hội chẩn hoặc điều chuyển lượt sang chuyên khoa phù hợp</li><li>Người bệnh bỏ khám giữa chừng → đánh dấu lượt 'bỏ khám', lưu dữ liệu đã nhập</li><li>Chờ kết quả CLS lâu → chuyển trạng thái 'Chờ CLS', cho phép gọi lượt kế; quay lại khi có KQ</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Phiếu khám có chẩn đoán ICD-10</li><li>Chỉ định CLS/đơn thuốc (nếu có)</li><li>Hướng xử trí</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-004</li><li>BR-005</li><li>BR-006</li><li>BR-008</li><li>BR-011</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-03.NT01: Màn hình khám hiển thị đủ tiền sử, dị ứng, KQ CLS liên quan mà không phải tra thủ công.</li><li>QT-03.NT02: Chẩn đoán bắt buộc mã ICD-10 hợp lệ mới cho kết luận.</li><li>QT-03.NT03: Chỉ định CLS/kê đơn tạo được ngay trong màn hình khám và ghi nhận chi phí.</li><li>QT-03.NT04: Phiếu khám ký số và trở thành tài liệu EMR không sửa được sau khóa.</li></ul></td></tr></tbody></table></div>

## 7.5. QT-04 — Chỉ định & thực hiện cận lâm sàng

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-04</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Chỉ định &amp; thực hiện cận lâm sàng (XN/CĐHA/TDCN/Nội soi)</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-07</p><p>PH-08</p><p>PH-09</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-04/VT-05/VT-06 Bác sĩ chỉ định</li><li>VT-11 KTV XN</li><li>VT-12 KTV CĐHA</li><li>VT-13 Bác sĩ CĐHA</li><li>VT-03 Thu ngân</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Có lượt điều trị hợp lệ; dịch vụ nằm trong danh mục kỹ thuật</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Chỉ định (loại DVKT, mẫu bệnh phẩm/vùng chụp), thông tin lâm sàng</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Bác sĩ tạo chỉ định CLS (TT-03) trong màn hình khám/điều trị (CPOE).</p><p>2. Kiểm tra điều kiện thanh toán/tạm ứng (BR-010) — với ngoại trú dịch vụ, thu phí trước (QT-11).</p><p>3. Gửi chỉ định sang LIS/RIS qua tích hợp (TH-01/TH-02).</p><p>4. Lấy mẫu/tiếp nhận người bệnh; định danh mẫu bằng barcode.</p><p>5. Thực hiện xét nghiệm/chụp; máy trả kết quả tự động hoặc nhập tay.</p><p>6. Duyệt kết quả (KTV/bác sĩ CĐHA ký), trả kết quả về HIS (TT-04) và PACS (ảnh).</p><p>7. Bác sĩ chỉ định nhận thông báo có kết quả, đọc và tiếp tục xử trí.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Mẫu không đạt / cần lấy lại → từ chối mẫu, tạo yêu cầu lấy lại, thông báo phòng khám</li><li>Kết quả bất thường nguy kịch (critical value) → cảnh báo khẩn tới bác sĩ chỉ định, ghi nhận thời điểm báo</li><li>Chưa thanh toán (ngoại trú dịch vụ) → giữ chỉ định ở trạng thái chờ thu phí, không thực hiện</li><li>Hủy chỉ định sau khi đã thu phí → chuyển nghiệp vụ hoàn phí/điều chỉnh (QT-11)</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Kết quả CLS số hóa (TT-04)</li><li>Hình ảnh lưu PACS</li><li>Cập nhật chi phí dịch vụ</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-004</li><li>BR-008</li><li>BR-009</li><li>BR-010</li><li>BR-014</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-04.NT01: Chỉ định đẩy sang LIS/RIS và nhận lại kết quả tự động, khớp đúng người bệnh – chỉ định.</li><li>QT-04.NT02: Kết quả và hình ảnh truy cập được ngay trong hồ sơ khám/điều trị.</li><li>QT-04.NT03: Giá trị nguy kịch sinh cảnh báo và được ghi nhận truy vết.</li><li>QT-04.NT04: Chi phí dịch vụ ghi nhận đúng đối tượng (BHYT/dịch vụ).</li></ul></td></tr></tbody></table></div>

## 7.6. QT-05 — Kê đơn & cấp phát thuốc/VTYT ngoại trú

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-05</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Kê đơn &amp; cấp phát thuốc/VTYT ngoại trú</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-11</p><p>PH-12</p><p>PH-13</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-04 Bác sĩ khám</li><li>VT-14 Dược sĩ lâm sàng</li><li>VT-15 Dược sĩ cấp phát</li><li>VT-03 Thu ngân</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Có chẩn đoán xác định trên lượt khám</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Đơn thuốc (hoạt chất/biệt dược, liều, đường dùng, số ngày), VTYT</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Bác sĩ kê đơn (TT-05); hệ thống cảnh báo tương tác/trùng hoạt chất/dị ứng/liều (BR-011).</p><p>2. Kiểm tra danh mục &amp; tồn kho khả dụng; với BHYT kiểm tra định mức/điều kiện thanh toán.</p><p>3. Duyệt đơn BHYT (nếu có) — dược sĩ/giám định (BR-016).</p><p>4. Thu phí phần người bệnh chi trả (QT-11).</p><p>5. Cấp phát tại nhà thuốc BHYT/kho lẻ (QT-16/QT-14): trừ tồn theo lô–hạn (BR-012).</p><p>6. In đơn/hướng dẫn dùng thuốc; ký số đơn (QT-13).</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Cảnh báo tương tác nghiêm trọng → yêu cầu bác sĩ xác nhận/điều chỉnh, ghi nhận lý do ghi đè</li><li>Hết thuốc trong kho cấp phát → đề xuất thay thế/điều chuyển kho hoặc kê thuốc thay thế</li><li>Đơn vượt định mức BHYT → cảnh báo, tách phần ngoài BHYT sang thu phí dịch vụ</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Đơn thuốc đã cấp phát (TT-05)</li><li>Cập nhật tồn kho</li><li>Chứng từ chi phí thuốc/VTYT</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-008</li><li>BR-009</li><li>BR-011</li><li>BR-012</li><li>BR-016</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-05.NT01: Kê đơn sinh cảnh báo an toàn thuốc theo dữ liệu dị ứng &amp; thuốc đang dùng.</li><li>QT-05.NT02: Cấp phát trừ đúng tồn theo lô–hạn (FEFO) và không cho xuất quá tồn.</li><li>QT-05.NT03: Phần BHYT/tự chi trả tách đúng và đồng bộ viện phí.</li><li>QT-05.NT04: Đơn thuốc ký số, tra cứu lại được đầy đủ.</li></ul></td></tr></tbody></table></div>

## 7.7. QT-06 — Chỉ định nhập viện & tiếp nhận nhập khoa

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-06</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Chỉ định nhập viện &amp; tiếp nhận nhập khoa</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-05</p><p>PH-01</p><p>PH-17</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-04/VT-06 Bác sĩ chỉ định</li><li>VT-01 Tiếp đón nội trú</li><li>VT-05 Bác sĩ điều trị</li><li>VT-09 Điều dưỡng</li><li>VT-03 Thu ngân</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Có chỉ định nhập viện từ khám ngoại trú/cấp cứu</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Chỉ định nhập viện, khoa tiếp nhận, chẩn đoán vào viện</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Tạo hồ sơ nhập viện; chuyển lượt sang loại nội trú (TT-02 → TT-06).</p><p>2. Thu tạm ứng nhập viện (QT-11) theo chính sách.</p><p>3. Phân khoa/buồng/giường; cập nhật trạng thái giường (TT-07).</p><p>4. Mở bệnh án nội trú (TT-06); kế thừa dữ liệu khám/cấp cứu (BR-004).</p><p>5. Điều dưỡng tiếp nhận, đánh giá ban đầu, lập kế hoạch chăm sóc.</p><p>6. Bác sĩ điều trị ra y lệnh ngày đầu → chuyển QT-07.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Hết giường khoa chỉ định → đề xuất khoa/giường thay thế hoặc danh sách chờ giường</li><li>Người bệnh từ chối nhập viện → ghi nhận cam kết, chuyển hướng ngoại trú/về</li><li>Chưa đủ tạm ứng → cảnh báo theo BR-010, xử lý theo chính sách miễn/giảm/cấp cứu</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Bệnh án nội trú mở (TT-06)</li><li>Giường được gán (TT-07)</li><li>Kế hoạch chăm sóc ban đầu</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-002</li><li>BR-004</li><li>BR-009</li><li>BR-010</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-06.NT01: Chuyển đổi lượt ngoại trú/cấp cứu sang nội trú kế thừa toàn bộ dữ liệu.</li><li>QT-06.NT02: Gán giường cập nhật trạng thái buồng/giường tức thời và không gán trùng.</li><li>QT-06.NT03: Bệnh án nội trú mở đúng khoa, đúng chẩn đoán vào viện.</li><li>QT-06.NT04: Tạm ứng ghi nhận và liên kết công nợ lượt điều trị.</li></ul></td></tr></tbody></table></div>

## 7.8. QT-07 — Điều trị nội trú & chăm sóc

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-07</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Điều trị nội trú &amp; chăm sóc</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-05</p><p>PH-06</p><p>PH-07</p><p>PH-15</p><p>PH-16</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-05 Bác sĩ điều trị</li><li>VT-22 Trưởng khoa</li><li>VT-09 Điều dưỡng</li><li>VT-10 ĐD trưởng</li><li>VT-15 Dược sĩ cấp phát</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Bệnh án nội trú đang mở, người bệnh đã có giường</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Diễn biến, y lệnh (thuốc/CLS/DVKT/chăm sóc/dinh dưỡng)</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Bác sĩ đi buồng, ghi diễn biến, ra y lệnh điện tử hằng ngày (CPOE).</p><p>2. Y lệnh thuốc → tổng hợp lĩnh thuốc theo khoa (QT-14); điều dưỡng thực hiện thuốc (eMAR) đúng 5 đúng.</p><p>3. Chỉ định CLS/DVKT → QT-04; chỉ định PTTT → QT-08; hội chẩn khi cần.</p><p>4. Điều dưỡng theo dõi sinh hiệu, thực hiện &amp; ghi phiếu chăm sóc theo phân cấp.</p><p>5. Ghi nhận chi phí thuốc/VTYT/DVKT theo thời gian thực (BR-009).</p><p>6. Đánh giá đáp ứng điều trị; điều chỉnh phác đồ; chuyển khoa (QT-09) nếu cần.</p><p>7. Khi đủ điều kiện → chuyển QT-10 ra viện.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Diễn biến nặng → chuyển hồi sức tích cực, kích hoạt y lệnh khẩn</li><li>Phản ứng thuốc/sự cố → ghi nhận sự cố, báo cáo KSNK/dược cảnh giác</li><li>Sai sót thực hiện thuốc → chặn/ghi nhận theo eMAR, cảnh báo trùng liều</li><li>Người bệnh xin về/trốn viện → ghi nhận theo quy định, tổng kết bệnh án phù hợp</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Bệnh án nội trú cập nhật (TT-06)</li><li>Bảng kê chi phí điều trị</li><li>Phiếu chăm sóc/thực hiện thuốc</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-004</li><li>BR-005</li><li>BR-007</li><li>BR-009</li><li>BR-011</li><li>BR-012</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-07.NT01: Y lệnh điện tử liên thông tới dược/CLS/điều dưỡng không phải nhập lại.</li><li>QT-07.NT02: eMAR ghi nhận đúng thời điểm thực hiện thuốc và cảnh báo sai sót.</li><li>QT-07.NT03: Toàn bộ chi phí phát sinh phản ánh vào bảng kê realtime.</li><li>QT-07.NT04: Diễn biến &amp; phiếu chăm sóc ký số, truy vết đầy đủ.</li></ul></td></tr></tbody></table></div>

## 7.9. QT-08 — Phẫu thuật – thủ thuật

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-08</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Phẫu thuật – thủ thuật (kèm gây mê hồi sức)</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-10</p><p>PH-12</p><p>PH-14</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-05 Bác sĩ điều trị</li><li>VT-22 Trưởng khoa</li><li>VT-07 Phẫu thuật viên</li><li>VT-08 Bác sĩ gây mê</li><li>VT-09 Điều dưỡng</li><li>VT-15 Dược sĩ</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Có chỉ định PTTT trên bệnh án; người bệnh đủ điều kiện</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Chỉ định PTTT, phương pháp, kíp mổ, dự trù thuốc/VTYT</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Tạo phiếu PTTT (TT-08); hội chẩn/duyệt mổ theo phân cấp.</p><p>2. Lập &amp; duyệt lịch mổ; bố trí phòng mổ, kíp, thiết bị.</p><p>3. Dự trù &amp; chuẩn bị thuốc/VTYT/máu (QT-14/QT-15).</p><p>4. Khám tiền mê; bàn giao người bệnh vào phòng mổ (checklist an toàn).</p><p>5. Thực hiện PTTT; ghi tường trình PT, hồ sơ gây mê, VTYT sử dụng (BR-009).</p><p>6. Xử trí sau mổ; chuyển hồi tỉnh/hồi sức; bàn giao về khoa.</p><p>7. Ký số hồ sơ PTTT (QT-13).</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Hoãn/hủy mổ → cập nhật lịch, hoàn trả dự trù thuốc/VTYT về kho</li><li>Phát sinh ngoài dự kiến (đổi phương pháp) → ghi nhận biến cố, bổ sung VTYT, cập nhật chi phí</li><li>Cần truyền máu khẩn → kích hoạt QT-15 phát máu khẩn, đối chiếu an toàn (BR-013)</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Hồ sơ PTTT hoàn chỉnh (TT-08)</li><li>Tường trình &amp; hồ sơ gây mê</li><li>Chi phí VTYT/thuốc PTTT</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-005</li><li>BR-006</li><li>BR-009</li><li>BR-012</li><li>BR-013</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-08.NT01: Lịch mổ, kíp mổ, phòng mổ được quản lý không xung đột.</li><li>QT-08.NT02: Checklist an toàn phẫu thuật bắt buộc trước khi rạch da.</li><li>QT-08.NT03: VTYT kỹ thuật cao ghi nhận đầy đủ theo người bệnh để thanh toán.</li><li>QT-08.NT04: Hồ sơ PTTT ký số, khóa và lưu trữ.</li></ul></td></tr></tbody></table></div>

## 7.10. QT-09 — Chuyển khoa / chuyển viện

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-09</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Chuyển khoa / chuyển viện</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-05</p><p>PH-19</p><p>PH-22</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-05 Bác sĩ điều trị</li><li>VT-22 Trưởng khoa</li><li>VT-24 KHTH</li><li>VT-09 Điều dưỡng</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Có chỉ định chuyển khoa hoặc chuyển tuyến</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Lý do chuyển, khoa/cơ sở tiếp nhận, tình trạng người bệnh</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Bác sĩ lập phiếu chuyển; duyệt theo phân cấp (trưởng khoa/KHTH).</p><p>2. Chuyển khoa: bàn giao bệnh án, cập nhật giường (TT-07), khoa mới tiếp nhận.</p><p>3. Chuyển viện: lập giấy chuyển tuyến, tổng kết điều trị, xuất dữ liệu tóm tắt.</p><p>4. Bàn giao thuốc/VTYT đang dùng; cập nhật chi phí đến thời điểm chuyển.</p><p>5. Cập nhật trạng thái lượt điều trị; ký số hồ sơ chuyển (QT-13).</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Cơ sở tiếp nhận từ chối → ghi nhận, tìm cơ sở khác hoặc giữ điều trị</li><li>Chuyển khẩn cấp → rút gọn thủ tục duyệt, hoàn thiện hồ sơ sau</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Phiếu chuyển khoa/tuyến</li><li>Bệnh án bàn giao</li><li>Cập nhật giường &amp; chi phí</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-002</li><li>BR-004</li><li>BR-005</li><li>BR-007</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-09.NT01: Chuyển khoa giải phóng &amp; gán giường chính xác, không mất dữ liệu bệnh án.</li><li>QT-09.NT02: Giấy chuyển tuyến sinh đúng mẫu, kèm tóm tắt điều trị.</li><li>QT-09.NT03: Chi phí chốt đến thời điểm chuyển; không phát sinh trùng.</li></ul></td></tr></tbody></table></div>

## 7.11. QT-10 — Ra viện & tổng kết bệnh án

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-10</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Ra viện &amp; tổng kết bệnh án</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-05</p><p>PH-17</p><p>PH-19</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-05 Bác sĩ điều trị</li><li>VT-22 Trưởng khoa</li><li>VT-09 Điều dưỡng</li><li>VT-03 Thu ngân</li><li>VT-20 Giám định BHYT</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Người bệnh đủ điều kiện ra viện</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Chẩn đoán ra viện, phương pháp điều trị, đơn ra viện, hẹn tái khám</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Bác sĩ lập tổng kết bệnh án &amp; giấy ra viện; kê đơn ra viện (nếu có).</p><p>2. Kiểm tra hoàn tất y lệnh, chi phí, hồ sơ; trưởng khoa duyệt.</p><p>3. Chốt bảng kê chi phí; đối chiếu tạm ứng; tất toán viện phí (QT-11).</p><p>4. Xác nhận dữ liệu BHYT phục vụ quyết toán (QT-12).</p><p>5. Ký số bộ hồ sơ bệnh án; khóa &amp; lưu trữ EMR (QT-13, BR-005).</p><p>6. Trả kết quả, giấy ra viện, hướng dẫn cho người bệnh; giải phóng giường.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Còn công nợ chưa thanh toán → ghi nhận công nợ, xử lý theo chính sách; không khóa nếu chờ quyết toán</li><li>Thiếu dữ liệu bắt buộc để ký/khóa → chặn khóa, liệt kê hạng mục thiếu để bổ sung</li><li>Ra viện đặc biệt (tử vong/xin về) → áp mẫu tổng kết tương ứng theo quy định</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Giấy ra viện &amp; tổng kết bệnh án</li><li>Bệnh án khóa &amp; lưu trữ (TT-11)</li><li>Tất toán viện phí</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-005</li><li>BR-006</li><li>BR-007</li><li>BR-009</li><li>BR-016</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-10.NT01: Không cho khóa bệnh án khi còn thiếu tài liệu/chữ ký bắt buộc.</li><li>QT-10.NT02: Bảng kê chi phí khớp toàn bộ dịch vụ/thuốc/VTYT đã dùng.</li><li>QT-10.NT03: Bệnh án ký số đầy đủ, khóa và không sửa được (chỉ đính chính có truy vết).</li><li>QT-10.NT04: Giải phóng giường và cập nhật trạng thái lượt 'Đã ra viện'.</li></ul></td></tr></tbody></table></div>

## 7.12. QT-11 — Viện phí & thanh toán

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-11</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Viện phí &amp; thanh toán (tạm ứng, thu phí, HĐĐT, không tiền mặt)</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-17</p><p>PH-13</p><p>PH-22</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-03 Thu ngân</li><li>VT-21 Kế toán viện phí</li><li>VT-27 Người bệnh</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Có chi phí phát sinh trên lượt điều trị</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Bảng kê dịch vụ/thuốc/VTYT, đối tượng thanh toán, mức hưởng BHYT</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Tổng hợp chi phí realtime theo lượt (TT-09); tách phần BHYT / tự chi trả.</p><p>2. Thu tạm ứng hoặc thu theo đợt/tất toán; hỗ trợ thanh toán không tiền mặt (TH-05).</p><p>3. Phát hành hóa đơn điện tử (TH-04) sau khi thu; gửi HĐĐT cho người bệnh.</p><p>4. Đối chiếu tạm ứng – phải thu – đã thu; xử lý hoàn/thu thêm.</p><p>5. Chốt công nợ &amp; doanh thu; đồng bộ kế toán.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Điều chỉnh hóa đơn sai sót → lập hóa đơn điều chỉnh/thay thế theo quy định HĐĐT</li><li>Hoàn phí (hủy dịch vụ) → tạo phiếu hoàn, cập nhật doanh thu &amp; tồn (nếu thuốc/VTYT)</li><li>Giao dịch không tiền mặt thất bại → hủy giao dịch, giữ trạng thái chờ, cho thử lại/đổi phương thức</li><li>Miễn/giảm viện phí → áp chính sách miễn giảm có phê duyệt, ghi nhận truy vết</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Phiếu thu/hóa đơn điện tử (TT-09)</li><li>Cập nhật công nợ &amp; doanh thu</li><li>Chứng từ đối soát</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-009</li><li>BR-010</li><li>BR-016</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-11.NT01: Chi phí tổng hợp đúng và tức thời theo mọi dịch vụ đã phát sinh.</li><li>QT-11.NT02: Phần BHYT/tự chi trả tính đúng theo mức hưởng.</li><li>QT-11.NT03: HĐĐT phát hành hợp lệ, gửi được cho người bệnh và tra cứu lại được.</li><li>QT-11.NT04: Thanh toán không tiền mặt đối soát khớp; xử lý được hoàn/điều chỉnh.</li></ul></td></tr></tbody></table></div>

## 7.13. QT-12 — Quyết toán BHYT (XML)

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-12</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Quyết toán BHYT (XML) &amp; đối soát cổng BHXH</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-18</p><p>PH-22</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-20 Giám định BHYT nội bộ</li><li>VT-21 Kế toán</li><li>VT-24 KHTH</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Đợt điều trị BHYT kết thúc; dữ liệu lâm sàng &amp; viện phí hoàn tất</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Dữ liệu KCB, chi phí, danh mục ánh xạ BHXH</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Sinh bộ hồ sơ XML quyết toán (TT-10) theo chuẩn cổng BHXH.</p><p>2. Kiểm tra tính đầy đủ/hợp lệ dữ liệu (BR-016); rà soát nội bộ.</p><p>3. Gửi XML lên cổng giám định BHXH (TH-03); nhận phản hồi.</p><p>4. Xử lý hồ sơ bị từ chối/xuất toán; bổ sung/giải trình; gửi lại.</p><p>5. Đối soát số duyệt – số đề nghị; chốt quyết toán kỳ.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Dữ liệu thiếu/không khớp → chặn gửi, liệt kê lỗi để bổ sung tại nguồn (lâm sàng/viện phí)</li><li>Hồ sơ bị xuất toán → ghi nhận lý do, quy trình giải trình &amp; gửi lại</li><li>Cổng BHXH gián đoạn → hàng đợi gửi lại tự động, cảnh báo vận hành</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Bộ XML quyết toán đã gửi (TT-10)</li><li>Kết quả giám định &amp; đối soát</li><li>Báo cáo quyết toán kỳ</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-008</li><li>BR-016</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-12.NT01: XML sinh đúng chuẩn, dữ liệu khớp lâm sàng – viện phí.</li><li>QT-12.NT02: Chặn gửi khi thiếu dữ liệu bắt buộc và chỉ rõ điểm lỗi.</li><li>QT-12.NT03: Ghi nhận &amp; xử lý được hồ sơ bị từ chối/xuất toán.</li><li>QT-12.NT04: Đối soát số duyệt – đề nghị chính xác theo kỳ.</li></ul></td></tr></tbody></table></div>

## 7.14. QT-13 — Bệnh án điện tử & ký số

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-13</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Bệnh án điện tử (EMR) &amp; ký số</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-19</p><p>PH-21</p><p>PH-22</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-04/VT-05 Bác sĩ</li><li>VT-09 Điều dưỡng</li><li>VT-22 Trưởng khoa</li><li>VT-25 Quản trị hệ thống</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Tài liệu lâm sàng được tạo trong quá trình KCB</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Tài liệu lâm sàng (phiếu khám, diễn biến, kết quả, tổng kết)</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Tổng hợp tài liệu lâm sàng vào hồ sơ EMR của lượt điều trị (TT-11).</p><p>2. Người có thẩm quyền ký số tài liệu (BR-006); hỗ trợ ký cá nhân &amp; ký theo phân cấp.</p><p>3. Khóa tài liệu sau ký; áp dấu thời gian; sinh log ký (BR-007).</p><p>4. Lưu trữ EMR theo quy định; phân quyền khai thác theo vai trò/phạm vi (BR-015).</p><p>5. Đính chính khi cần: tạo bản amendment có truy vết, giữ nguyên bản gốc (BR-005).</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Chữ ký số không hợp lệ/hết hạn CA → chặn ký, thông báo gia hạn chứng thư số</li><li>Yêu cầu sửa sau khóa → bắt buộc qua bản đính chính, không ghi đè bản gốc</li><li>Khai thác trái phạm vi → từ chối truy cập, ghi log truy cập bất thường</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Tài liệu EMR ký số &amp; khóa (TT-11)</li><li>Nhật ký ký/khai thác</li><li>Bản lưu trữ hợp lệ</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-005</li><li>BR-006</li><li>BR-007</li><li>BR-015</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-13.NT01: Chỉ tài liệu đã ký số hợp lệ mới được khóa &amp; công nhận pháp lý.</li><li>QT-13.NT02: Sau khóa không thể sửa nội dung; mọi thay đổi qua đính chính có truy vết.</li><li>QT-13.NT03: Mọi lượt xem/khai thác hồ sơ nhạy cảm được ghi log không sửa được.</li><li>QT-13.NT04: Phân quyền khai thác EMR theo đúng vai trò &amp; phạm vi.</li></ul></td></tr></tbody></table></div>

## 7.15. QT-14 — Kho Dược/VTYT/Hóa chất & cấp phát

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-14</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Quản lý kho Dược/VTYT/Hóa chất &amp; cấp phát</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-12</p><p>PH-11</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-16 Thủ kho</li><li>VT-15 Dược sĩ cấp phát</li><li>VT-14 Dược sĩ lâm sàng</li><li>VT-10 ĐD trưởng</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Danh mục thuốc/VTYT/HC &amp; kết quả thầu đã cấu hình</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Chứng từ nhập NCC, phiếu lĩnh khoa, dự trù, số liệu kiểm kê</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Nhập kho từ NCC theo kết quả thầu; ghi nhận lô, hạn dùng, số lượng (TT-12).</p><p>2. Điều chuyển nội bộ giữa các kho; pha chế/quy đổi (nếu có).</p><p>3. Tổng hợp lĩnh thuốc/VTYT theo khoa (từ y lệnh QT-07); duyệt &amp; xuất kho.</p><p>4. Cấp phát tới tủ trực/khoa; bù tủ trực theo định mức.</p><p>5. Xuất trả NCC/xuất khác; hủy thuốc thừa/hết hạn có phê duyệt.</p><p>6. Kiểm kê định kỳ; đối chiếu tồn sổ – tồn thực; xử lý chênh lệch.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Xuất vượt tồn → chặn giao dịch (BR-012), yêu cầu điều chuyển/nhập bổ sung</li><li>Hàng cận date/hết hạn → cảnh báo, ưu tiên xuất FEFO, lập biên bản hủy</li><li>Chênh lệch kiểm kê → lập biên bản, điều chỉnh có phê duyệt &amp; truy vết</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Chứng từ kho (TT-12)</li><li>Tồn kho cập nhật theo lô–hạn</li><li>Báo cáo xuất–nhập–tồn</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-003</li><li>BR-008</li><li>BR-009</li><li>BR-012</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-14.NT01: Mọi giao dịch kho cập nhật tồn theo lô–hạn chính xác, không cho âm tồn.</li><li>QT-14.NT02: Tổng hợp lĩnh khoa khớp y lệnh; xuất kho đúng số duyệt.</li><li>QT-14.NT03: Cảnh báo cận date/hết hạn và hỗ trợ FEFO.</li><li>QT-14.NT04: Kiểm kê đối chiếu và xử lý chênh lệch có truy vết.</li></ul></td></tr></tbody></table></div>

## 7.16. QT-15 — Ngân hàng máu

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-15</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Ngân hàng máu (tiếp nhận → truyền máu)</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-14</p><p>PH-08</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-18 KTV Ngân hàng máu</li><li>VT-11 KTV XN</li><li>VT-05 Bác sĩ điều trị</li><li>VT-09 Điều dưỡng</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Cấu hình danh mục nhóm máu/chế phẩm; kho máu hoạt động</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Đơn vị máu tiếp nhận, chỉ định truyền máu, nhóm máu người bệnh</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Tiếp nhận đơn vị máu/chế phẩm (TT-13); ghi mã túi, nhóm, hạn dùng.</p><p>2. Xét nghiệm sàng lọc (định nhóm, tác nhân lây truyền); phân loại đạt/loại.</p><p>3. Nhập kho máu đạt; quản lý theo nhóm – chế phẩm – hạn dùng.</p><p>4. Nhận chỉ định truyền máu; định nhóm &amp; phản ứng chéo (crossmatch) (BR-013).</p><p>5. Phát máu: đối chiếu người bệnh – đơn vị máu – chỉ định trước khi phát.</p><p>6. Truyền máu: điều dưỡng đối chiếu lần cuối tại giường, theo dõi phản ứng.</p><p>7. Ghi nhận kết quả truyền, phản ứng (nếu có); cập nhật tồn kho máu.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Đơn vị máu không đạt sàng lọc → loại bỏ theo quy định, lập biên bản hủy</li><li>Bất đồng nhóm/crossmatch dương → chặn phát, tìm đơn vị phù hợp khác</li><li>Phản ứng truyền máu → dừng truyền, xử trí, báo cáo sự cố &amp; lưu mẫu</li><li>Truyền máu khẩn cấp → quy trình phát máu khẩn có kiểm soát tối thiểu bắt buộc</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Kho máu cập nhật (TT-13)</li><li>Hồ sơ phát &amp; truyền máu</li><li>Báo cáo phản ứng (nếu có)</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-007</li><li>BR-012</li><li>BR-013</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-15.NT01: Không phát đơn vị máu chưa đạt sàng lọc hoặc bất đồng nhóm.</li><li>QT-15.NT02: Bắt buộc đối chiếu người bệnh – đơn vị máu tại thời điểm phát &amp; tại giường.</li><li>QT-15.NT03: Truy vết đầy đủ đường đi đơn vị máu từ tiếp nhận đến truyền.</li><li>QT-15.NT04: Ghi nhận &amp; báo cáo được phản ứng truyền máu.</li></ul></td></tr></tbody></table></div>

## 7.17. QT-16 — Nhà thuốc bán lẻ

<div class="joplin-table-wrapper"><table><tbody><tr><td><p><strong>Mã quy trình</strong></p></td><td><p>QT-16</p></td></tr><tr><td><p><strong>Tên quy trình</strong></p></td><td><p>Nhà thuốc bệnh viện – bán lẻ</p></td></tr><tr><td><p><strong>Phân hệ liên quan</strong></p></td><td><p>PH-13</p><p>PH-17</p><p>PH-22</p></td></tr><tr><td><p><strong>Tác nhân</strong></p></td><td><ul><li>VT-17 Dược sĩ nhà thuốc</li><li>VT-27 Khách hàng/Người bệnh</li></ul></td></tr><tr><td><p><strong>Điều kiện bắt đầu</strong></p></td><td><ul><li>Nhà thuốc có tồn kho; cấu hình giá bán &amp; HĐĐT</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu vào</strong></p></td><td><ul><li>Đơn thuốc ngoại trú hoặc yêu cầu mua lẻ</li></ul></td></tr><tr><td><p><strong>Luồng chính</strong></p></td><td><p>1. Tiếp nhận đơn/yêu cầu; kiểm tra tồn &amp; hạn dùng (BR-012).</p><p>2. Tư vấn/kiểm tra tương tác cơ bản với thuốc bán kèm (BR-011).</p><p>3. Lập hóa đơn bán lẻ; thu tiền (tiền mặt/không tiền mặt).</p><p>4. Phát hành hóa đơn điện tử (TH-04).</p><p>5. Xuất kho trừ tồn theo lô–hạn; in phiếu/hướng dẫn dùng.</p><p>6. Quản lý công nợ NCC &amp; nhập hàng bổ sung khi tồn thấp.</p></td></tr><tr><td><p><strong>Luồng ngoại lệ</strong></p></td><td><ul><li>Thuốc kê đơn nhưng không có đơn hợp lệ → từ chối bán thuốc kê đơn, yêu cầu đơn</li><li>Hết hàng → đề xuất thay thế hoặc hẹn nhập</li><li>Trả hàng/đổi → lập phiếu trả, điều chỉnh HĐĐT &amp; tồn</li></ul></td></tr><tr><td><p><strong>Dữ liệu đầu ra</strong></p></td><td><ul><li>Hóa đơn bán lẻ &amp; HĐĐT (TT-09)</li><li>Cập nhật tồn nhà thuốc</li><li>Doanh thu &amp; công nợ NCC</li></ul></td></tr><tr><td><p><strong>Quy tắc nghiệp vụ</strong></p></td><td><ul><li>BR-008</li><li>BR-009</li><li>BR-011</li><li>BR-012</li></ul></td></tr><tr><td><p><strong>Tiêu chí nghiệm thu</strong></p></td><td><ul><li>QT-16.NT01: Không bán thuốc kê đơn khi thiếu đơn hợp lệ.</li><li>QT-16.NT02: Bán hàng trừ tồn theo lô–hạn chính xác.</li><li>QT-16.NT03: Phát hành HĐĐT hợp lệ cho mỗi giao dịch.</li><li>QT-16.NT04: Báo cáo doanh thu &amp; tồn khớp giao dịch.</li></ul></td></tr></tbody></table></div>

# CHƯƠNG 8. BẢNG TRẠNG THÁI CÁC THỰC THỂ CHÍNH

Mỗi thực thể nghiệp vụ có một máy trạng thái xác định. Bảng dưới đây là chuẩn dùng chung; BRD chi tiết theo phân hệ có thể bổ sung trạng thái con nhưng không mâu thuẫn với chuẩn này.

## 8.1. TT-02 — Lượt tiếp nhận / khám

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT02-S01 | Chờ tiếp nhận | Đã lấy số, chưa đăng ký | S02, Hủy |
| TT02-S02 | Đã tiếp nhận | Đã tạo lượt, vào hàng đợi | S03 |
| TT02-S03 | Đang khám | Bác sĩ đang khám | S04, S05 |
| TT02-S04 | Chờ cận lâm sàng | Đang chờ kết quả CLS | S03 |
| TT02-S05 | Đã kết luận | Có chẩn đoán & hướng xử trí | S06, Nhập viện (TT06) |
| TT02-S06 | Chờ thanh toán | Chờ tất toán viện phí | S07 |
| TT02-S07 | Hoàn tất | Kết thúc lượt ngoại trú | —   |
| TT02-S08 | Hủy / Bỏ khám | Người bệnh không khám | —   |

## 8.2. TT-03 — Chỉ định cận lâm sàng / DVKT

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT03-S01 | Mới tạo | Bác sĩ vừa ra chỉ định | S02, Hủy |
| TT03-S02 | Chờ thu phí | Chờ thanh toán (ngoại trú DV) | S03, Hủy |
| TT03-S03 | Chờ thực hiện | Đã đủ điều kiện, chờ lấy mẫu/tiếp nhận | S04 |
| TT03-S04 | Đang thực hiện | Đang chạy XN/chụp | S05 |
| TT03-S05 | Có kết quả | Đã có kết quả thô | S06 |
| TT03-S06 | Đã duyệt kết quả | KTV/BS đã ký duyệt | S07 |
| TT03-S07 | Đã trả kết quả | Trả về hồ sơ khám/điều trị | —   |
| TT03-S08 | Hủy | Hủy chỉ định (có thể hoàn phí) | —   |

## 8.3. TT-05 — Đơn thuốc / Y lệnh thuốc

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT05-S01 | Nháp | Đang soạn | S02, Hủy |
| TT05-S02 | Đã kê | Bác sĩ ký kê đơn | S03, S04 |
| TT05-S03 | Chờ duyệt BHYT | Chờ dược sĩ/giám định duyệt | S04, Hủy |
| TT05-S04 | Chờ cấp phát | Đã duyệt, chờ phát thuốc | S05, S06 |
| TT05-S05 | Cấp phát một phần | Phát chưa đủ | S06 |
| TT05-S06 | Đã cấp phát | Phát đủ | —   |
| TT05-S07 | Hủy | Hủy đơn/thu hồi | —   |

## 8.4. TT-06 — Bệnh án nội trú

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT06-S01 | Chờ nhập khoa | Đã chỉ định nhập viện | S02 |
| TT06-S02 | Đang điều trị | Đang điều trị nội trú | S03, S04, S05 |
| TT06-S03 | Chuyển khoa | Đang chuyển khoa | S02 |
| TT06-S04 | Chờ ra viện | Đủ điều kiện ra viện | S05 |
| TT06-S05 | Đã ra viện | Ra viện/chuyển viện/tử vong | S06 |
| TT06-S06 | Đã khóa & lưu trữ | Ký số & khóa EMR | —   |

## 8.5. TT-07 — Giường bệnh

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT07-S01 | Trống | Sẵn sàng sử dụng | S02, S03 |
| TT07-S02 | Đã đặt | Đã giữ chỗ | S03, S01 |
| TT07-S03 | Đang sử dụng | Có người bệnh | S04 |
| TT07-S04 | Chờ vệ sinh | Vừa trả, chờ dọn | S01 |
| TT07-S05 | Bảo trì / Ngừng | Không khả dụng | S01 |

## 8.6. TT-09 — Phiếu thu / Hóa đơn

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT09-S01 | Tạm tính | Đang tổng hợp chi phí | S02 |
| TT09-S02 | Chờ thanh toán | Chờ thu | S03, S04 |
| TT09-S03 | Thanh toán một phần | Đã thu một phần | S04 |
| TT09-S04 | Đã thanh toán | Thu đủ | S05 |
| TT09-S05 | Đã phát hành HĐĐT | Đã xuất hóa đơn điện tử | S06, S07 |
| TT09-S06 | Điều chỉnh | HĐ điều chỉnh/thay thế | S05 |
| TT09-S07 | Hủy / Hoàn | Hủy hoặc hoàn phí | —   |

## 8.7. TT-10 — Hồ sơ quyết toán BHYT

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT10-S01 | Chưa gửi | XML đang chuẩn bị | S02, Lỗi |
| TT10-S02 | Đã gửi cổng | Đã đẩy cổng BHXH | S03 |
| TT10-S03 | Chờ giám định | Cổng tiếp nhận, chờ duyệt | S04, S05 |
| TT10-S04 | Được duyệt | Giám định chấp nhận | S06 |
| TT10-S05 | Từ chối / Xuất toán | Bị loại chi phí | S01 (bổ sung/gửi lại) |
| TT10-S06 | Đã quyết toán | Chốt quyết toán kỳ | —   |

## 8.8. TT-08 — Phiếu phẫu thuật – thủ thuật

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT08-S01 | Chỉ định | Có chỉ định PTTT | S02, Hủy |
| TT08-S02 | Chờ hội chẩn/duyệt | Chờ duyệt mổ | S03, Hủy |
| TT08-S03 | Đã lên lịch | Đã xếp lịch mổ | S04, Hoãn |
| TT08-S04 | Đang thực hiện | Đang PTTT | S05 |
| TT08-S05 | Hoàn tất | Kết thúc, đã tường trình | S06 |
| TT08-S06 | Đã ký & khóa | Ký số hồ sơ PTTT | —   |
| TT08-S07 | Hủy / Hoãn | Hủy hoặc hoãn mổ | S02 |

## 8.9. TT-11 — Tài liệu EMR (ký số)

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT11-S01 | Nháp | Đang soạn thảo | S02 |
| TT11-S02 | Chờ ký | Hoàn tất nội dung, chờ ký | S03 |
| TT11-S03 | Đã ký một phần | Ký theo phân cấp chưa đủ | S04 |
| TT11-S04 | Đã ký hoàn tất | Đủ chữ ký theo quy định | S05 |
| TT11-S05 | Khóa & lưu trữ | Không sửa được | S06 |
| TT11-S06 | Đính chính | Bản amendment có truy vết | S05 |

## 8.10. TT-13 — Đơn vị máu (Ngân hàng máu)

| **Mã** | **Trạng thái** | **Mô tả** | **Chuyển tiếp tới** |
| --- | --- | --- | --- |
| TT13-S01 | Tiếp nhận | Nhập đơn vị máu/chế phẩm | S02 |
| TT13-S02 | Chờ sàng lọc | Chờ xét nghiệm sàng lọc | S03, S04 |
| TT13-S03 | Đạt – Lưu kho | Đủ điều kiện lưu trữ | S05, Hết hạn |
| TT13-S04 | Loại bỏ | Không đạt sàng lọc | —   |
| TT13-S05 | Định danh/Đặt trước | Crossmatch cho người bệnh | S06, S03 |
| TT13-S06 | Đã phát | Phát cho khoa/truyền | S07 |
| TT13-S07 | Đã truyền / Hủy | Truyền xong hoặc hủy/hết hạn | —   |

# CHƯƠNG 9. MA TRẬN PHÂN QUYỀN THEO VAI TRÒ (RBAC)

Ma trận thể hiện quyền của từng nhóm vai trò trên các nhóm chức năng. Áp dụng nguyên tắc tối thiểu quyền (BR-015); phân quyền chi tiết cấp chức năng và phạm vi dữ liệu (khoa/phòng) do PH-21 cấu hình.

| **Ký hiệu** | **Ý nghĩa** |
| --- | --- |
| X   | Thực hiện / Nhập / Ghi (tạo, sửa dữ liệu nghiệp vụ) |
| R   | Chỉ xem (read-only) |
| A   | Duyệt / Ký / Phê duyệt (bao gồm quyền xem & thực hiện) |
| –   | Không có quyền |

_Chú thích cột nhóm vai trò: TĐ=Tiếp đón · TN=Thu ngân/Kế toán · BS=Bác sĩ · ĐD=Điều dưỡng · KTV=KTV CLS · DK=Dược/Kho · NHM=Ngân hàng máu · BH=Giám định BHYT · QL=Trưởng khoa/BGĐ/KHTH · QT=Quản trị HT · NB=Người bệnh._

| **Nhóm chức năng** | **TĐ** | **TN** | **BS** | **ĐD** | **KTV** | **DK** | **NHM** | **BH** | **QL** | **QT** | **NB** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Đăng ký / tiếp nhận | X   | R   | R   | R   | –   | –   | –   | R   | R   | A   | X   |
| Hàng đợi / lịch hẹn | X   | –   | R   | R   | –   | –   | –   | –   | R   | A   | X   |
| Khám & chẩn đoán | –   | –   | X   | R   | –   | –   | –   | R   | R   | –   | R   |
| Ra y lệnh / chỉ định (CPOE) | –   | –   | X   | R   | R   | R   | –   | R   | A   | –   | –   |
| Thực hiện CLS & duyệt KQ | –   | –   | R   | –   | X   | –   | –   | R   | R   | –   | R   |
| Kê đơn thuốc | –   | –   | X   | –   | –   | A   | –   | A   | R   | –   | R   |
| Thực hiện thuốc (eMAR) / chăm sóc | –   | –   | R   | X   | –   | –   | –   | –   | R   | –   | –   |
| Giường & nhập/xuất khoa | X   | –   | X   | X   | –   | –   | –   | –   | A   | R   | –   |
| Phẫu thuật / thủ thuật | –   | –   | X   | X   | –   | R   | –   | –   | A   | –   | –   |
| Kho & cấp phát dược/VTYT | –   | –   | R   | R   | –   | X   | –   | –   | A   | R   | –   |
| Nhà thuốc bán lẻ | –   | R   | –   | –   | –   | X   | –   | –   | R   | –   | –   |
| Ngân hàng máu | –   | –   | R   | X   | R   | –   | X   | –   | R   | –   | –   |
| Viện phí & thanh toán | R   | X   | –   | –   | –   | R   | –   | R   | R   | –   | X   |
| Quyết toán BHYT (XML) | –   | R   | –   | –   | –   | –   | –   | X   | A   | R   | –   |
| EMR: xem / khai thác | R   | –   | X   | X   | R   | –   | –   | R   | X   | R   | R   |
| EMR: ký số & khóa | –   | –   | A   | A   | A   | –   | –   | –   | A   | –   | –   |
| Danh mục dùng chung | –   | –   | –   | –   | –   | R   | –   | R   | R   | X   | –   |
| Quản trị người dùng & phân quyền | –   | –   | –   | –   | –   | –   | –   | –   | R   | X   | –   |
| Dashboard & báo cáo điều hành | –   | R   | R   | –   | –   | R   | –   | R   | X   | R   | –   |
| Nhật ký / Audit | –   | –   | –   | –   | –   | –   | –   | R   | R   | X   | –   |

_Ràng buộc phạm vi: Ma trận trên là mức nhóm vai trò. Người bệnh (NB) chỉ thao tác trên dữ liệu của chính mình qua cổng/kiosk. Quyền 'A' của Quản trị HT ở đăng ký/hàng đợi mang nghĩa cấu hình & giám sát, không thay người bệnh nhập liệu lâm sàng._

# CHƯƠNG 10. DANH SÁCH MÀN HÌNH UI THEO VỊ TRÍ TÁC NGHIỆP

Danh sách màn hình được tổ chức theo vị trí tác nghiệp nhằm tối ưu thao tác: mỗi vị trí có một không gian làm việc (workspace) gom các màn hình thường dùng, giảm số bước và số lần chuyển màn hình. Đây là danh sách đề xuất cấp nền tảng; wireframe chi tiết thuộc BRD & thiết kế UI/UX từng phân hệ.

## 10.1. Quầy tiếp đón & Cổng/Kiosk

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT** |
| --- | --- | --- | --- | --- |
| MH-TD-01 | Bảng lấy số / Kiosk STT | NB/VT-01 | Chọn dịch vụ, cấp STT, gọi số | QT-01 |
| MH-TD-02 | Đăng ký khám | VT-01 | Định danh, chọn phòng, tạo lượt, in phiếu | QT-01 |
| MH-TD-03 | Tra cứu / gộp hồ sơ | VT-01 | Tìm BN, phát hiện & gộp hồ sơ trùng | QT-01 |
| MH-TD-04 | Kiểm tra thẻ BHYT | VT-01 | Tra cứu trực tuyến, mức hưởng | QT-01 |
| MH-CO-01 | Cổng đăng ký trực tuyến/App | VT-27 | Đặt lịch, đăng ký, khai báo | QT-01 |
| MH-CO-02 | Tra cứu kết quả & thanh toán online | VT-27 | Xem KQ CLS, thanh toán, HĐĐT | QT-04, QT-11 |

## 10.2. Phòng khám & Cấp cứu

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT** |
| --- | --- | --- | --- | --- |
| MH-PK-01 | Hàng đợi phòng khám | VT-04/VT-09 | Danh sách chờ, gọi khám, ưu tiên | QT-03 |
| MH-PK-02 | Màn hình khám bệnh | VT-04 | Hỏi–khám, chẩn đoán ICD, tiền sử, dị ứng | QT-03 |
| MH-PK-03 | Chỉ định CLS/DVKT | VT-04 | Ra chỉ định, kiểm tra định mức, gửi LIS/RIS | QT-04 |
| MH-PK-04 | Kê đơn thuốc | VT-04 | Kê đơn, cảnh báo tương tác/dị ứng | QT-05 |
| MH-PK-05 | Đọc kết quả CLS | VT-04 | Xem KQ XN/CĐHA, hình ảnh PACS | QT-04 |
| MH-PK-06 | Kết luận & xử trí | VT-04 | Chốt chẩn đoán, kê đơn/nhập viện/hẹn | QT-03 |
| MH-CC-01 | Tiếp nhận cấp cứu nhanh | VT-06/VT-09 | Tạo lượt tối thiểu, triage | QT-02 |
| MH-CC-02 | Bảng theo dõi cấp cứu | VT-06/VT-09 | Theo dõi realtime, y lệnh khẩn | QT-02 |

## 10.3. Điều dưỡng & Nội trú

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT** |
| --- | --- | --- | --- | --- |
| MH-NT-01 | Sơ đồ buồng/giường | VT-01/VT-10 | Trạng thái giường, gán/đổi giường | QT-06 |
| MH-NT-02 | Bệnh án nội trú | VT-05 | Diễn biến, chẩn đoán, tổng kết | QT-07 |
| MH-NT-03 | Bảng y lệnh (CPOE) | VT-05 | Ra & theo dõi y lệnh ngày | QT-07 |
| MH-NT-04 | Tổng kết ra viện | VT-05 | Giấy ra viện, đơn ra viện, hẹn | QT-10 |
| MH-DD-01 | Danh sách chăm sóc/ca trực | VT-09/VT-10 | Phân công, việc cần làm theo ca | QT-07 |
| MH-DD-02 | Theo dõi sinh hiệu | VT-09 | Nhập sinh hiệu, biểu đồ | QT-07 |
| MH-DD-03 | Thực hiện thuốc (eMAR) | VT-09 | Xác nhận thực hiện, cảnh báo 5 đúng | QT-07 |
| MH-DD-04 | Phiếu chăm sóc | VT-09 | Ghi chăm sóc theo phân cấp | QT-07 |

## 10.4. Cận lâm sàng & Phòng mổ

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT** |
| --- | --- | --- | --- | --- |
| MH-XN-01 | Nhận mẫu & worklist XN | VT-11 | Nhận mẫu barcode, hàng chờ máy | QT-04 |
| MH-XN-02 | Nhập & duyệt kết quả XN | VT-11 | Kết nối máy, duyệt & ký, báo giá trị nguy kịch | QT-04 |
| MH-CD-01 | Worklist CĐHA | VT-12 | Danh sách chụp, gọi người bệnh | QT-04 |
| MH-CD-02 | Đọc & ký kết quả CĐHA | VT-13 | Đọc ảnh PACS, kết luận, ký số | QT-04 |
| MH-PM-01 | Lịch mổ & duyệt mổ | VT-07/VT-22 | Hội chẩn, duyệt, xếp lịch phòng mổ | QT-08 |
| MH-PM-02 | Tường trình PT & gây mê | VT-07/VT-08 | Ghi tường trình, hồ sơ gây mê, VTYT | QT-08 |
| MH-PM-03 | Checklist an toàn PT | VT-09 | Đối chiếu trước–trong–sau mổ | QT-08 |

## 10.5. Dược, Kho, Nhà thuốc, Ngân hàng máu, Dinh dưỡng

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT** |
| --- | --- | --- | --- | --- |
| MH-DU-01 | Duyệt đơn & cảnh báo dược | VT-14 | Duyệt đơn BHYT, cảnh báo lâm sàng | QT-05 |
| MH-DU-02 | Tổng hợp lĩnh / bù tủ trực | VT-15/VT-10 | Tổng hợp theo khoa, duyệt xuất | QT-14 |
| MH-KHO-01 | Nhập kho NCC | VT-16 | Nhập theo thầu, lô–hạn | QT-14 |
| MH-KHO-02 | Xuất/điều chuyển/kiểm kê | VT-16 | Xuất khoa, điều chuyển, kiểm kê, hủy | QT-14 |
| MH-KHO-03 | Báo cáo xuất–nhập–tồn | VT-16/VT-14 | Tồn theo lô–hạn, cận date | QT-14 |
| MH-NTH-01 | Bán lẻ nhà thuốc (POS) | VT-17 | Bán, HĐĐT, trừ tồn | QT-16 |
| MH-NHM-01 | Kho máu & sàng lọc | VT-18 | Tiếp nhận, sàng lọc, tồn theo nhóm | QT-15 |
| MH-NHM-02 | Phát & truyền máu | VT-18/VT-09 | Crossmatch, đối chiếu, phát, truyền | QT-15 |
| MH-DI-01 | Sàng lọc & chỉ định dinh dưỡng | VT-19 | Sàng lọc, hội chẩn, kê suất ăn | QT-07 |

## 10.6. Viện phí, BHYT, Điều hành, Quản trị

| **Mã MH** | **Màn hình** | **Vai trò** | **Chức năng chính** | **QT** |
| --- | --- | --- | --- | --- |
| MH-VP-01 | Thu tạm ứng / thu phí | VT-03 | Tạm ứng, thu, không tiền mặt | QT-11 |
| MH-VP-02 | Tất toán & hóa đơn điện tử | VT-03 | Tất toán, phát hành/điều chỉnh HĐĐT | QT-11 |
| MH-VP-03 | Công nợ & đối soát | VT-21 | Theo dõi công nợ, đối soát thanh toán | QT-11 |
| MH-BH-01 | Duyệt tuyến & định mức BHYT | VT-20 | Duyệt tuyến, kiểm tra điều kiện | QT-05, QT-12 |
| MH-BH-02 | Quản lý & gửi XML quyết toán | VT-20 | Sinh XML, kiểm tra, gửi cổng, đối soát | QT-12 |
| MH-DH-01 | Dashboard điều hành / KPI | VT-22/VT-23 | KPI realtime, cảnh báo, drill-down | PH-20 |
| MH-DH-02 | Báo cáo thống kê y tế | VT-24 | Báo cáo Bộ Y tế/BHXH, xuất biểu mẫu | PH-20 |
| MH-QT-01 | Quản lý danh mục dùng chung | VT-26 | Danh mục, ánh xạ BHXH | PH-21 |
| MH-QT-02 | Quản lý người dùng & vai trò | VT-25 | Tài khoản, vai trò, phân quyền | PH-21 |
| MH-QT-03 | Nhật ký & giám sát truy cập | VT-25 | Audit log, cảnh báo bất thường | PH-21 |

# CHƯƠNG 11. TIÊU CHÍ NGHIỆM THU NGHIỆP VỤ

Tiêu chí nghiệm thu gồm hai cấp: (1) tiêu chí theo từng quy trình (mã &lt;QT&gt;.NTxx tại Chương 7) và (2) tiêu chí nghiệm thu tổng thể (NTC) áp cho toàn hệ thống dưới đây. Nghiệm thu đạt khi tất cả tiêu chí bắt buộc PASS trong môi trường UAT với dữ liệu thực tế mô phỏng.

## 11.1. Tiêu chí nghiệm thu tổng thể

| **Mã** | **Nhóm** | **Tiêu chí nghiệm thu** | **Cách kiểm tra** |
| --- | --- | --- | --- |
| NTC-01 | Chức năng | Hoàn thành trọn vẹn luồng tiếp nhận → ra viện → quyết toán cho ≥1 ca ngoại trú, ≥1 ca nội trú, ≥1 ca cấp cứu, ≥1 ca có PTTT. | Kịch bản UAT đầu–cuối |
| NTC-02 | Dữ liệu | Không nhập lặp (BR-004); dữ liệu kế thừa đúng giữa các bước; một BN – một mã. | Đối chiếu dữ liệu qua các bước |
| NTC-03 | Danh mục | Chẩn đoán ICD-10 & thuốc/DVKT ánh xạ đúng danh mục BHXH. | Kiểm tra ánh xạ danh mục |
| NTC-04 | Tích hợp | Chỉ định/kết quả LIS/RIS/PACS, thẻ BHYT, HĐĐT, ký số hoạt động đúng end-to-end. | Kiểm thử tích hợp |
| NTC-05 | Viện phí | Chi phí realtime chính xác; tách BHYT/tự trả đúng; HĐĐT hợp lệ; đối soát khớp. | Đối chiếu bảng kê – hóa đơn |
| NTC-06 | BHYT | XML quyết toán đúng chuẩn, chặn gửi khi thiếu dữ liệu; xử lý xuất toán. | Gửi thử cổng/giả lập |
| NTC-07 | EMR & ký số | Tài liệu ký số hợp lệ, khóa không sửa; đính chính có truy vết. | Kiểm tra ký & khóa |
| NTC-08 | Phân quyền | Truy cập đúng ma trận RBAC; chặn truy cập trái phạm vi; log đầy đủ. | Kiểm thử phân quyền |
| NTC-09 | An toàn lâm sàng | Cảnh báo tương tác/dị ứng thuốc; an toàn truyền máu; FEFO kho. | Kịch bản cảnh báo |
| NTC-10 | Hiệu năng | ≥500 người dùng đồng thời; tác vụ thường <1s; báo cáo <5s; uptime ≥99,95%. | Kiểm thử tải & đo lường |
| NTC-11 | Bảo mật | Mã hóa dữ liệu nhạy cảm; audit log không sửa; phát hiện bất thường. | Rà soát bảo mật |
| NTC-12 | Báo cáo | Dashboard/KPI & báo cáo thống kê đúng số liệu nguồn. | Đối chiếu báo cáo – dữ liệu |

## 11.2. Điều kiện hoàn thành (Definition of Done) & UAT

- Mỗi quy trình QT-xx PASS toàn bộ tiêu chí &lt;QT&gt;.NTxx bắt buộc.
- Toàn bộ tiêu chí NTC-01…NTC-12 mức bắt buộc đạt PASS.
- Không tồn tại lỗi mức Blocker/Critical; lỗi Major có kế hoạch xử lý được chấp thuận.
- Người dùng nghiệp vụ đại diện mỗi vị trí tác nghiệp ký xác nhận UAT.
- Tài liệu vận hành, phân quyền và hướng dẫn sử dụng được bàn giao.

## 11.3. Ma trận truy vết quy trình – tiêu chí nghiệm thu

| **Quy trình** | **Số tiêu chí (QT.NT)** | **NTC liên quan** |
| --- | --- | --- |
| QT-01 Đăng ký & tiếp nhận | 4   | NTC-01,02,04 |
| QT-02 Cấp cứu | 4   | NTC-01,09 |
| QT-03 Khám ngoại trú | 4   | NTC-01,02,07 |
| QT-04 Chỉ định & CLS | 4   | NTC-04,09 |
| QT-05 Kê đơn & cấp phát | 4   | NTC-05,09 |
| QT-06 Nhập viện | 4   | NTC-01,02 |
| QT-07 Điều trị nội trú | 4   | NTC-02,09 |
| QT-08 PTTT | 4   | NTC-01,09 |
| QT-09 Chuyển khoa/viện | 3   | NTC-02 |
| QT-10 Ra viện & tổng kết | 4   | NTC-05,07 |
| QT-11 Viện phí | 4   | NTC-05 |
| QT-12 Quyết toán BHYT | 4   | NTC-06 |
| QT-13 EMR & ký số | 4   | NTC-07,08,11 |
| QT-14 Kho & cấp phát | 4   | NTC-09 |
| QT-15 Ngân hàng máu | 4   | NTC-09 |
| QT-16 Nhà thuốc | 4   | NTC-05 |

# CHƯƠNG 12. YÊU CẦU PHI CHỨC NĂNG (NFR)

| **Mã** | **Nhóm** | **Yêu cầu** |
| --- | --- | --- |
| NFR-01 | Hiệu năng | Tác vụ thông thường phản hồi <1s; báo cáo/thống kê <5s; đáp ứng tối thiểu 500 người dùng đồng thời. |
| NFR-02 | Khả dụng | Vận hành 24/7, uptime ≥99,95%; cơ chế HA, không có điểm chết đơn (SPOF). |
| NFR-03 | Mở rộng | Kiến trúc microservices, mở rộng ngang theo tải; tách dịch vụ độc lập. |
| NFR-04 | Bảo mật | Mã hóa khi lưu & truyền; xác thực tập trung (SSO), phân quyền RBAC/ABAC; audit log không sửa. |
| NFR-05 | Tin cậy dữ liệu | Sao lưu định kỳ, phục hồi có kiểm chứng (RPO/RTO mục tiêu); toàn vẹn giao dịch. |
| NFR-06 | Khả dụng vận hành | Giám sát hệ thống, cảnh báo, nhật ký tập trung, truy vết lỗi. |
| NFR-07 | Trải nghiệm | UI tối ưu theo vị trí tác nghiệp; hỗ trợ phím tắt, barcode/QR; thao tác tối thiểu. |
| NFR-08 | Tương thích | Nền tảng web đa trình duyệt; hỗ trợ thiết bị đầu cuối bệnh viện (máy in, kiosk, đầu đọc). |
| NFR-09 | Khả chuyển | Chuẩn dữ liệu mở; xuất/nhập theo HL7/FHIR; không khóa nhà cung cấp. |
| NFR-10 | Bảo trì | Tài liệu hóa; triển khai CI/CD; nâng cấp không gián đoạn dịch vụ trọng yếu. |

# CHƯƠNG 13. YÊU CẦU TÍCH HỢP

Các điểm tích hợp (TH) cốt lõi. Chi tiết hợp đồng dữ liệu/sự kiện thuộc BRD phân hệ PH-22.

| **Mã** | **Hệ thống / dịch vụ** | **Chuẩn/giao thức** | **Chiều dữ liệu** |
| --- | --- | --- | --- |
| TH-01 | LIS – Xét nghiệm | HL7 v2.x / API | Gửi chỉ định – nhận kết quả |
| TH-02 | RIS/PACS – CĐHA | HL7 / DICOM | Gửi chỉ định – nhận KQ & hình ảnh |
| TH-03 | Cổng giám định BHXH | XML / API cổng | Gửi hồ sơ – nhận kết quả giám định |
| TH-04 | Hóa đơn điện tử | API nhà cung cấp HĐĐT | Phát hành – tra cứu – điều chỉnh |
| TH-05 | Thanh toán không tiền mặt | API cổng thanh toán/ngân hàng | Khởi tạo – xác nhận – đối soát |
| TH-06 | Chữ ký số (CA) | PKI / NĐ130 | Ký số – kiểm tra hiệu lực |
| TH-07 | Định danh & thẻ BHYT | API tra cứu | Xác thực – tra cứu mức hưởng |
| TH-08 | EMR/HL7-FHIR liên thông | FHIR R4 | Trao đổi hồ sơ liên viện |
| TH-09 | Kho dữ liệu & BI | ETL / API | Đồng bộ dữ liệu phân tích |

# CHƯƠNG 14. TUÂN THỦ PHÁP LÝ & CHUẨN

| **Khía cạnh** | **Yêu cầu tuân thủ** |
| --- | --- |
| Khám chữa bệnh | Luật KBCB 15/2023 & TT32/2023: quy trình chuyên môn, quyền người bệnh, hồ sơ. |
| Bệnh án điện tử | TT13/2025: lập, ký số, lưu trữ, khai thác EMR; giá trị pháp lý thay hồ sơ giấy. |
| Chữ ký số | NĐ130/2018: ký số hợp lệ, dấu thời gian, kiểm tra hiệu lực chứng thư. |
| Bảo hiểm y tế | Quy định BHXH VN: danh mục dùng chung, quy tắc & định dạng XML quyết toán. |
| Hóa đơn điện tử | NĐ123/2020 & TT78: phát hành, điều chỉnh, lưu trữ HĐĐT. |
| Bảo vệ dữ liệu | NĐ13/2023: bảo vệ dữ liệu cá nhân; mã hóa & kiểm soát truy cập dữ liệu y tế. |
| Tiêu chuẩn tích hợp | HL7 v2.x, FHIR R4, DICOM cho liên thông và hình ảnh. |

# CHƯƠNG 15. DANH MỤC DÙNG CHUNG

Danh mục nền tảng dùng chung toàn viện (BR-003, BR-008); quản trị tập trung tại PH-21.

| **Nhóm danh mục** | **Ví dụ nội dung** |
| --- | --- |
| Hành chính | Đơn vị/khoa/phòng, nghề nghiệp, dân tộc, quốc gia, hành chính (tỉnh/huyện/xã). |
| Chuyên môn | ICD-10, danh mục DVKT, phẫu thuật/thủ thuật, phương pháp điều trị. |
| Dược & VTYT | Danh mục thuốc, hoạt chất, VTYT, hóa chất, đường dùng, đơn vị tính, hãng/NCC. |
| Bảo hiểm | Danh mục ánh xạ BHXH (thuốc/DVKT/VTYT), mức hưởng, tuyến. |
| Tài chính | Bảng giá dịch vụ, nhóm đối tượng, chính sách miễn giảm. |
| Hệ thống | Vai trò, nhóm quyền, loại tài liệu EMR, trạng thái, mẫu phiếu in. |

# CHƯƠNG 16. MA TRẬN TRUY VẾT & LỘ TRÌNH BRD THEO PHÂN HỆ

## 16.1. Ma trận truy vết yêu cầu

Ma trận liên kết Mục tiêu → Phân hệ → Quy trình → Tiêu chí nghiệm thu, bảo đảm mọi yêu cầu đều được hiện thực và kiểm thử.

| **Mục tiêu nghiệp vụ** | **Phân hệ** | **Quy trình** | **Nghiệm thu** |
| --- | --- | --- | --- |
| Số hóa tiếp nhận, giảm chờ | PH-01,02,23 | QT-01 | QT-01.NT\*, NTC-01 |
| Xử trí cấp cứu kịp thời | PH-04 | QT-02 | QT-02.NT\*, NTC-09 |
| Chuẩn hóa khám & chỉ định | PH-03,07,08,09 | QT-03,04 | NTC-01,04,09 |
| An toàn dùng thuốc | PH-11,12,13 | QT-05,14,16 | NTC-09 |
| Quản lý điều trị nội trú | PH-05,06,10 | QT-06,07,08,09 | NTC-01,02 |
| Ra viện & EMR pháp lý | PH-05,19 | QT-10,13 | NTC-07 |
| Minh bạch viện phí | PH-17 | QT-11 | NTC-05 |
| Đúng quyết toán BHYT | PH-18 | QT-12 | NTC-06 |
| An toàn truyền máu | PH-14 | QT-15 | NTC-09 |
| Điều hành dựa trên dữ liệu | PH-20 | Toàn hệ | NTC-12 |
| Bảo mật & tuân thủ | PH-21,22 | Toàn hệ | NTC-08,11 |

## 16.2. Lộ trình phân rã BRD chi tiết theo phân hệ

Từ tài liệu nền tảng này, mỗi phân hệ được phân rã thành một BRD chi tiết riêng, kế thừa mã định danh, quy trình, tác nhân, bảng trạng thái và tiêu chí nghiệm thu. Thứ tự đề xuất theo mức độ nền tảng và phụ thuộc:

| **Đợt** | **Nhóm phân hệ ưu tiên** | **Lý do** |
| --- | --- | --- |
| Đợt 1 | PH-21, PH-01, PH-02, PH-03, PH-17 | Nền tảng: danh mục/phân quyền, tiếp nhận, khám, viện phí |
| Đợt 2 | PH-07, PH-08, PH-09, PH-11, PH-12 | Chỉ định, CLS, dược & kho – trục lâm sàng |
| Đợt 3 | PH-05, PH-06, PH-10, PH-04 | Nội trú, điều dưỡng, PTTT, cấp cứu |
| Đợt 4 | PH-18, PH-19, PH-13, PH-14, PH-15, PH-16 | BHYT/quyết toán, EMR, nhà thuốc, NHM, dinh dưỡng, KSNK |
| Đợt 5 | PH-20, PH-22, PH-23 | Điều hành, tích hợp, cổng người bệnh |

## 16.3. Cấu trúc chuẩn của BRD chi tiết theo phân hệ

Mỗi BRD phân hệ áp dụng khung thống nhất để bảo đảm chất lượng và khả năng suy ra FRD/SRS/UI/API/testcase:

1\. Tổng quan phân hệ, mục tiêu, phạm vi, tác nhân (kế thừa VT-xx-xxx).

2\. Danh sách yêu cầu nghiệp vụ chi tiết (YCNV-&lt;HIS&gt;-xx-xxx-xxxx) kèm mức ưu tiên.

3\. Đặc tả quy trình chi tiết cấp thao tác (phân rã từ QT-xx-xxx).

4\. Đặc tả màn hình & trường dữ liệu (từ MH-xx-xxx), quy tắc validate.

5\. Bảng trạng thái chi tiết (kế thừa TT-xx-xxx), quy tắc chuyển trạng thái.

6\. Ma trận phân quyền chi tiết cấp chức năng & phạm vi dữ liệu.

7\. Yêu cầu tích hợp & dữ liệu của phân hệ.

8\. Tiêu chí nghiệm thu chi tiết & bộ test case gợi ý.

_Kết luận: Tài liệu nền tảng (Master BRD) và các BRD phân hệ tạo thành một bộ tài liệu truy vết khép kín: mọi mã định danh ở đây được kế thừa, không đánh lại, bảo đảm nhất quán xuyên suốt vòng đời dự án._

## 16.4. Kết luận

Tài liệu này thiết lập khung nghiệp vụ nền tảng đầy đủ cho hệ thống HIS: mã định danh chuẩn hóa, 16 quy trình đầu–cuối theo template, bảng trạng thái các thực thể chính, ma trận phân quyền theo vai trò, danh sách màn hình theo vị trí tác nghiệp và tiêu chí nghiệm thu nghiệp vụ. Đây là cơ sở vững chắc để triển khai lần lượt các BRD chi tiết theo từng phân hệ và suy ra các tài liệu FRD/SRS, thiết kế UI/UX, API, test case và kế hoạch triển khai.