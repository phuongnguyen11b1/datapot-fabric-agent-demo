# 📊 Dự án: Hệ thống Báo cáo Quản trị VanArsdel Retail (Data Analytics & Dashboard)

## Tóm tắt dự án & Cách tiếp cận
Dự án này nhằm xây dựng một hệ thống báo cáo (Dashboard) cho VanArsdel Retail, giúp Ban giám đốc (C-Level) và Quản lý vùng theo dõi hiệu suất bán hàng, đo lường tỷ lệ hoàn thành ngân sách và giám sát thị phần so với các đối thủ cạnh tranh.

Cách tiếp cận của dự án tuân theo quy trình:
1. **Khám phá & Chuẩn hóa:** Bắt đầu từ việc bóc tách dữ liệu thô và thống nhất ngôn ngữ kinh doanh chung.
2. **Xác định yêu cầu:** Đặt câu hỏi khai thác các điểm mờ của dữ liệu, chốt mục tiêu kinh doanh với Stakeholder.
3. **Đặc tả & Thiết kế:** Chuyển hóa yêu cầu nghiệp vụ thành "bản vẽ thi công" chi tiết (kỹ thuật & giao diện) để bàn giao cho đội ngũ Data Engineer / Data Analyst.

## Thứ tự đọc tài liệu (Reading Order)
Để nắm bắt toàn cảnh dự án một cách logic nhất, vui lòng đọc các tài liệu được đính kèm theo thứ tự sau:

### Phần 1: Nền tảng Dữ liệu & Nghiệp vụ
1. **[Business Glossary](business-glossary.md):** Định nghĩa các khái niệm kinh doanh cốt lõi (Hierarchy, Market Share, Campaign...).
2. **[Data Dictionary](data-dictionary.md):** Cấu trúc kỹ thuật của các bảng (Fact/Dimension), hạt dữ liệu (Grain) và công thức tính KPIs.
3. **[Data Gaps & Stakeholder Questions](data-gaps.md):** Các điểm bất cập trong dữ liệu hiện tại và những vấn đề cần Ban giám đốc quyết định trước khi xây dựng model.

### Phần 2: Đặc tả Bàn giao (Hand-off Specifications)
4. **[BRD (Business Requirements Document)](BRD.md):** Tài liệu chốt yêu cầu nghiệp vụ, định nghĩa người dùng mục tiêu, quyết định kinh doanh và phạm vi dự án (Scope).
5. **[Report Specification](report-spec.md):** Bản đặc tả kỹ thuật chi tiết hướng dẫn DA cách xây dựng các trang báo cáo, loại biểu đồ và luồng Filter.
6. **[UI Wireframe](wireframe.md):** Bản phác thảo bố cục giao diện trực quan (Layout) của Dashboard.
