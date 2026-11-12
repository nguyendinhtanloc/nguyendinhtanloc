<div align="center">

[English](README.md) | **Tiếng Việt**

</div>

# Nguyễn Đình Tấn Lộc

Sinh viên ngành Kỹ thuật Dữ liệu (Data Engineering) tại Trường Đại học Sư phạm Kỹ thuật TP.HCM (HCMUTE), tập trung xây dựng data pipeline và kiến trúc lakehouse đáng tin cậy. Hiện đang tìm kiếm cơ hội thực tập và vị trí entry-level về Data Engineering, đồng thời quan tâm đến Data Analytics và Computer Vision.

## Kinh nghiệm

| Thời gian | Vị trí | Đơn vị |
|---|---|---|
| 10/2026 – 12/2026 | Data Engineer Intern | AWS |
| 09/2026 – 11/2026 | Data Analyst Intern (remote) | QT-DATA VN |

## Chứng chỉ

- Samsung — Big Data 2024-2025

## Công nghệ

| Lĩnh vực | Công cụ |
|---|---|
| Ngôn ngữ | Python, SQL |
| Lakehouse & Cloud | AWS (S3, Glue Data Catalog, Athena, Step Functions, EventBridge, DynamoDB, QuickSight), Apache Iceberg, MinIO |
| Xử lý & Biến đổi dữ liệu | Polars, dbt, Apache Airflow |
| Cơ sở dữ liệu | PostgreSQL / PostGIS |
| BI | Metabase, Amazon QuickSight |
| ML & CV | PyTorch, Ultralytics YOLOv8, MLflow |
| DevOps & IaC | Docker, Docker Compose, AWS CDK (Python), pytest |

## Dự án nổi bật

### 1. [AWS Serverless Data Lakehouse cho đơn hàng logistics](https://github.com/nguyendinhtanloc-Org/aws-workshop) · Data Engineering
Data lakehouse serverless hai luồng cho đơn hàng thương mại điện tử vận chuyển qua GHN. Đơn hàng đổi trạng thái 5–7 lần (có vòng lặp giao lại, sự kiện đến sai thứ tự) được phục vụ qua fast path để tra cứu tức thời và batch path để merge vào bảng Apache Iceberg phục vụ báo cáo KPI, không cần vận hành cụm Spark.

- **Kiến trúc:** Webhook → API Gateway & Lambda → SQS FIFO → DynamoDB (fast path); S3 Bronze → Step Functions → Athena v3 `MERGE INTO` Iceberg (Silver/Gold) → QuickSight
- **Điểm nhấn:** pre-dedup bằng window function trước mỗi `MERGE` để tránh lỗi cardinality violation; Gold mart `delivery_kpis` (tỷ lệ giao lần đầu, tỷ lệ hoàn, tỷ lệ giao đúng hạn, lead time); lịch `OPTIMIZE` và `VACUUM` tự động qua EventBridge
- **Quy mô thiết kế:** 30.000+ đơn/ngày
- **Vai trò:** nhóm 5 người, phụ trách tầng lakehouse (DDL Iceberg, SQL MERGE trên Athena, điều phối Step Functions, bảo trì bảng)
- `Apache Iceberg` `Athena` `Step Functions` `Glue` `DynamoDB` `AWS CDK`

### 2. [PropMatch Engine: Khử trùng thực thể bất động sản](https://github.com/nguyendinhtanloc-Org/propmatch-engine) · Data Engineering · *Đang thực hiện*
Pipeline chạy local-first khử trùng các tin cho thuê nhà đăng lặp trên nhiều sàn tại Việt Nam, theo nguyên tắc zero false merge ở tầng Gold, kèm chấm điểm rủi ro và phân tích giá theo không gian địa lý.

- **Kiến trúc:** Crawler/Parser → MinIO (raw) → Polars ETL (Silver) → entity resolution & risk scoring → dbt + PostgreSQL/PostGIS (Gold marts) → Metabase
- **Điểm nhấn:** multi-pass blocking với overlapping buckets; phân cụm đồ thị có conflict-driven refinement (tách cụm khi vị trí mâu thuẫn quá 500 m); commit marker trên MinIO để đảm bảo idempotent
- **Mục tiêu đánh giá:** candidate recall ≥ 85% (tập synthetic), pairwise F1 ≥ 70% (tập gán nhãn thủ công)
- **Vai trò:** dự án cá nhân, thực hiện toàn bộ
- `Python` `Polars` `NetworkX` `PostGIS` `dbt` `MinIO` `Docker`

### 3. [Metadata-Stratified Active Learning cho Object Detection](https://github.com/nguyendinhtanloc-Org/metadata-stratified-active-learning) · Computer Vision
Active learning theo độ bất định thường chọn các ảnh quen thuộc ban ngày và bỏ sót điều kiện hiếm. Dự án phân tầng lấy mẫu theo metadata cảnh (thời tiết, bối cảnh, thời điểm), phân bổ hạn ngạch gán nhãn bằng Iterative Proportional Fitting, rồi huấn luyện lại YOLOv8 theo vòng lặp active learning trên BDD100K (~61.800 ảnh chưa gán nhãn, tập đánh giá cố định 2.000 ảnh).

- **Thời tiết xấu:** mAP50 0.3430 so với 0.3223 của baseline (+2.1 điểm)
- **Độ đa dạng batch:** entropy 3.70 → 5.06 bits (paired t-test p < 0.005, Cohen's d = 9.71)
- **Chất lượng mã nguồn:** 43/43 unit test đạt
- **Vai trò:** đề tài nghiên cứu độc lập, thực hiện toàn bộ (thiết kế phương pháp, mã nguồn, thực nghiệm, phân tích thống kê)
- `PyTorch` `YOLOv8` `SciPy` `pytest` `Docker`

<!-- 4. Dự án Data Analytics: sẽ bổ sung -->

## Liên hệ

- Email: [ndtl05062005@gmail.com](mailto:ndtl05062005@gmail.com)
- GitHub: [@nguyendinhtanloc](https://github.com/nguyendinhtanloc)
- LinkedIn: [liên kết của bạn]
