# Advanced Data Mining Project - Deliverable 1

## Dataset Summary

- **Dataset**: `ecommerce_user_dataset_cleaned.csv`
- **Records**: 1,000
- **Attributes**: 8
- **Domain**: E-commerce customer behavior and segmentation
- **Key fields**:
  - `Customer_ID`
  - `Purchase_History`
  - `Transaction_Frequency`
  - `Monetary_Value`
  - `Browsing_Behavior`
  - `Engagement_Score`
  - `Time_on_Site`
  - `Customer_Segment`

This dataset is appropriate for the project because it has sufficient size and dimensionality, includes numeric behavioral features for EDA and modeling, and contains a segment label useful for future classification tasks.

## Major Steps in Data Cleaning and Exploration

1. Loaded the dataset using Pandas and inspected shape, schema, and sample records.
2. Performed quality checks for:
   - Missing values
   - Duplicate rows
   - Basic value consistency for bounded features (for example, `Engagement_Score` in [0,1])
3. Applied a reusable cleaning pipeline:
   - Column name standardization
   - Duplicate removal
   - Generic missing value imputation logic (numeric median, categorical mode)
   - Numeric type enforcement
4. Addressed noisy data using IQR-based outlier detection and capping (winsorization), mainly affecting `Transaction_Frequency`.
5. Conducted EDA with visualizations:
   - Histograms and boxplots for numeric distributions and outliers
   - Segment count plot for class balance
   - Correlation heatmap
   - Segment-wise feature mean comparison

## Key Insights

- Data quality is strong (no missing values, no duplicates in the source file).
- `Customer_Segment` is imbalanced (`Copp` ~71.8%, `Iron` ~28.2%).
- Numeric features show weak linear correlations, suggesting potential value from non-linear models and interaction features in later stages.
- Outliers are limited and mostly concentrated in `Transaction_Frequency`.
- Segment-level averages are close, indicating that additional feature engineering may be important for stronger predictive performance.

## Challenges and How They Were Addressed

- **Challenge**: The dataset appears already cleaned, which can reduce visibility into cleaning decisions.
  - **Resolution**: Implemented a robust, reusable cleaning pipeline and documented each operation so the process remains reproducible.
- **Challenge**: Weak separability between customer segments in simple summary statistics.
  - **Resolution**: Highlighted next-step modeling strategies (class balancing, non-linear methods, and engineered features) to improve downstream performance.
- **Challenge**: Potential influence of extreme values.
  - **Resolution**: Used IQR-based capping to reduce noise impact while preserving records.

## Files

- `deliverable1_data_collection_cleaning_exploration.ipynb`: Full notebook with code, explanations, and visualizations.
- `README.md`: Summary of dataset, cleaning process, key findings, and challenges.
