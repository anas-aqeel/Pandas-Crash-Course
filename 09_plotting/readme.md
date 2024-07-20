
## Plotting

**Description:**
Plotting functions enable data visualization within pandas, allowing users to create various types of charts and plots to analyze and present data visually.

- **`DataFrame.plot()`**: Creates a plot based on DataFrame data.
- **`DataFrame.plot.bar()`**: Generates a bar chart from DataFrame data.
- **`DataFrame.plot.hist()`**: Creates a histogram from DataFrame data.
- **`DataFrame.plot.box()`**: Generates a box plot from DataFrame data.
- **`DataFrame.plot.scatter()`**: Creates a scatter plot from DataFrame data.
- **`DataFrame.plot.pie()`**: Generates a pie chart from DataFrame data.
- **`matplotlib.pyplot.show()`**: Displays the plot created by pandas.

### `DataFrame.plot()`

**Explanation:**
The `DataFrame.plot()` function is a versatile method for creating various types of plots from a DataFrame. It integrates with Matplotlib to generate line plots, bar plots, histograms, and more.

**Features:**
- **Plot Types:** Supports different types of plots including line, bar, histogram, box plot, and more.
- **Customization:** Allows customization of plot appearance using parameters.
- **Integration:** Works with Matplotlib, making it easy to extend plots with additional features.

**Problem Solved:**
- Provides a straightforward way to visualize data and analyze patterns, trends, and distributions.

**Parameters:**
- **kind**: Type of plot to generate. Options include 'line', 'bar', 'barh', 'hist', 'box', 'kde', 'density', 'area', 'pie', 'scatter', 'hexbin'.
- **x**: Column name or index for the x-axis (if not using default index).
- **y**: Column name or index for the y-axis (if not using default columns).
- **color**: Color or sequence of colors for the plot.
- **title**: Title of the plot.

**Example Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample DataFrame with numerical data
data = {
    'Month': ['Jan', 'Feb', 'Mar', 'Apr', 'May'],
    'Sales': [200, 240, 300, 280, 350]
}
df = pd.DataFrame(data)

# Creating a line plot
df.plot(kind='line', x='Month', y='Sales', color='blue', title='Monthly Sales')

# Displaying the plot
plt.show()
```
*Explanation:*
- `df.plot(kind='line', x='Month', y='Sales', color='blue', title='Monthly Sales')` creates a line plot of sales data over months.

#### `DataFrame.plot.bar()`

**Explanation:**
The `DataFrame.plot.bar()` function creates a bar plot, which is useful for comparing different categories or groups of data.

**Features:**
- **Vertical Bars:** Default to vertical bar charts.
- **Horizontal Bars:** Can create horizontal bar charts with the `kind='barh'` parameter.
- **Customization:** Supports customization of colors, titles, and labels.

**Problem Solved:**
- Helps in visualizing and comparing categorical data across different groups.

**Parameters:**
- **x**: Column name for the x-axis.
- **y**: Column name(s) for the y-axis.
- **color**: Color or sequence of colors for the bars.
- **title**: Title of the plot.

**Example Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample DataFrame with categorical data
data = {
    'Category': ['A', 'B', 'C', 'D'],
    'Values': [10, 20, 15, 25]
}
df = pd.DataFrame(data)

# Creating a vertical bar plot
df.plot(kind='bar', x='Category', y='Values', color='green', title='Category Values')

# Displaying the plot
plt.show()
```
*Explanation:*
- `df.plot(kind='bar', x='Category', y='Values', color='green', title='Category Values')` generates a vertical bar plot comparing values across categories.

#### `DataFrame.plot.hist()`

**Explanation:**
The `DataFrame.plot.hist()` function creates a histogram, which is used to visualize the distribution of numerical data.

**Features:**
- **Histogram Bins:** Allows specifying the number of bins or interval size.
- **Density Plot:** Can show the density plot with `density=True`.
- **Customization:** Supports customization of colors, labels, and titles.

**Problem Solved:**
- Provides insights into the distribution and frequency of numerical data.

**Parameters:**
- **bins**: Number of bins or interval size for the histogram.
- **density**: Boolean indicating whether to plot a density curve. Default is `False`.
- **color**: Color or sequence of colors for the histogram bars.
- **title**: Title of the plot.

**Example Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample DataFrame with numerical data
data = {
    'Values': [10, 20, 20, 30, 30, 30, 40, 50]
}
df = pd.DataFrame(data)

# Creating a histogram
df.plot(kind='hist', bins=5, color='purple', title='Value Distribution')

# Displaying the plot
plt.show()
```
*Explanation:*
- `df.plot(kind='hist', bins=5, color='purple', title='Value Distribution')` generates a histogram showing the distribution of values.

#### `DataFrame.plot.box()`

**Explanation:**
The `DataFrame.plot.box()` function creates a box plot, which is useful for visualizing the distribution of data and identifying outliers.

**Features:**
- **Box Plot Elements:** Displays quartiles, median, and outliers.
- **Customization:** Supports customization of colors, labels, and titles.

**Problem Solved:**
- Helps in understanding data distribution, identifying outliers, and comparing distributions across groups.

**Parameters:**
- **color**: Color or sequence of colors for the box plot elements.
- **title**: Title of the plot.

**Example Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample DataFrame with numerical data
data = {
    'Values': [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
}
df = pd.DataFrame(data)

# Creating a box plot
df.plot(kind='box', color='orange', title='Value Distribution')

# Displaying the plot
plt.show()
```
*Explanation:*
- `df.plot(kind='box', color='orange', title='Value Distribution')` creates a box plot to visualize the distribution of values and identify outliers.

#### `DataFrame.plot.scatter()`

**Explanation:**
The `DataFrame.plot.scatter()` function creates a scatter plot, which is useful for visualizing the relationship between two numerical variables.

**Features:**
- **Scatter Plot Elements:** Plots data points on a Cartesian plane.
- **Customization:** Allows customization of point size, color, and labels.

**Problem Solved:**
- Helps in identifying correlations and relationships between two numerical variables.

**Parameters:**
- **x**: Column name for the x-axis.
- **y**: Column name for the y-axis.
- **s**: Size of the scatter plot markers.
- **c**: Color or sequence of colors for the markers.
- **title**: Title of the plot.

**Example Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample DataFrame with numerical data
data = {
    'X': [1, 2, 3, 4, 5],
    'Y': [10, 20, 15, 25, 30]
}
df = pd.DataFrame(data)

# Creating a scatter plot
df.plot(kind='scatter', x='X', y='Y', color='red', title='X vs Y')

# Displaying the plot
plt.show()
```
*Explanation:*
- `df.plot(kind='scatter', x='X', y='Y', color='red', title='X vs Y')` generates a scatter plot to visualize the relationship between variables X and Y.

#### `DataFrame.plot.pie()`

**Explanation:**
The `DataFrame.plot.pie()` function creates a pie chart, which is useful for showing the proportions of a whole.

**Features:**
- **Pie Chart Elements:** Displays the proportion of each category as a slice of the pie.
- **Customization:** Allows customization of colors, labels, and percentages.

**Problem Solved:**
- Helps in visualizing the proportion of categories within a dataset.

**Parameters:**
- **y**: Column name for the data to plot.
- **labels**: Labels for the pie slices.
- **colors**: Colors for the pie slices.
- **autopct**: Format string to display the percentage value.

**Example Code:**
```python
import pandas as pd
import matplotlib.pyplot as plt

# Sample DataFrame with categorical data
data = {
    'Category': ['A', 'B', 'C', 'D'],
    'Values': [10, 20, 30, 40]
}
df = pd.DataFrame(data)

# Creating a pie chart
df.plot(kind='pie', y='Values', labels=df['Category'], autopct='%1.1f%%', title='Category Proportions')

# Displaying the plot
plt.show()
```
*Explanation:*
- `df.plot(kind='pie', y='Values', labels=df['Category'], autopct='%1.1f%%', title='Category Proportions')` creates a pie chart to show the proportions of categories.

