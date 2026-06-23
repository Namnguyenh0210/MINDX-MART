# MINDX-MART

## Xây dựng hệ thống Data Lakehouse trên Microsoft Fabric phục vụ phân tích dữ liệu bán hàng

---

# 1. Tổng quan dự án

MINDX-MART là dự án Data Engineering được xây dựng trên nền tảng Microsoft Fabric nhằm mô phỏng kiến trúc dữ liệu hiện đại trong doanh nghiệp.

Dự án triển khai mô hình Data Lakehouse theo kiến trúc Medallion bao gồm các tầng:

* Raw Layer
* Bronze Layer
* Silver Layer
* Gold Layer

Thông qua quy trình ETL nhiều tầng, hệ thống thực hiện việc thu thập, làm sạch, chuẩn hóa, chuyển đổi và tổng hợp dữ liệu nhằm phục vụ cho hoạt động phân tích và hỗ trợ ra quyết định.

---

# 2. Bối cảnh nghiệp vụ

Trong môi trường doanh nghiệp, dữ liệu thường phát sinh từ nhiều hệ thống khác nhau như:

* Hệ thống bán hàng.
* Hệ thống quản lý khách hàng.
* Dữ liệu tài chính.
* Dữ liệu tỷ giá.
* Dữ liệu giao dịch.

Các vấn đề phổ biến bao gồm:

* Dữ liệu phân tán.
* Thiếu tính nhất quán.
* Dữ liệu trùng lặp.
* Khó tổng hợp báo cáo.
* Khó mở rộng hệ thống phân tích.

Dự án MINDX-MART được xây dựng nhằm giải quyết các vấn đề trên thông qua kiến trúc Data Lakehouse hiện đại.

---

# 3. Mục tiêu dự án

* Xây dựng hệ thống Data Lakehouse trên Microsoft Fabric.
* Thiết kế quy trình ETL hoàn chỉnh.
* Áp dụng kiến trúc Medallion.
* Chuẩn hóa dữ liệu kinh doanh.
* Xây dựng mô hình dữ liệu phân tích.
* Hỗ trợ báo cáo và Business Intelligence.
* Tăng khả năng mở rộng hệ thống dữ liệu.

---

# 4. Kiến trúc hệ thống

```text
Nguồn dữ liệu
      │
      ▼
Raw Layer
      │
      ▼
Bronze Layer
      │
      ▼
Silver Layer
      │
      ▼
Gold Layer
      │
      ▼
Power BI Dashboard
```

Kiến trúc Medallion giúp phân tách rõ ràng các giai đoạn xử lý dữ liệu, từ đó nâng cao khả năng quản lý, bảo trì và mở rộng hệ thống.

---

# 5. Công nghệ sử dụng

| Công nghệ        | Vai trò                 |
| ---------------- | ----------------------- |
| Microsoft Fabric | Nền tảng dữ liệu        |
| Lakehouse        | Lưu trữ dữ liệu         |
| PySpark          | Xử lý dữ liệu           |
| Notebook         | Phát triển ETL          |
| Data Pipeline    | Điều phối luồng dữ liệu |
| SQL Endpoint     | Truy vấn dữ liệu        |
| Delta Table      | Lưu trữ dữ liệu         |
| Power BI         | Trực quan hóa dữ liệu   |

---

# 6. Cấu trúc thư mục

```text
MINDX-MART
│
├── assets/
│   └── Mindx_workspace.png
│
├── data_pipelines/
│   └── PL_INGEST_RAW
│
├── notebooks/
│   ├── NB_BRONZE.ipynb
│   ├── NB_SILVER.ipynb
│   └── NB_GOLD.ipynb
│
├── sample_data/
│   ├── sales/
│   └── exchange_rate/
│
└── README.md
```

---

# 7. Nguồn dữ liệu

## Dữ liệu bán hàng

Bao gồm:

* Mã đơn hàng.
* Thông tin khách hàng.
* Thông tin sản phẩm.
* Số lượng bán.
* Giá bán.
* Doanh thu.

## Dữ liệu tỷ giá

Bao gồm:

* Mã tiền tệ.
* Tỷ giá.
* Ngày hiệu lực.

---

# 8. Quy trình ETL

## 8.1 Data Ingestion

Pipeline thực hiện việc thu thập dữ liệu và lưu vào Raw Layer.

Mục tiêu:

* Lưu trữ dữ liệu gốc.
* Đảm bảo khả năng truy vết.
* Hỗ trợ kiểm tra dữ liệu.

---

## 8.2 Bronze Layer

Thực hiện:

* Kiểm tra dữ liệu.
* Chuẩn hóa định dạng.
* Kiểm tra kiểu dữ liệu.
* Loại bỏ dữ liệu lỗi.

Notebook:

```text
NB_BRONZE.ipynb
```

---

## 8.3 Silver Layer

Thực hiện:

* Làm sạch dữ liệu.
* Xử lý giá trị NULL.
* Loại bỏ dữ liệu trùng lặp.
* Chuẩn hóa dữ liệu nghiệp vụ.
* Chuyển đổi kiểu dữ liệu.

Notebook:

```text
NB_SILVER.ipynb
```

---

## 8.4 Gold Layer

Thực hiện:

* Tổng hợp dữ liệu.
* Tạo Fact Table.
* Tạo Dimension Table.
* Chuẩn bị dữ liệu phân tích.

Notebook:

```text
NB_GOLD.ipynb
```

---

# 9. Kiểm soát chất lượng dữ liệu

Hệ thống thực hiện một số kiểm tra chất lượng dữ liệu:

* Kiểm tra dữ liệu NULL.
* Loại bỏ dữ liệu trùng.
* Chuẩn hóa kiểu dữ liệu.
* Kiểm tra tính hợp lệ của trường dữ liệu.
* Kiểm tra khóa chính.

Việc kiểm soát chất lượng dữ liệu giúp nâng cao độ chính xác của báo cáo và phân tích.

---

# 10. Mô hình dữ liệu

```text
              Dim_Date
                   │
                   │
Dim_Customer ─ Fact_Sales ─ Dim_Product
```

## Fact Table

### gold_fact_sales

Lưu trữ:

* Doanh thu.
* Số lượng bán.
* Giá bán.

---

## Dimension Tables

### gold_dim_customer

Thông tin khách hàng.

### gold_dim_product

Thông tin sản phẩm.

### gold_dim_date

Thông tin thời gian.

---

# 11. Các bảng Gold

| Bảng                 | Chức năng            |
| -------------------- | -------------------- |
| gold_fact_sales      | Phân tích doanh thu  |
| gold_dim_customer    | Phân tích khách hàng |
| gold_dim_product     | Phân tích sản phẩm   |
| gold_dim_date        | Phân tích thời gian  |
| gold_monthly_revenue | Doanh thu theo tháng |
| gold_promotion       | Phân tích khuyến mãi |

---

# 12. Giá trị doanh nghiệp

Hệ thống mang lại các lợi ích:

* Tập trung dữ liệu.
* Chuẩn hóa dữ liệu.
* Giảm thời gian xử lý thủ công.
* Tăng độ chính xác báo cáo.
* Hỗ trợ ra quyết định.
* Phân tích hiệu quả kinh doanh.

---

# 13. Khả năng mở rộng

Kiến trúc hiện tại cho phép:

* Bổ sung nguồn dữ liệu mới.
* Tăng khối lượng dữ liệu.
* Tích hợp Dashboard.
* Triển khai Machine Learning.
* Mở rộng sang dữ liệu thời gian thực.

---

# 14. Hiệu năng hệ thống

Việc phân tầng dữ liệu giúp:

* Giảm tải truy vấn.
* Tăng tốc độ xử lý.
* Dễ tối ưu dữ liệu.
* Giảm chi phí lưu trữ.
* Tăng hiệu quả phân tích.

---

# 15. Hạn chế hiện tại

Dự án hiện tại vẫn còn một số hạn chế:

* Chưa hỗ trợ dữ liệu thời gian thực.
* Chưa triển khai monitoring.
* Chưa có cảnh báo pipeline lỗi.
* Chưa triển khai CI/CD.
* Chưa hỗ trợ incremental load.

---

# 16. Hướng phát triển

* Tích hợp Power BI Dashboard.
* Triển khai Incremental Load.
* Xây dựng hệ thống cảnh báo.
* Tích hợp Machine Learning.
* Dự báo doanh thu.
* Phân tích hành vi khách hàng.
* Triển khai dữ liệu thời gian thực.

---

# 17. Kết quả đạt được

* Xây dựng thành công Data Lakehouse.
* Áp dụng kiến trúc Medallion.
* Thiết kế ETL Pipeline.
* Chuẩn hóa dữ liệu.
* Xây dựng Star Schema.
* Tạo dữ liệu phân tích.
* Hỗ trợ Business Intelligence.

---

# 18. Kết luận

MINDX-MART là dự án mô phỏng quy trình xử lý dữ liệu trong doanh nghiệp trên nền tảng Microsoft Fabric.

Thông qua kiến trúc:

```text
Raw → Bronze → Silver → Gold
```

hệ thống giúp quản lý dữ liệu hiệu quả, dễ mở rộng và hỗ trợ hoạt động phân tích dữ liệu trong doanh nghiệp.

---

# Tác giả

Nguyễn Hữu Nam

Data Engineering Project

Microsoft Fabric Lakehouse
