# Data Dictionary (VanArsdel)

> **Tổng quan nội dung:** 
> Tài liệu này quy định cấu trúc các bảng (Tables) sẽ được nạp vào Power BI. Nó giúp Data Analyst biết chính xác bảng nào là Fact (chứa số liệu giao dịch), bảng nào là Dimension (chứa thông tin phân tích), cột nào dùng để liên kết (Key) và cần áp dụng kiểu dữ liệu (Data Type) gì cho đúng.
>
> **Cách tổ chức trình bày:** 
> Tài liệu chia làm 2 phần chính:
> 1. **Các bảng dữ liệu (Tables):** Mỗi bảng được mô tả `Grain` (hạt dữ liệu - mức độ chi tiết của 1 dòng) và liệt kê chi tiết từng cột (Ý nghĩa, Kiểu dữ liệu, Khóa chính/Khóa ngoại).
> 2. **Các chỉ số (Measures):** Danh sách các công thức tính toán (DAX) cần tạo dùng chung cho toàn bộ Dashboard.
>
> **Quy ước (Conventions):**
> * **Model Name:** Tên cột sau khi đã đổi tên cho thân thiện với người dùng (hiển thị trên báo cáo).
> * **Source Column:** Tên cột gốc trong file Excel thô.
> * **Type:** Kiểu dữ liệu (`int64` = số nguyên, `double` = số thập phân, `string` = chữ/văn bản, `dateTime` = ngày tháng).
> * **Key:** `PK` (Primary Key - Khóa chính), `FK` (Foreign Key - Khóa ngoại).
> * **Hidden:** Có ẩn cột này khỏi góc nhìn của người dùng (End-user) hay không.

---

## 1. Tables

### Table: Date (Dimension)
* **Grain:** Mỗi dòng tương ứng với một ngày cụ thể trong lịch (từ 2015 đến 2020+).
* **Source file:** `VanArsdel_Actuals.xlsx` (Sheet: Date)

| Model Name | Source Column | Type | Key | Hidden | Description | Example |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Date | Date | dateTime | PK | no | Ngày giao dịch cụ thể | 2015-01-01 |
| Year | Year | int64 | - | no | Năm dương lịch | 2015 |
| Month | Month | string | - | no | Tên tháng (dùng để hiển thị) | Jan, Feb |
| Month Number | MonthNum | int64 | - | yes | Số thứ tự tháng (dùng để sắp xếp) | 1, 2 |

### Table: Product (Dimension)
* **Grain:** Mỗi dòng tương ứng với một mã định danh sản phẩm duy nhất.
* **Source file:** `VanArsdel_Actuals.xlsx` (Sheet: Product)

| Model Name | Source Column | Type | Key | Hidden | Description | Example |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Product ID | ProductID | string | PK | yes | Mã định danh hệ thống của sản phẩm | PRD01 |
| Product Name | Product | string | - | no | Tên sản phẩm cụ thể | Maximus UM-43 |
| Manufacturer | Manufacturer | string | - | no | Nhà sản xuất (VanArsdel hoặc Đối thủ) | VanArsdel, Natura |
| Category | Category | string | - | no | Nhóm danh mục chính | Urban, Mix |
| Segment | Segment | string | - | no | Phân khúc chi tiết | Convenience |

### Table: Geo (Dimension)
* **Grain:** Mỗi dòng tương ứng với một khu vực địa lý cụ thể (phân biệt bằng mã Zip).
* **Source file:** `VanArsdel_Actuals.xlsx` (Sheet: Geo)

| Model Name | Source Column | Type | Key | Hidden | Description | Example |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Zip | Zip | string | PK | yes | Mã bưu chính / Vùng | 10001 |
| City | City | string | - | no | Tên Thành phố | New York |
| State | State | string | - | no | Tên Bang / Tỉnh | NY |
| Country | Country | string | - | no | Quốc gia | USA |

### Table: Campaign (Dimension)
* **Grain:** Mỗi dòng tương ứng với một chiến dịch tiếp thị duy nhất.
* **Source file:** `VanArsdel_Actuals.xlsx` (Sheet: Campaign)

| Model Name | Source Column | Type | Key | Hidden | Description | Example |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Campaign ID | CampaignID | string | PK | yes | Mã định danh chiến dịch | CMP-001 |
| Campaign Name | Campaign | string | - | no | Tên chiến dịch tiếp thị | Summer Sale |

### Table: Customer (Dimension)
* **Grain:** Mỗi dòng tương ứng với một hồ sơ khách hàng.
* **Source file:** `VanArsdel_Actuals.xlsx` (Sheet: Customer)

| Model Name | Source Column | Type | Key | Hidden | Description | Example |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Customer ID | CustomerID | string | PK | yes | Mã định danh khách hàng | CUST-1029 |
| Customer Name | Name | string | - | no | Tên đầy đủ của khách hàng | John Doe |

### Table: Sales (Fact)
* **Grain:** Mỗi dòng tương ứng với một giao dịch bán hàng của một Sản phẩm, tại một Khu vực, trong một Ngày.
* **Source file:** `VanArsdel_Actuals.xlsx` (Sheet: Sales)

| Model Name | Source Column | Type | Key | Hidden | Description | Example |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Date | Date | dateTime | FK | yes | Liên kết tới bảng Date | 2015-01-05 |
| Product ID | ProductID | string | FK | yes | Liên kết tới bảng Product | PRD01 |
| Zip | Zip | string | FK | yes | Liên kết tới bảng Geo | 10001 |
| Units | Units | int64 | - | yes | Số lượng sản phẩm bán ra | 5 |
| Revenue | Revenue | double | - | yes | Tổng doanh thu của giao dịch đó | 150.50 |

### Table: Budget_Forecast (Fact)
* **Grain:** Mỗi dòng tương ứng với mục tiêu Ngân sách hoặc Dự báo của một Nhóm sản phẩm (Segment-Category) trong một Tháng cụ thể.
* **Source file:** `VanArsdel_Budget_Forecast.xlsx` *(Lưu ý: DA cần dùng Power Query để unpivot dữ liệu dạng Wide thành dạng Tidy bảng này trước khi đưa vào mô hình).*

| Model Name | Source Column | Type | Key | Hidden | Description | Example |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Date | *Calculated* | dateTime | FK | yes | Ngày đầu tháng (Ghép từ cột Year và Month) | 2020-01-01 |
| Product Group | Segment-Category | string | FK | yes | Mã nhóm SP để nối với Dimension tương ứng | Urban-Convenience |
| Type | Type | string | - | no | Phân loại dòng dữ liệu: Budget hoặc Forecast | Budget |
| Target Value | *Unpivoted Val*| double | - | yes | Giá trị ngân sách/dự báo đã unpivot | 50000.00 |

---

## 2. Measures (Tất cả gom vào bảng [Key Measures])

| Measure | Folder | Format | DAX (Pseudo-code) | Definition |
| :--- | :--- | :--- | :--- | :--- |
| Total Units | 1. Actuals | #,##0 | `SUM(Sales[Units])` | Tổng số lượng hàng hóa bán ra thực tế. |
| Total Revenue | 1. Actuals | $#,##0.00 | `SUM(Sales[Revenue])` | Tổng doanh thu thực tế. |
| Total Budget | 2. Targets | $#,##0.00 | `CALCULATE(SUM(Value), Type = "Budget")` | Tổng ngân sách mục tiêu. |
| Total Forecast | 2. Targets | $#,##0.00 | `CALCULATE(SUM(Value), Type = "Forecast")` | Tổng dự báo doanh thu. |
| Budget Attainment | 3. Variances | 0.0% | `DIVIDE([Total Revenue], [Total Budget])` | Tỷ lệ % hoàn thành so với ngân sách. |