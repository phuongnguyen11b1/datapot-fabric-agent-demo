# Data Gaps & Stakeholder Questions

> **Tổng quan nội dung:** 
> Bất kỳ bộ dữ liệu thực tế nào cũng sẽ có những điểm mờ, thiếu sót hoặc không đồng nhất. Tài liệu này tổng hợp các "lỗ hổng" (Data Gaps) được phát hiện trong quá trình phân tích file thô, kèm theo các câu hỏi cần Stakeholder (Ban Giám đốc/Khách hàng) xác nhận trước khi Data Analyst bắt tay vào xây dựng Dashboard. Việc này giúp tránh tình trạng làm xong phải đập đi xây lại.
>
> **Cách tổ chức trình bày:** 
> Danh sách được đánh số thứ tự, chia thành 2 phần rõ ràng: Nêu vấn đề của dữ liệu và Câu hỏi chốt (Điều cần Stakeholder quyết định).

---

### 1. Sự chênh lệch về mức độ chi tiết (Granularity Mismatch)
* **Vấn đề:** Trong bảng `Sales` (Actuals), dữ liệu được ghi nhận cực kỳ chi tiết đến từng *Ngày (Day)* và từng *Mã sản phẩm (ProductID)*. Tuy nhiên, trong bảng `Budget_Forecast`, mục tiêu lại chỉ được giao ở cấp độ gộp là *Tháng (Month)* và *Cụm Phân khúc - Danh mục (Segment-Category)*.
* **Câu hỏi cho Stakeholder:** 
  1. Khi xem báo cáo so sánh Thực tế vs. Ngân sách (Budget Attainment), Stakeholder có đồng ý rằng chúng ta chỉ có thể xem ở cấp độ **Tháng** và cấp độ **Segment/Category** không? 
  2. Nếu người dùng cố tình filter báo cáo theo một Mã sản phẩm cụ thể (ProductID), biểu đồ ngân sách sẽ không hiển thị (hoặc hiển thị sai). Stakeholder có chấp nhận giới hạn kỹ thuật này không?

### 2. Định nghĩa chính xác về "Revenue"
* **Vấn đề:** Bảng `Sales` đã có sẵn cột `Revenue`. Tuy nhiên, không có từ điển nào ghi chép lại cách con số này được tạo ra từ hệ thống gốc.
* **Câu hỏi cho Stakeholder:** Con số `Revenue` này là Doanh thu gộp (Gross Revenue) hay Doanh thu thuần (Net Revenue)? Nó đã bao gồm thuế (Tax) và đã trừ đi các khoản chiết khấu/khuyến mãi (Discounts) chưa?

### 3. Phạm vi thời gian (Timeframe) & So sánh YoY
* **Vấn đề:** Dữ liệu Actuals có từ năm 2015 đến 2020. Tuy nhiên, cần xác nhận lại khoảng thời gian bao phủ của file Budget. Nếu Budget chỉ có của năm 2020, chúng ta sẽ không thể tính tỷ lệ hoàn thành ngân sách cho các năm trước.
* **Câu hỏi cho Stakeholder:** Yêu cầu Dashboard cần hiển thị dữ liệu lịch sử từ năm nào? Đối với những năm trong quá khứ không có dữ liệu Budget, chúng ta sẽ ẩn các biểu đồ so sánh ngân sách đi, hay Stakeholder sẽ cung cấp thêm file dữ liệu Budget bổ sung?

### 4. Tính toàn vẹn của dữ liệu Đối thủ (Competitor Data)
* **Vấn đề:** Hệ thống ghi nhận cả doanh thu của các Nhà sản xuất khác (Natura, Pirum...) để tính Thị phần (Market Share).
* **Câu hỏi cho Stakeholder:** Dữ liệu bán hàng của đối thủ được thu thập từ nguồn nào và có độ trễ (latency) bao lâu so với dữ liệu nội bộ của VanArsdel? Điều này quan trọng để ghi chú vào Dashboard, giúp người xem không bị hiểu lầm khi thấy Thị phần có sự biến động bất thường ở những ngày gần nhất.