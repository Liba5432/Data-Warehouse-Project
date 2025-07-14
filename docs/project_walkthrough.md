# Data Warehouse Project (SQL)

In this project, I built a data warehouse using SQL Server. I collected data from various sources (ETL), structured it clearly (data modeling), and created dashboards for insights, following best practices to ensure the system is efficient, reliable, and easy to use.

- [Project Requirements](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/docs/project_requirements.md)
- [Naming Convention](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/docs/naming_convention.md): *Conventions used across scripts and tables*
- [Datasets](https://github.com/Liba5432/Data-Warehouse-Project/tree/main/datasets): *Original CRM and ERP CSVs*
- [Notion Project Steps](https://www.notion.so/Data-Warehouse-Project-22c7873853dd801286dcdc81ce2daecd?source=copy_link)
---

### 🧠 Datawarehouse Approach

The diagram below outlines multiple data warehouse designs. For this project, I used the **Medallion pattern** for its clarity and ability to support scaling.

![image](https://github.com/user-attachments/assets/c7ef2d68-222d-4364-bce7-9c51ff6228bf)

This model separates data into three layers:
- 🥉 **Bronze**: raw imports  
- 🥈 **Silver**: cleansed and validated  
- 🥇 **Gold**: organized for business reporting
---

### 🏛️ Data Architecture

This visualization maps how files move from the source systems through each processing layer into the warehouse.

![image](https://github.com/user-attachments/assets/1357cc52-cc93-4661-9ae8-b3f7eef4450a)

---

### 🗂️ Bronze, Silver, Gold Layer Guide

![image](https://github.com/user-attachments/assets/f0640eaa-8f03-4313-84cf-14163dc63eb7)

---

### 🗄️ Initial Setup – Database & Schemas

The setup was initialized in SQL Server Management Studio (SSMS) using a script that creates a new database named DataWarehouse. If an existing version of the database is found, it is dropped and recreated. The script also defines three schemas — bronze, silver, and gold — which represent the layers of the Medallion Architecture.

[Database & Schemas Script](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/scripts/init_database.sql)

### 🔍 Validation

After running the script:

1. Open `Object Explorer`
2. Navigate to `Databases → DataWarehouse → Security → Schemas`

You should see: `bronze`, `silver`, `gold`

---

### 🔄 ETL Overview

The diagram below highlights various techniques in an ETL (Extraction, Transformation, Load) pipeline. The elements marked are the ones implemented for this solution:

![image](https://github.com/user-attachments/assets/15e6b9dc-c698-4fd3-a19c-c0afe16a83dd)

---

## 🥉 Bronze Layer – Raw Input Storage

The Bronze Layer captures data in its untouched format straight from CSV files sourced from CRM and ERP systems. This preserves traceability and makes debugging easier.

Process Steps:

![image](https://github.com/user-attachments/assets/a43d7f8f-af04-4a4a-8e93-bbb136fea6d9)

The files were reviewed alongside any available documentation or input from data owners to identify field formats, separators, and structural patterns.

![image](https://github.com/user-attachments/assets/bf601bb5-4018-4e91-b670-4cffe2710145)

### 🛠️ Coding and Validating 

[DDL Script for Silver Layer](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/scripts/bronze/ddl_bronze.SQL) - *Creates the bronze tables*

[Stored Procedure for Bronze Layer](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/scripts/bronze/proc_load_bronze.sql) - *Uses `BULK INSERT` to import CSV data*

Bronze tables were created using a DDL script. A stored procedure loaded data from CSV files into these tables using BULK INSERT. After loading, simple checks were done to confirm row counts and correct column alignment.

---

### 🥈 Silver Layer – Data Cleaning & Refinement

In the Silver Layer, the focus is on preparing clean, usable datasets by removing duplicates, correcting errors, and enforcing formats.

Process Steps:

![image](https://github.com/user-attachments/assets/87c72f27-422e-425e-8d45-9c54bc955b6a)

### 🔗 Data Integration
Before creating the silver tables, the data in the bronze layer was reviewed to understand how the tables were connected (like CustomerID linking data from CRM and ERP). This helped write clearer transformation steps.

![image](https://github.com/user-attachments/assets/a4ef5148-6f7a-4cc1-95bc-6369292c838b)

### 🛠️ Coding and Validating 

[DDL Script for Silver Layer](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/scripts/silver/ddl_silver.sql) - *Sets up the structure for the cleaned (silver) tables.*

[ETL Stored Procedure for Silver Layer](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/scripts/silver/proc_load_silver.sql) - *Applies cleaning rules and loads the data into silver tables.*

[Data Quality Check for Silver Layer](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/tests/quality_checks_silver.sql) - *Verifies the quality of cleaned data in the silver layer*

Silver tables were built with an updated DDL script. The ETL procedure extracted data from Bronze, cleaned it, and inserted it into the Silver tables. Data quality was checked before and after loading.

---

### 🥇 Gold Layer – Business-Ready Data

In this final layer, I modeled the cleaned data into dimensions and facts that support clear analysis, reporting, and business understanding.

Process Steps:






