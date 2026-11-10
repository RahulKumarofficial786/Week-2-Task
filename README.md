# Week 2: Data Collection and Preprocessing Framework

Data analytics internship project: **E-Governance Service Delivery Analytics**.

This folder holds the Week 2 plan (DOC) and a Python prototype that runs the whole framework, from raw files to analysis-ready data.

> **Data note:** the two raw files are **simulated** to look like messy public data (mixed date formats, state-name variants, NA tokens, hours mixed with days, duplicates, impossible values). Results describe the method only and are **not real government statistics**.

## Files

| File | What it is |
|---|---|
| `egov_week2_framework.docx` | Main deliverable: data sources and metadata, collection plan, preprocessing steps, Python libraries, validation methods, workflow and timeline |
| `egov_week2_preprocessing.ipynb` | Notebook: metadata log, standardisation, validation, cleaning, integration, transformation, charts, HTML export |
| `egov_week2_workbook.xlsx` | Dataset catalog, collection plan, preprocessing plan, validation rules, timeline (34 hours), raw and clean data, quality report formulas |
| `egov_quality_report.html` | Self-contained quality report (open in any browser) |
| `data/raw/` | Simulated raw files, never edited |
| `data/processed/` | `cleaned_service_data.csv` and `analysis_ready.csv` |
| `logs/` | `metadata_log.csv`, `cleaning_log.csv`, `validation_report.csv`, `metrics.json` |
| `charts/` | Workflow diagram and quality charts |

## How to run

1. Install Python 3.9 or newer.
2. Install the libraries:
   ```
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```
3. In this folder run `jupyter notebook`, open `egov_week2_preprocessing.ipynb` and choose **Run All**.
4. The notebook creates the folders it needs, regenerates the simulated raw files, and writes `egov_quality_report.html`.

## Pipeline stages in the notebook

1. Setup and state-name mapping
2. Collect raw files and write the metadata log (rows, columns, checksum)
3. Parse and standardise (column names, text, dates, numbers, units)
4. Validation rule set R1 to R10 (run before and after cleaning)
5. Clean: hours to days, invalid values, duplicates, outliers (IQR), missing values (group median and KNN imputation)
6. Integrate the digital readiness source and engineer features (index, log, quarter, speed category)
7. Scale (StandardScaler, MinMaxScaler) and encode (one-hot), then save analysis-ready data
8. Quality report, charts and HTML export

## Using real data

1. Download real extracts (see the Dataset Catalog sheet) and check each source's terms of use.
2. Save them in `data/raw/` with the same columns as the simulated files, and remove the lines in the notebook that regenerate the simulated files.
3. Extend `VARIANTS` (state spellings) as new name variants appear in the cleaning log.
4. Re-run the notebook and update the blue input values in the Excel workbook.
