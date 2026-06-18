# House Pricing Prediction

This notebook focuses on preparing a dataset for predicting house prices. The following steps have been completed:

## 1. Importing Libraries
Necessary libraries such as pandas, numpy, matplotlib, seaborn, scikit-learn modules (MinMaxScaler, LabelEncoder, OneHotEncoder, mutual_info_regression, train_test_split) have been imported.

## 2. Loading Dataset
The `House_Pricing.csv` dataset has been loaded into a pandas DataFrame. Basic overview (`.head()`, `.shape`, `.info()`, `.describe()`) of the dataset has been performed.

## 3. Duplicates Handling
Checked for duplicate rows and columns in the dataset. No duplicates were found.

## 4. Missing Value Checking and Handling
- Identified columns with missing values.
- `No of Times Visited` column was dropped due to a high percentage of missing values.
- Rows with missing 'Sale Price' were dropped as it's the target variable.
- Missing values in 'No of Bathrooms' were imputed with the mode.
- Missing values in 'Flat Area (in Sqft)', 'Lot Area (in Sqft)', 'Area of the House from Basement (in Sqft)', and 'Living Area after Renovation (in Sqft)' were imputed with their respective medians.
- Rows with missing values in 'Zipcode', 'Latitude', and 'Longitude' were dropped due to their unique nature and small number of missing entries.

## 5. Dataset Visualization
Histograms of key numerical features like 'Sale Price', 'No of Bedrooms', 'Flat Area (in Sqft)', 'Lot Area (in Sqft)', 'Area of the House from Basement (in Sqft)', 'Zipcode', 'Latitude', 'Longitude', and 'Living Area after Renovation (in Sqft)' were plotted to understand their distribution.

## 6. Fixing Target and Feature Columns
- 'Sale Price' was assigned as the target variable `y`.
- All other columns were assigned as features `X`.

## 7. Feature Engineering
- Numerical and categorical columns were identified.
- The 'Date House was Sold' column was split into 'day', 'month', and 'year' and the original column was dropped.
- Numerical columns were scaled using `MinMaxScaler`.
- Categorical columns (`Waterfront View`, `Condition of the House`, `month`) were inspected for unique values.
- `Waterfront View` was label encoded as it is a binary categorical feature.
- `Condition of the House` and `month` were one-hot encoded.
- The original categorical columns were dropped, and the one-hot encoded columns were concatenated back to `X`.

## 8. Mutual Information of Dataset
- Mutual information was calculated for each feature in `X` with respect to the target variable `y`.
- Features with a mutual information score greater than 0.01 were selected to reduce dimensionality and retain important features.

## 9. Outlier Handling
- Boxplots were generated to visualize outliers before handling.
- A function `clip_outliers_iqr` was defined to clip outliers using the Interquartile Range (IQR) method. This method adjusts extreme values to the upper or lower bounds instead of removing the data points entirely.
- The `clip_outliers_iqr` function was applied to all columns in `X`.
- Boxplots were generated again to visualize the effect of outlier clipping.

## 10. Train Test Split
The dataset `X` and `y` have been split into training and testing sets (`X_train`, `X_test`, `y_train`, `y_test`) with a test size of 20% and a random state of 42 for reproducibility.
