## Utilities

**Description:**


Utilities offer additional functionality for configuring pandas options and retrieving specific settings.

- **`pd.set_option()`**: Sets options for pandas configuration.
- **`pd.get_option()`**: Retrieves the current value of a pandas configuration option.



### `pd.set_option()`

**Explanation:**
The `pd.set_option()` function is used to configure display options for pandas. This allows users to adjust how pandas displays data, such as the maximum number of rows and columns shown, or the precision of floating-point numbers.

**Features:**
- **Customizable Display:** Control over the appearance of DataFrames in the output.
- **Performance Tuning:** Adjust settings to optimize performance and readability based on user needs.

**Problem Solved:**
- Provides flexibility in controlling the display and behavior of pandas, enhancing the user experience and tailoring outputs to specific needs.

**Parameters:**
- **option**: The name of the option to set (e.g., 'display.max_rows').
- **value**: The value to set for the option.

**Example Code:**
```python
import pandas as pd

# Set display options
pd.set_option('display.max_rows', 10)  # Show a maximum of 10 rows
pd.set_option('display.float_format', '{:.2f}'.format)  # Format float numbers to 2 decimal places

# Sample DataFrame
df = pd.DataFrame({
    'A': [1.12345, 2.67890, 3.54321],
    'B': [10, 20, 30]
})

# Display DataFrame
print("DataFrame with set options:")
print(df)
```
*Explanation:*
- `pd.set_option('display.max_rows', 10)` limits the display to 10 rows, and `pd.set_option('display.float_format', '{:.2f}'.format)` formats floating-point numbers to 2 decimal places.

#### `pd.get_option()`

**Explanation:**
The `pd.get_option()` function retrieves the current value of a pandas display option. This is useful for checking configuration settings and debugging.

**Features:**
- **Retrieve Settings:** Allows you to see the current settings for display options.
- **Debugging:** Helps in troubleshooting display issues or verifying configuration.

**Problem Solved:**
- Provides a way to query and confirm the current settings for display options, aiding in debugging and verification.

**Parameters:**
- **option**: The name of the option to retrieve (e.g., 'display.max_rows').

**Example Code:**
```python
import pandas as pd

# Get current display options
max_rows = pd.get_option('display.max_rows')
float_format = pd.get_option('display.float_format')

# Display current options
print("Current display options:")
print(f"Max rows: {max_rows}")
print(f"Float format: {float_format}")
```
*Explanation:*
- Retrieves and prints the current values of the display options for maximum rows and float format.



