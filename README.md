# Sales Data Cleaning & CSV Operations (Pandas)

**Student:** Javaria Rizwan
**Program:** AI Engineering Bootcamp | Module 02 | Sunday Project
**GitHub Repo:** https://github.com/JavariaRizwan/sales-data-cleaning-pandas

---

## What this project does

This is a beginner-level Pandas project that takes a messy sales CSV and turns it into clean, usable data. It then edits that cleaned data and saves a separate updated file.

The work is split into two parts, both inside one notebook.

### Part A: Data quality and basic insights
- Loads `sales_raw.csv` and inspects it (head, shape, columns, data types, missing values, duplicates)
- Cleans the data:
  - trims extra spaces and fixes inconsistent text in `region` and `category` (e.g. `" food "`, `"SOUTH"`, `"books"`)
  - converts invalid dates, quantities and prices to proper types
  - fills missing values (mode for text columns, mean or median for numeric ones)
  - fixes negative quantity and the extreme price outlier (10000)
  - removes duplicate rows
- Compares row counts before and after cleaning (21 raw rows, 20 after cleaning)
- Adds a `revenue` column (`quantity x unit_price`)
- Summarises revenue with `groupby()` by region and category
- Creates two labelled charts (bar chart by region, pie chart by category) and two written findings
- Saves the result as `cleaned_sales.csv`

### Part B: CSV file handling and manipulation
- Loads `cleaned_sales.csv` and adds a `tax_amount` column (5% of revenue)
- Uses `.loc[]` to raise the `unit_price` of Books items by 10%, then recalculates `revenue` and `tax_amount`
- Removes one row using an existing `transaction_id`
- Adds a temporary `review_status` column and removes it with `drop(columns=...)`
- Saves the result as `sales_updated.csv`, reads it back and shows the first five rows and final column names

---

## Project files

| File | Description |
|------|-------------|
| `JavariaRizwan_TRN_2026_000286.ipynb` | Main notebook with Part A and Part B |
| `sales_raw.csv` | Original input data (never modified) |
| `cleaned_sales.csv` | Output of Part A (cleaned data with revenue) |
| `sales_updated.csv` | Output of Part B (tax, price update, row removed) |
| `README.md` | This file |

---

## How to run

All file paths are relative, so the notebook works in both Jupyter and Google Colab as long as the CSV sits in the same folder as the notebook.

### Option 1: Jupyter Notebook (local)

1. Make sure Python 3 is installed.
2. Install the required libraries:
   ```bash
   pip install pandas matplotlib notebook
   ```
3. Put the notebook and `sales_raw.csv` in the same folder.
4. Open a terminal in that folder and start Jupyter:
   ```bash
   jupyter notebook
   ```
5. Open `JavariaRizwan_TRN_2026_000286.ipynb`.
6. Click **Kernel > Restart & Run All**.

### Option 2: Google Colab

1. Go to [colab.research.google.com](https://colab.research.google.com) and choose **File > Upload notebook**.
2. Upload `JavariaRizwan_TRN_2026_000286.ipynb`.
3. Open the **Files** panel on the left and upload `sales_raw.csv` into the default folder.
4. Click **Runtime > Run all**.

### What you should see after running
- `cleaned_sales.csv` is created (20 rows, 7 columns)
- `sales_updated.csv` is created (19 rows, 8 columns)
- Two charts appear in Part A
- `sales_raw.csv` stays unchanged

---

## Requirements

- Python 3.8+
- pandas
- matplotlib

---

## Notes

- Run the notebook from top to bottom, because Part B depends on the output of Part A.
- Running it again overwrites `cleaned_sales.csv` and `sales_updated.csv` with fresh copies.
