 # retail data engineering project

## Overview

This project simulates a real-world enterprise retail data platform
implementation using SQL Server and SSIS. The objective is to design,
build, secure, and automate a complete data pipeline consisting of:

-   A **RetailStaging** database (raw ingestion layer)
-   A **RetailDataWarehouse** database (Star Schema warehouse)
-   SSIS automation for loading 12 monthly CSV files
-   Role-based access control (RBAC)
-   Analytical views for business reporting

The dataset represents retail sales transactions from January to
December 2025, with 100,000 records per month (1.2 million total
records).

------------------------------------------------------------------------

## Architecture

### Databases

1.  **RetailStaging**
    -   Stores raw CSV data
    -   No transformations allowed
    -   Used as ingestion layer
2.  **RetailDataWarehouse**
    -   Implements Star Schema design
    -   Contains dimension tables and fact table
    -   Used for reporting and analytics

------------------------------------------------------------------------

## Data Model (Star Schema)

### Fact Table

-   **FactSales**
    -   Quantity
    -   UnitPrice
    -   TotalAmount
    -   Foreign Keys:
        -   ProductKey
        -   StoreKey
        -   CashierKey
        -   DateKey

### Dimension Tables

-   DimProduct
-   DimStore
-   DimCashier
-   DimDate

------------------------------------------------------------------------

## ETL Process (SSIS Required)

All data loading must be automated using SSIS:

-   Load 12 CSV files into RetailStaging
-   Populate dimension tables
-   Populate fact table
-   Ensure idempotent (re-runnable) package design
-   Include logging and error handling

Manual BULK INSERT statements are not allowed.

------------------------------------------------------------------------

## Security & Roles

### StoreManager

-   Full control
-   Can insert, update, delete
-   Can execute SSIS packages

### DataAnalyst

-   Read-only access to RetailDataWarehouse
-   Can create analytical views
-   Cannot modify tables

### CashierUser

-   Read-only access to reporting views only
-   Cannot access staging tables
-   Cannot modify data

------------------------------------------------------------------------

## Required Analytical Views

-   vw_DailySales
-   vw_StorePerformance
-   vw_CategoryRevenue
-   vw_Top10Products
-   vw_CashierPerformance
-   vw_ProvinceRevenue
-   vw_MonthlySalesSummary

------------------------------------------------------------------------

## Learning Outcomes

-   Enterprise database architecture
-   Dimensional modelling (Star Schema)
-   SSIS automation
-   SQL Server security implementation
-   Retail analytics development
-   Real-world data engineering practices

------------------------------------------------------------------------

## Deliverables

-   SQL script file
-   SSIS package
-   Completed analytical views
-   Documentation
-   Final presentation/demo

------------------------------------------------------------------------

