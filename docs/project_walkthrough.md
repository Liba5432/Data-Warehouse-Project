# Data Warehouse Project (SQL)

In this project, I built a data warehouse using SQL Server. I collected data from various sources (ETL), structured it clearly (data modeling), and created dashboards for insights, following best practices to ensure the system is efficient, reliable, and easy to use.

- [Project Requirements](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/docs/project_requirements.md)
- [Naming Convention](https://github.com/Liba5432/Data-Warehouse-Project/blob/main/docs/naming_convention.md): *Conventions used across scripts and tables*
- [Datasets](https://github.com/Liba5432/Data-Warehouse-Project/tree/main/datasets): *Original CRM and ERP CSVs*
- [Notion Project Steps] (https://www.notion.so/Data-Warehouse-Project-22c7873853dd801286dcdc81ce2daecd?source=copy_link)
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

### 🔍 Bronze, Silver, Gold Layer Guide

![image](https://github.com/user-attachments/assets/f0640eaa-8f03-4313-84cf-14163dc63eb7)
---

### 🗄️ Initial Setup – Database & Schemas

The setup was initialized in SQL Server Management Studio (SSMS) using a script that creates a new database named DataWarehouse. If an existing version of the database is found, it is dropped and recreated. The script also defines three schemas — bronze, silver, and gold — which represent the layers of the Medallion Architecture.






