# Walmart Data Analysis: End-to-End SQL + Python Project

## Project Overview

![Project Pipeline](https://github.com/najirh/Walmart_SQL_Python/blob/main/walmart_project-piplelines.png)


> Analyzing 10,000+ Walmart transactions to answer real business questions using Python (data pipeline) and SQL (analytical queries).

---

## 📌 Project Overview

This project builds a complete data analysis pipeline for Walmart sales data. Python is used to source the dataset from Kaggle and load it into a MySQL database, while SQL is used to query and answer key business questions around sales performance, customer behavior, payment trends, branch ratings, and more.

---

## 🗂️ Repository Structure

```
Walmart_Sql_Python/
│
├── Walmart.csv                  # Raw dataset (10,000+ records)
├── walmart_clean_data.csv       # Cleaned and processed dataset
├── walmart.sql                  # All SQL queries for business analysis
├── Walmart Business Problems.pdf # Business questions addressed
├── Walmart_python.pdf           # Python pipeline documentation
└── README.md
```

---

## ⚙️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Data extraction from Kaggle, cleaning, MySQL insertion |
| MySQL | Database storage and analytical querying |
| Pandas | Data wrangling and preprocessing |
| Kaggle API | Dataset sourcing |
| SQL (CTEs, Window Functions) | Business problem solving |

---

## 🔄 Pipeline Workflow

```
Kaggle Dataset
      ↓
Python (Download + Clean)
      ↓
MySQL Database (walmart table)
      ↓
SQL Queries → Business Insights
```

1. **Extract** - Python pulls the Walmart sales dataset from Kaggle using the Kaggle API.
2. **Transform** - Data is cleaned (nulls, formatting, types) using Pandas.
3. **Load** - Cleaned data is inserted into a local MySQL database.
4. **Analyze** - SQL queries answer the defined business questions.

---

## 📊 Business Questions Answered

| # | Question |
|---|----------|
| Q1 | What are the different payment methods used and how many transactions per method? |
| Q2 | Which branch has the highest average rating per product category? |
| Q3 | *(Additional queries in `walmart.sql`)* |
| ... | *(See `Walmart Business Problems.pdf` for the full list)* |

### Sample SQL — Q1: Payment Method Analysis
```sql
SELECT
    payment_method,
    COUNT(*) AS transaction_count
FROM walmart
GROUP BY payment_method;
```

### Sample SQL — Q2: Highest Average Rating per Branch (using CTE)
```sql
WITH branch_rating AS (
    SELECT
        branch,
        category,
        AVG(rating) AS avg_rating
    FROM walmart
    GROUP BY branch, category
),
ranked_rating AS (
    ...
)
...
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- MySQL Server
- Kaggle account + API key (`kaggle.json`)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/Roushan9991/Walmart_Sql_Python.git
cd Walmart_Sql_Python

# 2. Install Python dependencies
pip install pandas mysql-connector-python kaggle

# 3. Place your Kaggle API key
# Copy kaggle.json to ~/.kaggle/kaggle.json

# 4. Run the Python pipeline
python walmart_pipeline.py

# 5. Open MySQL and run the queries
mysql -u root -p < walmart.sql
```

---

## 📁 Dataset

- **Source:** [Kaggle — Walmart Sales Dataset](https://www.kaggle.com/)
- **Records:** ~10,000 transactions
- **Key Columns:** `branch`, `city`, `category`, `payment_method`, `rating`, `quantity`, `unit_price`, `date`, `time`

---

## 💡 Key Insights

- Multiple payment methods analyzed by transaction volume
- Branch-level performance benchmarked by category rating
- Revenue and sales trends uncovered through SQL aggregations

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 👤 Author

**Roushan Kumar Mourya**
MBA Analytics @ IIM Kashipur
Graduate from NIT Bhopal
[GitHub Profile](https://github.com/Roushan9991)
