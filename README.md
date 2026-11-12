<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.svg">
  <img alt="Nguyễn Đình Tấn Lộc: Data Engineer, Data Analyst, Computer Vision" src="assets/banner-light.svg" width="100%">
</picture>

<div align="center">

<a href="README.md"><img src="assets/lang-en-active.svg" alt="English" height="26"></a>&nbsp;
<a href="README.vi.md"><img src="assets/lang-vi.svg" alt="Tiếng Việt" height="26"></a>

<br>

<a href="mailto:ndtl05062005@gmail.com"><img src="assets/contact-email.svg" alt="Email" height="26"></a>&nbsp;
<a href="https://www.linkedin.com/in/YOUR-LINKEDIN-ID"><img src="assets/contact-linkedin.svg" alt="LinkedIn" height="26"></a>&nbsp;
<a href="https://github.com/nguyendinhtanloc"><img src="assets/contact-github.svg" alt="GitHub" height="26"></a>

</div>

## About

Data Engineering student at HCMC University of Technology and Education (HCMUTE), focused on building reliable data pipelines and lakehouse architectures. Currently looking for internship and entry-level opportunities in Data Engineering, with a secondary interest in Data Analytics and Computer Vision.

## Experience

| Period | Role | Organization |
|---|---|---|
| Oct 2026 – Dec 2026 | **Data Engineer Intern** | AWS |
| Sep 2026 – Nov 2026 | **Data Analyst Intern** (remote) | QT-DATA VN |

**Certification:** Samsung, Big Data 2024-2025

## Tech Stack

| Area | Tools |
|---|---|
| **Languages** | <img src="assets/tech/python.svg" alt="Python" height="26"> <img src="assets/tech/sql.svg" alt="SQL" height="26"> |
| **Cloud & Lakehouse** | <img src="assets/tech/s3.svg" alt="S3" height="26"> <img src="assets/tech/glue.svg" alt="Glue" height="26"> <img src="assets/tech/athena.svg" alt="Athena" height="26"> <img src="assets/tech/step-functions.svg" alt="Step Functions" height="26"> <img src="assets/tech/eventbridge.svg" alt="EventBridge" height="26"> <img src="assets/tech/dynamodb.svg" alt="DynamoDB" height="26"> <img src="assets/tech/apache-iceberg.svg" alt="Apache Iceberg" height="26"> <img src="assets/tech/minio.svg" alt="MinIO" height="26"> |
| **Processing & Transformation** | <img src="assets/tech/polars.svg" alt="Polars" height="26"> <img src="assets/tech/dbt.svg" alt="dbt" height="26"> <img src="assets/tech/airflow.svg" alt="Airflow" height="26"> |
| **Databases** | <img src="assets/tech/postgresql.svg" alt="PostgreSQL" height="26"> <img src="assets/tech/postgis.svg" alt="PostGIS" height="26"> |
| **BI** | <img src="assets/tech/metabase.svg" alt="Metabase" height="26"> <img src="assets/tech/quicksight.svg" alt="QuickSight" height="26"> |
| **ML & CV** | <img src="assets/tech/pytorch.svg" alt="PyTorch" height="26"> <img src="assets/tech/yolov8.svg" alt="YOLOv8" height="26"> <img src="assets/tech/mlflow.svg" alt="MLflow" height="26"> |
| **DevOps & IaC** | <img src="assets/tech/docker.svg" alt="Docker" height="26"> <img src="assets/tech/aws-cdk.svg" alt="AWS CDK" height="26"> <img src="assets/tech/pytest.svg" alt="pytest" height="26"> |

## Featured Projects

### 1. [AWS Serverless Data Lakehouse for Logistics Orders](https://github.com/nguyendinhtanloc-Org/aws-workshop)
<sub>**Data Engineering** · Team of 5 · I owned the lakehouse layer</sub>

A dual-path serverless lakehouse for e-commerce orders shipped via GHN. Orders change status 5–7 times (with re-delivery loops and out-of-order events), so one path serves instant lookups while the other merges into Apache Iceberg tables for KPI reporting, without running Spark clusters.

| Scale target | Fast-path latency target | Gold KPIs |
|:---:|:---:|:---:|
| **30,000+** orders/day | **< 15 ms** | **4** (first-attempt delivery, return rate, on-time delivery, lead time) |

<details>
<summary><b>Architecture and highlights</b></summary>

```mermaid
flowchart LR
  subgraph FAST["Fast path: instant lookup"]
    direction LR
    W["GHN webhook"] --> G["API Gateway + Lambda"] --> Q["SQS FIFO"] --> D[("DynamoDB")]
  end
  subgraph BATCH["Batch path: KPI reporting"]
    direction LR
    B["S3 Bronze"] --> SF["Step Functions"] --> M["Athena MERGE INTO"] --> I[("Iceberg Silver / Gold")] --> QS["QuickSight"]
  end
```

- Window-function pre-dedup before every `MERGE` to prevent cardinality violations
- Gold mart `delivery_kpis`, built by Step Functions: merge events → merge orders → daily aggregation
- Scheduled `OPTIMIZE` (bin-pack) and `VACUUM` via EventBridge to control small files and storage cost
- My part: Iceberg DDL (Medallion), Athena MERGE SQL, Step Functions orchestration, table maintenance

</details>

`Apache Iceberg` `Athena` `Step Functions` `Glue` `DynamoDB` `AWS CDK`

### 2. [PropMatch Engine: Real Estate Entity Resolution](https://github.com/nguyendinhtanloc-Org/propmatch-engine)
<sub>**Data Engineering** · Solo project · *In progress*</sub>

A local-first pipeline that deduplicates Vietnamese rental listings posted across multiple platforms, with a zero-false-merge rule for the Gold layer, plus risk scoring and spatial price analytics.

| Candidate recall (target) | Pairwise F1 (target) | False merges into Gold |
|:---:|:---:|:---:|
| **≥ 85%** (synthetic set) | **≥ 70%** (human-labeled set) | **0** (design rule) |

<details>
<summary><b>Architecture and highlights</b></summary>

```mermaid
flowchart LR
  A["Crawler / Parser"] --> B[("MinIO raw")] --> C["Polars ETL - Silver"] --> D["Entity resolution + risk scoring"] --> E[("PostgreSQL / PostGIS - Gold via dbt")] --> F["Metabase"]
```

- Multi-pass blocking with overlapping buckets to shrink the matching space without losing edge cases
- Graph clustering with conflict-driven refinement: clusters split when locations conflict by more than 500 m
- Commit markers on MinIO for idempotent, integrity-safe runs
- Dimensional modeling in dbt, spatial queries with PostGIS, dashboards in Metabase

</details>

`Python` `Polars` `NetworkX` `PostGIS` `dbt` `MinIO` `Docker`

### 3. [Metadata-Stratified Active Learning for Object Detection](https://github.com/nguyendinhtanloc-Org/metadata-stratified-active-learning)
<sub>**Computer Vision** · Independent research thesis</sub>

Uncertainty-based active learning tends to pick familiar daytime images and miss rare conditions. This project stratifies sampling by scene metadata (weather, scene, time of day) and allocates the labeling budget across strata with Iterative Proportional Fitting, then retrains YOLOv8 on BDD100K (~61,800 unlabeled images, 2,000-image fixed evaluation set).

| Adverse-weather mAP50 | Batch diversity (entropy) | Unit tests |
|:---:|:---:|:---:|
| **0.3430** vs 0.3223 baseline (+2.1 pts) | **3.70 → 5.06** bits (p < 0.005, Cohen's d = 9.71) | **43 / 43** passing |

<details>
<summary><b>Pipeline and highlights</b></summary>

```mermaid
flowchart LR
  A["BDD100K images + labels"] --> B["Metadata extraction"] --> C["Uncertainty scoring + hybrid top-k"] --> D["IPF quota allocation"] --> E["YOLOv8 retraining"] --> F["Per-domain evaluation + paired t-test"]
  E -. "next AL round" .-> C
```

- End to end: method design, modular code (`sampling`, `active_learning`, `analysis`, `metrics`), experiments on Kaggle GPU, statistical analysis
- Tests cover sample-count conservation, IPF convergence tolerance and exhausted-pool fallback

</details>

`PyTorch` `YOLOv8` `SciPy` `pytest` `Docker`

<!-- 4. Data Analytics project: to be added -->

---

<div align="center"><sub>Open to Data Engineering internships and entry-level roles</sub></div>
