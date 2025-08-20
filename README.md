# SQL_Project_data_warehouse

Welcome to the **Data Warehouse and Analytics Project** repository! 🚀  
This project showcases a comprehensive data warehousing and analytics solution, from building a data warehouse to generating actionable insights. Designed as a portfolio project, it highlights industry best practices in data engineering and analytics.

---

## 🏗️ Data Architecture

The data architecture for this project follows Medallion Architecture **Bronze**, **Silver**, and **Gold** layers:

![Data Architecture](images/Design_Data_Architecture.png)


1. **Bronze Layer**: Stores raw data as-is from the source systems. Data is ingested from CSV Files into SQL Server Database.
2. **Silver Layer**: This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.
3. **Gold Layer**: Houses business-ready data modeled into a star schema required for reporting and analytics.

---

# General Principles:

- Naming Convetions: snake_case, with lowercase letters and underscores (_) to separate words. 
- Example: customer_info ← Lowercase | Underscor | Lowercase.
- Language: Use English for names. Spanish/English for comments.
- Avoid Reserved Words: Do not use SQL reserved Words as object Names.

## 📖 Project Overview

This project involves:

1. **Data Architecture**: Designing a Modern Data Warehouse Using Medallion Architecture **Bronze**, **Silver**, and **Gold** layers.
2. **ETL Pipelines**: Extracting, transforming, and loading data from source systems into the warehouse.
3. **Data Modeling**: Developing fact and dimension tables optimized for analytical queries.
4. **Analytics & Reporting**: Creating SQL-based reports and dashboards for actionable insights.

# **Bronze Layer** 

Store raw data as-is from the source systems. Data is ingested from CSV files into SQL Server.

We used the bulk insert option from SQL to populate our tables. The tables are created to correspond to the tables needed. At the same time, we created Procedures to facilitate future updates.

**Final documents:**
- Creation of tables.
- Bulk insert of information.
- Creation of BRONZE procedure to facilitate future inserts or new information.

**Queries:**
- scripts/bronze/proc_load_bronze.sql

This stored procedure loads data into the 'bronze' schema from external CSV files. It performs the following actions:
    - Truncates the bronze tables before loading data.
    - Uses the `BULK INSERT` command to load data from csv Files to bronze tables.
 

- scripts/bronze/ddl_bronze.sql

This script creates tables in the 'bronze' schema, dropping existing tables if they already exist. Run this script to re-define the DDL structure of 'bronze' Tables

![Data_Bronze](images/data_flow_diagram_bronze.png)

# **Silver Layer** 

This layer includes data cleansing, standardization, and normalization processes to prepare data for analysis.

Re-define the tables from bronze sctructure. Change the data types and the information needed.

**Final documents:**

- Creation of SILVER procedure to facilitate future inserts transformed and cleansed data from Bronze into Silver tables.

**Querires:**

 - scripts/silver/ddl_silver.sql

This script creates tables in the 'silver' schema, dropping existing tables if they already exist. Run this script to re-define the DDL structure of 'bronze' Tables

- scripts/silver/proc_load_silver.sql 
    
 This stored procedure performs the ETL (Extract, Transform, Load) process to populate the 'silver' schema tables from the 'bronze' schema.
 
Actions Performed:
		- Truncates Silver tables.
		- Inserts transformed and cleansed data from Bronze into Silver tables.
  
![Data_Silver](images/data_flow_diagram_silver.png)

