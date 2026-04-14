# databricks-ecommerce-etl-pipeline
End-to-end E-commerce Data Engineering project using Databricks, PySpark, and Medallion Architecture (Bronze, Silver, Gold)
# 🚀 E-commerce Data Engineering Pipeline (Databricks + PySpark)

## 📌 Project Overview
This project demonstrates an end-to-end data engineering pipeline built using **Databricks, PySpark, and Delta Lake**.  
The pipeline follows the **Medallion Architecture (Bronze, Silver, Gold)** to transform raw e-commerce data into meaningful business insights.

The dataset used is an e-commerce dataset from Kaggle containing customer transactions such as product details, payment methods, and purchase amounts.

---

## 🏗️ Architecture

The project follows the Medallion Architecture:

### 🥉 Bronze Layer (Raw Data)
- Raw data ingestion from CSV files into Databricks
- No transformations applied

### 🥈 Silver Layer (Cleaned Data)
- Removed null values
- Handled duplicate records
- Standardized column names
- Converted data types (e.g., Purchase_Amount → numeric)
- Converted Transaction_Date into proper date format

### 🥇 Gold Layer (Business Insights)
- Applied aggregations and transformations
- Created business KPIs and insights:
  - Revenue by Country
  - Revenue by Product Category
  - Payment Method Analysis
  - Monthly Sales Trends
  - Customer Spending Analysis

---

## ⚙️ Technologies Used
- Databricks
- Apache Spark (PySpark)
- Delta Lake
- SQL
- Python

---

## 📊 Key Transformations Performed

### Data Cleaning (Silver Layer)
- Removed null values using `dropna()`
- Removed duplicates using `dropDuplicates()`
- Casted data types for accurate analysis
- Standardized date formats

### Feature Engineering
- Extracted year and month from Transaction_Date
- Created aggregated revenue fields

### Business Aggregations (Gold Layer)
- GroupBy operations on Country, Product Category, and Payment Method
- Calculated total and average revenue
- Identified top customers and best-selling categories

---

## 📈 Business Insights Generated
- Identified top revenue-generating countries
- Found most popular product categories
- Analyzed customer purchasing behavior
- Discovered monthly sales trends
- Evaluated payment method preferences

---

##  Sample Code

```python
from pyspark.sql.functions import sum

df.groupBy("Country") \
  .sum("Purchase_Amount") \
  .orderBy("sum(Purchase_Amount)", ascending=False) \
  .show()
