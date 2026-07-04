# UI Wireframe - VanArsdel Dashboard

> **Chú thích:** 
> Bản vẽ này phác thảo bố cục và vị trí đặt các biểu đồ cho Trang 1 (Executive Overview).

## Page 1: Executive Overview Layout

```text
+-----------------------------------------------------------------------+
|  [Logo VanArsdel]    EXECUTIVE OVERVIEW DASHBOARD                     |
|  -------------------------------------------------------------------  |
|  Filters:  [ Slicer: Year v ]  [ Slicer: Month v ]  [ Slicer: Geo v ] |
+-----------------------------------------------------------------------+
|                                                                       |
|  +----------------+  +-------------------+  +----------------------+  |
|  | TOTAL REVENUE  |  | BUDGET ATTAINMENT |  | VANARSDEL MKT SHARE  |  |
|  |   $ 54.2M      |  |      102.5%       |  |        34.2%         |  |
|  |  (vs Budget)   |  |   (Target: 100%)  |  |  (vs Competitors)    |  |
|  +----------------+  +-------------------+  +----------------------+  |
|                                                                       |
+-----------------------------------------+-----------------------------+
|                                         |                             |
|  REVENUE VS BUDGET TREND                |  MARKET SHARE BY COMPETITOR |
|  (Line & Clustered Column Chart)        |  (Donut Chart)              |
|                                         |                             |
|    |  [] Rev  -- Bud                    |          / \                |
|    |  []      []                        |        /     \              |
|    |  []      []      []                |       |       |             |
|    |  []      []      []                |        \     /              |
|    +------------------------            |          \ /                |
|       Jan     Feb    Mar                |    (VanArsdel vs Others)    |
|                                         |                             |
+-----------------------------------------+-----------------------------+
|                                                                       |
|  REVENUE BREAKDOWN BY CATEGORY                                        |
|  (Horizontal Bar Chart)                                               |
|                                                                       |
|  Urban  |==============================                               |
|  Rural  |==================                                           |
|  Mix    |========                                                     |
|                                                                       |
+-----------------------------------------------------------------------+
```

### Chú thích Data cho Trang 1:
1. **Khối Filters (Trên cùng):** Dùng dữ liệu từ bảng `Date` và bảng `Geo`.
2. **Khối KPI Cards (Hàng 1):** Gọi 3 measures chính: `[Total Revenue]`, `[Budget Attainment]`, `[Market Share]`.
3. **Biểu đồ Trend (Giữa trái):** 
   * Trục X: Cột `Month` (bảng Date).
   * Cột (Column): Measure `[Total Revenue]`.
   * Đường (Line): Measure `[Total Budget]`.
4. **Biểu đồ Market Share (Giữa phải):** 
   * Legend (Chú giải): Cột `Manufacturer`.
   * Values: Measure `[Total Revenue]`.
5. **Biểu đồ Revenue Breakdown (Dưới cùng):**
   * Trục Y: Cột `Category` (bảng Product).
   * Trục X: Measure `[Total Revenue]`.