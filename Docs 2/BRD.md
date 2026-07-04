# Business Requirements Document (BRD)

**Project:** VanArsdel Sales & Market Share Dashboard

> **Tổng quan tài liệu:**
> Tài liệu này xác định rõ yêu cầu nghiệp vụ của dự án báo cáo VanArsdel. Nó định nghĩa đối tượng sử dụng, các quyết định kinh doanh cần đưa ra, bộ chỉ tiêu đo lường (KPI) và khoanh vùng phạm vi dự án để đội ngũ kỹ thuật bám sát khi phát triển.

---

## 1. Đối tượng người dùng (Target Users)

Báo cáo này được thiết kế để phục vụ 2 nhóm người dùng chính:

- **C-Level Executive (Ban Giám đốc):** Giám đốc điều hành (CEO), Giám đốc Kinh doanh (CSO). Họ cần cái nhìn tổng quan ở mức độ cao về tình hình doanh nghiệp, đặc biệt là so sánh với đối thủ cạnh tranh.
- **Regional Managers (Quản lý vùng):** Những người chịu trách nhiệm cho từng khu vực địa lý cụ thể. Họ cần đi sâu vào chi tiết để xem vùng của mình quản lý, danh mục sản phẩm nào đang bán chạy hoặc bị chậm so với chỉ tiêu.

## 2. Mục đích & Quyết định kinh doanh (Decisions)

Dashboard này được xây dựng để hỗ trợ Stakeholder đưa ra các quyết định hành động:

- **Điều phối ngân sách Marketing & Bán hàng:** Xác định nhóm sản phẩm (Segment/Category) đang hụt chỉ tiêu (Budget) để tăng cường ngân sách quảng cáo hoặc tung khuyến mãi kịp thời.
- **Chiến lược cạnh tranh:** Đánh giá xem VanArsdel đang giành được hay đánh mất thị phần vào tay đối thủ nào (Natura, Pirum...), từ đó điều chỉnh chiến lược giá hoặc ra mắt sản phẩm mới.
- **Đánh giá hiệu suất Vùng:** Khen thưởng hoặc tái cấu trúc hoạt động tại các Bang/Thành phố có hiệu suất bán hàng kém.

## 3. Câu hỏi nghiệp vụ (Key Business Questions)

Dashboard cần phải trả lời được các câu hỏi trọng tâm sau:

1. Tổng doanh thu (Revenue) hiện tại của VanArsdel là bao nhiêu? Tiến độ hoàn thành mục tiêu (Budget Attainment) đang ở mức nào?
2. Thị phần (Market Share) của chúng ta đang chiếm bao nhiêu phần trăm toàn thị trường? Xu hướng thị phần đang tăng hay giảm so với tháng trước/năm trước?
3. Phân khúc (Segment) và Danh mục (Category) sản phẩm nào đang mang lại doanh thu cao nhất? Nhóm nào đang hụt ngân sách nhiều nhất?
4. Đâu là khu vực địa lý (Bang, Thành phố) có mức tăng trưởng doanh thu tốt nhất?

## 4. KPIs & Định nghĩa Metrics (KPIs & Metrics Definition)

Bộ chỉ số đo lường chính bao gồm:

- **Total Revenue (USD):** Tổng doanh thu bán hàng thực tế của riêng VanArsdel.
- **Budget Attainment (%):** Tỷ lệ phần trăm hoàn thành kế hoạch.
  - _Công thức:_ `Total Revenue / Total Budget`. (Cần đạt > 100% là tốt).
- **VanArsdel Market Share (%):** Tỷ trọng doanh thu của VanArsdel trên toàn thị trường.
  - _Công thức:_ `VanArsdel Revenue / (VanArsdel Revenue + Competitors Revenue)`.
- **YoY Revenue Growth (%):** Tỷ lệ tăng trưởng doanh thu năm nay so với cùng kỳ năm trước.

## 5. Giả định & Phạm vi dự án (Assumptions & Scope)

### In-Scope (Trong phạm vi triển khai)

- Phân tích doanh số bán hàng từ năm 2015 đến năm có dữ liệu thực tế gần nhất.
- So sánh Actuals vs Budget ở cấp độ `Segment-Category` và cấp độ `Month/Year`.
- Phân tích thị phần cạnh tranh theo thời gian và khu vực địa lý.

### Out-of-Scope (Ngoài phạm vi triển khai)

- **KHÔNG** phân tích lợi nhuận ròng (Net Profit) hay chi phí vận hành (Operating Costs) do dữ liệu đầu vào không cung cấp các yếu tố cấu thành chi phí.
- **KHÔNG** đi sâu phân tích ở cấp độ nhân viên bán hàng cá nhân hay hồ sơ khách hàng đơn lẻ.

### Assumptions (Giả định nghiệp vụ)

- Hệ thống mặc định dữ liệu bán hàng của Đối thủ thu thập được là chính xác và đã bao phủ đầy đủ toàn thị trường mục tiêu.
- Phân cấp sản phẩm (Category -> Segment) là cấu trúc chuẩn và không thay đổi hồi tố trong các năm tài chính.
