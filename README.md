# Real-Time Customer Personalization Data Platform

[![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)](https://azure.microsoft.com)
[![Databricks](https://img.shields.io/badge/Databricks-FF3621?style=flat-square&logo=databricks&logoColor=white)](https://databricks.com)
[![Event Hubs](https://img.shields.io/badge/Azure_Event_Hubs-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)](https://azure.microsoft.com/en-us/products/event-hubs)
[![Apache Spark](https://img.shields.io/badge/Apache_Spark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)](https://spark.apache.org)
[![Delta Lake](https://img.shields.io/badge/Delta_Lake-003366?style=flat-square&logoColor=white)](https://delta.io)

> A streaming analytics platform processing 50M+ subscriber interaction records and 2M+ events/hour, powering real-time personalization models and campaign targeting for enterprise telecom.

---

## Overview

This platform enables near-real-time clickstream analytics and personalization feature generation across digital engagement channels. By ingesting and processing high-volume customer interaction data through **Azure Event Hubs** and **Databricks Structured Streaming**, it powers downstream ML models that drive subscriber retention and campaign optimization.

---

## Architecture

```
┌────────────────────────────────────────────────────────────────┐
│                      DATA SOURCES                              │
│  Clickstream Events · App Interactions · Web Behaviour · CRM   │
└────────────────────────┬───────────────────────────────────────┘
                         │  2M+ events/hour
                         ▼
┌────────────────────────────────────────────────────────────────┐
│               STREAMING INGESTION                              │
│              Azure Event Hubs (Partitioned)                    │
│         Schema Registry · Consumer Groups · Checkpointing      │
└────────────────────────┬───────────────────────────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────────────────────────┐
│           STREAM PROCESSING — Databricks                       │
│         Spark Structured Streaming · PySpark                   │
│    Sessionization · Deduplication · Feature Extraction         │
└────────────────────────┬───────────────────────────────────────┘
                         │
                         ▼
┌────────────────────────────────────────────────────────────────┐
│          FEATURE STORE — Delta Lake on ADLS Gen2               │
│    Bronze (Raw) → Silver (Cleaned) → Gold (Feature-Ready)      │
│     50M+ subscriber records · Z-ordered · ACID compliant       │
└──────────────┬─────────────────────────┬───────────────────────┘
               │                         │
               ▼                         ▼
┌──────────────────────┐    ┌────────────────────────────────────┐
│   ML FEATURE LAYER   │    │       ANALYTICS & BI LAYER         │
│  Personalization     │    │  Power BI Dashboards               │
│  Model Training      │    │  Campaign Performance Reports      │
│  Churn Prediction    │    │  Subscriber Engagement Metrics     │
└──────────────────────┘    └────────────────────────────────────┘
```

---

## Key Components

### 1. High-Throughput Ingestion — Azure Event Hubs
- Partitioned event ingestion handling **2M+ events per hour**
- Consumer group isolation for streaming and batch consumers
- Checkpointing and offset management for exactly-once processing guarantees

### 2. Stream Processing — Databricks Structured Streaming
- Real-time clickstream sessionization and deduplication
- Micro-batch feature extraction for personalization signals
- Watermarking for late-arriving event handling
- Contributed to **12% reduction in subscriber churn**

### 3. Feature Engineering — Delta Lake
- Curated feature datasets from **50M+ subscriber interaction records**
- Delta Lake optimization (Z-ordering, compaction) reducing query latency by **35%**
- Versioned feature tables supporting model reproducibility
- Reusable ML-ready dataset preparation framework

### 4. Compute Optimization — Spark Tuning
- Databricks cluster autoscaling strategies
- Spark execution plan analysis and shuffle optimization
- Compute consumption reduced by **22%** through execution strategy tuning

### 5. Governance — Azure Purview
- SOC2 and GDPR traceability across analytics and ML dataset pipelines
- Metadata lineage enforcement from raw events to feature store

---

## Results

| Metric | Result |
|--------|--------|
| Event Throughput | **2M+ events/hour** |
| Subscriber Records Processed | **50M+** |
| Subscriber Churn Reduction | **12%** |
| Analytics Query Latency | **35% reduction** |
| Databricks Compute Savings | **22%** |
| Compliance Coverage | SOC2 + GDPR |

---

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| Ingestion | Azure Event Hubs, Azure Data Factory |
| Stream Processing | Databricks, Spark Structured Streaming, PySpark |
| Feature Storage | Delta Lake, ADLS Gen2 |
| Batch Processing | Azure Data Factory, Apache Spark |
| Governance | Azure Purview |
| Orchestration | Apache Airflow, Azure DevOps |
| IaC | Terraform |
| BI | Power BI |

---

## Repository Structure

```
realtime-personalization-platform/
├── ingestion/
│   ├── event_hubs/             # Event Hubs consumer configs
│   └── adf_pipelines/          # Batch ingestion templates
├── streaming/
│   ├── structured_streaming/   # Spark Structured Streaming jobs
│   ├── sessionization/         # Clickstream sessionization logic
│   └── deduplication/          # Event dedup strategies
├── feature_engineering/
│   ├── bronze_layer/           # Raw event landing
│   ├── silver_layer/           # Cleaned & enriched events
│   └── gold_layer/             # ML-ready feature datasets
├── optimization/
│   ├── delta_tuning/           # Z-order, compaction scripts
│   └── spark_tuning/           # Execution plan optimizations
├── governance/
│   └── purview_policies/       # Lineage & compliance configs
├── infrastructure/
│   └── terraform/              # Infrastructure as code
└── docs/
    └── architecture.md
```

---

## Author

**Samhitha Alapati** — Senior Data Engineer

[![Portfolio](https://img.shields.io/badge/Portfolio-000000?style=flat-square)](https://applywizz-samhitha-26024.vercel.app/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/samhitha-alapati-data-engineer)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:samhitha3107@gmail.com)

