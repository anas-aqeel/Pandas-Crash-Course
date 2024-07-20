## Data Handling

**Description:**
Handling missing data involves identifying, removing, or imputing missing values in a DataFrame or Series. Pandas provides functions to detect and manage these gaps effectively.

- **`DataFrame.isnull()`**: Detects missing values in a DataFrame.
- **`DataFrame.notnull()`**: Detects non-missing values in a DataFrame.
- **`DataFrame.dropna()`**: Removes missing values from a DataFrame.
- **`DataFrame.fillna()`**: Fills missing values with specified data.


### `DataFrame.isnull()`

**Explanation:**
The `DataFrame.isnull()` function is used to detect missing values in a DataFrame. It returns a DataFrame of the same shape as the original, with `True` indicating where values are missing (i.e., `NaN`), and `False` otherwise.

**Features:**
- **Detection:** Identifies missing values in the DataFrame.
- **Boolean DataFrame:** Returns a DataFrame with boolean values indicating the presence of missing data.
- **Comprehensive:** Can be used to detect missing values in all columns and rows.

**Problem Solved:**
- Helps in identifying missing data points so that appropriate handling can be performed (e.g., filling or dropping missing values).

**Parameters:**
- No additional parameters are required. The function operates directly on the DataFrame to detect `NaN` values.

**Example Code:**
```python
import pandas as pd
import numpy as np

# Sample DataFrame with missing values
data = {
    'Name': ['Alice', 'Bob', np.nan, 'David'],
    'Age': [25, np.nan, 35, 40],
    'City': ['New York', 'Los Angeles', 'Chicago', np.nan]
}
df = pd.DataFrame(data)

# Detecting missing values
missing_values = df.isnull()

# Displaying the result
print("Missing Values DataFrame:")
print(missing_values)
```
*Explanation:*
- `df.isnull()` returns a DataFrame of the same shape as `df`, with `True` for missing values and `False` otherwise.

#### `DataFrame.notnull()`

**Explanation:**
The `DataFrame.notnull()` function is the opposite of `isnull()`. It detects non-missing values in a DataFrame and returns a DataFrame of the same shape with `True` where values are not missing and `False` where values are missing.

**Features:**
- **Non-Missing Detection:** Identifies non-missing values in the DataFrame.
- **Boolean DataFrame:** Returns a DataFrame with boolean values indicating the presence of non-missing data.
- **Useful for Filtering:** Helps in filtering out missing values by focusing on non-missing data.

**Problem Solved:**
- Facilitates operations on data by identifying and focusing on the non-missing values.

**Parameters:**
- No additional parameters are required. The function operates directly on the DataFrame to detect non-missing values.

**Example Code:**
```python
import pandas as pd
import numpy as np

# Sample DataFrame with missing values
data = {
    'Name': ['Alice', 'Bob', np.nan, 'David'],
    'Age': [25, np.nan, 35, 40],
    'City': ['New York', 'Los Angeles', 'Chicago', np.nan]
}
df = pd.DataFrame(data)

# Detecting non-missing values
non_missing_values = df.notnull()

# Displaying the result
print("Non-Missing Values DataFrame:")
print(non_missing_values)
```
*Explanation:*
- `df.notnull()` returns a DataFrame of the same shape as `df`, with `True` for non-missing values and `False` otherwise.

#### `DataFrame.dropna()`

**Explanation:**
The `DataFrame.dropna()` function is used to remove missing values from a DataFrame. It can be used to drop rows or columns containing missing values, depending on the specified parameters.

**Features:**
- **Removal:** Removes rows or columns with missing values.
- **Flexible:** Can be customized to drop rows or columns based on the extent of missing values.
- **Threshold Parameter:** Allows specifying a minimum number of non-NA values required to keep the row/column.

**Problem Solved:**
- Provides a method for cleaning data by removing entries with missing values, which is essential for ensuring data quality.

**Parameters:**
- **axis**: Determines whether to drop rows (`axis=0`) or columns (`axis=1`). Default is `0`.
- **how**: Determines how to drop rows/columns. Options are `'any'` (drop if any value is missing) or `'all'` (drop if all values are missing).
- **thresh**: Minimum number of non-NA values required to keep the row/column.
- **subset**: Specifies a subset of columns or rows to consider for missing values.

**Example Code:**
```python
import pandas as pd
import numpy as np

# Sample DataFrame with missing values
data = {
    'Name': ['Alice', 'Bob', np.nan, 'David'],
    'Age': [25, np.nan, 35, 40],
    'City': ['New York', 'Los Angeles', 'Chicago', np.nan]
}
df = pd.DataFrame(data)

# Dropping rows with any missing values
df_dropped_rows = df.dropna(axis=0, how='any')

# Dropping columns with any missing values
df_dropped_columns = df.dropna(axis=1, how='any')

# Displaying the results
print("DataFrame with Rows Dropped:")
print(df_dropped_rows)
print("\nDataFrame with Columns Dropped:")
print(df_dropped_columns)
```
*Explanation:*
- `df.dropna(axis=0, how='any')` removes rows with any missing values.
- `df.dropna(axis=1, how='any')` removes columns with any missing values.

#### `DataFrame.fillna()`

**Explanation:**
The `DataFrame.fillna()` function is used to fill missing values in a DataFrame with specified values. It can be used to replace missing values with a scalar value, forward fill, backward fill, or other methods.

**Features:**
- **Imputation:** Provides various methods to fill missing values, ensuring that the DataFrame remains complete.
- **Flexible:** Allows filling with scalar values, methods like forward/backward fill, or using other data.

**Problem Solved:**
- Allows for the imputation of missing values to maintain a complete dataset, which is crucial for analysis and modeling.

**Parameters:**
- **value**: Scalar value or dictionary of values to use for filling missing data.
- **method**: Method to use for filling missing values. Options are `'ffill'` (forward fill) or `'bfill'` (backward fill).
- **axis**: Axis along which to fill missing values. Default is `None`.
- **inplace**: Whether to modify the DataFrame in place. Default is `False`.

**Example Code:**
```python
import pandas as pd
import numpy as np

# Sample DataFrame with missing values
data = {
    'Name': ['Alice', 'Bob', np.nan, 'David'],
    'Age': [25, np.nan, 35, 40],
    'City': ['New York', 'Los Angeles', 'Chicago', np.nan]
}
df = pd.DataFrame(data)

# Filling missing values with a specific value
df_filled_value = df.fillna(value={'Name': 'Unknown', 'Age': df['Age'].mean(), 'City': 'Unknown'})

# Forward filling missing values
df_filled_ffill = df.fillna(method='ffill')

# Displaying the results
print("DataFrame with Missing Values Filled:")
print(df_filled_value)
print("\nDataFrame with Forward Fill:")
print(df_filled_ffill)
```
*Explanation:*
- `df.fillna(value={'Name': 'Unknown', 'Age': df['Age'].mean(), 'City': 'Unknown'})` fills missing values with specified values.
- `df.fillna(method='ffill')` performs forward filling to replace missing values with the previous non-missing value.

