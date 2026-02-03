# Customer Service Request Analysis

## Project Overview

This repository contains an exploratory data analysis and preprocessing pipeline for a NYC-style customer service requests dataset (311 service requests). The work is implemented in `main.ipynb` and focuses on cleaning, basic feature engineering, and visualization to prepare the data for further analysis or modeling.

## Dataset

- Source file: `datasets/311_Service_Requests_from_2010_to_Present.csv`
- A raw complaints dataset containing timestamps, location fields, complaint types, borough/city information, and other metadata.

## Key Steps Performed

1. Data loading
	- Read the CSV with `pd.read_csv(..., low_memory=False)` to avoid dtype warnings.

2. Missing values analysis
	- Implemented a helper `missing_values_table(df)` to list columns with missing counts, percentages and dtypes.
	- Dropped columns with more than 50% missing data.

3. Datetime conversion and cleanup
	- Converted `Closed Date` and `Created Date` to `datetime` using `pd.to_datetime(..., errors='coerce')`.
	- Dropped rows with invalid or null `Closed Date` and then dropped remaining nulls where necessary.

4. Feature engineering
	- Computed `Resolution time` as `(Closed Date - Created Date).dt.days` (integer days to close a request).

5. Exploratory Data Analysis (visualizations)
	- City-wise complaint counts (bar plot).
	- Top-5 cities breakdown by `Complaint Type` (stacked horizontal bar chart).
	- Borough-level geographic visualizations for Brooklyn using scatter and hexbin plots of `Latitude` and `Longitude`.
	- Complaint type frequency (horizontal bar chart for most common complaints).
	- Average resolution times by `Complaint Type` (horizontal bar plot of mean `Resolution time`).

## Findings / Notes

- Several columns had extremely high missingness and were removed to focus analysis on reliable fields.
- A small fraction of rows had invalid datetime values and were removed rather than imputed, since their proportion was negligible.
- The computed `Resolution time` enables comparison of how long different complaint types take to resolve.

## How to run

1. Create / activate your virtual environment (example using the provided `myenv`):

```
myenv\Scripts\Activate.ps1  # PowerShell on Windows
```

2. Install dependencies (see `requirements.txt`):

```
pip install -r requirements.txt
```

3. Open and run the notebook:

```
jupyter lab  # or jupyter notebook
```

Open `main.ipynb` and run the cells sequentially.

## Files

- [main.ipynb](main.ipynb) — analysis notebook with data cleaning, EDA and plots.
- `datasets/311_Service_Requests_from_2010_to_Present.csv` — raw dataset.
- `requirements.txt` — required Python packages.

## Next steps (suggestions)

- Add more feature engineering (e.g., week-of-year, complaint subcategories).
- Build models to predict resolution time or priority of complaints.
- Use spatial clustering or map visualizations for richer geospatial insights.

---
*README generated from the analysis in `main.ipynb`.*
