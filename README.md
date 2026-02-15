# Healthcare Revenue Cycle Management (RCM) Data Engineering Pipeline – Azure

This project is an end-to-end Azure Data Engineering solution built for the Healthcare Revenue Cycle Management (RCM) domain.
Revenue Cycle Management (RCM) is the financial process used by hospitals to manage billing and payments — from patient registration to insurance claim processing and final payment collection.

## Architecture Used:
The solution is built using the Medallion Architecture:
1. Landing Layer – Raw flat files from insurance providers
2. Bronze Layer – Source-of-truth data stored in Parquet format
3. Silver Layer – Cleaned, enriched, SCD Type 2 implemented Delta tables
4. Gold Layer – Aggregated fact and dimension tables for reporting

## Azure Technology Stack Used
1. Azure Data Factory (ADF) – Data ingestion & orchestration
2. Azure Databricks – Data transformation & processing
3. Azure SQL Database – EMR source system
4. Azure Data Lake Storage Gen2 (ADLS) – Data storage
5. Azure Key Vault – Secure credential management

## Datasets
1. EMR Data (Azure SQL DB)
Patients
Providers
Departments
Transactions
Encounters
Data loaded using metadata-driven incremental & full loads.

3. Claims Data (Insurance)
Monthly flat file dumps (CSV)
Loaded from Landing → Bronze

4. Healthcare Code Data
NPI (National Provider Identifier) – API
ICD Codes – API
CPT Codes – Flat files

The pipeline ingests EMR data from Azure SQL DB, insurance claims from flat files, and healthcare codes from APIs. Using Azure Data Factory and Databricks, I implemented a metadata-driven ingestion framework with incremental loading and an audit logging mechanism. Data was processed using Medallion Architecture, with SCD Type 2 implemented in the silver layer. The gold layer contains fact and dimension tables to support KPIs such as Accounts Receivable aging and Days in AR.
