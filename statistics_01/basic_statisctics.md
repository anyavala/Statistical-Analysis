# STATISTICS WITH PYTHON FOR BEGINNERS

Implementation of basic statistical analysis is quite straightforward in Python. There are several important libraries with built-in methods to help achieve this. The most efficient ones are the NumPy and SciPy libraries. I’ll walk you through a complete, step-by-step example.

First, install the required libraries in your environment:
```bash
pip install numpy scipy 
```

### Suppose we have the data as follows:
```bash
# Sample data
data = [2, 4, 6, 8, 10, 4, 7, 3, 5]
```

## 1. Measures of Central Tendency
### Using Pure Python
- Mean:
```bash
mean = sum(data) / len(data)
```
Output:
```bash
5.444444444444445
```

- Median:
Sort the data then check whether the number of data is even or odd. 

```bash
data_sorted = sorted(data)
n = len(data)
if n % 2 == 0:
    median = (data_sorted[n//2 - 1] + data_sorted[n//2]) / 2
else:
    median = data_sorted[n//2]
```

- Mode: `Counter(data)` creates a dictionary-like object where keys are the unique values and values are their frequencies. `data_count.items()` gives all (value, frequency) pairs. Print all the result at the end. 

```bash
from collections import Counter
data_count = Counter(data)
mode = [k for k, v in data_count.items() if v == max(data_count.values())]

print("Mean:", mean)
print("Median:", median)
print("Mode:", mode)
```

### Using NumPy and SciPy
Although some basic statistics can be implemented using pure Python, the more complicated the code gets, the harder it becomes to do it that way. Therefore, it is much more efficient and convenient to use libraries with built-in methods, such as NumPy and SciPy. Here are some exmaples:

```bash
import numpy as np
from scipy import stats

mean_np = np.mean(data)
median_np = np.median(data)
mode_np = stats.mode(data).mode[0]

print("Mean (NumPy):", mean_np)
print("Median (NumPy):", median_np)
print("Mode (SciPy):", mode_np)
```

## 2. Measures of Dispersion
### Using Pure Python

- Range : 
  
```bash
range_data = max(data) - min(data)
```

- Calculation of Variance :
```bash
variance_population = sum((x - mean)**2 for x in data) / len(data)
variance_sample = sum((x - mean)**2 for x in data) / (len(data)-1)
```

- Calculation of Standard Devation (std) and output of all together:
```bash
std_population = variance_population**0.5
std_sample = variance_sample**0.5

print("Range:", range_data)
print("Population Variance:", variance_population)
print("Sample Variance:", variance_sample)
print("Population SD:", std_population)
print("Sample SD:", std_sample)
```

### Using NumPy
Let's implement above codes using NumPy library :
``` bash
variance_np_population = np.var(data)
variance_np_sample = np.var(data, ddof=1)
std_np_population = np.std(data)
std_np_sample = np.std(data, ddof=1)

print("Population Variance (NumPy):", variance_np_population)
print("Sample Variance (NumPy):", variance_np_sample)
print("Population SD (NumPy):", std_np_population)
print("Sample SD (NumPy):", std_np_sample)
```

### Interquartile Range (IQR) Using NumPy
The **Interquartile Range (IQR)** measures the spread of the **middle 50% of the data**.  

It is calculated as the difference between the third quartile (Q3) and the first quartile (Q1):

$$
\text{IQR} = Q_3 - Q_1
$$

- **Q1 (25th percentile):** The value below which 25% of the data fall.  
- **Q3 (75th percentile):** The value below which 75% of the data fall.  

The IQR is **resistant to outliers**, making it a better measure of spread for skewed data compared to range or standard deviation.  

It is commonly visualized in **boxplots**, where the box spans from Q1 to Q3.
```bash
Q1 = np.percentile(data, 25)
Q3 = np.percentile(data, 75)
IQR = Q3 - Q1

print("Q1:", Q1)
print("Q3:", Q3)
print("Interquartile Range (IQR):", IQR)
```

After gaining a basic understanding of these concepts, let's apply the same ideas to real-world data using pandas. Seaborn is a Python library for data visualisation that includes several built-in example datasets, such as Titanic, Iris, Tips, and Penguins. In this example, we will focus on the Iris dataset, which contains measurements of various iris flower species.

- Load the dataset of Iris :

```bash
import seaborn as sns

# Load the Iris dataset
iris = sns.load_dataset('iris')
print(iris.head())
```
Since the dataset contains both strings and numbers, we will create a new DataFrame with only the numerical columns to perform calculations. In our case, the numerical columns are `sepal_length, sepal_width, petal_length and petal_width`.

```bash
# Select numeric columns only
numeric_cols = ['sepal_length', 'sepal_width', 'petal_length', 'petal_width']
iris_numeric = iris[numeric_cols]
```

Calculating basic statistical measures on a DataFrame is simple:

```bash
# Central Tendency; mean, median, mode
mean_df = iris_numeric.mean()
median_df = iris_numeric.median()
mode_df = iris_numeric.mode().iloc[0]  
print("Mean (DataFrame):\n", mean_df)
print("Median (DataFrame):\n", median_df)
print("Mode (DataFrame):\n", mode_df)
```

```bash
# Dispersion
range_df = iris_numeric.max() - iris_numeric.min()
variance_df = iris_numeric.var()      
std_df = iris_numeric.std()          
iqr_df = iris_numeric.quantile(0.75) - iris_numeric.quantile(0.25)
print("Range (DataFrame):\n", range_df)
print("Variance (DataFrame):\n", variance_df)
print("Standard Deviation (DataFrame):\n", std_df)
print("Interquartile Range (DataFrame):\n", iqr_df)
```
Combine all statistics into a single DataFrame:

```bash
import pandas as pd
iris_stats_df = pd.DataFrame({
    'Mean': mean_df,
    'Median': median_df,
    'Mode': mode_df,
    'Range': range_df,
    'Variance': variance_df,
    'Standard Deviation': std_df,
    'IQR': iqr_df
})

# Display the result
print(iris_stats_df)
```
Lastly, I want to touch on the difference between population (where variance is divided by N) and sample (divided by n-1 ).


#### Population :
- A population is the entire set of items or individuals that you want to study.
- Example: All 150 iris flowers in the Iris dataset, or all passengers on the Titanic.
Parameters like mean (μ), variance (σ²), and standard deviation (σ) describe the true characteristics of the population.
- Usually large and sometimes impossible or expensive to measure fully.
- We divide by N because we know the true population mean (μ), so the squared deviations we calculate represent the true average spread. There's no estimation; we have the complete data.

#### Sample:
- A sample is a subset of the population that is actually measured or observed.
- Example: 50 randomly selected iris flowers, or 200 Titanic passengers.
- Statistics like sample mean (x̄), sample variance (s²), and sample standard deviation (s) are estimates of the population parameters.
- Easier and cheaper to collect, but may contain sampling error (difference from true population values).
- We divide by n−1  instead of n because the sample mean (x̄) is only an estimate of the population mean μ. Dividing by n−1 corrects for bias in estimating the population variance. This is called Bessel's correction.

✅ Tip: Most statistical analyses in practice are done on samples, and results are generalised to the population using inferential statistics.