<!-- Banner động -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F2027,50:203A43,100:2C5364&height=200&section=header&text=Nguyễn%20Đình%20Tấn%20Lộc&fontSize=38&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Data%20Engineer%20%7C%20Data%20Analyst%20%7C%20Computer%20Vision&descAlignY=58&descSize=16" width="100%"/>
</div>

<!-- Thanh chuyển đổi ngôn ngữ & Liên hệ -->
<div align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/Language-English-0969DA?style=for-the-badge" alt="English"></a>
  <a href="README.vi.md"><img src="https://img.shields.io/badge/Ngôn%20ngữ-Tiếng%20Việt-21262D?style=for-the-badge" alt="Tiếng Việt"></a>
  <br><br>
  <a href="mailto:ndtl05062005@gmail.com"><img src="https://img.shields.io/badge/Email-ndtl05062005%40gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white" alt="Email"></a>
  <a href="https://www.linkedin.com/in/YOUR-LINKEDIN-ID"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://github.com/nguyendinhtanloc"><img src="https://img.shields.io/badge/GitHub-nguyendinhtanloc-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub"></a>
</div>

<br>

## 👨‍💻 About Me

Data Engineering student at **HCMC University of Technology and Education (HCMUTE)**, focused on building reliable, scalable data pipelines and lakehouse architectures. Currently open to **internship and entry-level opportunities in Data Engineering**, with strong secondary capabilities in **Data Analytics** and **Computer Vision**.

- 🌱 **Core Focus:** Serverless Data Lakehouse, CDC/Streaming Pipelines, Spatial Analytics & Entity Resolution.
- 🎓 **Certification:** Samsung Innovation Campus — Big Data (2024–2025).
- ⚡ **Fun fact:** I enjoy optimizing SQL queries and table compaction almost as much as training object detection models.

---

## 💼 Experience

| Period | Role | Organization | Highlights |
| :--- | :--- | :--- | :--- |
| **Oct 2026 – Dec 2026** | **Data Engineer Intern** | **AWS** | Serverless Lakehouse, Apache Iceberg, Step Functions orchestration |
| **Sep 2026 – Nov 2026** | **Data Analyst Intern** *(Remote)* | **QT-DATA VN** | Data modeling, KPI reporting, BI dashboards |

---

## 🛠️ Tech Stack

| Category | Technologies |
| :--- | :--- |
| **Languages** | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white) |
| **Cloud & Lakehouse** | ![AWS S3](https://img.shields.io/badge/Amazon_S3-569A31?style=flat-square&logo=amazons3&logoColor=white) ![AWS Glue](https://img.shields.io/badge/AWS_Glue-232F3E?style=flat-square&logo=amazonaws&logoColor=white) ![Amazon Athena](https://img.shields.io/badge/Amazon_Athena-232F3E?style=flat-square&logo=amazonaws&logoColor=white) ![Step Functions](https://img.shields.io/badge/Step_Functions-FF4F8B?style=flat-square&logo=amazonaws&logoColor=white) ![EventBridge](https://img.shields.io/badge/EventBridge-FF4F8B?style=flat-square&logo=amazonaws&logoColor=white) ![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=flat-square&logo=amazondynamodb&logoColor=white) ![Apache Iceberg](https://img.shields.io/badge/Apache_Iceberg-008080?style=flat-square&logo=apache&logoColor=white) ![MinIO](https://img.shields.io/badge/MinIO-C72E49?style=flat-square&logo=minio&logoColor=white) |
| **Processing & ETL** | ![Polars](https://img.shields.io/badge/Polars-CD792C?style=flat-square&logo=polars&logoColor=white) ![dbt](https://img.shields.io/badge/dbt-FF694B?style=flat-square&logo=dbt&logoColor=white) ![Apache Airflow](https://img.shields.io/badge/Apache_Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white) |
| **Databases** | ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![PostGIS](https://img.shields.io/badge/PostGIS-336791?style=flat-square&logo=postgresql&logoColor=white) |
| **BI & Visualization** | ![Metabase](https://img.shields.io/badge/Metabase-509EE3?style=flat-square&logo=metabase&logoColor=white) ![QuickSight](https://img.shields.io/badge/Amazon_QuickSight-232F3E?style=flat-square&logo=amazonaws&logoColor=white) |
| **ML & Computer Vision** | ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white) ![YOLOv8](https://img.shields.io/badge/YOLOv8-00FFFF?style=flat-square&logo=yolo&logoColor=black) ![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white) |
| **DevOps & IaC** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![AWS CDK](https://img.shields.io/badge/AWS_CDK-232F3E?style=flat-square&logo=amazonaws&logoColor=white) ![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white) |

---

## 🚀 Featured Projects

### 1. [AWS Serverless Data Lakehouse for Logistics Orders](https://github.com/nguyendinhtanloc-Org/aws-workshop)
> **Data Engineering** · Team of 5 · *Role: Owned the Lakehouse & Orchestration Layer*

A dual-path serverless lakehouse for e-commerce orders shipped via GHN. Because orders change status 5–7 times (with re-delivery loops and out-of-order events), one path serves instant lookups while the other merges into **Apache Iceberg** tables for KPI reporting—without running expensive Spark clusters.

| Scale Target | Fast-Path Latency | Gold KPIs |
| :---: | :---: | :---: |
| **30,000+** orders/day | **< 15 ms** | **4** *(First-attempt, Return rate, On-time, Lead time)* |

<details>
<summary><b>🔍 View Architecture & Engineering Highlights</b></summary>
<br>

```mermaid
flowchart LR
  subgraph FAST["⚡ Fast Path: Instant Lookup"]
    direction LR
    W["GHN Webhook"] --> G["API Gateway + Lambda"] --> Q["SQS FIFO"] --> D[("DynamoDB")]
  end
  subgraph BATCH["📊 Batch Path: KPI Reporting"]
    direction LR
    B["S3 Bronze"] --> SF["Step Functions"] --> M["Athena MERGE INTO"] --> I[("Iceberg Silver / Gold")] --> QS["QuickSight"]
  end
