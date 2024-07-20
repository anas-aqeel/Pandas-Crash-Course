## Statistical Functions

**Description:**
Statistical functions provide tools for performing statistical analysis and summarization on data, including calculations of central tendencies and dispersion.

- **`DataFrame.describe()`**: Generates descriptive statistics of DataFrame columns.
- **`DataFrame.mean()`**: Calculates the mean of each column.
- **`DataFrame.median()`**: Calculates the median of each column.
- **`DataFrame.mode()`**: Finds the mode (most frequent value) of each column.
- **`DataFrame.std()`**: Computes the standard deviation of each column.
- **`DataFrame.var()`**: Computes the variance of each column.
- **`DataFrame.sum()`**: Calculates the sum of each column.
- **`DataFrame.cumsum()`**: Computes the cumulative sum of each column.
- **`DataFrame.cumprod()`**: Computes the cumulative product of each column.



### `DataFrame.describe()`

**Explanation:**
The `DataFrame.describe()` function generates descriptive statistics for the numerical columns of a DataFrame. It provides a quick overview of the central tendencies, spread, and shape of the data distribution.

**Features:**
- **Summary Statistics:** Includes count, mean, standard deviation, min, max, and quartiles.
- **Numeric Data:** By default, works with numerical columns, but can be customized to include object data types.
- **Percentiles:** Provides quantiles such as the 25th, 50th (median), and 75th percentiles.

**Problem Solved:**
- Provides a concise summary of the statistical properties of the data, useful for initial data exploration and understanding the data distribution.

**Parameters:**
- **percentiles**: List of percentiles to include in the output. Default is `[.25, .5, .75]`.
- **include**: Data types to include (e.g., `object` for strings). Default is `None`.
- **exclude**: Data types to exclude.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Generating descriptive statistics
description = df.describe()

# Displaying the result
print("Descriptive Statistics:")
print(description)
```
*Explanation:*
- `df.describe()` provides a statistical summary of the numerical columns in the DataFrame.

#### `DataFrame.mean()`

**Explanation:**
The `DataFrame.mean()` function calculates the mean (average) of each numerical column. It is used to determine the central tendency of the data.

**Features:**
- **Mean Calculation:** Computes the arithmetic mean of the numerical values in each column.
- **Axis Control:** Allows calculation along rows or columns.

**Problem Solved:**
- Computes the central tendency of data, which is essential for understanding the average value in the dataset.

**Parameters:**
- **axis**: Axis to compute the mean along. `0` for columns, `1` for rows. Default is `0`.
- **skipna**: Boolean indicating whether to exclude NA/null values. Default is `True`.
- **numeric_only**: Boolean indicating whether to include only numeric columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Calculating the mean of each column
mean_values = df.mean()

# Displaying the result
print("Mean Values:")
print(mean_values)
```
*Explanation:*
- `df.mean()` calculates the mean of the numerical columns in the DataFrame.

#### `DataFrame.median()`

**Explanation:**
The `DataFrame.median()` function computes the median value for each numerical column. The median is the middle value when data is ordered, providing a measure of central tendency that is less affected by outliers than the mean.

**Features:**
- **Median Calculation:** Computes the middle value of the data.
- **Axis Control:** Allows calculation along rows or columns.

**Problem Solved:**
- Provides a measure of central tendency that is robust to outliers, useful for understanding the distribution of data.

**Parameters:**
- **axis**: Axis to compute the median along. `0` for columns, `1` for rows. Default is `0`.
- **skipna**: Boolean indicating whether to exclude NA/null values. Default is `True`.
- **numeric_only**: Boolean indicating whether to include only numeric columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Calculating the median of each column
median_values = df.median()

# Displaying the result
print("Median Values:")
print(median_values)
```
*Explanation:*
- `df.median()` calculates the median of the numerical columns in the DataFrame.

#### `DataFrame.mode()`

**Explanation:**
The `DataFrame.mode()` function computes the mode (most frequent value) for each column. For columns with multiple modes, it returns all of them.

**Features:**
- **Mode Calculation:** Identifies the most frequently occurring value(s).
- **Multiple Modes:** Can return multiple values if more than one value has the highest frequency.

**Problem Solved:**
- Provides insight into the most common values in the dataset, useful for categorical data and frequency analysis.

**Parameters:**
- **axis**: Axis to compute the mode along. `0` for columns, `1` for rows. Default is `0`.
- **dropna**: Boolean indicating whether to exclude NA/null values. Default is `True`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with categorical data
data = {
    'A': ['x', 'y', 'x', 'z', 'y'],
    'B': [1, 2, 2, 3, 1]
}
df = pd.DataFrame(data)

# Calculating the mode of each column
mode_values = df.mode()

# Displaying the result
print("Mode Values:")
print(mode_values)
```
*Explanation:*
- `df.mode()` calculates the mode of each column in the DataFrame and returns all modes if multiple values have the highest frequency.

#### `DataFrame.std()`

**Explanation:**
The `DataFrame.std()` function computes the standard deviation of each numerical column. The standard deviation measures the dispersion of data points from the mean.

**Features:**
- **Standard Deviation Calculation:** Measures the spread of data points.
- **Axis Control:** Allows calculation along rows or columns.

**Problem Solved:**
- Provides a measure of data variability, which is useful for understanding how spread out the data is.

**Parameters:**
- **axis**: Axis to compute the standard deviation along. `0` for columns, `1` for rows. Default is `0`.
- **skipna**: Boolean indicating whether to exclude NA/null values. Default is `True`.
- **numeric_only**: Boolean indicating whether to include only numeric columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Calculating the standard deviation of each column
std_values = df.std()

# Displaying the result
print("Standard Deviation Values:")
print(std_values)
```
*Explanation:*
- `df.std()` calculates the standard deviation of the numerical columns in the DataFrame.

#### `DataFrame.var()`

**Explanation:**
The `DataFrame.var()` function computes the variance of each numerical column. Variance measures the average squared deviation of data points from the mean.

**Features:**
- **Variance Calculation:** Measures the spread of data points.
- **Axis Control:** Allows calculation along rows or columns.

**Problem Solved:**
- Provides a measure of data variability, similar to standard deviation but in squared units.

**Parameters:**
- **axis**: Axis to compute the variance along. `0` for columns, `1` for rows. Default is `0`.
- **skipna**: Boolean indicating whether to exclude NA/null values. Default is `True`.
- **numeric_only**: Boolean indicating whether to include only numeric columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Calculating the variance of each column
var_values = df.var()

# Displaying the result
print("Variance Values:")
print(var_values)
```
*Explanation:*
- `df.var()` calculates the variance of the numerical columns in the DataFrame.

#### `DataFrame.sum()`

**Explanation:**
The `DataFrame.sum()` function computes the sum of each numerical column or row. It aggregates the data by summing up the values.

**Features:**
- **Sum Calculation:** Computes the total sum of values.
- **Axis Control:** Allows summing along rows or columns.

**Problem Solved:**
- Provides a total aggregation of numerical data, useful for summarizing data and performing aggregate calculations.

**Parameters:**
- **axis**: Axis to compute the sum along. `0` for columns, `1` for rows. Default is `0`.
- **skipna**: Boolean indicating whether to exclude NA/null values. Default is `True`.
- **numeric_only**: Boolean indicating whether to include only numeric columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df

 = pd.DataFrame(data)

# Calculating the sum of each column
sum_values = df.sum()

# Displaying the result
print("Sum Values:")
print(sum_values)
```
*Explanation:*
- `df.sum()` calculates the sum of the numerical columns in the DataFrame.

#### `DataFrame.cumsum()`

**Explanation:**
The `DataFrame.cumsum()` function calculates the cumulative sum of each numerical column. It provides a running total of the values.

**Features:**
- **Cumulative Sum Calculation:** Provides a running total of values in each column.
- **Axis Control:** Allows cumulative summation along rows or columns.

**Problem Solved:**
- Useful for generating cumulative totals, which can be helpful for time series analysis or sequential data.

**Parameters:**
- **axis**: Axis to compute the cumulative sum along. `0` for columns, `1` for rows. Default is `0`.
- **skipna**: Boolean indicating whether to exclude NA/null values. Default is `True`.
- **numeric_only**: Boolean indicating whether to include only numeric columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Calculating the cumulative sum of each column
cumsum_values = df.cumsum()

# Displaying the result
print("Cumulative Sum Values:")
print(cumsum_values)
```
*Explanation:*
- `df.cumsum()` calculates the cumulative sum of the numerical columns in the DataFrame.

#### `DataFrame.cumprod()`

**Explanation:**
The `DataFrame.cumprod()` function calculates the cumulative product of each numerical column. It provides a running product of the values.

**Features:**
- **Cumulative Product Calculation:** Provides a running total of the product of values in each column.
- **Axis Control:** Allows cumulative multiplication along rows or columns.

**Problem Solved:**
- Useful for generating cumulative products, which can be helpful for financial or sequential data analysis.

**Parameters:**
- **axis**: Axis to compute the cumulative product along. `0` for columns, `1` for rows. Default is `0`.
- **skipna**: Boolean indicating whether to exclude NA/null values. Default is `True`.
- **numeric_only**: Boolean indicating whether to include only numeric columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'A': [1, 2, 3, 4, 5],
    'B': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Calculating the cumulative product of each column
cumprod_values = df.cumprod()

# Displaying the result
print("Cumulative Product Values:")
print(cumprod_values)
```
*Explanation:*
- `df.cumprod()` calculates the cumulative product of the numerical columns in the DataFrame.

