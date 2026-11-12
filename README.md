<div align="center">

**English** | [Tiếng Việt](README.vi.md)

</div>

# Nguyễn Đình Tấn Lộc

Data Engineering student at HCMC University of Technology and Education (HCMUTE), focused on building reliable data pipelines and lakehouse architectures. Currently looking for internship and entry-level opportunities in Data Engineering, with a secondary interest in Data Analytics and Computer Vision.

## Experience

| Period | Role | Organization |
|---|---|---|
| Oct 2026 – Dec 2026 | Data Engineer Intern | AWS |
| Sep 2026 – Nov 2026 | Data Analyst Intern (remote) | QT-DATA VN |

## Certifications

- Samsung — Big Data 2024-2025

## Tech Stack

| Area | Tools |
|---|---|
| Languages | Python, SQL |
| Lakehouse & Cloud | AWS (S3, Glue Data Catalog, Athena, Step Functions, EventBridge, DynamoDB, QuickSight), Apache Iceberg, MinIO |
| Processing & Transformation | Polars, dbt, Apache Airflow |
| Databases | PostgreSQL / PostGIS |
| BI | Metabase, Amazon QuickSight |
| ML & CV | PyTorch, Ultralytics YOLOv8, MLflow |
| DevOps & IaC | Docker, Docker Compose, AWS CDK (Python), pytest |

## Featured Projects

### 1. [AWS Serverless Data Lakehouse for Logistics Orders](https://github.com/nguyendinhtanloc-Org/aws-workshop) · Data Engineering
A dual-path serverless lakehouse for e-commerce orders shipped via GHN. Order status changes (5–7 times per order, with re-delivery loops and out-of-order events) are served through a fast path for instant lookup and a batch path that merges into Apache Iceberg tables for KPI reporting, without running Spark clusters.

- **Architecture:** Webhook → API Gateway & Lambda → SQS FIFO → DynamoDB (fast path); S3 Bronze → Step Functions → Athena v3 `MERGE INTO` Iceberg (Silver/Gold) → QuickSight
- **Highlights:** window-function pre-dedup before every `MERGE` to prevent cardinality violations; Gold mart `delivery_kpis` (first-attempt delivery rate, return rate, on-time delivery rate, lead time); scheduled `OPTIMIZE` and `VACUUM` via EventBridge
- **Scale target:** 30,000+ orders/day
- **My role:** team of 5, I owned the lakehouse layer (Iceberg DDL, Athena MERGE SQL, Step Functions orchestration, table maintenance)
- `Apache Iceberg` `Athena` `Step Functions` `Glue` `DynamoDB` `AWS CDK`

### 2. [PropMatch Engine: Real Estate Entity Resolution](https://github.com/nguyendinhtanloc-Org/propmatch-engine) · Data Engineering · *In progress*
A local-first pipeline that deduplicates Vietnamese rental listings posted across multiple platforms, with a zero-false-merge rule for the Gold layer, plus risk scoring and spatial price analytics.

- **Architecture:** Crawler/Parser → MinIO (raw) → Polars ETL (Silver) → entity resolution and risk scoring → dbt + PostgreSQL/PostGIS (Gold marts) → Metabase
- **Highlights:** multi-pass blocking with overlapping buckets; graph clustering with conflict-driven refinement (clusters split when locations conflict by more than 500 m); commit markers on MinIO for idempotent runs
- **Evaluation targets:** candidate recall ≥ 85% (synthetic set), pairwise F1 ≥ 70% (human-labeled set)
- **My role:** solo project, end to end
- `Python` `Polars` `NetworkX` `PostGIS` `dbt` `MinIO` `Docker`

### 3. [Metadata-Stratified Active Learning for Object Detection](https://github.com/nguyendinhtanloc-Org/metadata-stratified-active-learning) · Computer Vision
Uncertainty-based active learning tends to pick familiar daytime images and miss rare conditions. This project stratifies sampling by scene metadata (weather, scene, time of day) and allocates the labeling budget across strata with Iterative Proportional Fitting, then retrains YOLOv8 in an active learning loop on BDD100K (~61,800 unlabeled images, 2,000-image fixed evaluation set).

- **Adverse weather:** mAP50 0.3430 vs 0.3223 baseline (+2.1 points)
- **Batch diversity:** entropy 3.70 → 5.06 bits (paired t-test p < 0.005, Cohen's d = 9.71)
- **Quality:** 43/43 unit tests passing
- **My role:** independent research thesis, end to end (method design, code, experiments, statistical analysis)
- `PyTorch` `YOLOv8` `SciPy` `pytest` `Docker`

<!-- 4. Data Analytics project: to be added -->

## Contact

- Email: [ndtl05062005@gmail.com](mailto:ndtl05062005@gmail.com)
- GitHub: [@nguyendinhtanloc](https://github.com/nguyendinhtanloc)
- LinkedIn: [Nguyễn Đình Tấn Lộc](https://www.linkedin.com/in/...)
