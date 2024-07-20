## Window Functions

**Description:**
Window functions allow for calculations over a defined window or range of data points, useful for time-series analysis and moving averages.

- **`DataFrame.rolling()`**: Applies a rolling window calculation to DataFrame data.
- **`DataFrame.expanding()`**: Applies an expanding window calculation to DataFrame data.
- **`DataFrame.ewm()`**: Applies an exponentially weighted window calculation to DataFrame data.


### `DataFrame.rolling()`

**Explanation:**
The `DataFrame.rolling()` function provides rolling window calculations for a DataFrame. It allows you to compute statistics over a moving window of a specified size, which is particularly useful for time series analysis and smoothing.

**Features:**
- **Rolling Window:** Applies calculations over a fixed-size window that moves through the data.
- **Flexibility:** Supports various window functions such as mean, sum, and custom functions.
- **Adjustable Parameters:** Allows customization of window size and other settings.

**Problem Solved:**
- Useful for smoothing data, calculating moving averages, and other rolling statistics in time series analysis.

**Parameters:**
- **window**: Size of the moving window. Can be an integer specifying the number of observations, or a string for time-based windows (e.g., '7D' for 7 days).
- **min_periods**: Minimum number of observations in the window required to have a value. Default is `None`.
- **center**: Boolean indicating whether the window should be centered around the current data point. Default is `False`.
- **axis**: Axis to apply the function along. Default is `0` (rows).

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'Date': pd.date_range(start='2024-01-01', periods=10, freq='D'),
    'Values': [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
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
- `df.rolling(window=3).mean()` calculates the rolling mean of the 'Values' column over a 3-day window.

#### `DataFrame.expanding()`

**Explanation:**
The `DataFrame.expanding()` function provides expanding window calculations. Unlike the rolling window, the expanding window grows as more data points are included, from the start to the current data point.

**Features:**
- **Expanding Window:** Computes statistics from the start of the DataFrame up to the current point.
- **Accumulation:** Suitable for cumulative calculations.

**Problem Solved:**
- Useful for computing cumulative statistics such as cumulative sums or means over time.

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
- `df.expanding().mean()` calculates the expanding mean from the start of the data up to each data point.

#### `DataFrame.ewm()`

**Explanation:**
The `DataFrame.ewm()` function provides exponential weighted calculations. It applies an exponentially decreasing weight to the observations, giving more importance to recent observations.

**Features:**
- **Exponential Weighting:** Applies weights that decrease exponentially, which is useful for time series data with trends.
- **Customizable:** Allows customization of the span, halflife, or alpha for exponential weighting.

**Problem Solved:**
- Useful for smoothing time series data and calculating exponentially weighted moving averages or other statistics.

**Parameters:**
- **com**: Center of mass for exponential weighting (1 / alpha - 1).
- **span**: Span for the exponential weighting.
- **halflife**: Half-life for the exponential weighting.
- **alpha**: Smoothing factor.
- **adjust**: Boolean indicating whether to adjust the weights (default `True`).

**Example Code:**
```python
import pandas as pd

# Sample DataFrame with numerical data
data = {
    'Values': [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)

# Calculating exponentially weighted mean with a span of 2
ewm_mean = df.ewm(span=2).mean()

# Displaying the result
print("Exponentially Weighted Mean:")
print(ewm_mean)
```
*Explanation:*
- `df.ewm(span=2).mean()` calculates the exponentially weighted mean with a span of 2.

