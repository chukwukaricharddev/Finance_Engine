# 🏦 Serverless Finance ETL Engine

A completely automated, serverless ETL (Extract, Transform, Load) pipeline that converts messy, unstructured PDF bank statements into a clean, queryable SQLite database using Python and GitHub Actions.

## 🏗️ Architecture & Data Flow

* **Extract:** The script reads a static `statement.pdf` file using `pdfplumber`, parsing raw transaction text from the document grid.
* **Transform:** `pandas` cleans the unstructured strings, removes headers/footers, standardizes date formats, and categorizes transaction types.
* **Load:** The clean, structured dataset is inserted directly into a local relational database (`finance_engine.db`).
* **Automate:** A GitHub Actions cron job wakes up a headless Ubuntu server on the 1st of every month to execute the script.
* **Commit:** The cloud runner automatically commits the updated `.db` file back to the repository using a customized Git configuration.

## 🛠️ Tech Stack

* **Language:** Python 3.10
* **Data Processing:** Pandas, PDFPlumber
* **Database:** SQLite
* **CI/CD & Cloud:** GitHub Actions (Ubuntu-latest)

## 🚀 How to Use This Architecture

Instead of manually typing expenses into a spreadsheet or paying for a syncing app, you can use this headless engine to own your raw financial data.

1. **Fork the Repository:** Click the 'Fork' button at the top right to copy this pipeline to your own account.
2. **Upload Your Data:** Delete the dummy `statement.pdf` and upload your own bank statement (ensure it is named exactly `statement.pdf`).
3. **Adjust the Logic:** Bank statement layouts vary heavily. Tweak the `pdfplumber` extraction logic inside `finance_engine.py` to match the exact column structures of your specific bank.
4. **Grant Permissions:** Navigate to `Settings > Actions > General` and grant "Read and write permissions" so the automated runner is authorized to save the updated database back to your repository.
5. **Execute:** Let the cron job run automatically on the 1st, or navigate to the Actions tab and click "Run workflow" to build your database instantly.
