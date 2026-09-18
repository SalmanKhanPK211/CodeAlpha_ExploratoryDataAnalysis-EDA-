# 🔍 Exploratory Data Analysis of Remote Data Jobs

---

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on a dataset of remote **Data and Data Science job listings**, collected via web scraping in Task 1 of the internship.

The goal is to take the raw scraped dataset, understand its structure, clean it, and ask meaningful questions of it — turning unstructured, imperfect real-world data into something trustworthy enough to visualize and draw conclusions from.

The analysis pipeline uses:

**Raw CSV → Structure Check → Cleaning & Feature Engineering → Exploration → Insights**

This project was developed for **Task 2 — Exploratory Data Analysis (EDA)** of the **CodeAlpha Data Analytics Internship**.

---

## 🎯 Objectives

The main objectives of this project are to:

* Understand the dataset's structure, column types, and completeness.
* Identify and quantify missing data.
* Clean and engineer features needed for analysis (salary parsing, date parsing, category cleanup).
* Ask meaningful questions about the job market represented in the data.
* Detect and document data quality issues before they affect downstream analysis.
* Summarize findings to prepare a reliable dataset for the visualization stage (Task 3).

---

## 🛠️ Technologies Used

| Technology          | Purpose                                    |
| -------------------- | ------------------------------------------- |
| **Python**           | Core programming language                  |
| **Pandas**           | Data loading, cleaning, and analysis        |
| **NumPy**            | Numeric operations and missing-value handling |
| **Regular Expressions (`re`)** | Parsing salary ranges from text  |
| **Jupyter Notebook** | Interactive analysis environment           |

---

## 🔎 Data Source

**Input file:** `data/remote_data_science_jobs.csv`
**Origin:** collected in Task 1 via web scraping of [Remote First Jobs](https://remotefirstjobs.com/)

The raw dataset contains 250 job listings with the following fields: `scrape_category`, `job_title`, `company`, `location`, `category`, `job_level`, `salary`, `published_date`, `job_url`.

---

## 🧹 Cleaning & Feature Engineering

The raw data required the following processing before analysis:

| Step | Description |
| ---- | ----------- |
| Drop constant column | `scrape_category` only ever contained `"Data"` and carried no analytical value — removed. |
| Parse salary | Free-text values like `"$93k-$118k"` or `"$42k"` were parsed with regex into numeric `salary_min`, `salary_max`, and `salary_avg` columns. |
| Flag salary disclosure | Added a `has_salary` boolean to track which postings disclosed pay at all. |
| Parse dates | `published_date` converted from ISO text to a proper datetime, with a `published_month` field extracted for trend analysis. |
| Clean emoji/flags | `location`, `category`, and `job_level` contained emoji prefixes (scraper artifacts) — stripped into `*_clean` columns. |

---

## ❓ Questions Explored

1. Which job categories and seniority levels dominate the remote data-science market?
2. Where in the world are these remote roles based?
3. How does disclosed pay vary by seniority level?
4. Does salary disclosure rate differ by seniority level?
5. Has posting volume changed over time?

---

## 📈 Key Findings

* **Category mix:** postings are dominated by the *Data* category, with Mid-level and Senior roles making up the bulk of listings — Entry Level and Executive postings are rare.
* **Geography:** the United States leads remote hiring by a wide margin, followed by Canada and the UK.
* **Salary transparency:** roughly 60% of postings do not disclose a salary at all, so any pay-based conclusion reflects only the transparent minority, not the full market.
* **Pay trend:** where disclosed, average salary rises with seniority, though some levels have too few data points (e.g. Entry Level, Executive) to be statistically reliable.
* **Data quality issues found:** a redundant constant column, emoji-prefixed categorical text, and inconsistent missingness across `salary` and `location` — all documented and handled before analysis.

---

## 🧩 Project Workflow

```text
                Raw CSV Dataset
                        │
                        ▼
              Structure & Missing
                Value Check
                        │
                        ▼
              Cleaning & Feature
                Engineering
                        │
                        ▼
              Ask & Answer
              Meaningful Questions
                        │
                        ▼
              Document Data
              Quality Issues
                        │
                        ▼
                EDA Summary
                        │
                        ▼
              Task 3: Data
              Visualization
```

---

## 📁 Project Structure

```text
CodeAlpha_DataAnalysisEDA/
│
├── task2_eda.ipynb
│
├── data/
│   └── remote_data_science_jobs.csv
│
├── README.md
│
└── requirements.txt
```

---

## ▶️ Installation

Clone the repository:

```bash
git clone https://github.com/SalmanKhanPK211/CodeAlpha_DataAnalysisEDA.git
```

Move into the project directory:

```bash
cd CodeAlpha_DataAnalysisEDA
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Or install them individually:

```bash
pip install pandas numpy jupyter
```

---

## 🚀 Run the Notebook

Launch Jupyter:

```bash
jupyter notebook task2_eda.ipynb
```

Run all cells to:

1. Load the raw dataset.
2. Inspect structure and missing values.
3. Clean and engineer features.
4. Explore the 5 core questions.
5. Review the documented data quality issues and summary.

---

## 📌 CodeAlpha Internship Task

This repository was developed for:

**CodeAlpha — Data Analytics Internship**

### Task 2: Exploratory Data Analysis (EDA)

The project demonstrates:

* Dataset structure and missing-value assessment
* Data cleaning and feature engineering
* Hypothesis-driven exploration of real-world data
* Identification and documentation of data quality issues
* Preparation of a clean dataset for downstream visualization

---

## 👨‍💻 Author

**Salman Khan**
BS Computer Science Student
Interested in **Data Analytics, Data Science, Machine Learning, and AI**

GitHub:
https://github.com/SalmanKhanPK211/CodeAlpha_EDA
---

## ⭐ Project Purpose

This project continues the internship's end-to-end data workflow:

> **Raw Data → Cleaning → Exploratory Analysis → Insights → Visualization**

The cleaned dataset and findings from this stage feed directly into **Task 3: Data Visualization**.
