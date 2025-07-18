# 🧠 Data Quality Pipeline in Databricks: Transaction Audit Project

## 📌 Project Overview

This project implements a **data quality pipeline** in **Databricks**, designed to simulate a real-world data audit on transactional data using **Python (pandas)**.  
It detects common data quality issues, applies business validation rules, and generates a report.

The pipeline was developed in **Databricks Notebooks** and uses **Pandas code**.

---

## 🎯 Objectives

- Ingest and inspect transactional data in Databricks.
- Perform initial profiling (nulls, distributions, duplicates).
- Apply data quality rules using Python.
- Generate a summary of violations.
- Save outputs (DQ report) to the Databricks File System (DBFS).

---

## ⚙️ Technologies Used

- **Databricks Community / Enterprise**
- Python
- Pandas
- Databricks File System (DBFS)

---

## 📁 Dataset

**File:** `transactions.csv`  
**Location:** `/dbfs/FileStore/transactions.csv`  
**Rows:** ~1,000 

### Fields:

| Column             | Description                                  |
|--------------------|----------------------------------------------|
| `transaction_id`   | Unique identifier of a transaction           |
| `customer_id`      | Customer's unique ID                         |
| `amount`           | Transaction amount (numeric)                 |
| `status`           | Status: `completed`, `failed`, `pending`     |
| `transaction_date` | Date of transaction    |

---

## ✅ Data Quality Rules (DQ Rules)

| Rule | Description |
|------|-------------|
| **DQ1** | `customer_id` and `amount` must not be null |
| **DQ2** | `amount` must be greater than 0             |
| **DQ3** | `transaction_id` must be unique             |
| **DQ4** | If `status = 'completed'`, and `amount > 0` |

---

## 🔄 Pipeline Structure in Databricks

The following notebook cells reflect each stage of the quality check:

1. **Data Ingestion**
   - Load the CSV file from DBFS
   - Preview schema and row count
2. **Data Profiling**
   - Null value summary
   - Duplicate detection
   - Unique values
3. **Validation Rules (DQ1–DQ4)**
   - Each rule checked via Python
   - Invalid records flagged and counted
4. **Reporting**
   - Generate a summary table of all DQ violations
   - Save as CSV

---

## 🧪 Example Violation Summary (error_raport.csv)

| Rule                        | Error Count |
|-----------------------------|-------------|
| DQ1_missing_customer_id     | 10          |
| DQ1_missing_amount          | 8           |
| DQ2_negative_amount         | 12          |
| DQ3_duplicate_transaction_id| 2           |
| DQ4_inconsistent_completed  | 5           |

---

## 📂 Output Files (stored in DBFS)

- `/dbfs/FileStore/error_raport.csv` — summary of all violations  

---

## 🧩 Skills Demonstrated

- Building quality pipelines in Databricks notebooks
- Writing pandas-based logic
- Combining data engineering & business validation
- Modular pipeline design (each step = one notebook section)
- Exporting validated outputs from DBFS

---

## 🚀 How to Run This Project

1. Open your Databricks workspace (Community or Enterprise).
2. Upload the `transactions.csv` file to `/FileStore/`.
3. Import the notebook file (`transactions_pipeline.ipynb`).
4. Run notebook cells step-by-step.
5. Check the outputs in DBFS.

---

## 👨‍💻 Author & Contact

Created by an aspiring Data Quality Analyst passionate about building clean and auditable data pipelines.  
If you'd like to connect or give feedback — feel free to reach out on LinkedIn or GitHub.

---

