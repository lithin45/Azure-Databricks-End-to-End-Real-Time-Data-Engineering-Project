# 🚀 Azure Databricks End-to-End Real-Time Data Engineering Project

## ✅ Objective

To design and implement a **real-world, enterprise-level data engineering pipeline** using **Azure Databricks**, simulating a production-grade architecture that includes:

- Data ingestion
- Data transformation
- Dimensional modeling
- Real-time analytics and BI

All implemented using **Medallion architecture (bronze → silver → gold)**, **Delta Live Tables**, **Unity Catalog**, and **Power BI**.

---

## 🧱 Architecture Overview

![Azure Databricks Architecture](databricks-architecture.png)


### Cloud Platform & Tools

| Component            | Tool/Service                              |
|----------------------|-------------------------------------------|
| Cloud Provider       | Microsoft Azure                           |
| Data Lake            | Azure Data Lake Gen2 (with HNS)           |
| Processing Engine    | Apache Spark on Azure Databricks          |
| Data Governance      | Unity Catalog                             |
| ETL Orchestration    | Databricks Workflows + Delta Live Tables  |
| Data Format          | Parquet (columnar)                        |
| Visualization        | Power BI (via Databricks SQL Warehouse)   |

### Architecture Layers

- **Bronze Layer**: Raw data ingestion
- **Silver Layer**: Data cleansing, transformation, and enrichment
- **Gold Layer**: Business-ready analytical models (e.g., Star Schema)

---

## 📂 Data Used

- **Domain**: Retail / E-commerce
- **Files**: `orders`, `customers`, `products`, `regions`
- **Format**: Parquet

### Why Parquet?
- Efficient for big data processing
- Supports schema evolution
- Optimized for read-heavy workloads

### Why These Datasets?
- Intuitive and easy to model
- Reflect real-world transactional and reference data
- Keeps focus on engineering rather than interpretation

---

## 🛠️ Implementation Steps

### 1. Azure Setup
- Created Azure free trial account
- Provisioned:
  - Resource Group
  - Storage Account (Data Lake Gen2 enabled)
  - Containers:
    - `source` (raw data)
    - `bronze`, `silver`, `gold`
    - `metastore` (for Unity Catalog)

### 2. Databricks Workspace Setup
- Created Databricks workspace
- Configured **Access Connector** for secure ADLS Gen2 access
- Assigned proper IAM roles and permissions

### 3. Unity Catalog Configuration
- Created Unity Metastore
- Assigned metastore to the Databricks workspace
- Created external locations for:
  - `source`, `bronze`, `silver`, `gold`
- Created catalog & schemas to organize data

### 4. Data Ingestion (Bronze Layer)
- Ingested data using **Databricks Data Ingestion Tool (No-code)**
- Implemented **incremental loading** using **Spark Structured Streaming**
- Enforced **idempotency** to avoid duplicates
- Stored in **Delta format** for ACID compliance & time travel

### 5. Data Transformation (Silver Layer)
- Transformed data using **PySpark DataFrame APIs**
- Applied **OOP principles in Python** for modular code
- Created **shared business logic functions** in Unity Catalog
- Output stored in `silver` schema as Delta tables

### 6. Business Modeling (Gold Layer)
- Built a **Star Schema**:
  - **Dimension Tables**: `customers`, `products`, `regions`
  - **Fact Table**: `orders`
- Implemented **Slowly Changing Dimensions**:
  - **Type 1**: Manual with PySpark
  - **Type 2**: Automated with Delta Live Tables
- Used **Databricks Workflows** for orchestration

### 7. Data Serving & BI Integration
- Enabled **Databricks SQL Warehouse**
- Connected **Power BI** to gold layer
- Built real-time dashboards for analytics

---

## 💡 Key Features Demonstrated

| Feature                 | Description |
|--------------------------|-------------|
| **Medallion Architecture** | Structured data layers (bronze → silver → gold) |
| **Delta Lake**             | Time travel, schema enforcement, ACID transactions |
| **Incremental Loading**    | Spark Structured Streaming for real-time processing |
| **Data Governance**        | Unity Catalog for centralized access control |
| **ETL Orchestration**      | Delta Live Tables & Workflows |
| **Python + PySpark**       | OOP + modular transformation code |
| **Real-Time Concepts**     | Idempotency, schema evolution, auditing |
| **SCD Type 1 & 2**         | History tracking with PySpark & DLT |
| **BI Integration**         | Power BI dashboards via SQL Warehouse |

---

## 📊 Final Output

- Real-time pipeline simulating modern enterprise data stack
- Queryable gold-layer tables via SQL
- Interactive Power BI dashboards built on top of optimized data models

---

## 📎 License

This project is for learning and demonstration purposes only.
