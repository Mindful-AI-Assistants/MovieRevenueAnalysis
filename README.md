<br><br>

 <p align="center">
<img src="https://github.com/user-attachments/assets/44205022-1828-4be5-96ce-390a0ce9436c" />

<br><br>

#  <p align="center"> 🎬💰  Movie Companies Revenue Analysis: Statistical Insights and Release Strategies

Analyze movie companies' revenue, release strategies, and financial performance using statistical techniques for actionable insights. This project explores data on total revenue, number of releases, and lifetime gross to uncover patterns that can drive strategic decisions in the film industry.

## 📄 Project Description
This project focuses on a financial and strategic analysis of movie companies, examining key variables such as **total revenue**, **number of releases**, and **lifetime gross** over time. We employ descriptive and inferential statistical techniques to uncover valuable insights that can support strategic decision-making in the film industry.

## 🔍 Analysis Objectives
- **Explore and understand the data** to identify patterns and trends in the film industry.
- **Apply statistical techniques** to test hypotheses about the financial performance of companies.
- **Visualize the relationships among key variables** such as release count and revenue to gain insights.

## 📈 Techniques Used
The analysis uses several statistical methods and visualizations, including:
- **Descriptive Analysis**: Basic statistics (mean, median, mode, variance).
- **T-Tests**: Comparison of variable means with specific reference values.
- **Correlation Heatmap**: Visualization of numeric variable relationships to identify correlations.

## 📂 Project Structure

```bash
├── Movie companies.xlsx   # Data file used in the analysis
├── analysis.ipynb         # Full code in Jupyter Notebook
├── README.md              # Project documentation
```

## 🗂️ Dataset

👉🏻 Click to [access the dataset](https://github.com/Mindful-AI-Assistants/MovieRevenueAnalysis/blob/91121a46ec589808505cffe5eba221114625ae9b/dataset/Movie%20companies.xlsx).

The file `Movie companies.xlsx` includes the following variables:
- **Total**: Total cumulative revenue per company.
- **Releases**: Number of movie releases by the company.
- **Lifetime Gross**: Cumulative revenue over the lifetime of the releases.
   
## 🚀 Getting Started

### Installation and Setup 🚀

To set up this project locally, follow these steps:

### Prerequisites

Ensure you have Python 3.7 or above and the following packages installed:

- `pandas`
- `numpy`
- `scipy`
- `seaborn`
- `matplotlib`
- `openpyxl`

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/movie-revenue-analysis.git
   cd movie-revenue-analysis
   ```

2. **Install the required dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   *(Optional)*: Create a virtual environment to keep dependencies isolated:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Run the Jupyter Notebook** to explore the analysis:
   ```bash
   jupyter notebook analysis.ipynb
   ```

## 💻 Code

Here's the complete code, divided into sections for calculations, tests, and visualizations.

### 1. Importing Libraries and Loading Data
```python
# Import necessary libraries
import pandas as pd
import statistics as st
import scipy.stats as stats
import matplotlib.pyplot as plt
import seaborn as sns
```

####  Load data file and verify the file path

```python
try:
    df = pd.read_excel('Movie companies.xlsx')
except FileNotFoundError:
    print("File not found. Please check the file name and path.")
```
    
#### Display the data header to understand the structure

```python
df.head()
```

### 2. Descriptive Analysis

```python
# Perform descriptive analysis with statistical metrics for each numeric variable
df.describe()
```

### 3. Variance Calculations

```python
# Calculate variances (difference between max and min values)
# Helps to understand the range of values in revenue and releases
variance_total = df['Total'].max() - df['Total'].min()
variance_releases = df['Releases'].max() - df['Releases'].min()
variance_lifetime_gross = df['Lifetime Gross'].max() - df['Lifetime Gross'].min()
```
#### Display variances for analysis

```python
print("Variance - Total:", variance_total)
print("Variance - Releases:", variance_releases)
print("Variance - Lifetime Gross:", variance_lifetime_gross)
```

### 4. Mode and Median Calculations

```python
# Calculate modes (values that occur most frequently in each column)
# Useful for identifying common values in main variables
modes = pd.concat([df['Total'].mode(), df['Releases'].mode(), df['Lifetime Gross'].mode()], axis=1)
modes.columns = ['Mode_Total', 'Mode_Releases', 'Mode_Lifetime_Gross']
print("Variable Modes:\n", modes)
```
#### Calculate medians for central tendency in distributions

```python
median_total = int(df['Total'].median())
median_releases = int(df['Releases'].median())
median_lifetime_gross = int(df['Lifetime Gross'].median())
print("Median - Total:", median_total)
print("Median - Releases:", median_releases)
print("Median - Lifetime Gross:", median_lifetime_gross)
```

### 5. T-Tests

```python
# Apply t-tests to check if the variable means differ from a specific reference value
# Using reference values as per provided data

# T-test for 'Total' with a reference value of 2 billion
t_test_total = stats.ttest_1samp(df['Total'], 2_000_000_000)
print("T-Test for Total:", t_test_total)

# T-test for 'Releases' with a reference value of 22
t_test_releases = stats.ttest_1samp(df['Releases'], 22)
print("T-Test for Releases:", t_test_releases)

# T-test for 'Lifetime Gross' with a reference value of 250 million
t_test_lifetime_gross = stats.ttest_1samp(df['Lifetime Gross'], 250_000_000)
print("T-Test for Lifetime Gross:", t_test_lifetime_gross)
```


### 6. Correlation Heatmap
```python
# Creating the correlation heatmap to visualize relationships between numeric variables
# The heatmap helps identify strong or weak relationships between variables
plt.figure(figsize=(8, 6))
sns.heatmap(df.corr(numeric_only=True), annot=True, center=0, cmap="coolwarm")
plt.title('Correlation Heatmap of Variables')
plt.show()
```




#
 
##### <p align="center">Copyright 2024 Mindful-AI-Assistants. Code released under the  [MIT license.]( https://github.com/Mindful-AI-Assistants/.github/blob/ad6948fdec771e022d49cd96f99024fcc7f1106a/LICENSE)
