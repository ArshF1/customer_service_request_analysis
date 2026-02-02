# Data Cleaning & Preprocessing Summary

This project focuses on **cleaning and preparing a customer service request dataset** by handling missing values and validating data types.

- Missing values were analyzed across all columns.
- Columns with very high missing percentages were removed, while columns with low missing rates were treated selectively.
- Datetime fields (e.g., `Closed Date`) were converted from string format to proper `datetime` objects.
- Invalid or missing datetime values were safely identified and, due to their very low frequency (~0.65%), corresponding rows were removed instead of being imputed.
- Final checks were performed to ensure all columns have appropriate data types.

The dataset is now clean, consistent, and ready for exploratory analysis and modeling.
