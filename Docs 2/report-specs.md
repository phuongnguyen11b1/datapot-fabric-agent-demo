# Đặc tả Báo cáo (Report Specification) - VanArsdel

> **📝 Mô tả tổng quan:**
> Report Spec là bản thi công chi tiết dành riêng cho Data Analyst (DA). Tài liệu này dịch các yêu cầu kinh doanh trừu tượng thành các chỉ thị kỹ thuật cụ thể: từ việc bố cục trang báo cáo ra sao, dùng loại biểu đồ nào, cho đến công thức tính từng chỉ số (KPIs) và các bộ lọc (Filters) cần thiết. DA có thể build Dashboard mà không cần phải hỏi lại BA hoặc Stakeholder quá nhiều lần.

---

## 1. Mục đích & Khán giả (Purpose & Audience)
* **Khán giả (Audience):** Ban Giám đốc C-Level (CEO, CSO) và các Giám đốc Kinh doanh Vùng (Regional Sales Managers).
* **Hỗ trợ quyết định (Decisions supported):** 
  * Điều chỉnh hoặc phân bổ thêm ngân sách Marketing dựa trên nhóm sản phẩm đang bị hụt chỉ tiêu.
  * Đánh giá lại chiến lược giá và năng lực cạnh tranh khi quan sát sự biến động thị phần so với đối thủ.
  * Khen thưởng hoặc cải tổ hoạt động của các Vùng địa lý dựa trên hiệu suất doanh thu thực tế.
* **Tần suất cập nhật (Refresh):** Hàng tháng (Monthly - Hệ thống sẽ tự động nạp thêm các tệp dữ liệu Thực tế (Actuals) và Ngân sách (Budget) của tháng mới vào mô hình).

## 2. Các câu hỏi trọng tâm (Key Questions)
Báo cáo sau khi hoàn thiện phải giúp người xem trả lời ngay lập tức 4 câu hỏi sau:
1. Tổng doanh thu hiện tại là bao nhiêu và tiến độ hoàn thành ngân sách đang ở mức nào?
2. Thị phần (Market Share) của VanArsdel đang chiếm bao nhiêu phần trăm và xu hướng biến động ra sao so với đối thủ?
3. Nhóm sản phẩm (Category/Segment) nào đang mang lại nguồn thu tốt nhất và nhóm nào đang tụt hậu so với chỉ tiêu?
4. Khu vực địa lý (Bang/Thành phố) nào đang là thị trường trọng điểm mang lại doanh thu cao nhất?

## 3. Chỉ số đo lường (KPIs)
Danh sách các thước đo cốt lõi và công thức định nghĩa cơ bản để DA tạo Measure:

| Chỉ số (KPI) | Tên Measure hiển thị | Ghi chú & Định nghĩa |
| :--- | :--- | :--- |
| **Tổng doanh thu** | `[Total Revenue]` | Tổng giá trị bán hàng thực tế (Quy đổi tiền tệ USD). |
| **Tiến độ Ngân sách** | `[Budget Attainment]` | Tỷ lệ phần trăm hoàn thành. Công thức: Tổng doanh thu / Tổng ngân sách. |
| **% Thị phần** | `[Market Share]` | Công thức: Doanh thu của VanArsdel / Tổng doanh thu toàn thị trường (gồm cả đối thủ). |
| **Tăng trưởng YoY** | `[YoY Growth %]` | Tỷ lệ phần trăm tăng trưởng doanh thu so với cùng kỳ năm trước. |
| **Tổng sản lượng** | `[Total Units]` | Tổng số lượng sản phẩm vật lý được bán ra. |

## 4. Mức độ chi tiết & Chiều phân tích (Grain & Dimensions)
* **Hạt dữ liệu (Fact grain):** 
  * Bảng `Sales`: Ghi nhận ở cấp độ từng giao dịch (Transaction-level).
  * Bảng `Budget_Forecast`: Ghi nhận gộp ở cấp độ Nhóm sản phẩm theo Tháng (Segment-Category * Month).
* **Các chiều phân tích (Slicers/Dimensions):** 
  * Thời gian (Năm, Quý, Tháng).
  * Địa lý (Quốc gia -> Bang -> Thành phố -> Mã Zip).
  * Sản phẩm (Danh mục -> Phân khúc -> Sản phẩm).
  * Nhà sản xuất (Manufacturer).

## 5. Bố cục các trang báo cáo (Pages Layout)

### Trang 1 — Tổng quan (Executive Overview)
* **Thẻ số liệu (KPI Cards):** Hiển thị 4 chỉ số chính: Total Revenue, Budget Attainment, Market Share %, YoY Revenue Growth.
* **Biểu đồ xu hướng (Trend):** So sánh Doanh thu và Ngân sách theo Tháng. (Sử dụng biểu đồ Line and Clustered Column: Doanh thu thể hiện bằng cột, Ngân sách thể hiện bằng đường).
* **Phân tích cơ cấu (Breakdown 1):** Thị phần theo Nhà sản xuất. (Sử dụng biểu đồ Donut).
* **Phân tích cơ cấu (Breakdown 2):** Tổng doanh thu theo Danh mục sản phẩm (Category). (Sử dụng biểu đồ thanh ngang - Horizontal Bar).

### Trang 2 — Chi tiết Hiệu suất (Detail Performance)
* **Bảng ma trận (Matrix):** 
  * Hàng (Rows): Cây phân cấp Địa lý (Bang/Thành phố) hoặc Sản phẩm (Danh mục/Phân khúc).
  * Giá trị (Values): Total Revenue, Budget Attainment, Market Share %.
  * Định dạng có điều kiện (Conditional Formatting): Gắn cảnh báo Đỏ/Xanh lá cho cột Budget Attainment để nhận diện nhanh khu vực trượt chỉ tiêu.
* **Bản đồ (Map):** Hiển thị Tổng doanh thu theo từng Bang (Sử dụng Bubble Map - Bản đồ bong bóng, bong bóng càng to doanh thu càng lớn).

## 6. Bộ lọc (Filters)
* **Cấp độ Báo cáo (Report-level):** Năm (Mặc định chọn mức hiển thị là năm mới nhất trong dữ liệu).
* **Cấp độ Trang (Page-level cho Trang 1):** Lọc theo Bang (State) và Tháng (Month).
* **Cấp độ Trang (Page-level cho Trang 2):** Lọc theo Nhà sản xuất (Manufacturer) và Danh mục (Category).

## 7. Ghi chú thiết kế (Design Notes)
* Tất cả các trường dữ liệu liên quan đến `Revenue` và `Budget` phải được định dạng tiền tệ ($) chuẩn xác, có dấu phẩy phân cách hàng nghìn, không để số thập phân nếu không cần thiết.
* Thống nhất logic màu sắc xuyên suốt báo cáo: Màu nhận diện thương hiệu chính của VanArsdel áp dụng cho các khối hiển thị Doanh thu (Revenue). Đối với đường Ngân sách (Budget line), ưu tiên sử dụng màu xám/đen hoặc nét đứt để tạo sự tương phản dễ nhìn.