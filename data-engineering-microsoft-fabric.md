# Data Engineering using Microsoft Fabric

## Data Engineering
Data engineering is the practice of designing, building, and maintaining of pipelines to collect, transform, and store raw data from source systems. It enables organizations or businesses make data-driven decisions by providing curated data for end users.

## What is Lakehouse?
Lakehouse is the combination of Data Warehouse and Data Lake. It is a data storage with capabilities to store structured, semi-structure, and unstructured data optimized for analytical queries and reporting.

Data Warehouse - stores structured data in the form of tables. 
Data Lake - stores semi-structure and unstructured data. Flexible to store any type of files (e.g., Parquet, CSV, JSON, Images, videos, etc.)

## How does Lakehouse work?
Lakehouse uses Delta Lake format to gain understanding about the data. It also relies on underlying storage service to store objects (e.g., S3 on AWS, GCS on GCP, OneLake on Azure).  

When a parquet file gets uploaded to Lakehouse, the engine creates Delta log, which is a folder that contains files that tells about the descriptive context or additional information of the data (e.g., when was it uploaded? what is the schema? etc.). Parquet file defines its schema at the bottom of its payload.

If a DML operation gets committed, a corresponding JSON file will be created inside the Delta log folder. This enables the Lakehouse to have the capabitilies of Data warehouse, such as time travel, ACID transaction, indexing.

## Medallion Architecture
Medallion Architecture is a data modelling architecture with 3 key phases in managing data.

1. Bronze tier - a phase concern in ingesting data from source systemss. The copied or loaded data to semantic model stays as-is — meaning the format and actual value does not change from the original source.

2. Silver tier - is the transformation phase that processes data from Bronze tier. It curates data (e.g., creating new table, adding a new column, removing a column, removing nulls, etc.). The data made available here will be used in Gold tier.

3. Gold tier - is the delivery of data. It is the actual analytical reports and dashboard built from curated data in Silver tier.

## Microsoft Fabric
Microsoft Fabric is an end-to-end data analytics platform that goes from data lake to business users.

### Hierarchy
- Tenant / Organization
    - Capacity
        - Workspace
            - Item

| Name | Description |
| - | - |
| Capacity | The pool of resources that Microsoft Fabric uses (e.g., Memory, Compute) |
| Workspace | Logical group of items / services |
| Item | Container of a particular service (e.g., Lakehouse, Warehouse, Power BI)| 

### OneLake
OneLake is a single, unified data storage system. It is a shared storage used by all items across workspaces within the organization.

## Fabric Lakehouse
Microsoft Fabric Lakehouse is a combination of Data Lake and Warehouse with capabilities to store and manage structure, unstructure, semi-structured data. OneLake is the actual storage solution behind Fabric Lakehouse.

Lakehouse has two components:
- Files
- Tables

When you upload / dump a file to Lakehouse,  you may generate a table on top of this file. This is to enable data warehousing capability such as being able to execute analytical queries, DML operation, etc. 

In loading a table from this file, the engine converts it into a Delta Lake format, together with Delta log and metadata folder.

Table has two types:
- External = data files resides outside table itself and is user-specified. Deleting the table does not purge the data.
- Managed = contains data files in actual table itself. Deleting the table purges the actual data.

**What made Delta Lake Format so important?**
It enables capabilities that is only applicable for tables in Delta Lake Format.

For example:

**Time travel** - allows your table to be restored to a particular version  

**Optimization** - runs optimization to improve performance
- OPTIMIZE command helps to reduce number of data files by merging them into a bigger and fewer files 
- Z-ORDER sorts the data which helps improve query performance by skipping data in unnecessary partitions
- V-ORDER helps to compress the data files to improve reading speed
- Vacuum helps to save storage space by removing data files based on retention

**Streaming** - allows you to increment data to destination without having to read from entire source. 
- Enforces idempotency
- Streaming only works on external tables.
- checkpoint location must be included in streaming.

## Parquet file
Columnar-oriented data storage format designed for efficient storage and retrieval of big data for analytics.

## Fabric Shortcut
Fabric shortcuts are objects in OneLake that point to other storage locations. It can be internal or external to OneLake (e.g., S3 on AWS, GCS on GCP, etc.). It is to guarantee that there is only one true copy of data and prevent data duplication.

Shortcut can be:
- File -> file
- Table -> file
- File -> table

On top of this, you can enable caching in shortcuts as well. This reduces egress cost for transmitted data going across regions, cloud providers, and public internet by creating a temporary local copy. Take note, you have to manually reset the cache to reflect the latest changes in data.

### Internal shortcut
Use case

- If the data resides on the same OneLake, but multiple workspaces want to gain access of it, then use internal shortcut to create virtual pointer to it.

### External shortcut
Use case

- If the data is residing outside OneLake or even Fabric, for example S3 on AWS or GCS on GCP, you can still directly access the data without copying it by creating an external shortcut in your workspace.

### Lakehouse with schema
Rather than just creating a shortcut for table, you can create a shortcut for schema. Schema is a collection of tables.
For example, if you have multiple delta files within the same folder, you can create a shortcut of schema target to that folder.

### SQL endpoint
SQL endpoint is an endpoint used to gain access to Lakehouse and run SQL query against it for data analysis. Take note, a SQL endpoint is restricted to read access only. You won't be able to execute write queries to modify / create data.

## Fabric Data Factory
Fabric Data Factory allows you run Extract, Transform, and Load data ingested into OneLake by managing pipelines to orchestrate data workflows.

Pipeline is a set of activities to accomplish a certain goal.
Activity is the task or action needed to complete the pipeline.

## Notebook
Notebook allows you to explore, analyze, build and process data using different frameworks.

### PySpark
One of the frameworks designed to efficiently process Big data. It is the Python wrapper of Apache Spark.

#### Pools in Fabric
Starter pool - predefined cluster / pool of nodes. 
Custom pool - customized cluster / pool of nodes based on customer specification.

#### NotebookUtils
A built-in package that helps to easily perform common tasks in Fabric Notebook. (e.g., work with filesystems, chain Notebooks, work with secrets, etc.)

#### SparkStreaming
Allows to stream data from source to destination. It guarantees data idempotency by only applying changes in data or incrementing it.

### Environment
Allows you to create an isolated environment containing specific dependencies, runtime, configuration, resources, etc. for Notebooks.

