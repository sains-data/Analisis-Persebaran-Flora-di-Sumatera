# 📊Analysis of Flora Distribution in Sumatra Through Data Lake System Using Descriptive Spatial Analysis Based on Hadoop and Apache Spark
Welcome to the Flora Distribution Analysis in Sumatra repository! 🌿 This project presents a comprehensive approach to analyzing flora species distribution across the island of Sumatra using Data Lake systems and descriptive spatial analysis techniques. Built on Hadoop and Apache Spark infrastructure, this project demonstrates large-scale geographic data processing to generate actionable ecological insights. Designed as a portfolio project, this repository showcases the implementation of best practices in geospatial data analysis, biodiversity conservation, and distributed data processing.

**Team Members:**
- Asa Doa Uyi (122450005)
- Elok Fiola (122450051)
- Dea Mutia Risani (122450099)
- Yohana Manik (122450126)

---
## 🏗️ **System Architecture**

### Service Layer Distribution

| Layer                | Services                              | Technology           | Ports            | Purpose                    |
|----------------------|----------------------------------------|-----------------------|------------------|-----------------------------|
| **Storage Layer**    | NameNode, DataNode, HistoryServer      | Hadoop 3.4.1          | 9870, 9864, 8188 | Distributed file system     |
| **Resource Management** | ResourceManager, NodeManager       | YARN (Hadoop)         | 8088, 8042       | Cluster resource allocation |
| **Batch Processing**  | Spark Master                          | Spark 3.5.4           | 8080             | Large-scale data processing  |
| **SQL Interface**     | Hive Server                           | Hive 4.0.1             | 10000, 10002     | Data warehouse queries   |
| **NoSQL Database**     | HBase Master, RegionServer          | HBase 2.6.1             | 16010, 16030     | Fast NoSQL data access   |


---
## 📖 **Project Overview**
This project is an end-to-end implementation of a Big Data–based spatial analytics system designed to understand and map the distribution patterns of flora in the Sumatra region. The project is developed using the **Waterfall methodology**, which provides a systematic, measurable, and well documented process structure. Each phase is executed sequentially and thoroughly from planning, data collection and storage, transformation, and spatial analysis, to the final presentation of results in the form of informative visualizations.

💡 **Key System Components:**
- **Data Lake Design**: Implements the Medallion Architecture (Bronze → Silver → Gold) to organize data based on processing stages. Raw data from external sources is ingested into the Bronze layer, transformed data is moved to the Silver layer, and analysis-ready data is stored in the Gold layer.
- **Data Source & Initial Storage**: The primary dataset is obtained from GBIF (Global Biodiversity Information Facility), consisting of flora records from Sumatra including species names, observation locations (GPS coordinates), observation times, and additional ecological attributes. Raw data is loaded into the Hadoop Distributed File System (HDFS) as the Bronze layer to ensure distributed and fault-tolerant storage.
- **Data Transformation & Cleaning**: Using MapReduce and Apache Hive, the data is processed in the Silver layer. This process includes removing duplicates and null values, validating spatial data, and enriching the dataset with additional ecological attributes to prepare it for further analysis.
- **Structured Storage**: After the transformation stage, the data is stored in HBase as a structured storage layer in the Gold stage. This enables fast access for advanced analysis and supports large-scale spatial queries.
- **Spatial Analysis**: The processed data is used to identify flora distribution patterns, analyze their correlation with topography and administrative zones, and detect biodiversity hotspots across Sumatra.


---
## 🛠 **Key Focus Areas**
-  Hadoop Distributed File System (HDFS)
-  Apache Hive
-  Apache Spark
-  Apache HBase
-  Docker

---
## ⚙️ **System Components & Tech Stack**
| Component         | Role                          |
|-------------------|-------------------------------|
| **Hadoop HDFS**   | Distributed storage for raw data (Bronze Layer) |
| **Apache Spark**  | Data cleaning, transformation, and aggregation (Silver → Gold Layer) |
| **Apache Hive**   | SQL-based querying and metadata management |
| **Apache HBase**  | NoSQL storage for processed data (Gold Layer) |
| **Docker**        | Containerized cluster deployment |
| **Apache Superset** | Dashboard for visualizing flora distribution |


---
## 🔄 **Workflow DAG (Airflow)**
```plaintext
dag_flora_distribution_pipeline:
├── task_1: fetch_flora_data_from_GBIF
├── task_2: load_raw_data_to_HDFS (Bronze Layer)
├── task_3: run_spark_cleaning (Silver Layer)
├── task_4: aggregate_data_and_cluster_analysis (Gold Layer)
├── task_5: register_hive_tables_and_refresh_metadata
├── task_6: update_visualizations_on_superset_dashboard
└── task_7: notify_team_on_completion

---
## 🗂️ **Folder Structure**
```text
Analisis-Persebaran-Flora-di-Sumatera
├── data/
│   └── flora_sumatera.csv
├── hdfs/
│   └── core-site.xml
├── hive/
│   └── create_tables.hql
├── spark/
│   └── transform_flora.py
├── hbase/
│   └── hbase_commands.txt
├── docker-compose.yml
├── README.md
└── LICENSE

---

## 🚀 **Setup & Deployment**

### 1. Prerequisites

- Docker + WSL2 (Windows) / Docker Desktop (macOS/Linux)  
- Python 3.8+ (for data ingestion scripts)  

### 2. Run the Hadoop-Spark Cluster

```bash
git clone https://github.com/sains-data/Analisis-Persebaran-Flora-di-Sumatera.git
cd Analisis-Persebaran-Flora-di-Sumatera
docker-compose up -d  # Launches Hadoop, Spark, Hive, and HBase
```

---

## 📌 **Sample Use Case:**

### Scenario: Identifying Conservation Hotspots of Endangered Flora in Sumatra

**Problem:**  
Conservation agencies need to understand which regions in Sumatra have high concentrations of endangered flora to allocate protection efforts.

**Approach:**

1. Load biodiversity data from GBIF into HDFS (**Bronze Layer**).  
2. Clean and normalize records via Apache Spark (**Silver Layer**), filtering valid observations with IUCN conservation status.  
3. Use **Spark MLlib** to perform **K-Means clustering** based on geolocation data.  
4. Store clustered results in **Apache HBase** and register them in **Hive** for fast querying.  
5. Visualize analysis results.

**Outcome:**

- Authorities identify **Central and Northern Sumatra** as high-risk zones.  
- Visual dashboards and spatial insights support **funding allocation** and **real-time conservation planning**.
