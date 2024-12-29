## PySpark ETL Pipelines with Factory Pattern


## Project Overview:
This project demonstrates the creation of multiple ETL (Extract, Transform, Load) pipelines using the Python API of Apache Spark, PySpark, within the DataBricks environment. The goal of the project is to process and transform data from various sources (CSV, Delta tables) and load the processed data into DBFS (Databricks File System) and Delta tables. The project also implements the Factory Design Pattern to streamline the creation of different data source readers for flexibility and scalability.

## Key Features:
**Data Sources:** CSV files and Delta tables
**Design Pattern:** Factory Pattern to abstract data reading logic
**Transformation Logic:** Applied using PySpark DataFrame API and Spark SQL
**Data Loading:** Writing data to DBFS and Delta tables
**Scalability:** Designed to handle large volumes of data efficiently in Databricks.

## Technology Stack:
Apache Spark (PySpark)
DataBricks (for managing the cluster and running ETL pipelines)
Python (for scripting the ETL logic)

## Architecture:
**1. Extract**
In this phase, we read data from various sources:

* CSV files: CSV files stored in cloud storage or DBFS are read using PySpark’s spark.read.csv() method.
* Delta Tables: Data from Delta tables is read using spark.read.format("delta").load().

**2. Factory Pattern**
We implemented the Factory Pattern to create a Reader class. The Factory Pattern is used to abstract the logic for reading from different data sources. This ensures that adding a new data source in the future does not require significant changes to the existing code. Here is a brief description of how the Factory Pattern is applied:

* A Factory class is responsible for instantiating the correct data reader class (CSV reader, Delta reader, etc.) based on the data source type.
* Each reader class contains the logic for reading data from its respective source.

**3. Transform**
Data transformation is done using the PySpark DataFrame API and Spark SQL. Business logic transformation includes tasks such as:

* Data cleaning (removing duplicates, handling missing values)
* Aggregations and joins
* Applying business rules and calculations
* The transformations are written using Spark DataFrame API.

**4. Load**
The processed data is loaded into the following storage locations:

* DBFS: The data is written to DBFS (Databricks File System) in formats like CSV or Parquet.
* Delta Table: The processed data is also loaded into a Delta table for fast querying and ACID transactions.

**Folder Structure:**

├── Data
│   ├── raw data  
│ 
├── Extract
│   ├── extractor.ipynb
│   ├── reader_factory.ipynb
│   
├── Transformer
│   ├── transform.ipynb
│ 
├── Load
│   ├── loader.ipynb
│   ├── loader_factory.ipynb
│
├── Main_Analysis
│   ├── apple_analysis.ipynb
    

## Conclusion:
This project highlights the use of PySpark in DataBricks to create scalable and maintainable ETL pipelines. By implementing the Factory Pattern, we've made the code more flexible, allowing for easy expansion with additional data sources in the future. The project also emphasizes the importance of using Delta Lake for handling large-scale data processing with ACID transactions.
