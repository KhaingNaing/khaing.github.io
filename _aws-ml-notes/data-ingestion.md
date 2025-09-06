---
layout: page
title: "Data Ingestion"
parent: "AWS ML Certification Study Note"   # optional if your theme uses it
nav_order: 1
---
This post is all about types of data, their properties.


## Type of Data
In this certification, we will be tested on 3 main types of data:
1. Structure Data
2. Unstructure Data
3. Semi-structure Data

 | Type of Data | Definition | Characteristics | Examples |
 |-|-|-|-|
 | structure | organized in a defined manner or schema | easily queryable | database tables, csv, excel |
 | unstructure | doesn't have a predefined structure or schema | not easily queryable without preprocessing | text files, videos & audio files, images, emails |
 | semi-structure | not as organized as structure but has some level of structure  | more flexible than structured but not as chaotic as unstructured | xml & json, email headers, log files |

## Properties of Data (3 Vs)
- Volume
- Velocity 
- Variety

 | Properties of Data | Definition | Characteristics | Examples |
 |-|-|-|-|
 | Volume | size of data to deal with at any given time | challenges in storing, processing and analyzing high volumes of data | social media platform processing TB of data daily |
 | Velocity | speed at which new data is generated, collected and processed | real-time or near-real-time processing, rapid ingestion and processing (batch?) | high frequency trading systems |
 | Variety | different types, structures and sources of data  | data can come from multiple sources and in various formats | businesses analyzing data from RDS (structured), emails (unstructured), JSON logs (semi-structured) |

## Data Warehouse vs Data Lakes
| Data Warehouse | Data Lake |
|-|-|
| stored data in a structured format | stored data in its native/raw format |
| ETL (schema-on-write) | ELT (schema-on-read) |
| less agile | more agile |
| for analysis, read-heavy operations | can store large volumes of raw data; supports batch, real-time, and stream processing |
| more expensive | cost-effective |
| e.g., Amazon Redshift | e.g., Amazon Simple Storage Service (s3)

**Use a Data Warehouse when**:
- dealing with structured data 
- require fast and complex queries 
- provide performance, reliability and capabilities 
- Use Case: business intelligence & analytics

**Use a Data Lake when**:
- dealing with mix data formats 
- require scalable and cost-effective to store massive amounts of data 
- provide flexibility, scale and low-cost storage
- Use Case: advanced analytics, ML or data discovery 

## Data Lakehouse
- combines the best features of data lakes and data warehouse 
- e.g., AWS Lake Formation (with S3 and Redshift Spectrum)

## Data Mesh 
- Domain-based data management: more about governance and organization rather than specific technology

## ETL Pipelines 
Process to move data from source systems into a **data warehouse**.
- **Extract**: 
  - retrieve raw data from source systems
  - ensure data integrity
  - in real-time or in batches 

- **Transform**:
  - convert the extracted data into a predefined schema
  - involve operations such as:
    - data cleaning
    - data enrichment
    - format changes 
    - aggregations or computations
    - encoding or decoding data
    - handling missing values 

- **Load**:
  - move the transformed data into target data warehouse
  - in batches or in a streaming manner
  - ensure data integrity 
- Can be automated using:
  - AWS Glue
  - Orchestration services 
    - EventBridge
    - Amazon Managed Workflows for Apache Airflow 
    - AWS Step Functions 
    - Lambda 
    - Glue Workflows

## Data Sources
- **JDBC**: Java Database Connectivity
  - platform independent
  - language dependent
- **ODBC**: Open Database Connectivity 
  - platform dependent
  - language independent 
- **Raw logs**
- **API's**
- **Streams**

## Data Formats
- CSV:
  - for small to medium datasets
  - for data interchange between systems with different technologies 
  - for human-readable and editable data 
  - import/export data from databases or spreadsheets
  - **systems**: 
    - Databases (SQL based)
    - Excel 
    - Pandas, R
    - many ETL tools 
- **JSON**:
  - for lightweight, text-based & human-readable data 
  - for data interchange between a web server and client
  - configurations and settings for software apps
  - when need a flexible schema or nested data structures
  - **systems**:
    - Web browser
    - many programming languages (python, java etc)
    - RESTful APIs
    - NoSQL 
    - Databases (like MongoDB)
- **Arvo**:
  - binary format stores both the data and it schema 
  - for big data and real-time processing systems
  - when changes in data structure is needed (schema evolution)
  - efficient serialization for data transport 
  - **systems**:
    - Apache Kafka
    - Apache Spark 
    - Apache Flink
    - Hadoop ecosystem 
- **Parquet**:
  - columnar storage format optimized for analytics
  - for analyzing big datasets with analytics engines
  - for accessing specific columns instead of entire records
  - for storing data on distributed systems where IO operations and storage need optimization
  - **systems**:
    - Hadoop ecosystem 
    - Apache Spark 
    - Apache Hive 
    - Apache Impala
    - Amazon Redshift Spectrum
