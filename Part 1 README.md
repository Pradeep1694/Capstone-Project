# Data Loading
Loaded the dataset into a Pandas DataFrame.
Explored the dataset using head(), and shape
Identified numerical and categorical columns.

# Data Cleaning
Checked null values.
Find the missing value and missing percentage.
check the columns with >20% missing values and  fill numeric columns with the column median
Verified the data types after conversion.

# Duplicate detection and removal
Checked all columns for missing values.
find the Duplicate values and removal.

# Data type correction: 
Checked all column data types using df.dtypes.
Converted columns stored as object to numeric where possible using pd.to_numeric(errors='ignore').
Converted repetitive string columns to category data type to reduce memory usage.
Compared memory usage before and after conversion using df.memory_usage(deep=True).sum().
The conversion reduced memory usage while preserving the data.

# Descriptive statistics and skewness
Calculated descriptive statistics using df.describe().
Computed skewness for all numeric columns using df.skew().
The column with the highest absolute skewness is <column_name> with a skewness of <value>.
If skewness is positive, the distribution is right-skewed (long tail on the right), so the median is a better choice for imputing missing values because it is less affected by extreme values.
If skewness is negative, the distribution is left-skewed (long tail on the left), and the median is also generally more robust than the mean for imputation.

# Outlier Detection
Used the IQR method to detect outliers.
Calculated Q1, Q3, and IQR.
Identified outliers in discounted_price and actual_price.
Outliers were kept because they represent genuine variations in product price and ratings rather than data errors.

# Data Visualization
# Line Plot
Choosing one numeric column of discounted_price.
Ploting against the row index 
Adding a title, x-axis label, and y-axis label.
# Bar Chart
Choosing one categorical column of category and one numeric column average Discounted Price.
Group the data by the category.
Compute the mean of the numeric column for each category.
Ploting those mean values as a bar chart.
# Histogram
Creating a histogram with 20 bins.
the distribution is right-skewed.
# Scatter Plot
Two numeric columns that you expect to be related actual_price and discounted_price.
The relationship appears positive b/w two variables.
# Box Plot
one numeric column and one categorical column.
visualized the distribution and detected outlier
# Correlation Heatmap
Generated a Pearson correlation heatmap.
actual_price and discounted_price showed strong positive correlation.

# Imputation Strategy Comparison
Compared mean and median values for skewed columns.
Since the columns were skewed, median imputation was selected.
Filled missing values using the median.
# Spearman Rank Correlation
Computed the Spearman correlation matrix.
Compared Spearman and Pearson correlations.
Spearman correlation was preferred for monotonic relationships.

# Grouped Aggregation
Grouped the dataset by category.
Calculated mean and standard deviation for discounted_price.
Highest mean category: (42990.0)
Highest standard deviation category: (0.0)
Ratio of highest mean to lowest mean: (Ratio: 558.3116883116883)
The results indicate whether category is a useful predictor of price.

# Save Cleaned Dataset
Saved the cleaned dataset as cleaned_data.csv.

# Tools Used
source of dataset: kaggle
Python
Pandas
NumPy
Matplotlib
Seaborn
Google Colab
