# Data Engineering using Microsoft Fabric

## Data Engineering
Data engineering is the practice of designing, building, and maintaining of pipelines to collect, transform, and store raw data from source systems. It enables organizations or businesses make data-driven decisions by providing curated data for end users.

## What is Lakehouse?
Lakehouse is the combination of Data Warehouse and Data Lake. It is a data storage with capabilities to store structured, semi-structure, and unstructured data optimized for analytical queries and reporting.

Data Warehouse - stores structured data in the form of tables. 
Data Lake - stores semi-structure and unstructured data. Flexible to store any type of files (e.g., Parquet, CSV, JSON, Images, videos, etc.)

## How does Data Lake work in Lakehouse?
Data Lake uses Delta format or Delta lake to gain understanding about the data. It also relies on underlying storage service to store objects (e.g., S3 on AWS, GCS on GCP, ADLS on Azure).  

When a parquet file gets uploaded to Lakehouse, the engine creates Delta log, which is a folder that contains files that tells about the descriptive context or additional information of the data (e.g., when was it uploaded? what is the schema? etc.). Parquet file defines its schema at the bottom of its payload.

If a DML operation gets committed, a corresponding JSON file will be created inside the Delta log folder. This enables the Lakehouse to have the capabitilies of Data warehouse, such as time travel, ACID transaction, indexing.

## Medallion Architecture
Medallion Architecture is a data modelling architecture with 3 key phases in managing data.

1. Bronze tier - a phase concern in ingesting data from source systemss. The copied or loaded data to semantic model stays as-is — meaning the format and actual value does not change from the original source.

2. Silver tier - is the transformation phase that processes data from Bronze tier. It curates data (e.g., creating new table, adding a new column, removing a column, removing nulls, etc.). The data made available here will be used in Gold tier.

3. Gold tier - is the delivery of data. It is the actual analytical reports and dashboard built from curated data in Silver tier.

