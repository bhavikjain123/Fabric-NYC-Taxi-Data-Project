<p align="center">
  <img src="Finaldashboard.jpeg" alt="NYC Taxi Dashboard" width="100%">
</p>

This repository has been created for the Microsoft Fabric NYC Yellow Taxi end to end data project.
Please refer to the [Wiki](https://github.com/malvik01/Fabric-NYC-Taxi-Data-Project/wiki) for the code used in the data pipelines, stored procedures, variables and parameters.

Dataset [Link](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
Please refer to the above link to download latest year's Parquet files for Yellow Taxi.

# 🚖 Microsoft Fabric: NYC Yellow Taxi End-to-End Data Engineering Project

A production-grade, metadata-driven data pipeline built entirely within the **Microsoft Fabric** ecosystem. This project demonstrates the transformation of raw NYC Yellow Taxi Parquet data into actionable revenue and trip insights using a full **Medallion Architecture**.

**📂 [Access the Project Wiki for Full Code and Pipelines](https://github.com/malvik01/Fabric-NYC-Taxi-Data-Project/wiki)**

---

## 📊 Final Analytics Dashboard

The culmination of this engineering effort is an interactive Power BI dashboard analyzing revenue, trip trends, and geographic patterns across **48M+ trips**.

![NYC Taxi Dashboard](Finaldashboard.jpeg)

*Dashboard Key Insights: A total revenue of **$1.295 Billion**, driven by high volume in September and geographic concentration in Manhattan.*

---

## 🛠️ Project Technical Overview

This project implements a robust **Medallion Architecture** (Staging to Presentation) to process a high-volume dataset.

**Medallion Architecture Overview**
* [Diagram or detailed description of Medallion Architecture: Bronze to Silver to Gold]

### 1. Ingestion & Orchestration (Data Factory)

Automated **Fabric Pipelines** are the backbone of this solution. Key engineering principles implemented include:

* **Dynamic Ingestion:** Used dynamic SQL expressions and variables (`@formatDateTime`, `@pipeline().RunId`) to manage incremental loads based on metadata.
* **Idempotency:** Implemented pre-copy scripts via **SQL Stored Procedures** (e.g., `delete from stg.nyc_taxi_yellow`) to ensure staging is cleared before each load, allowing for safe retries.
* **Metadata Logging:** A custom `processing_log` table tracks every pipeline run, including rows processed and timestamp, providing a detailed audit trail.

### 2. Transformation Layer (Synapse)

Data is refined and curated using a mix of low-code and high-code tools:

* **Bronze to Silver:** Leveraged **Dataflows Gen2** (Power Query M) for column renaming, data type casting, and complex "Merge" operations (e.g., joining fact tables with dimensional lookups like Taxi Zones).
* **Silver to Gold:** Authored advanced **SQL Stored Procedures** to populate the final, highly optimized **Presentation (Gold)** layer (`dbo.nyctaxi_yellow`).

### 3. Reporting Layer (Power BI)

A final semantic model was built to support the high-performance Power BI dashboard:

* **Model Design:** Implemented an efficient **Star Schema** to enable fast, intuitive reporting.
* **Complex DAX:** Created measures for tracking key financial (Total Revenue, Avg. Fare) and operational metrics (Avg. Trip Distance, Passanger Count).

---

## 🚀 Microsoft DP-600 & DP-700 Alignment

This project provides practical validation for the core competencies tested in key Microsoft Fabric certifications:

| Certification | Focus Areas Demonstrated |
| :--- | :--- |
| **DP-600** (Fabric Analytics Engineer) | End-to-end data transformation, Dataflows Gen2 optimization, Star Schema design, Power BI optimization. |
| **DP-700** (Data Engineer) | Metadata-driven orchestration, SQL Stored Procedure authoring, Medallion Architecture implementation, Pipeline automation. |

---

## 💾 Dataset Information

The data used is the official NYC Taxi & Limousine Commission (TLC) Trip Record Data.

* **[Download Latest Parquet Files](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)**

---

*This project was completed by **[Bhavik Jain](https://www.linkedin.com/in/bhavik-jain-70a123226)**.*
