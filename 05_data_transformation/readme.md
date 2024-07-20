## Data Transformation

**Description:**
Data transformation involves applying operations to modify or reshape data for analysis. Pandas offers various functions to transform, pivot, and reshape data to meet analytical needs.

- **`DataFrame.apply()`**: Applies a function along an axis (rows or columns) of a DataFrame.
- **`DataFrame.applymap()`**: Applies a function to each element of a DataFrame.
- **`DataFrame.map()`**: Maps values from one set of values to another in a Series.
- **`DataFrame.pivot()`**: Reshapes data by creating a pivot table with specific rows and columns.
- **`DataFrame.pivot_table()`**: Creates a pivot table with aggregation of data.
- **`DataFrame.melt()`**: Unpivots a DataFrame from wide format to long format.
- **`DataFrame.stack()`**: Stacks the levels of columns into rows.
- **`DataFrame.unstack()`**: Unstacks rows into columns.
- **`DataFrame.transpose()`**: Transposes rows and columns of a DataFrame.

### `DataFrame.apply()`

**Explanation:**
The `DataFrame.apply()` function allows you to apply a function along an axis (rows or columns) of the DataFrame. This is useful for performing operations or transformations that need to be applied to each row or column.

**Features:**
- **Flexibility:** Can apply custom functions to each row or column.
- **Axis Parameter:** Allows specifying whether to apply the function along rows (`axis=0`) or columns (`axis=1`).
- **Return Type:** The result can be a DataFrame or Series, depending on the function applied.

**Problem Solved:**
- Enables the application of complex operations or transformations across rows or columns, which is useful for data manipulation and analysis.

**Parameters:**
- **func**: The function to apply. It can be a user-defined function or a built-in function.
- **axis**: Axis along which to apply the function. `0` for rows, `1` for columns. Default is `0`.
- **raw**: Whether to pass data as ndarray to the function. Default is `False`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'Salary': [50000, 60000, 70000]
}
df = pd.DataFrame(data)

# Applying a function to calculate tax on salary (e.g., 10% tax)
def calculate_tax(salary):
    return salary * 0.10

df['Tax'] = df['Salary'].apply(calculate_tax)

# Displaying the result
print("DataFrame with Tax Calculated:")
print(df)
```
*Explanation:*
- `df['Salary'].apply(calculate_tax)` applies the `calculate_tax` function to each value in the 'Salary' column.

#### `DataFrame.applymap()`

**Explanation:**
The `DataFrame.applymap()` function applies a function element-wise to all values in the DataFrame. This is useful for performing operations or transformations on each individual element.

**Features:**
- **Element-wise Operations:** Applies a function to each element of the DataFrame.
- **Flexible:** Can use any function that operates on individual elements.
- **Return Type:** Returns a DataFrame with the same shape as the original, but with transformed values.

**Problem Solved:**
- Facilitates element-wise transformations, such as formatting or scaling data, which is essential for data preparation and cleaning.

**Parameters:**
- **func**: The function to apply to each element of the DataFrame.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'Salary': [50000, 60000, 70000]
}
df = pd.DataFrame(data)

# Applying a function to format salary with a dollar sign
df_formatted = df.applymap(lambda x: f"${x:,.2f}" if isinstance(x, (int, float)) else x)

# Displaying the result
print("DataFrame with Formatted Salaries:")
print(df_formatted)
```
*Explanation:*
- `df.applymap(lambda x: f"${x:,.2f}" if isinstance(x, (int, float)) else x)` formats numeric values with a dollar sign and commas.

#### `DataFrame.map()`

**Explanation:**
The `DataFrame.map()` function applies a function to each element of a Series or DataFrame, similar to `applymap()`. It is primarily used for mapping values from one representation to another.

**Features:**
- **Mapping Values:** Allows mapping values based on a function, dictionary, or Series.
- **Flexible:** Can use functions, dictionaries, or Series for mapping values.
- **Return Type:** Returns a Series with the transformed values.

**Problem Solved:**
- Useful for transforming values based on a mapping or applying a function to each element.

**Parameters:**
- **mapper**: Function, dictionary, or Series for mapping values. If a function, it is applied to each value.
- **na_action**: Whether to apply the function to missing values. Options are `'ignore'` or `None`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35]
}
df = pd.DataFrame(data)

# Creating a mapping dictionary
age_mapping = {25: 'Twenty-five', 30: 'Thirty', 35: 'Thirty-five'}

# Applying the mapping to the 'Age' column
df['Age'] = df['Age'].map(age_mapping)

# Displaying the result
print("DataFrame with Age Mapped:")
print(df)
```
*Explanation:*
- `df['Age'].map(age_mapping)` replaces the values in the 'Age' column based on the provided dictionary.

#### `DataFrame.pivot()`

**Explanation:**
The `DataFrame.pivot()` function reshapes data by pivoting columns into rows and vice versa. It is used to create a new DataFrame with a specified index and columns, aggregating values accordingly.

**Features:**
- **Reshaping:** Converts unique values from one column into new columns, with corresponding data values.
- **Flexible:** Allows specifying index, columns, and values for the reshaping.
- **Unaggregated:** Does not aggregate data; each combination of index and columns must be unique.

**Problem Solved:**
- Enables restructuring data to fit specific analytical requirements, such as creating summary tables or reorganizing data for visualization.

**Parameters:**
- **index**: Column(s) to use as new index for the pivoted DataFrame.
- **columns**: Column(s) to use as new columns for the pivoted DataFrame.
- **values**: Column(s) to use for populating the new DataFrame.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Date': ['2024-01-01', '2024-01-01', '2024-01-02', '2024-01-02'],
    'City': ['New York', 'Los Angeles', 'New York', 'Los Angeles'],
    'Temperature': [32, 75, 30, 72]
}
df = pd.DataFrame(data)

# Pivoting the DataFrame
df_pivoted = df.pivot(index='Date', columns='City', values='Temperature')

# Displaying the result
print("Pivoted DataFrame:")
print(df_pivoted)
```
*Explanation:*
- `df.pivot(index='Date', columns='City', values='Temperature')` creates a pivot table where dates are rows, cities are columns, and temperature values are filled accordingly.

#### `DataFrame.pivot_table()`

**Explanation:**
The `DataFrame.pivot_table()` function creates a pivot table by aggregating data based on specified rows and columns. It allows for grouping and summarizing data with aggregation functions.

**Features:**
- **Aggregation:** Supports aggregating data using functions like sum, mean, etc.
- **Grouping:** Groups data based on specified index and columns.
- **Flexible Aggregation:** Allows specifying multiple aggregation functions and handling missing data.

**Problem Solved:**
- Useful for creating summary tables and performing aggregations on grouped data, which is essential for exploratory data analysis.

**Parameters:**
- **values**: Column(s) to aggregate.
- **index**: Column(s) to use as new index for the pivot table.
- **columns**: Column(s) to use as new columns for the pivot table.
- **aggfunc**: Aggregation function(s) to apply. Default is `numpy.mean`.
- **fill_value**: Value to replace missing values with.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Date': ['2024-01-01', '2024-01-01', '2024-01-02', '2024-01-02'],
    'City': ['New York', 'Los Angeles', 'New York', 'Los Angeles'],
    'Temperature': [32, 75, 30, 72],
    'Humidity': [55, 20, 60, 25]
}
df = pd.DataFrame(data)

# Creating a pivot table
pivot_table = df.pivot_table(index='Date', columns='City', values='Temperature', aggfunc='mean')

# Displaying the result
print("Pivot Table:")
print(pivot_table)
```
*Explanation:*
- `df.pivot_table(index='Date', columns='City', values='Temperature', aggfunc='mean')` creates a pivot table that shows the average temperature for each city on each date.

#### `DataFrame.melt()`

**Explanation:**
The `DataFrame.melt()` function is used to unpivot or reshape a DataFrame from wide format to long format. It converts columns into rows, making the DataFrame longer and narrower.

**Features:**
- **Reshaping:** Converts wide-format data into long-format.
- **Flexible:** Allows specifying which columns to keep and which to unpivot.
- **Useful for Analysis:** Facilitates data transformation for certain types of analysis and visualization.

**Problem Solved:**
- Useful for restructuring data to a format suitable for analysis and visualization, especially when data is in wide format.

**Parameters:**
- **id_vars**: Columns to keep as identifier variables

.
- **value_vars**: Columns to unpivot into rows.
- **var_name**: Name for the new column that holds the unpivoted column names.
- **value_name**: Name for the new column that holds the unpivoted values.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Date': ['2024-01-01', '2024-01-02'],
    'New York Temp': [32, 30],
    'LA Temp': [75, 72]
}
df = pd.DataFrame(data)

# Melting the DataFrame
df_melted = pd.melt(df, id_vars='Date', var_name='City', value_name='Temperature')

# Displaying the result
print("Melted DataFrame:")
print(df_melted)
```
*Explanation:*
- `pd.melt(df, id_vars='Date', var_name='City', value_name='Temperature')` transforms the DataFrame from wide format to long format, with 'Date' as an identifier and temperatures in a single column.

#### `DataFrame.stack()`

**Explanation:**
The `DataFrame.stack()` function stacks the columns of a DataFrame into a Series, creating a multi-level index. This is useful for reshaping data, especially for hierarchical indexing.

**Features:**
- **Stacking Columns:** Converts columns into rows, creating a hierarchical index.
- **Multi-level Index:** Results in a Series with a multi-level index, useful for complex data structures.
- **Flexible:** Allows reshaping data for various analysis needs.

**Problem Solved:**
- Facilitates complex reshaping and hierarchical indexing of data, making it easier to handle multi-dimensional data.

**Parameters:**
- **level**: Level(s) to stack if the DataFrame has a multi-level index. Default is `None`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Date': ['2024-01-01', '2024-01-02'],
    'New York': [32, 30],
    'LA': [75, 72]
}
df = pd.DataFrame(data)

# Setting 'Date' as index
df.set_index('Date', inplace=True)

# Stacking the DataFrame
df_stacked = df.stack()

# Displaying the result
print("Stacked DataFrame:")
print(df_stacked)
```
*Explanation:*
- `df.stack()` converts the columns into rows, resulting in a Series with a multi-level index, with 'Date' as the first level and city names as the second level.

#### `DataFrame.unstack()`

**Explanation:**
The `DataFrame.unstack()` function is the reverse of `stack()`. It pivots the innermost level of the row index to columns, effectively converting rows into columns.

**Features:**
- **Unstacking Rows:** Converts rows into columns, creating a DataFrame with a new level of columns.
- **Multi-level Index:** Works with DataFrames having multi-level indices.
- **Flexible:** Allows converting hierarchical data into a more readable format.

**Problem Solved:**
- Converts hierarchical or multi-level row indices into columns, facilitating easier data analysis and visualization.

**Parameters:**
- **level**: Level(s) to unstack. Default is the innermost level.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with multi-level index
data = {
    'Temperature': [32, 30, 75, 72]
}
index = pd.MultiIndex.from_tuples(
    [('2024-01-01', 'New York'), ('2024-01-01', 'LA'),
     ('2024-01-02', 'New York'), ('2024-01-02', 'LA')],
    names=['Date', 'City']
)
df = pd.DataFrame(data, index=index)

# Unstacking the DataFrame
df_unstacked = df.unstack()

# Displaying the result
print("Unstacked DataFrame:")
print(df_unstacked)
```
*Explanation:*
- `df.unstack()` converts the 'City' level of the index into columns, creating a DataFrame with dates as rows and cities as columns.

#### `DataFrame.transpose()`

**Explanation:**
The `DataFrame.transpose()` function transposes the DataFrame, swapping rows and columns. This is useful for changing the orientation of the data.

**Features:**
- **Transpose:** Swaps rows and columns, effectively flipping the DataFrame.
- **Simple Operation:** A straightforward way to change data orientation.

**Problem Solved:**
- Facilitates the reorientation of data, making it easier to perform operations or analyses that require data in a different format.

**Parameters:**
- **None:** This function does not take any parameters.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame
data = {
    'Date': ['2024-01-01', '2024-01-02'],
    'New York': [32, 30],
    'LA': [75, 72]
}
df = pd.DataFrame(data)

# Transposing the DataFrame
df_transposed = df.transpose()

# Displaying the result
print("Transposed DataFrame:")
print(df_transposed)
```
*Explanation:*
- `df.transpose()` swaps rows and columns, making dates the new columns and cities the new rows.

