# Netflix Data Engineering Project

## Overview

This project builds a scalable ETL (Extract, Transform, Load) pipeline for analyzing Netflix's content catalog, using Azure Data Engineering tools. The goal is to create a data pipeline that automates the ingestion, transformation, and visualization of Netflix content data to derive meaningful insights on content distribution, genre popularity, and content trends. The project incorporates Azure Synapse Analytics, Data Lake Storage, Data Factory, and Power BI.

## Dataset

- **Source**: [Netflix Titles dataset on Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows)
- **Description**: Contains metadata for Netflix's movies and TV shows, including details like title, director, cast, country, date added, release year, rating, duration, genre, and description.

## Architecture

1. **Data Storage**:
   - Azure Blob Storage hosts the raw data, while Azure Data Lake Storage (ADLS) is used to store data across Bronze, Silver, and Gold layers.

2. **Data Processing**:
   - **Bronze Layer**: Stores raw data from the source without transformation.
   - **Silver Layer**: Cleaned data with duplicates removed, nulls handled, and columns cast to appropriate data types.
   - **Gold Layer**: Aggregated data optimized for analytics, with metrics like genre counts, release counts per year, and monthly additions.

3. **Data Transformation**:
   - Azure Synapse Analytics and PySpark are used for transformations across Bronze, Silver, and Gold layers.

4. **Data Visualization**:
   - Power BI is used to create interactive dashboards and reports, connecting directly to the Gold layer in Synapse.

## Steps to Execute

### 1. Data Ingestion
   - Use SQL Server Management Studio (SSMS) to connect to the database, import the Netflix dataset, and transfer it to Blob Storage.
   - Azure Data Factory (ADF) is configured with a pipeline to copy data from SQL Server to the Blob storage's raw container.

### 2. Data Transformation
   - **Bronze Layer**: Store raw data in ADLS Gen2.
   - **Silver Layer**: Use PySpark in Synapse Analytics to clean the data, removing duplicates and nulls, and save it in Parquet format.
   - **Gold Layer**: Further transformations and aggregations (e.g., counts by genre and release year), stored as Parquet files.

### 3. Data Modeling
   - External tables in Synapse SQL Pool allow Power BI to connect and access pre-aggregated Gold layer data.

### 4. Reporting with Power BI
   - Connect Power BI to Synapse SQL Pool to create visualizations, including genre distributions, yearly release trends, and monthly content additions.

## Key Findings

- **Top Genres**: Insights into the most popular genres and trends.
- **Regional Content**: Analysis of content distribution by country.
- **Content Growth**: Historical trends of Netflix's content catalog additions.

## Challenges & Solutions

- **Integration Runtime Setup**: Configured self-hosted integration for on-premises SQL to Azure.
- **Data Transformation**: Handled null values, duplicates, and data type mismatches.
- **Performance Optimization**: Used Parquet format and Synapse Analytics for efficient storage and querying.

## Future Enhancements

- **Data Quality Checks**: Automate data validation to improve reliability.
- **Enhanced Visualizations**: Expand Power BI reports for deeper insights.
- **Error Handling**: Implement advanced error logging and handling in the pipeline.

## Conclusion

This project demonstrates a robust Azure-based ETL pipeline for managing Netflix content data. With automation, scalability, and efficient visualization, this solution offers a comprehensive foundation for data analysis and insights.



