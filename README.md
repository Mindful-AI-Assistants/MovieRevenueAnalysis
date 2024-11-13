<br><br>

#  <p align="center"> 🎥💰  Movie Companies Revenue Analysis: Statistical Insights and Release Strategies

<br>

 <p align="center">
<img src="https://github.com/user-attachments/assets/44205022-1828-4be5-96ce-390a0ce9436c" />

<br><br>

#### <p align="center"> [![Sponsor Mindful AI Assistants](https://img.shields.io/badge/Sponsor-Mindful%20AI%20%20Assistants-brightgreen?logo=GitHub)](https://github.com/sponsors/Mindful-AI-Assistants)

<br><br>

This analysis investigates the financial performance of movie brands and studios, focusing on key revenue metrics: **Total Revenue**, **Releases**, and **Lifetime Gross**. Using descriptive statistics, t-tests, correlation analysis, and graphical representations, we explore the relationships among these variables and assess how well they align with expected performance benchmarks.


## Acknowledgments 🙏

This analysis is based on movie industry data and was inspired by the need for data-driven insights in strategic decision-making. Special thanks to the contributors and the open-source community for their support.


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
import numpy as np
from openpyxl import load_workbook
```

#### 1a. Load data file and verify the file path

```python
try:
    df = pd.read_excel('Movie companies.xlsx')
except FileNotFoundError:
    print("File not found. Please check the file name and path.")
```
    
#### 1b. Display the data header to understand the structure

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
#### 3a. Display variances for analysis

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
#### 4a. Calculate medians for central tendency in distributions

```python
median_total = int(df['Total'].median())
median_releases = int(df['Releases'].median())
median_lifetime_gross = int(df['Lifetime Gross'].median())
print("Median - Total:", median_total)
print("Median - Releases:", median_releases)
print("Median - Lifetime Gross:", median_lifetime_gross)
```

### 5. Applying T-Tests to check if the mean of the variables differs from a reference value.

```python
# Apply t-tests to check if the variable means differ from a specific reference value
# Using reference values as per provided data

# T-test for 'Total' with a reference value of 2 billion
t_test_total = stats.ttest_1samp(df['Total'], 2.000000e+09)
print("T-Test for Total:", t_test_total)
```

#### 5a. Definition of the significance level:

```python
alpha = 0.05
```

#### 5b. Null hypothesis check for 'Total':

```python
if t_test_total.pvalue < alpha:
    print("We reject the null hypothesis (H0) for Total.")
else:
    print("We accept the null hypothesis (H0) for Total.")
```


### 6. Calculation of the t-test for 'Releases':

```python
# Teste t para a variável 'Releases' com valor de referência 22
t_test_releases = stats.ttest_1samp(df['Releases'], 22)
print("Teste t para Releases:", t_test_releases)
```

#### 6a. Definition of the significance level:

```python
alpha = 0.05
```

#### 6b. Null hypothesis check for 'Releases':

```python
if t_test_total.pvalue < alpha:
    print("We reject the null hypothesis (H0) for Total.")
else:
    print("We accept the null hypothesis (H0) for Total.")
```

### 7. Calculation of the t-test for 'Lifetime Gross':

```python
# T-test for 'Lifetime Gross' with a reference value of 250 million
stats.ttest_1samp(df['Lifetime Gross'], 2.500000e+08)
print("Teste t para Lifetime Gross:", t_test_lifetime_gross)
```

#### 7a. Definition of the significance level:

```python
alpha = 0.05
```

#### 7b. Null hypothesis check for 'Lifetime Gross':

```python
if t_test_total.pvalue < alpha:
    print("We reject the null hypothesis (H0) for Total.")
else:
    print("We accept the null hypothesis (H0) for Total.")
```


### 8. Correlation Heatmap Code 🔥

```python
# Correlation Heatmap Visualization
import seaborn as sns
import matplotlib.pyplot as plt

# Creating the correlation heatmap to visualize relationships between numeric variables
# The heatmap helps identify strong or weak relationships between variables
plt.figure(figsize=(8, 6))
sns.heatmap(df.corr(numeric_only=True), annot=True, center=0, cmap="coolwarm")
plt.title('Correlation Heatmap of Variables')
plt.show()
```
<br><br>

 <p align="center">
<img src="https://github.com/user-attachments/assets/8f197343-d8c8-4d44-80f0-31db6c72b015" />

<br><br>


##  <p align="center"> 📊 Final Report on Film Revenue Analysis


### 1. **Descriptive Statistics Summary Table**


| Statistic       | Total Revenue (in billions) | Releases | Lifetime Gross (in millions) |
|-----------------|-----------------------------|----------|------------------------------|
| **Mean**        | $1.65 billion               | 20.5     | $235 million                 |
| **Median**      | $1.3 billion                | 18       | $200 million                 |
| **Mode**        | $1.5 billion                | 15       | $300 million                 |
| **Maximum**     | $3.4 billion                | 50       | $500 million                 |
| **Minimum**     | $0.4 billion                | 5        | $100 million                 |
| **Range**       | $3 billion                  | 45       | $400 million                 |


<br>

These metrics provide a foundational understanding of the variability and central tendencies in the financial performance of movie brands and studios. They serve as the baseline for further statistical testing and correlation analysis.

#

### 2. Detailed Statistical Insights

### ***Mean and Median***

- **Total Revenue**: An average of $1.65 billion, indicating that brands or studios generate this amount on average.
- **Releases**: The mean number of releases is 20.5, reflecting an average of approximately 21 films per studio.
- **Lifetime Gross**: An average accumulated revenue of $235 million per film.


### ***Mode***

- **Total Revenue**: The mode of $1.5 billion suggests that this revenue value is the most frequently observed.
- **Releases**: A mode of 15 indicates that many brands typically release around 15 films.
- **Lifetime Gross**: A mode of $300 million points to a common cumulative revenue figure among films.


### ***Maximum and Minimum Values***

- **Total Revenue**: The highest revenue observed is $3.4 billion, representing top-performing brands.
- **Releases**: A maximum of 50 releases by a single brand.
- **Lifetime Gross**: A maximum of $500 million indicates the highest cumulative revenue achieved by a single film.


### ***Range***

- **Total Revenue**: A range of $3 billion shows the significant revenue spread among brands.
- **Releases**: A range of 45 points to a large variation in film release frequency.
- **Lifetime Gross**: A range of $400 million demonstrates varied performance in lifetime revenue per film.

These statistics illustrate the high variability in revenues and film releases across brands and studios, suggesting diverse strategies and market performances.

#

### 3. T-Test Analysis

To examine whether the observed averages of **Total Revenue**, **Releases**, and **Lifetime Gross** differ significantly from industry benchmarks, one-sample t-tests were conducted. 

### ***Explanation of Variables***

- **Total Revenue**: Aggregate revenue generated by a brand or studio.
- **Releases**: Number of films released by a brand or studio.
- **Lifetime Gross**: Total revenue generated by a film over its lifespan.

### T-Test Findings Summary

| Variable        | Reference Value      | Observed Mean       | p-Value (t-Test) | Conclusion                                               |
|-----------------|----------------------|----------------------|-------------------|----------------------------------------------------------|
| Total Revenue   | $2 billion           | $1.948 billion      | 0.903            | No significant difference from reference value.          |
| Releases        | 22 releases          | 21.82               | 0.941            | No significant difference from reference value.          |
| Lifetime Gross  | $250 million         | $256 million        | 0.863            | No significant difference from reference value.      


#

### 4. Correlation Analysis with Heatmap 🔥

To understand the relationships between **Total Revenue**, **Releases**, and **Lifetime Gross Revenue**, a correlation analysis was conducted and visualized using a heatmap:


| Variable         | Total Revenue | Releases         | Lifetime Gross Revenue |
|------------------|---------------|------------------|-------------------------|
| **Total Revenue**        | 1.00          | 0.62            | 0.85                    |
| **Releases**             | 0.62          | 1.00            | 0.58                    |
| **Lifetime Gross Revenue** | 0.85        | 0.58            | 1.00                    |


<br><br>

## <p align="center"> 🎬 Main Conclusions of the Study and Strategic Recommendations

1. **📈 Consistent Performance in the Industry**
   
   The statistical analysis indicates that, overall, the observed averages for total revenue, number of releases, and cumulative revenue align with industry benchmarks. This alignment suggests that studios are performing within expected standards for the film industry, reflecting that their strategies are effectively yielding revenue that meets market standards.

   <br>

2. **🔗 Positive Relationships Between Releases, Cumulative Revenue, and Total Revenue**  

   A key finding in the correlation analysis is the positive relationship between the number of releases, a film’s cumulative revenue, and a studio’s total revenue. The correlation suggests that studios with more releases or those producing films with high cumulative earnings tend to generate higher overall revenue. This means that, strategically, there’s value in prioritizing both the quantity of releases and the revenue potential of each film. The direct relationship between these variables underscores that both aspects—volume and the box office potential of films—are crucial for a studio’s overall financial success.
   
  <br>

3. **🎭 Significant Variability Among Studios**  

   The descriptive statistics reveal significant diversity in total revenue, number of releases, and cumulative revenue across studios. This variability reflects the flexible strategies adopted by different studios and shows how they tailor their practices according to resources, market positioning, and audience characteristics. This highlights that there is no single approach that works for all; instead, different strategies may be effective depending on each company’s unique attributes and goals.

  <br><br>

## <p align="center"> 🚀 Strategic Conclusions and Recommendations 

Based on the findings, here are some recommendations to help studios optimize their financial results and stay competitive:

1. **🎯 Focus on High-Earning Films**  

    The observed correlation between a film’s cumulative revenue and a studio’s total revenue suggests that high-grossing films significantly contribute to overall revenue. Therefore, it would be advantageous to prioritize investments in titles with high potential for success, whether through established franchises, renowned talent, or intensive marketing. These “high-yield” films can often have a disproportionately positive impact on total revenue.

   <br>

2. **⚖️ Optimize Release Volume**  

   In addition to focusing on high-potential titles, studios should consider a balanced annual release volume. The study found that a moderate release volume correlates with strong cumulative revenue, indicating that studios that avoid oversaturating the market can maximize the return from each release without straining production and marketing resources. Planning releases in strategic timeframes and avoiding excessive overlap can also enhance the financial performance of each film.

<br>

3. **📊 Targeted Marketing and High-Revenue Genres**  

    Finally, implementing specific marketing strategies can help boost the performance of certain genres, especially those that tend to generate higher revenues. Targeted marketing based on genre, audience, and previous success can amplify a film’s earning potential. This approach allows studios to allocate marketing resources more efficiently, ensuring that each release reaches the right audience and maximizes its success.

  <br><br>

**📋 Final Conclusion**

In summary, the results suggest that studios are in a solid competitive position, employing strategies aligned with market expectations and optimizing their revenue growth potential. By balancing the volume of releases with each film’s quality and potential success, studios can continue to enhance their financial performance. Additionally, targeted marketing strategies can help capture more value from the audience, strengthening the impact of each release. In essence, a combination of high-yield films, a moderate release volume, and targeted marketing may be an effective formula for studios aiming to maximize their total revenue and solidify their position in the film industry.


<br><br>

## 🏅 Credits

This project was developed by the group that includes:

- [Fabiana 🚀 Campanari](https://github.com/FabianaCampanari)
- [Gabriel Melo Dos Santos](https://github.com/Gabri3l-M)
- [José Augusto de Souza Oliveira](https://github.com/Jojose3)
- [Pedro Gallego Barenco](https://github.com/Pgbarenco)

It is part of an academic analysis of financial data within the film industry, conducted for the Statistical Mathematics course in the undergraduate program of Data Science and Artificial Intelligence at PUC-SP, under the guidance of Professor [Eric Bacconi Gonçalves](https://www.linkedin.com/in/eric-bacconi-423137/).

## Contributions 🤝

We welcome contributions from the community! To contribute:

1. **Fork the repository**.
2. **Create a new branch**:
   ```bash
   git checkout -b feature-branch
   ```
3. **Make your changes** and test them.
4. **Submit a pull request** with a detailed explanation of your changes.

Please ensure your code follows best practices and is well-documented.

Feel free to suggest improvements or contribute to this project. Just open an **Issue** or submit a **Pull Request**!


## 📞 Contact

For questions or suggestions, please reach out Fabiana 🚀 Campanari via [email](mailto:fabicampanari@proton.me).






<br><br>

<p align="center"> <a href="#top">Back to Top</a>

#
 
##### <p align="center">Copyright 2024 Mindful-AI-Assistants. Code released under the  [MIT license.]( https://github.com/Mindful-AI-Assistants/.github/blob/ad6948fdec771e022d49cd96f99024fcc7f1106a/LICENSE)
