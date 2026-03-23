# Data Dictionary

This document defines all tables and columns used in the Power BI data model.

- Notes:
    - **Column Name**: Must match exactly with the data model
    - **Description**: Focus on technical definition (source, transformation logic if needed).
    - **Data Type**: Use source system type or standardized type (INT, FLOAT, STRING, DATE, BOOLEAN).
    - **Business Meaning**: Explain how to interpret and use this field.


---

## Table: dim_incident

| Column Name | Description | Data Type | Business Meaning |
|-------------|------------|----------|------------------|
| IncidentID | Unique identifier of incident | INT | Key to classify production issues |
| Incident | Name/description of incident | STRING | Type of issue affecting production |
| Type | Incident category | STRING | Groups incidents (e.g., Unplanned Downtime, Planned Downtime) |

---

## Table: dim_machine

| Column Name | Description | Data Type | Business Meaning |
|-------------|------------|----------|------------------|
| MachineID | Unique machine identifier | STRING | Key for tracking machine-level performance |
| Machine | Machine name | STRING | Human-readable machine label |
| Machine Type | Machine category | STRING | Groups machines (LATHE, SAW, OTHER) |

---

## Table: dim_operator

| Column Name | Description | Data Type | Business Meaning |
|-------------|------------|----------|------------------|
| OperatorID | Unique operator identifier | INT | Key to track labor performance |
| Operator | Operator name | STRING | Person responsible for production |

---

## Table: dim_time

| Column Name | Description | Data Type | Business Meaning |
|-------------|------------|----------|------------------|
| Hour | Time value (HH:MM:SS) | TIME | Base time grain |
| Hour Number | Hour component (0–23) | INT | Used for hourly aggregation |
| Minute Number | Minute component (0–59) | INT | Enables minute-level analysis |
| Seconds Number | Second component (0–59) | INT | Fine-grain time tracking |
| AMPM | AM/PM flag | STRING | Time classification |
| Period | Time bucket | STRING | Business grouping (shift segmentation) |
| Period Sort | Sorting key for Period | INT | Ensures correct order in visuals |

---

## Table: dim_product

| Column Name | Description | Data Type | Business Meaning |
|-------------|------------|----------|------------------|
| ProductID | Unique product identifier | STRING | Key for product-level analysis |
| Description | Product description | STRING | Human-readable product name |
| ItemsPerHour | Standard production rate | FLOAT | Benchmark for productivity / OEE |

---

## Table: fact_production

| Column Name | Description | Data Type | Business Meaning |
|-------------|------------|----------|------------------|
| PO_ID | Production order ID | INT | Tracks production jobs |
| OperatorID | Foreign key to operator | INT | Links production to operator |
| IncidentID | Foreign key to incident | INT | Links downtime/issue classification |
| MachineID | Foreign key to machine | STRING | Links production to machine |
| ProductID | Foreign key to product | STRING | Links production to product |
| StartDate | Production start date | DATE | Beginning of production |
| StartTime | Production start time | TIME | Start timestamp component |
| EndDate | Production end date | DATE | End of production |
| EndTime | Production end time | TIME | End timestamp component |
| QtyProduced | Quantity produced | INT | Output volume |
| QtyRejected | Quantity rejected | INT | Quality loss |
| Hours | Total production duration | FLOAT | Used for utilization / OEE |

---