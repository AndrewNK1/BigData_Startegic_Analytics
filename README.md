This project implements an end-to-end big data pipeline using **PySpark** to analyze historical Citi Bike trip data in New York City. The workflow processes large-scale data to extract actionable business intelligence, featuring data cleaning, spatial feature engineering, complex analytical queries, and a machine learning task to predict rider demographics. 

The final output is designed to integrate with Business Intelligence tools (like Power BI) to inform operational decisions, such as station maintenance and fleet distribution.

---

## 🛠️ Technology Stack
* **Big Data Processing:** PySpark (DataFrames, RDDs), Spark SQL
* **Machine Learning:** Spark MLlib (Pipelines, Classification models)
* **Data Visualization / BI:** Power BI (via CSV pipeline exports)
* **Languages:** Python, SQL

---

## 🏗️ Pipeline Architecture

### 1. ETL & Feature Engineering
The foundation of the project involves cleaning noisy data and generating new features to enable deeper geographical and temporal analysis:
* **Data Cleansing:** Handled null values, removed duplicate records, and standardized categorical data (e.g., mapping numeric gender codes to descriptive strings).
* **Spatial Engineering:** Calculated actual trip distances using the Haversine formula via PySpark User Defined Functions (UDFs) and derived average trip speeds.
* **Temporal Engineering:** Extracted start months and categorized trips into distinct periods of the day (Morning, Afternoon, Evening, Night).
* **Anomaly Detection:** Flagged and segregated noisy records, isolating trips under 60 seconds, impossible speeds (over 40 km/h), and extreme age outliers.

### 2. Business Intelligence & Analytics (Spark SQL)
Using Spark SQL window functions and aggregations, the pipeline answers critical business questions across three main areas:

| Focus Area | Strategic Insights Extracted |
| :--- | :--- |
| **Operational Logistics** | Identified peak rush hours (8 AM & 5 PM) and flagged over-utilized bike IDs based on accumulated hours to prioritize preventative maintenance. |
| **User Behavior** | Analyzed speed and duration across demographics, and calculated round-trip percentages (Customer vs. Subscriber behavior). |
| **Spatial & Temporal Trends** | Mapped the top 10 most popular start stations, highest-demand routes, and seasonal ridership peaks (Summer/Autumn). |

> **Key Insight:** Subscribers primarily utilize the network for commuting to business districts, whereas casual Customers drive demand at parks and tourist destinations, heavily skewing toward weekend leisure usage.

### 3. Predictive Modeling (Spark ML)
A machine learning pipeline was built to predict rider demographics (Gender) based on trip behavior, which can be utilized for targeted marketing campaigns.
* **Feature Pipeline:** Utilized `StringIndexer`, `OneHotEncoder`, `VectorAssembler`, and `StandardScaler` to prepare the data.
* **Models Evaluated:** Logistic Regression, Decision Tree, and Random Forest Classifiers.
* **Evaluation:** Extracted feature importance metrics, identifying **Age** and **User Type** as the most significant predictors of demographic behavior.

---

## 📊 Dashboard & Reporting
To bridge the gap between big data processing and stakeholder presentation, the results of the Spark SQL queries and ML predictions are automatically exported as clean CSV files. These datasets are structured specifically for semantic layer integration and visualization in **Power BI**, providing a final, interactive dashboard for fleet management and strategic growth planning.

---

## 🚀 How to Run
1. Clone this repository to your local machine.
2. Ensure you have an active Spark environment (or run the provided `.ipynb` notebook directly in Google Colab).
3. The dataset is automatically fetched from the cloud via the initial setup cell in the notebook.
4. Run the notebook sequentially to execute the ETL process, view query outputs, and generate the reporting CSVs.


<img width="872" height="483" alt="image" src="https://github.com/user-attachments/assets/b763fda2-758b-4e60-86e3-92040c7438ca" />


