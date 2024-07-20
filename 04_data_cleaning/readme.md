## Data Cleaning

**Description:**
Data cleaning involves preparing and tidying data for analysis by addressing issues like duplicate entries and inconsistent formatting. Pandas provides tools for renaming, replacing, and removing duplicate data.

- **`DataFrame.replace()`**: Replaces specified values with new values.
- **`DataFrame.rename()`**: Renames columns or index labels.
- **`DataFrame.duplicated()`**: Identifies duplicate rows in a DataFrame.
- **`DataFrame.drop_duplicates()`**: Removes duplicate rows from a DataFrame.

### `DataFrame.replace()`

**Explanation:**
The `DataFrame.replace()` function is used to replace specified values with other values. This can be used to correct erroneous or inconsistent data in a DataFrame by replacing certain values with new ones.

**Features:**
- **Value Replacement:** Allows replacing specified values in the DataFrame.
- **Flexible:** Supports replacing multiple values with different replacements.
- **Method:** Can use regular expressions and provide replacement values for both single and multiple columns.

**Problem Solved:**
- Enables cleaning and standardizing data by replacing specific values, which is useful for correcting typos or inconsistencies in the dataset.

**Parameters:**
- **to_replace**: Value or list of values to be replaced. Can be a scalar, list, dictionary, or regex.
- **value**: Value(s) to replace the `to_replace` values with. Can be a scalar, list, dictionary, or regex.
- **inplace**: Whether to modify the DataFrame in place or return a new DataFrame. Default is `False`.
- **regex**: Whether to interpret `to_replace` and `value` as regex patterns. Default is `False`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'Bob'],
    'Age': [25, 30, 35, 30],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Los Angeles']
}
df = pd.DataFrame(data)

# Replacing 'Bob' with 'Robert' in the 'Name' column
df_replaced = df.replace(to_replace='Bob', value='Robert')

# Replacing multiple values with different replacements
df_replaced_multi = df.replace(to_replace={'City': 'Los Angeles'}, value={'City': 'LA'})

# Displaying the results
print("DataFrame with 'Bob' Replaced:")
print(df_replaced)
print("\nDataFrame with Multiple Replacements:")
print(df_replaced_multi)
```
*Explanation:*
- `df.replace(to_replace='Bob', value='Robert')` replaces all occurrences of 'Bob' with 'Robert' in the DataFrame.
- `df.replace(to_replace={'City': 'Los Angeles'}, value={'City': 'LA'})` replaces 'Los Angeles' with 'LA' in the 'City' column.

#### `DataFrame.rename()`

**Explanation:**
The `DataFrame.rename()` function is used to rename labels of rows or columns. This can be useful for making column names more descriptive or correcting typos in column or index labels.

**Features:**
- **Label Renaming:** Allows renaming row and column labels.
- **Flexible:** Supports renaming labels using dictionaries or functions.
- **Inplace Option:** Can modify the DataFrame in place or return a new DataFrame with updated labels.

**Problem Solved:**
- Facilitates renaming of labels to improve readability or correct mistakes, making the DataFrame easier to work with.

**Parameters:**
- **mapper**: Function or dictionary for renaming labels. If a dictionary, keys are old labels, and values are new labels.
- **axis**: Axis along which to rename (0 for index/rows, 1 for columns). Default is `None`.
- **inplace**: Whether to modify the DataFrame in place. Default is `False`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'Los Angeles', 'Chicago']
}
df = pd.DataFrame(data)

# Renaming columns
df_renamed_columns = df.rename(columns={'Name': 'Full Name', 'City': 'Location'})

# Renaming index
df_renamed_index = df.rename(index={0: 'row1', 1: 'row2', 2: 'row3'})

# Displaying the results
print("DataFrame with Renamed Columns:")
print(df_renamed_columns)
print("\nDataFrame with Renamed Index:")
print(df_renamed_index)
```
*Explanation:*
- `df.rename(columns={'Name': 'Full Name', 'City': 'Location'})` renames the 'Name' column to 'Full Name' and 'City' column to 'Location'.
- `df.rename(index={0: 'row1', 1: 'row2', 2: 'row3'})` renames the row indices 0, 1, and 2 to 'row1', 'row2', and 'row3', respectively.

#### `DataFrame.duplicated()`

**Explanation:**
The `DataFrame.duplicated()` function is used to identify duplicate rows in a DataFrame. It returns a boolean Series indicating whether each row is a duplicate of a previous row.

**Features:**
- **Duplicate Detection:** Identifies duplicate rows based on specified criteria.
- **Boolean Series:** Returns a Series of `True` and `False` values indicating duplicates.
- **Subset Option:** Can check for duplicates based on specific columns.

**Problem Solved:**
- Helps in identifying and handling duplicate rows in a dataset, which is crucial for data quality and integrity.

**Parameters:**
- **subset**: Columns to consider for identifying duplicates. Default is `None` (all columns).
- **keep**: Determines which duplicates to mark as `True`. Options are `'first'` (mark duplicates except for the first occurrence), `'last'` (mark duplicates except for the last occurrence), or `False` (mark all duplicates).

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with duplicates
data = {
    'Name': ['Alice', 'Bob', 'Alice', 'Charlie'],
    'Age': [25, 30, 25, 35],
    'City': ['New York', 'Los Angeles', 'New York', 'Chicago']
}
df = pd.DataFrame(data)

# Identifying duplicate rows
duplicates = df.duplicated()

# Identifying duplicates based on specific columns
duplicates_subset = df.duplicated(subset=['Name', 'City'])

# Displaying the results
print("Duplicate Rows:")
print(duplicates)
print("\nDuplicates Based on Subset of Columns:")
print(duplicates_subset)
```
*Explanation:*
- `df.duplicated()` marks rows that are duplicates of previous rows.
- `df.duplicated(subset=['Name', 'City'])` identifies duplicates based on the combination of 'Name' and 'City' columns.

#### `DataFrame.drop_duplicates()`

**Explanation:**
The `DataFrame.drop_duplicates()` function is used to remove duplicate rows from a DataFrame. It can be customized to keep the first or last occurrence of duplicates or drop all duplicates.

**Features:**
- **Removal:** Removes duplicate rows from the DataFrame.
- **Flexible:** Can keep the first occurrence, last occurrence, or drop all duplicates.
- **Subset Option:** Allows specifying columns to consider for identifying duplicates.

**Problem Solved:**
- Provides a method to clean up datasets by removing redundant rows, which is essential for accurate analysis.

**Parameters:**
- **subset**: Columns to consider for identifying duplicates. Default is `None` (all columns).
- **keep**: Determines which duplicates to keep. Options are `'first'` (keep the first occurrence), `'last'` (keep the last occurrence), or `False` (drop all duplicates).
- **inplace**: Whether to modify the DataFrame in place. Default is `False`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with duplicates
data = {
    'Name': ['Alice', 'Bob', 'Alice', 'Charlie'],
    'Age': [25, 30, 25, 35],
    'City': ['New York', 'Los Angeles', 'New York', 'Chicago']
}
df = pd.DataFrame(data)

# Removing duplicate rows
df_deduplicated = df.drop_duplicates()

# Removing duplicates based on specific columns
df_deduplicated_subset = df.drop_duplicates(subset=['Name', 'City'])

# Displaying the results
print("DataFrame with Duplicate Rows Removed:")
print(df_deduplicated)
print("\nDataFrame with Duplicates Removed Based on Subset of Columns:")
print(df_deduplicated_subset)
```
*Explanation:*
- `df.drop_duplicates()` removes duplicate rows from the DataFrame.
- `df.drop_duplicates(subset=['Name', 'City'])` removes duplicates based on the combination of 'Name' and 'City' columns.

