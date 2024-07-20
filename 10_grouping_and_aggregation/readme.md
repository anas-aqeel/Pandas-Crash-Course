


## Advanced Grouping and Aggregation

**Description:**
Advanced grouping and aggregation functions provide tools for performing complex data manipulations, such as applying transformations and aggregating over rolling windows.

- **`DataFrame.transform()`**: Applies a function to each group within a DataFrame and returns a DataFrame with the same shape.
- **`DataFrame.rolling()`**: Provides rolling window calculations for time-series analysis.
- **`DataFrame.expanding()`**: Performs expanding window calculations for cumulative analysis.

### `DataFrame.transform()`

**Explanation:**
The `DataFrame.transform()` function allows you to perform a transformation on each group of a DataFrame. It is often used in conjunction with the `groupby()` function to apply a function to each group independently.

**Features:**
- **Transformation Function:** Applies a function to each group, returning a DataFrame of the same shape.
- **Flexibility:** Can apply various functions like aggregation, scaling, or custom transformations.
- **Alignment:** Maintains the original DataFrame’s shape.

**Problem Solved:**
- Useful for applying complex transformations to each group of data, while preserving the original DataFrame’s structure.

**Parameters:**
- **func**: Function to apply to each group. Can be a callable function or a list of functions.
- **axis**: Axis to apply the function along. Default is `0` (rows).

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with categorical and numerical data
data = {
    'Category': ['A', 'A', 'B', 'B', 'C', 'C'],
    'Values': [10, 15, 10, 20, 15, 25]
}
df = pd.DataFrame(data)

# Transform function to normalize values within each category
transformed_df = df.groupby('Category').transform(lambda x: (x - x.mean()) / x.std())

# Displaying the result
print("Transformed DataFrame:")
print(transformed_df)
```
*Explanation:*
- `df.groupby('Category').transform(lambda x: (x - x.mean()) / x.std())` normalizes the values within each category.

#### `DataFrame.rolling()`

**Explanation:**
The `DataFrame.rolling()` function provides rolling window calculations. It is useful for time series analysis where you need to compute statistics over a rolling window of a given size.

**Features:**
- **Window Size:** Allows specifying the size of the rolling window.
- **Window Functions:** Supports various functions like mean, sum, and more.
- **Flexibility:** Can be used with different types of rolling functions.

**Problem Solved:**
- Useful for smoothing time series data and calculating rolling statistics.

**Parameters:**
- **window**: Size of the moving window. Can be an integer or a string (e.g., '7D' for 7 days).
- **min_periods**: Minimum number of observations required in the window. Default is `None`.
- **center**: Boolean indicating whether to set the labels at the center of the window. Default is `False`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with time series data
data = {
    'Date': pd.date_range(start='2024-01-01', periods=10, freq='D'),
    'Values': [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
}
df = pd.DataFrame(data)
df.set_index('Date', inplace=True)

# Calculating rolling mean with a window of 3 days
rolling_mean = df.rolling(window=3).mean()

# Displaying the result
print("Rolling Mean:")
print(rolling_mean)
```
*Explanation:*
- `df.rolling(window=3).mean()` calculates the rolling mean over a 3-day window.

#### `DataFrame.expanding()`

**Explanation:**
The `DataFrame.expanding()` function provides expanding window calculations. It computes statistics over an expanding window from the start of the DataFrame to the current data point.

**Features:**
- **Expanding Window:** Expands the window size as more data points are included.
- **Window Functions:** Supports various functions like mean, sum, and more.
- **Flexibility:** Useful for cumulative statistics.

**Problem Solved:**
- Useful for computing cumulative statistics over time, such as cumulative sums or means.

**Parameters:**
- **axis**: Axis to apply the function along. Default is `0` (rows).

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'Values': [1, 2, 3, 4, 5]
}
df = pd.DataFrame(data)

# Calculating expanding mean
expanding_mean = df.expanding().mean()

# Displaying the result
print("Expanding Mean:")
print(expanding_mean)
```
*Explanation:*
- `df.expanding().mean()` calculates the expanding mean from the start to each data point.
