# 🚀 Real-Time Social Media Sentiment Analysis Platform

> **End-to-End Azure Data Engineering Project** using Azure Event Hub, Azure Data Lake Storage Gen2 (ADLS Gen2), Azure Databricks, PySpark, Delta Lake, dbt, Apache Airflow, SQL, and Power BI.

---

# 📌 Project Overview

This project demonstrates an end-to-end real-time data engineering pipeline that ingests streaming social media data, processes it using the Medallion Architecture (Bronze → Silver → Gold), performs analytics transformations, and delivers interactive dashboards for business insights.

The solution is designed to simulate a production-grade Azure data platform with real-time ingestion, scalable data processing, orchestration, monitoring, and reporting.

---

# 🏗 Solution Architecture

## High-Level Architecture (HLD)

The high-level architecture illustrates the complete data flow from streaming ingestion to business reporting.

```
Social Media Data
        │
        ▼
Azure Event Hub
        │
        ▼
Azure Databricks
(Bronze Layer)
        │
        ▼
Azure Databricks
(Silver Layer)
        │
        ▼
dbt Gold Models
        │
        ▼
Azure Data Lake Storage Gen2
        │
        ▼
Power BI Dashboards
```

![High Level Architecture](Architecture/High%20Level%20Architecture.png)

---

## Low-Level Design (LLD)

The low-level design describes the detailed implementation of the pipeline, including:

* Event Hub streaming ingestion
* PySpark Structured Streaming
* Bronze Delta tables
* Silver transformation layer
* dbt Gold models
* Airflow orchestration
* Monitoring & alerts
* Dashboard refresh

![Low Level Design](Architecture/Low%20Level%20Design.png)

---

## ⭐ Star Schema

The Gold Layer follows a dimensional model optimized for analytics.

### Fact Table

* Fact_SocialMedia

### Dimension Tables

* Dim_User
* Dim_Date
* Dim_Topic
* Dim_Sentiment

![Star Schema](Architecture/Star%20Schema.png)

---

# 📊 End-to-End Data Flow

```
Social Media Source
        │
        ▼
Python Event Producer
        │
        ▼
Azure Event Hub
        │
        ▼
Azure Databricks Structured Streaming
        │
        ▼
Bronze Delta Tables
(Raw Data)
        │
        ▼
Silver Delta Tables
(Cleansed Data)
        │
        ▼
dbt Gold Models
(Business Tables)
        │
        ▼
Azure Data Lake Storage Gen2
        │
        ▼
Power BI
        │
        ▼
Business Insights
```

---

# ⚙ How Data Enters the Pipeline

### Step 1

Python Event Producer scripts continuously read CSV datasets.

Examples:

* Tweets
* Sentiment
* Trends
* User Metadata
* Valid Tweets

---

### Step 2

The producer publishes events into Azure Event Hub.

Each dataset is sent to its corresponding Event Hub.

Example:

```
Tweets
      ↓
tweet-hub

Sentiment
      ↓
sentiment-hub

Trends
      ↓
trends-hub
```

---

### Step 3

Azure Databricks Structured Streaming continuously consumes Event Hub events.

The streaming pipeline processes records in near real time.

---

### Step 4

Raw records are stored in the **Bronze Layer** as Delta tables.

---

### Step 5

PySpark transforms the Bronze data into the **Silver Layer** by applying:

* Duplicate removal
* Null handling
* Standardization
* Data validation
* Business rules
* Schema enforcement

---

### Step 6

dbt creates analytics-ready Gold tables.

These include:

* Fact tables
* Dimension tables
* Aggregate tables

---

### Step 7

Power BI connects to Gold tables to create dashboards.

---

# 🏛 Medallion Architecture

## Bronze Layer

Purpose

* Raw streaming ingestion

Tables

* bronze_tweets
* bronze_sentiment
* bronze_trends
* bronze_user_metadata
* bronze_valid_tweets

Features

* Streaming ingestion
* Delta format
* Append-only
* Audit columns
* Checkpointing

---

## Silver Layer

Purpose

Business-ready cleaned data.

Transformations

* Remove duplicates
* Handle null values
* Standardize formats
* Apply business rules
* Data quality validation
* Logging
* Exception handling

---

## Gold Layer

Business reporting layer.

Dimension Tables

* Dim_User
* Dim_Date
* Dim_Topic
* Dim_Sentiment

Fact Table

* Fact_SocialMedia

Aggregate Tables

* Daily Summary
* Country Summary
* Topic Summary
* Executive KPI

---

# 🔄 Workflow Orchestration

Apache Airflow orchestrates the pipeline.

Typical DAG

```
Start

↓

Run Bronze Streaming

↓

Run Silver Transformation

↓

Execute dbt Models

↓

Run dbt Tests

↓

Refresh Gold Tables

↓

Power BI Refresh

↓

Send Notification

↓

End
```

*(Insert your Airflow DAG image.)*

---

# 🚨 Monitoring & Alerts

Pipeline monitoring includes:

* Application logging
* Exception handling
* Pipeline execution logs
* Streaming status monitoring
* Data quality validation
* Failed job alerts
* Success notifications

*(Insert monitoring architecture or screenshots.)*

---

# 📊 Analytics Dashboards

Power BI dashboards provide:

* Executive KPI Dashboard
* Sentiment Distribution
* Trending Topics
* Tweet Volume Analysis
* Country-wise Analysis
* User Engagement
* Influencer Analysis
* Daily Activity Trends
* Positive vs Negative Sentiment
* Topic Performance

*(Insert dashboard screenshots.)*

---

# 📈 Business Insights

The platform enables:

### Sentiment Analysis

Track positive, neutral, and negative trends.

### Topic Analysis

Identify the most discussed topics.

### Geographic Analysis

Analyze sentiment by country.

### User Influence

Identify highly engaged users.

### Trend Monitoring

Monitor trending hashtags and topics.

### Peak Activity

Identify peak posting hours.

### Data Quality

Track valid versus invalid tweets.

---

# 🛠 Technology Stack

| Category        | Technology                   |
| --------------- | ---------------------------- |
| Cloud           | Microsoft Azure              |
| Streaming       | Azure Event Hub              |
| Storage         | Azure Data Lake Storage Gen2 |
| Processing      | Azure Databricks             |
| Data Processing | PySpark                      |
| Storage Format  | Delta Lake                   |
| Transformation  | dbt                          |
| Workflow        | Apache Airflow               |
| Analytics       | SQL                          |
| Visualization   | Power BI                     |
| Programming     | Python                       |
| Version Control | Git & GitHub                 |

---

# 📂 Project Structure

```
Real-Time-SocialMedia-Sentiment-Analysis
│
├── Architecture
├── Dashboard
│   ├── Dashboard Images
│   └── SQL Datasets
├── Data Ingestion
├── Datasets
├── Development
│   ├── bronze
│   └── silver
├── DBT
├── Logging
├── Testing
├── README.md
```

---

# 🚀 How to Run

1. Upload datasets to Azure Data Lake Storage Gen2.
2. Run Python Event Producer scripts.
3. Stream data into Azure Event Hub.
4. Execute Bronze notebooks.
5. Execute Silver notebooks.
6. Run dbt models.
7. Execute Airflow DAG.
8. Refresh Power BI dashboards.

---

# 🎯 Project Highlights

* End-to-End Azure Data Engineering Pipeline
* Real-Time Streaming Architecture
* Azure Event Hub Integration
* Azure Databricks Structured Streaming
* Medallion Architecture
* Delta Lake Storage
* Bronze, Silver, and Gold Layers
* dbt Data Modeling
* Apache Airflow Orchestration
* Data Quality Validation
* Logging & Monitoring
* Power BI Dashboards
* Star Schema Data Warehouse
* Production-style Data Pipeline

---
# 👥 Team Members

This project was developed collaboratively during Azure Data Engineering training.

| Team Member | Role |
|------------|------|
| Mallikarjun Mandava | DBT, Gold Layer, Star Schema, Data Modeling |
| Dara Naga Sai Sudheer | Bronze Layer, Silver Layer, Azure Databricks, PySpark, Data Pipeline Development |
| Chandrika | Data Engineering & Testing |
| Santhosh | Data Processing & Validation |
| Suhan | Analytics & Dashboard Support |

---

# 👨‍💻 Author

**Mallikarjun Mandava**

**Azure Data Engineer**

**Skills**

Azure Databricks | PySpark | Azure Event Hub | Azure Data Lake Storage Gen2 (ADLS Gen2) | Delta Lake | dbt | Apache Airflow | SQL | Python | Power BI | ETL/ELT | Data Warehousing
