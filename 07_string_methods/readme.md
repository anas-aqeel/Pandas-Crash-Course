## String Methods

**Description:**
String methods provide functionalities for manipulating and analyzing textual data within DataFrames and Series. They support operations such as searching, replacing, and splitting strings.

- **`DataFrame.str.contains()`**: Checks if a pattern or substring exists in each element of a Series.
- **`DataFrame.str.replace()`**: Replaces occurrences of a pattern or substring in each element of a Series.
- **`DataFrame.str.extract()`**: Extracts substrings based on a regular expression pattern.
- **`DataFrame.str.split()`**: Splits each element of a Series into a list based on a delimiter.


### `DataFrame.str.contains()`

**Explanation:**
The `DataFrame.str.contains()` function checks if each element in a Series contains a specified substring. This is useful for filtering or extracting rows based on substring matches.

**Features:**
- **Substring Matching:** Checks if a substring is present within each element.
- **Regular Expressions:** Supports regular expressions for more complex matching.
- **Case Sensitivity:** Can be controlled using the `case` parameter.

**Problem Solved:**
- Allows for filtering and extracting rows based on whether a substring or pattern is present in the text data.

**Parameters:**
- **pat**: The substring or regular expression pattern to search for.
- **case**: Boolean indicating whether to perform a case-sensitive search. Default is `True`.
- **na**: Value to return for missing values (optional).

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with text data
data = {
    'Description': ['Apple fruit', 'Banana fruit', 'Carrot vegetable']
}
df = pd.DataFrame(data)

# Checking if 'fruit' is in the Description column
df['Contains Fruit'] = df['Description'].str.contains('fruit')

# Displaying the result
print("DataFrame with 'Contains Fruit' column:")
print(df)
```
*Explanation:*
- `df['Description'].str.contains('fruit')` checks each entry in the 'Description' column to see if it contains the substring 'fruit' and creates a new column with the boolean result.

#### `DataFrame.str.replace()`

**Explanation:**
The `DataFrame.str.replace()` function replaces occurrences of a specified substring or pattern within each element of a Series. It supports both simple replacements and regular expression-based replacements.

**Features:**
- **Replacement:** Replaces substrings or patterns with a specified value.
- **Regular Expressions:** Supports using regular expressions for advanced replacements.
- **Case Sensitivity:** Can be controlled using the `case` parameter.

**Problem Solved:**
- Facilitates modifying text data by replacing specified substrings or patterns.

**Parameters:**
- **pat**: The substring or regular expression pattern to replace.
- **repl**: The replacement value.
- **case**: Boolean indicating whether to perform a case-sensitive replacement. Default is `True`.
- **regex**: Boolean indicating whether `pat` is a regular expression. Default is `True`.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with text data
data = {
    'Description': ['Apple fruit', 'Banana fruit', 'Carrot vegetable']
}
df = pd.DataFrame(data)

# Replacing 'fruit' with 'fresh fruit'
df['Description'] = df['Description'].str.replace('fruit', 'fresh fruit')

# Displaying the result
print("DataFrame with replaced text:")
print(df)
```
*Explanation:*
- `df['Description'].str.replace('fruit', 'fresh fruit')` replaces occurrences of 'fruit' with 'fresh fruit' in the 'Description' column.

#### `DataFrame.str.extract()`

**Explanation:**
The `DataFrame.str.extract()` function extracts substrings that match a specified regular expression pattern. It is useful for parsing and extracting specific parts of text data.

**Features:**
- **Regular Expressions:** Extracts substrings based on regular expression patterns.
- **Capture Groups:** Supports extracting specific parts of a pattern using capture groups.

**Problem Solved:**
- Allows extraction of specific data from text based on patterns, which is useful for parsing and data cleaning.

**Parameters:**
- **pat**: The regular expression pattern to match.
- **expand**: Boolean or integer. If `True`, return a DataFrame with extracted groups; if `False`, return a Series.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with text data
data = {
    'Description': ['Apple fruit - 1', 'Banana fruit - 2', 'Carrot vegetable - 3']
}
df = pd.DataFrame(data)

# Extracting the number after '-'
df['Number'] = df['Description'].str.extract(r'-(\d+)')

# Displaying the result
print("DataFrame with extracted numbers:")
print(df)
```
*Explanation:*
- `df['Description'].str.extract(r'-(\d+)')` extracts numbers following the '-' character using a regular expression.

#### `DataFrame.str.split()`

**Explanation:**
The `DataFrame.str.split()` function splits each element in a Series into a list of substrings based on a specified delimiter. This is useful for tokenizing text or breaking text into components.

**Features:**
- **Splitting:** Splits each string based on a specified delimiter.
- **Regular Expressions:** Supports splitting based on regular expressions.

**Problem Solved:**
- Tokenizes or breaks text data into substrings for further analysis or processing.

**Parameters:**
- **pat**: The delimiter or regular expression to split by.
- **n**: Number of splits to perform (optional).
- **expand**: Boolean indicating whether to expand the split lists into separate columns.

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with text data
data = {
    'Description': ['Apple fruit', 'Banana fruit', 'Carrot vegetable']
}
df = pd.DataFrame(data)

# Splitting the Description column into two columns
df[['Fruit', 'Type']] = df['Description'].str.split(' ', n=1, expand=True)

# Displaying the result
print("DataFrame with split columns:")
print(df)
```
*Explanation:*
- `df['Description'].str.split(' ', n=1, expand=True)` splits each entry in the 'Description' column into two columns based on the first space.

