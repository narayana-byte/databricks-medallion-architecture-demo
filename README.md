# databricks-medallion-architecture-demo


## Overview

This project demonstrates the implementation of the Medallion Architecture using Databricks and Delta Lake. The solution processes student performance data through Bronze, Silver, and Gold layers to transform raw data into business-ready insights.

The Medallion Architecture is a widely adopted data engineering design pattern in modern Lakehouse platforms. It enables organizations to improve data quality, maintain historical records, and provide reliable analytics for decision-making.

---

# Project Objectives

The primary objectives of this project are:

* Understand the Medallion Architecture pattern.
* Implement Bronze, Silver, and Gold layers using Databricks.
* Store data in Delta format.
* Apply data quality checks.
* Generate business-ready metrics.
* Create visualizations and dashboards.
* Demonstrate an end-to-end Data Engineering workflow.

---

# Business Scenario

An educational institution wants to analyze student performance across different courses.

The source data arrives as CSV files and contains:

* Student information
* Course details
* Scores
* Attendance percentages

The data may contain:

* Missing values
* Duplicate records
* Data quality issues

The goal is to transform this raw data into reliable business insights that can be consumed by dashboards and reports.

---

# Technology Stack

| Component         | Technology                   |
| ----------------- | ---------------------------- |
| Data Platform     | Databricks Community Edition |
| Storage Format    | Delta Lake                   |
| Processing Engine | Apache Spark                 |
| Language          | PySpark                      |
| Query Language    | SQL                          |
| Visualization     | Databricks SQL Visualization |
| Source File       | CSV                          |

---

# Medallion Architecture

The Medallion Architecture organizes data into multiple quality layers.

```text
students.csv
      │
      ▼
Bronze Layer
(Raw Data)
      │
      ▼
Silver Layer
(Cleansed Data)
      │
      ▼
Gold Layer
(Business Metrics)
      │
      ▼
Dashboard & Reporting
```

---

# Dataset Description

File Name:

students.csv

Columns:

| Column     | Description               |
| ---------- | ------------------------- |
| student_id | Unique student identifier |
| name       | Student name              |
| course     | Course enrolled           |
| score      | Student score             |
| attendance | Attendance percentage     |

Dataset Features:

* Contains null values
* Contains duplicate records
* Suitable for demonstrating data cleansing techniques

---

# Bronze Layer

## Purpose

The Bronze layer stores data exactly as received from source systems.

No transformations are applied.

The objective is to preserve the original data for auditing, troubleshooting, and reprocessing.

## Activities Performed

* Read CSV file
* Infer schema
* Store as Delta table
* Preserve raw records

## Table Created

bronze_students

## Benefits

* Maintains raw history
* Supports data lineage
* Enables reprocessing

---

# Silver Layer

## Purpose

The Silver layer focuses on improving data quality.

Data validation and cleansing rules are applied before data is used for analytics.

## Activities Performed

* Read Bronze table
* Identify missing values
* Remove records with null scores
* Prepare analytics-ready dataset

## Table Created

silver_students

## Benefits

* Improved data quality
* Reduced downstream errors
* Consistent datasets

---

# Gold Layer

## Purpose

The Gold layer contains aggregated business metrics.

This layer is optimized for dashboards, reporting, and analytics.

## Activities Performed

* Group data by course
* Calculate average score
* Calculate average attendance
* Count students per course

## Table Created

gold_student_performance

## Metrics Generated

| Metric         | Description                   |
| -------------- | ----------------------------- |
| avg_score      | Average score per course      |
| avg_attendance | Average attendance per course |
| student_count  | Total students per course     |

---

# Visualizations

The following visualizations were created using Databricks SQL.

## Average Score by Course

Purpose:

Compare academic performance across courses.

Chart Type:

Bar Chart

---

## Average Attendance by Course

Purpose:

Compare attendance levels across courses.

Chart Type:

Bar Chart

---

## Student Distribution by Course

Purpose:

Understand enrollment distribution.

Chart Type:

Pie Chart

---

# Results

The Medallion Architecture successfully transformed raw student data into business-ready insights.

Key outcomes:

* Raw data ingested successfully.
* Data quality issues addressed.
* Aggregated KPIs generated.
* Dashboard-ready dataset produced.


# Conclusion

This project demonstrates a complete Data Engineering workflow using Databricks, Delta Lake, and Medallion Architecture.

The implementation showcases how organizations can transform raw operational data into meaningful business insights through a structured Bronze → Silver → Gold pipeline.

This architecture forms the foundation of modern Lakehouse-based analytics platforms and is widely used across industries for scalable data processing and reporting.
