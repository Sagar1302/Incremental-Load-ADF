# Incremental-Load-ADF
Git used to store the the files for incremental load 
<img width="1578" height="459" alt="image" src="https://github.com/user-attachments/assets/374328d2-c55e-4fdd-b1fc-d6ad3de40fde" />

# Incremental Data Load Pipeline (Azure Data Factory)

## 📌 Overview
This project implements an **incremental data load pipeline** using **Azure Data Factory (ADF)**.  
The pipeline ensures that only **new rows** since the last access are processed, optimizing resource usage and maintaining data freshness.

---

## ⚙️ Workflow Steps

1. **Lookup Last Access**
   - Retrieves the last access timestamp or identifier from a control table.

2. **Set Variable**
   - Stores the retrieved value in a pipeline variable (`lastAccess`).

3. **Script: Get Total New Rows**
   - Executes a SQL script to calculate the number of new rows since the last access.

4. **If Condition: Check New Rows**
   - Evaluates whether new rows exist.
   - **True branch** → Executes the data copy and update steps.
   - **False branch** → Ends pipeline execution (no new data).

5. **Copy Data from SQL**
   - Extracts new rows from the source SQL database.

6. **Lookup Latest Access**
   - Retrieves the latest timestamp/identifier after the copy.

7. **Copy Data to Update Control Table**
   - Updates the control table with the new `lastAccess` value.

---

## 🏗️ Architecture Diagram
*(Insert the workflow diagram here — the one you shared in the image)*

---

## ✅ Key Features
- **Incremental Loads**: Avoids reprocessing old data.
- **Resource Optimization**: Runs only when new data is available.
- **Data Consistency**: Maintains a control table for tracking last access.
- **Scalable Design**: Can be extended to multiple sources and destinations.

---

## 🚀 How to Run
1. Deploy the pipeline JSON into your Azure Data Factory instance.
2. Configure linked services for:
   - Source SQL Database
   - Destination (Data Lake / Synapse / SQL)
   - Control Table
3. Trigger the pipeline manually or schedule via ADF triggers.

---

## 📊 Example Use Cases
- Daily incremental loads from transactional databases.
- CDC (Change Data Capture) style ingestion for analytics.
- Optimized ETL workflows for large datasets.



