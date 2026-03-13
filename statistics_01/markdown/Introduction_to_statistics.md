# INTRODUCTION INTO STATISCTICS


Statistics helps us organize and understand data. It allows us to summarize large datasets and draw meaningful conclusions. By applying statistical methods, we can identify trends, test hypotheses, and make data-driven decisions.

## 1. Types of Statistics

### Descriptive Statistics

Descriptive statistics summarize and organize data. Common tools include:

- **Central Tendency:** Mean, Median, Mode — measures the “center” of data.
- **Measures of Dispersion:** Range, Variance, Standard Deviation — measure how spread out the data is.

### Inferential Statistics

Inferential statistics use a sample to make generalizations about a population. This includes probability, estimation, hypothesis testing, and predictive modeling.

## 2. Types of Data

### Quantitative (Numerical) Data

- **Discrete:** Countable values (e.g., number of students).
- **Continuous:** Measurable values (e.g., height, weight).

### Qualitative (Categorical) Data

- **Nominal:** Categories without order (e.g., blood type, gender).
- **Ordinal:** Ranked categories (e.g., satisfaction ratings: low, medium, high).



## Measures of Central Tendency

**Definition:**
Measures of central tendency are statistical values that describe the center or typical value of a dataset. They summarize data with a single number that represents the “middle” or most typical observation.

### Common Measures

- **Mean (Average)**
	- Formula:

		$$
			ext{Mean} = \frac{\sum_{i=1}^n x_i}{n}
		$$

	- Use: Best for quantitative data without extreme outliers.
	- Example: Data = [2, 4, 6, 8, 10] → Mean = 
  
  
	- $\dfrac{2+4+6+8+10}{5} = 6$.

- **Median**
	- Definition: The middle value when data is ordered. If there is an even number of values, take the average of the two middle values.
	- Use: Best when data has outliers or is skewed.
	- Example: Data = [1, 3, 7, 8, 20] → Median = 7.
	- For even $n$: if ordered values are $x_{(1)},\dots,x_{(n)}$, median = $\dfrac{x_{(n/2)} + x_{(n/2 + 1)}}{2}$.

- **Mode**
	- Definition: The most frequent value in the dataset.
	- Use: Useful for categorical or discrete data where the most common value matters.
	- Example: Data = [2, 4, 4, 6, 8] → Mode = 4.

**Key Idea:**

- **Mean:** sensitive to outliers.
- **Median:** resistant to outliers.
- **Mode:** shows the most common value.

These three measures give different views of the dataset's center; choose the one that best fits the data type and distribution.

## Measures of Dispersion

**Definition:**
Measures of dispersion tell us how spread out or varied the data is. They complement measures of central tendency because knowing the average alone doesn’t show variability.

### Common Measures

- **Range**
	- Formula:

		$$
			ext{Range} = \text{Maximum value} - \text{Minimum value}
		$$

	- Use: Simple to compute but very sensitive to outliers.
	- Example: Data = [3, 5, 7, 10] → Range = $10 - 3 = 7$.

- **Variance**
	- Formula (population):

		$$
		\sigma^2 = \frac{1}{n}\sum_{i=1}^n (x_i - \bar{x})^2
		$$

		Formula (sample):

		$$
		s^2 = \frac{1}{n-1}\sum_{i=1}^n (x_i - \bar{x})^2
		$$

	- Use: Measures the average squared deviation from the mean; useful for theoretical work and further calculations.
	- Example: Data = [2, 4, 6] → Mean $\bar{x}=4$ → Variance (population) = $\dfrac{(2-4)^2+(4-4)^2+(6-4)^2}{3} = \dfrac{4+0+4}{3} \approx 2.67$.

- **Standard Deviation (SD)**
	- Formula: $\text{SD} = \sqrt{\text{Variance}}$ (use $\sigma$ for population, $s$ for sample)
	- Use: Measures average deviation from the mean in the same units as the data.
	- Example: For variance $\approx 2.67$, SD $= \sqrt{2.67} \approx 1.63$.

- **Interquartile Range (IQR)**
	- Formula:

		$$
			ext{IQR} = Q_3 - Q_1
		$$

	- Use: Resistant to outliers; represents the spread of the middle 50% of the data and is commonly shown in boxplots.

**Key Idea:**

- High dispersion → data points are spread out.
- Low dispersion → data points are close to the mean.

Choose dispersion measures based on sensitivity to outliers and the needs of your analysis (e.g., use IQR for skewed data, SD/variance for parametric methods).
