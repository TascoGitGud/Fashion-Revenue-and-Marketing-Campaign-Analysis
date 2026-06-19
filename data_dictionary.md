# 📖 Data Dictionary - Fashion Marketing & Sales Analysis Dataset

## 📂 Overview

The dataset contains **4 main tables** covering e-commerce orders, product catalog, and marketing campaign performance (Facebook/Meta Ads) for a fashion retail business.

| Table (Sheet Name) | Rows | Description |
|---|---|---|
| `order` | 3,451 | Transaction-level order/order-line data |
| `danh sach san pham` | 2,250 | Product catalog / master product list |
| `mkt_camp_cost` | 854 | Daily marketing campaign cost & performance (campaign level) |
| `mkt_camp_by_sku_cost` | 3,874 | Marketing campaign performance broken down by product/SKU |

---

## 1️⃣ Table: `order`

Order/transaction line-level data. One row = one product line within a customer order.

| Column Name | Data Type | Description |
|---|---|---|
| `ID` | Integer | Unique order ID |
| `Thời gian` | Datetime | Order date & time |
| `Nguồn` | Text | Order source/channel (e.g., Admin) |
| `Tên khách hàng` | Text | Customer name |
| `Mã khách hàng` | Number | Customer ID (mostly blank) |
| `Cấp độ khách hàng` | Text | Customer tier (Membership, Silver VIP, Gold VIP, Platinum VIP, Diamond VIP) |
| `Sinh nhật` | Date | Customer date of birth |
| `Thành phố` | Text | Customer's city |
| `Quận huyện` | Text | Customer's district |
| `Phường xã` | Text | Customer's ward/commune |
| `Sản phẩm` | Text | Product name + variant (size), e.g., "*Malina Skirt - XS" |
| `Mã sản phẩm cha` | Text | Parent product code |
| `Tên sản phẩm cha` | Text | Parent product name (without size variant) |
| `Mã sản phẩm` | Text | Product/SKU code (incl. size), used as join key to `danh sach san pham` |
| `Mã vạch` | Integer | Product barcode |
| `Danh mục sản phẩm` | Text | Product category at time of order |
| `Chiết khấu` | Number | Discount amount applied (VND) |
| `Giá` | Integer | Selling price of the order line (VND) |
| `Số lượng` | Integer | Quantity ordered |
| `Giá vốn` | Integer | Cost of goods (COGS) for the order line (VND) |
| `Trạng thái` | Text | Order status (Mới, Đang xác nhận, Đang đóng gói, Đã đóng gói, Thành công, Hệ thống hủy) |
| `Lý do hủy` | Text/Number | Cancellation reason (mostly blank) |

---

## 2️⃣ Table: `danh sach san pham` (Product List)

Master product catalog with pricing, cost, and attribute details.

| Column Name | Data Type | Description |
|---|---|---|
| `ID` | Integer | Internal product record ID |
| `Mã vạch` | Integer | Product barcode |
| `Loại sản phẩm` | Text | Product type (Sản phẩm = finished product, Sản phẩm cân đo = sold by weight/measure, Dụng cụ = tools/materials) |
| `Mã sản phẩm` | Text | Product/SKU code (incl. size variant) — join key to `order` and `mkt_camp_by_sku_cost` |
| `Tên sản phẩm` | Text | Product name |
| `Giá nhập` | Number | Import/purchase cost price (VND) |
| `Giá bán` | Number | Listed selling price (VND) |
| `Giá bán + VAT` | Number | Selling price including VAT (VND) |
| `Giá vốn` | Number | Cost of goods sold (VND) |
| `Trạng thái` | Text | Product status (Mới = New, Đang bán = Currently selling) |
| `Mã danh mục` | Text | Category code |
| `Danh mục` | Text | Product category name (e.g., Váy Chiết Eo Xoè, Set Váy Áo, Áo Tách Set) |
| `Mã danh mục nội bộ` | Text | Internal category code (e.g., usage occasion grouping such as "Đi làm đi chơi", "Đi biển") |
| `Thương hiệu` | Text | Pattern/print style attribute (e.g., Hoa = floral, Trơn = plain, Sọc = striped) |
| `Màu sắc` | Text | Color |
| `Chất liệu` | Text | Material/fabric (e.g., Tơ, Ren, Lụa) |

---

## 3️⃣ Table: `mkt_camp_cost` (Campaign Cost - Daily)

Daily-level marketing campaign cost and performance metrics (campaign granularity).

| Column Name | Data Type | Description |
|---|---|---|
| `Tên chiến dịch` | Text | Campaign name |
| `Ngày` | Date | Reporting date |
| `Số tiền đã chi tiêu` | Integer | Amount spent on the campaign that day (VND) |
| `Phân phối chiến dịch` | Text | Delivery status (active / inactive) |
| `Ngân sách chiến dịch` | Integer | Campaign budget (VND) |
| `Loại ngân sách chiến dịch` | Text | Budget type (e.g., Daily) |
| `CPM (Chi phí trên mỗi 1.000 lần hiển thị)` | Number | Cost per 1,000 impressions (VND) |
| `CPC (Chi phí trên mỗi lượt click vào liên kết)` | Number | Cost per link click (VND) |
| `Lượt hiển thị` | Integer | Number of impressions |
| `Click` | Integer | Number of link clicks |

---

## 4️⃣ Table: `mkt_camp_by_sku_cost` (Campaign Performance by SKU)

Marketing campaign performance allocated/broken down to individual product SKUs.

| Column Name | Data Type | Description |
|---|---|---|
| `Tên chiến dịch` | Text | Campaign name |
| `Ngày` | Date | Reporting date |
| `Đơn vị tiền tệ` | Text | Currency (VND) |
| `Số tiền đã chi tiêu (VND)` | Number | Total amount spent on the campaign that day (VND) |
| `Phân phối chiến dịch` | Text | Delivery status (active / inactive) |
| `Ngân sách chiến dịch` | Number | Campaign budget (VND) |
| `Loại ngân sách chiến dịch` | Text | Budget type (e.g., Daily) |
| `Lần bắt đầu cuộc trò chuyện qua tin nhắn` | Number | Number of new messaging conversations started |
| `Bình luận về bài viết` | Number | Number of comments on the ad post |
| `CPM` | Number | Cost per 1,000 impressions (VND) |
| `CPC` | Number | Cost per link click (VND) |
| `CTR` | Number | Click-through rate (ratio) |
| `Tin nhắn mới` | Number | Number of new messages |
| `Lượt hiển thị` | Number | Number of impressions |
| `Mã Sản phẩm` | Text | Product/SKU code — join key to `danh sach san pham` |
| `Tên Sản Phẩm` | Text | Product name |
| `Giá bán` | Number | Selling price of the product (VND) |
| `Tên Bài Chạy` | Text | Ad/creative name |
| `Bài chạy theo ngày` | Text | Ad run ID by day (concatenation of date code + ad name) |
| `Tên Sản phẩm` | Text | Product name (duplicate of `Tên Sản Phẩm`) |
| `Tiền đã chạy Theo Sản phẩm` | Number | Ad spend allocated to this product (VND) |
| `Ngân sách Theo sản phẩm` | Number | Budget allocated to this product (VND) |
| `Inbox Theo AM` | Number | Inbox conversations allocated to this product |
| `Comments Theo AM` | Number | Comments allocated to this product |
| `Inbox + Comments Theo AM` | Number | Total inbox + comments allocated to this product |
| `CP/KQ Theo AM` | Number | Cost per result allocated to this product (VND) |
| `CPM Theo AM` | Number | Cost per 1,000 impressions allocated to this product (VND) |
| `CPC Theo AM` | Number | Cost per click allocated to this product (VND) |
| `CTR Theo AM` | Number | Click-through rate allocated to this product |
| `Khách mới Theo AM` | Number | New customers allocated to this product |
| `Khách cũ Theo AM` | Number | Returning customers allocated to this product |
| `Lượt hiển thị Theo AM` | Number | Impressions allocated to this product |
| `SL bán tổng` | Integer | Total units sold (this product, all campaigns) |
| `Tổng CMT trên SP` | Number | Total comments on this product's posts |
| `SL bán được phân bổ theo tỉ lệ` | Number | Units sold allocated to this campaign by ratio |
| `SL tồn` | Integer | Remaining stock quantity |
| `Tổng SL bán theo Campaign` | Number | Total units sold attributed to this campaign |

> ℹ️ Note: "Theo AM" = "per Account Manager / per ad-set allocation"; "Theo Sản phẩm" = "per product".

---

## 📝 Notes for Analysts

- All monetary values are in **VND** unless otherwise noted.
- `Mã sản phẩm` (SKU code) is the primary key linking products across `order`, `danh sach san pham`, and `mkt_camp_by_sku_cost`.
- Column headers in `mkt_camp_by_sku_cost` contain line breaks (`\n`) - watch for trailing/leading spaces in column names (e.g., `Inbox Theo AM`).
- Some rows in `mkt_camp_by_sku_cost` contain repeated header text as data values (data quality issue) - filter these out before analysis.
