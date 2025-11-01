# 🏗️ Matillion for Beginners — GitHub Project Cheat Sheet

This project is a beginner-friendly cheat sheet for Matillion, a cloud-based ETL/ELT platform. It simplifies key components, workflows, and examples for easy understanding and quick reference.


---

## 🧱 What is Matillion?

Matillion is a **cloud-based ETL/ELT platform** that moves and prepares data for cloud data warehouses like:

* **Snowflake** ❄️
* **Amazon Redshift** 📦
* **Google BigQuery** 🔍
* **Azure Synapse** ☁️

### 🔸 Core Concepts

* **ETL/ELT Approach:** Transform data inside the database using **pushdown SQL execution** for speed.
* **Two Job Types:**

  * 🧱 **Orchestration Job:** The plan that controls workflow, data movement, and triggers.
  * ⚙️ **Transformation Job:** Cleans, joins, filters, and transforms data inside the warehouse.
* **Low-Code Interface:** Drag-and-drop design to build pipelines quickly.

### 🍳 Kitchen Analogy

* **Orchestration Job → Recipe (plan)**
* **Transformation Job → Cooking (actual data prep)**

---

## 🧩 Component Categorization

| **Category**       | **Components**                                                                                                                                                                                                      | **Purpose**                                                        | **When to Use**                                 | **Why to Use**                                       | **Example (Easy to Understand)**                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------- | ---------------------------------------------------- | ----------------------------------------------------------------------------- |
| **Orchestration**  | `Create Table`, `S3 Load`, `Fixed Flow`, `File/Table/Fixed Iterator`, `End Success`, `End Failure`, `TFlow Comment`                                                                                                 | Manage workflow, data load, control looping, success/failure paths | When you need to organize or move data          | To make tasks run in correct order and handle errors | “Load customer.csv, create table, loop files, end when all done.”             |
| **Transformation** | `Input Table`, `Join`, `Filter`, `Calculation`, `Aggregation`, `Rename`, `Remove Duplicate`, `Table Output`, `Table Rewrite`, `Convert Type`, `Extract Nested Data`, `Flatten Variant`, `Data Query`, `Excel Query` | Clean, standardize, and load data into target models               | When you need to clean, join, or summarize data | To make data ready for reports or final tables       | “Join two tables (sales + products), filter bad data, calculate total price.” |

---

## 🔶 Orchestration Components

| **Component**     | **Purpose / Function**                     | **When to Use**                       | **Why to Use**                       | **Example (Easy to Understand)**                                |
| ----------------- | ------------------------------------------ | ------------------------------------- | ------------------------------------ | --------------------------------------------------------------- |
| **Create Table**  | Creates an empty table in target DB        | Before initial data load              | To hold new data                     | “Make an empty ‘sales’ table before loading files.”             |
| **S3 Load**       | Loads raw data from S3 into the target     | When importing CSV/JSON/Parquet files | To bring raw data into warehouse     | “Load sales.csv from S3 into warehouse.”                        |
| **Fixed Flow**    | Generates static or constant datasets      | When constants or metadata are needed | To have reference or constant values | “Create list of months (Jan–Dec).”                              |
| **All Iterator**  | Loops through files, folders, or variables | When multiple inputs to process       | To automate repeated tasks           | “Go through each file: sales_2025_01.csv, sales_2025_02.csv...” |
| **TFlow Comment** | Adds notes to the job                      | Any time                              | To explain workflow                  | “Note: Load data before cleaning.”                              |
| **End Success**   | Marks successful job end                   | End of workflow                       | To show job completed                | “Show green tick when all is done.”                             |
| **End Failure**   | Marks failed job execution                 | End of workflow                       | To handle errors                     | “Show red cross if file missing.”                               |

💡 **Tip:** Use `TFlow Comment` often — helps others understand your flow.

---

## 🟢 Transformation Components

| **Component**           | **Purpose / Function**         | **When to Use**         | **Why to Use**                      | **Example (Easy to Understand)**             |
| ----------------------- | ------------------------------ | ----------------------- | ----------------------------------- | -------------------------------------------- |
| **Input Table**         | Reads data from a table        | Start of transformation | To get raw data                     | “Read data from sales_raw table.”            |
| **Filter**              | Filters data using conditions  | Early in job            | To remove unwanted rows             | “Keep only rows where qty > 0.”              |
| **Convert Type**        | Changes column data types      | Early in job            | To fix schema mismatches            | “Change price from text to number.”          |
| **Extract Nested Data** | Extracts fields from JSON      | Early in job            | To access nested information        | “Pull customer name from JSON.”              |
| **Flatten Variant**     | Converts JSON arrays into rows | Early in job            | To simplify nested structures       | “Turn order_items array into multiple rows.” |
| **Join**                | Combines multiple datasets     | Mid job                 | To enrich or merge data             | “Combine sales table with product info.”     |
| **Calculation**         | Creates new columns or KPIs    | Mid job                 | To apply formulas or business logic | “Add total = qty × price.”                   |
| **Aggregation**         | Groups and summarizes data     | Mid/End job             | To get summaries or totals          | “Sum total sales per day.”                   |
| **Remove Duplicate**    | Removes duplicate rows         | End of job              | To clean final data                 | “Keep only one row per order_id.”            |
| **Rename Table**        | Renames or standardizes names  | End of job              | To clarify column names             | “Rename ‘cust_name’ to ‘customer_name’.”     |
| **Table Output**        | Writes final data to new table | End of job              | To store final cleaned dataset      | “Save cleaned data to sales_clean.”          |
| **Table Rewrite**       | Overwrites target table        | End of job              | For full data refresh               | “Replace yesterday’s data with new.”         |
| **Data Query**          | Runs custom SQL queries        | Start/Mid job           | To perform advanced logic           | “Run custom SQL for advanced join.”          |
| **Excel Query**         | Reads Excel data               | Start of job            | For small/ad-hoc datasets           | “Read staff_list.xlsx from uploads.”         |

💡 **Best Practice:** Always filter and convert types early to avoid downstream errors.

---

## 🔁 Iterator Types Explained

| **Iterator Type**  | **Purpose**                    | **When to Use**                    | **Why to Use**                     | **Example (Easy to Understand)**            |
| ------------------ | ------------------------------ | ---------------------------------- | ---------------------------------- | ------------------------------------------- |
| **File Iterator**  | Iterates through files         | When daily files must be processed | To automate repetitive file loads  | “Loop through all sales_2025_*.csv files.”  |
| **Table Iterator** | Iterates through tables        | When applying logic to many tables | To reuse same transformation logic | “Apply transformation to all stg_* tables.” |
| **Fixed Iterator** | Iterates through static values | For fixed lists like months        | To process each fixed value        | “Run job for Jan, Feb, Mar.”                |

💡 **Tip:** Combine Iterators with Variables for dynamic pipelines (e.g., by date or region).

---

**Summary:** This cheat sheet provides a simple, beginner-friendly overview of Matillion components, pipelines, and practical examples, ready for use as a GitHub project reference.
