# Big Data Processing with PySpark on GCP Dataproc

## Project Overview

This project focuses on implementing a scalable data engineering pipeline using Apache Spark on Google Cloud Dataproc. The workflow involves data ingestion, cleaning, transformation, integration, optimization, and serving to enable efficient large-scale data processing.

## Tech Stack & Tools Used

- Apache Spark (PySpark for distributed data processing)

- Google Cloud Platform (GCP) (Dataproc for cluster computing, HDFS for storage)

- Kaggle (Data source for the Brazilian E-commerce dataset)

- Parquet, Hive, CSV (Data storage formats)

- Shell & Python (For automation and scripting)

## Project Workflow

### Setting Up the Spark Environment

In a production setting, instead of using Google Colab, we:

1. Deploy a Spark Cluster using GCP Dataproc.

2. Store Data in HDFS instead of local storage.

3. Use PySpark for efficient data interaction.

Data Ingestion: The dataset is fetched from Kaggle and extracted into the required storage format.

```
#!/bin/bash
curl -L -o ~/olist/brazilian-ecommerce.zip \
https://www.kaggle.com/api/v1/datasets/download/olistbr/brazilian-ecommerce
unzip brazilian-ecommerce.zip -d ~/olist/data/
```

### Module 1: Data Ingestion and Exploration

- Store raw data into HDFS/Object Storage.

- Use Spark DataFrames for scalable operations.

- Perform initial exploration focused on business use cases.

- Document all findings for future reference.

### Module 2: Data Cleaning and Transformation

This module covers real-world data engineering best practices for cleaning and transforming large-scale data using PySpark.

Steps in Data Cleaning & Transformation:

1. Identify Issues: Detect missing values, duplicates, and invalid data.

2. Handle Missing Values: Drop or impute null values.

3. Standardize Formats: Convert datetime, normalize categorical fields.

4. Correct Data Types: Ensure proper data type usage.

5. Deduplication: Remove duplicate records.

6. Feature Engineering: Transform raw data into structured insights.

7. Store Cleaned Data: Save processed data in HDFS (Parquet format).

### Module 3: Data Integration and Aggregation

- Join Datasets Efficiently using Spark's distributed join strategies.

- Optimize Joins by tuning broadcast join threshold.

- Perform Aggregations to generate insights.

- Cache & Optimize Queries for better performance.

### Module 4: Performance Optimization

Key Considerations for Dataproc Cluster Configuration

1. Cluster Resources:

- Master Node: n2-standard-4 (4 vCPUs, 16 GB RAM, 32GB disk)

- Worker Nodes (x2): n2-standard-4 (4 vCPUs, 16 GB RAM, 64GB disk each)

- Total Resources: 8 worker vCPUs, ~32 GB RAM (excluding master node)

2. Dataproc Features Disabled:

- No autoscaling, Metastore, or advanced optimizations.

- Storage Type: pd-balanced (no SSDs, so I/O tuning is crucial).

- Networking: Internal IP enabled.

3. Optimization Strategies:

- Tune shuffle partitions, broadcast join thresholds, and storage persistence.

- Adjust parallelism based on 2 workers x 4 cores.

- Avoid excessive caching due to disk-based storage constraints.

### Module 5: Data Serving

- Store and retrieve processed data efficiently in Dataproc.

- Serve structured data for analysis & reporting.

- Use Parquet, Hive, and CSV for optimized storage and retrieval.

## Conclusion

This project provides a scalable, cloud-based data processing pipeline using PySpark on GCP Dataproc. It demonstrates best practices in data ingestion, cleaning, transformation, integration, and optimization, ensuring efficient data processing for industrial-scale applications.
