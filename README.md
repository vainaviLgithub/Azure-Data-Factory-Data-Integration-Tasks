

---

#  Azure Data Factory Data Integration Tasks

---

##  Overview

This document describes the processes implemented using **Azure Data Factory (ADF)** for integrating, extracting, and loading data from various sources like **on-premises servers**, **FTP/SFTP servers**, and **incremental loading pipelines** into **Azure SQL Database**. These pipelines are automated to run on specific schedules, ensuring efficient, secure, and reliable data movement for cloud-based analytics and reporting.

---

##  Technologies Used

* Microsoft Azure Data Factory
* Self-hosted Integration Runtime (SHIR)
* Azure SQL Database
* FTP/SFTP Server
* Incremental Load Techniques (Watermarking, Change Tracking)
* Azure Triggers (Time-based and Custom)
* Azure Portal
* SQL Server Management Studio / Azure Query Editor

---

##  Task Process

---

### 1 Configure Self-hosted Integration Runtime (SHIR)

**Purpose:**
Securely connect Azure Data Factory to an on-premises/local server to extract data and load it into Azure SQL Database.

**Key Steps:**

* Install and register **Self-hosted Integration Runtime** on local machine.
* Configure linked services in ADF for both **local SQL Server/CSV file** and **Azure SQL Database**.
* Create a pipeline with a **Copy Data activity**.
* Test connection and run the pipeline.
* Validate data in Azure SQL Database.

**Key Concepts:**

* Secure data movement across network boundaries.
* Hybrid data integration.

---

### 2 Configure FTP/SFTP Server and Create ADF Pipeline for Data Extraction

**Purpose:**
Extract data from external **FTP/SFTP servers** and ingest into Azure SQL Database for integrated processing.

**Key Steps:**

* Set up FTP/SFTP server credentials and configure an **FTP Linked Service** in ADF.
* Define a **dataset** pointing to the FTP file.
* Create a **Copy Data pipeline** from FTP to Azure SQL.
* Test pipeline and validate data transfer.

**Key Concepts:**

* Secure file transfer.
* Partner system integrations.

---

### 3 Create Incremental Load Pipeline and Automate on a Daily Basis

**Purpose:**
Optimize data processing by transferring only new or modified records instead of full data loads.

**Key Steps:**

* Implement **Watermark columns** (like `ModifiedDate`, `LastUpdated`).
* Create a pipeline with **Lookup**, **Stored Procedure**, and **Copy Data** activities.
* Set a **daily trigger** using Azure Triggers.
* Test incremental logic by modifying source records and confirming selective loads.

**Key Concepts:**

* Incremental load via **Watermarking/Change Tracking**.
* Performance optimization.

**Learning:**
Avoid redundant data transfer and improve efficiency.

---

### 4 Automate a Pipeline to Trigger Every Last Saturday of the Month

**Purpose:**
Schedule batch jobs for periodic reporting or large-scale data processing.

**Key Steps:**

* Create a pipeline for data processing.
* Configure a **time-based trigger** with a custom **CRON expression** for the last Saturday of each month.
* Publish and monitor trigger runs.

**Key Concepts:**

* Custom scheduling using **Azure Triggers** and **CRON expressions**.

**Learning:**
Automated scheduled pipelines remove manual intervention.

---

### 5 Implement Retry Logic for Data Retrieval Failures

**Purpose:**
Handle transient errors gracefully during data extraction or transfer operations.

**Key Steps:**

* Configure **retry policies** in **Copy Data activities**.
* Set **retry count** and **interval in seconds**.
* Monitor pipeline run status.
* Test by simulating transient failures.

**Key Concepts:**

* Resilience and fault tolerance in **ETL pipelines**.

**Learning:**
Minimizes job failure rates, improving pipeline reliability.

---

##  Learnings Summary

* How to securely connect **on-premises data sources** to Azure using **Self-hosted Integration Runtime**.
* Integrating external systems via **FTP/SFTP** into Azure Data Factory.
* Designing efficient **incremental load** strategies.
* Automating data workflows using **custom triggers**.
* Implementing **retry mechanisms** for enhanced pipeline resilience.
* Using Azure Data Factory’s **Monitoring tab** to track pipeline runs, activity success/failure, and data movement logs.
* Understanding **real-world enterprise ETL pipeline patterns**.

---

