# HYPOTHESIS TESTING 

## BASIC OF HYPOTHESIS TESTING
### NULL HYPOTHESIS (H₀)
Null hypothesis claims that there is no effect, no difference or no relationship. Example:
- Drug has no effect on patient. 
- The average exam score is 70.
- There is no difference between two teaching methods.
- We assume H₀ is true until the data provides strong evidence against it.

### Alternative Hypothesis (H₁ / Hₐ)
It represents real effect or difference. For example:
- The new drug improves recovery.
- The average exam score is not 70.
- Teaching method A is different from method B.
- Try to collect evidence against H₀
- If evidence is strong → reject H₀ and support H₁.

Why do we need a null or alternative hypothesis? They are starting assumptions that help us identify possibilities and determine which is supported by the results.

### Test Statistic


A test statistic is a number calculated from your sample data that helps decide whether to reject $H_0$.
It measures how far your sample result is from what we expect under the null hypothesis.

#### Common Test Statistics

- **z-statistic** (Z-test)
- **t-statistic** (t-test)
- **χ² statistic** (Chi-square test)
- **F-statistic** (ANOVA)

#### General Formula

$$\text{Test Statistic} = \frac{\text{Observed Result} - \text{Expected Result}}{\text{Standard Error}}$$

The test statistic quantifies the difference between what we observed in our sample and what we would expect if the null hypothesis were true, normalized by the standard error. A larger absolute value of the test statistic indicates stronger evidence against the null hypothesis.

#### Sampling Distribution

The sampling distribution describes how a statistic (like the sample mean) behaves if we repeatedly take samples from the population.

- It tells us what results are normal and what results are rare under $H_0$.
- It provides the foundation for making statistical inferences about the population. Example: 

If $H_0$ says the mean = 70, the sampling distribution shows how sample means would vary around 70 due to randomness.


### One-Tailed vs Two-Tailed Tests

- One-tailed test:  Used when we care about direction. Right-tailed: H₁: μ > 70 Left-tailed: H₁: μ < 70
- Two-tailed test : Used when we care about any difference (higher or lower). Hypotheses: H₀: μ = 70 H₁: μ ≠ 70. We check both extremes of the distribution. Is the average score different from 70?

### p-Values and Significance
p-value: Probability of observing data at least as extreme as your sample, assuming H₀ is true.
Interpreting p-values:
- p ≤ α → reject H₀ (evidence supports H₁)
- p > α → fail to reject H₀ (not enough evidence)


# t-test
A t-test is a statistical method used to determine whether there is a significant difference between means of groups or between a sample and a population when the population standard deviation is unknown.

* It uses the Student’s t-distribution to calculate how unusual your observed difference is under the null hypothesis.


## Types of t-tests
1. **One-sample t-test**
- Compares the mean of a single sample to a known population mean.
- Example: Is the average exam score of students different from 70?
2. **Independent two-sample t-test (unpaired)**
- Compares the means of two independent groups.
- Example: Do men and women have different average heights?
3. **Paired t-test (dependent samples)**
- Compares means from the same group at two time points or matched pairs.
- Example: Test scores before vs after a training program.

## How It Works 

### 1. State Hypotheses

- **$H_0$**: No difference in means
- **$H_1$**: Means are different (or one is greater)

### 2. Calculate t-statistic

$$t = \frac{\text{Sample Mean Difference}}{\text{Standard Error of Difference}}$$

### 3. Compare with t-distribution

- Look up critical $t$-value using degrees of freedom
- Or compute $p$-value

### 4. Decision

- **$p \leq \alpha$** → reject $H_0$ → difference is statistically significant
- **$p > \alpha$** → fail to reject $H_0$ → difference not significant

### Summary

The decision rule is straightforward: if the $p$-value is less than or equal to your significance level (usually 0.05), you have sufficient evidence to reject the null hypothesis and conclude that the difference is statistically significant.


# z-test
A Z-test is a statistical test used to determine whether there is a significant difference between sample and population means, or between two sample means, when the population standard deviation is known (or the sample size is large, usually n > 30).


## Types of Z-tests
1. One-sample Z-test
- Compares the mean of a single sample to a known population mean.
- Example: Is the average height of students different from 170 cm?
2. Two-sample Z-test (independent samples)
- Compares means of two independent groups.
- Example: Compare average test scores between students from two schools.
3. Proportion Z-test
- Compares sample proportion to population proportion or between two sample proportions.
- Example: Does 60% of people like a product, compared to 50% expected?

## How It Works (Steps)
Great progress — this is clear and complete! I’ve converted your procedure into clean markdown with formulas and decision rules.

1. State Hypotheses
H₀: No difference
H₁: Difference exists (one-sided or two-sided)
2. Compute Z-statistic (one-sample mean)
For a one-sample mean test:

$$
Z = \frac{\bar{x} - \mu}{\sigma / \sqrt{n}}
$$

Where:

- $\bar{x}$ = sample mean
- $(\mu)$ = population mean under (H_0)
- $(\sigma)$ = population standard deviation
- $(n)$ = sample size
3. Compare with Z-distribution
Look up critical z-value for significance level $\alpha$
Or compute p-value directly
4. Decision
- If $p \le \alpha$: reject $H_0$ → significant difference
- If $p > \alpha$: fail to reject $H_0$ → not significant

# ANOVA
ANOVA (Analysis of Variance) is a statistical method used to determine whether there are significant differences between the means of three or more groups.
Instead of doing multiple t-tests (which increases the chance of errors), ANOVA tests all groups simultaneously.

### Types of ANOVA

#### 1. One-way ANOVA
- Involves **one factor** (independent variable) with multiple levels (groups)  
- **Example:** Compare test scores among students from 3 different teaching methods

#### 2. Two-way ANOVA
- Involves **two factors**, can also study **interaction effects**  
- **Example:** Study the effect of teaching method (factor 1) and gender (factor 2) on test scores

#### 3. Repeated Measures ANOVA
- Used when the **same subjects** are measured under different conditions or time points  


### Steps in ANOVA

1. **State Hypotheses**  
   - **Null Hypothesis (H₀):** All group means are equal  
   - **Alternative Hypothesis (H₁):** At least one group mean is different  

2. **Calculate F-statistic**  

$F = \frac{\text{Mean Square Between Groups (MSB)}}{\text{Mean Square Within Groups (MSE)}}$

1. **Compare with critical F-value** (from F-distribution) or compute p-value  

2. **Decision Rule**  
   - If \(p \leq \alpha\) → reject H₀ → at least one group is significantly different  
   - If \(p > \alpha\) → fail to reject H₀ → no significant difference  

3. **Post-hoc tests** (if H₀ rejected)  
   - Identify **which groups differ**  
   - **Examples:** Tukey’s HSD, Bonferroni

## One-Way ANOVA: Bacteria Growth under 3 Antibiotics

## 1. Hypotheses

- **Null Hypothesis (H₀):** μA = μB = μC  
- **Alternative Hypothesis (Hₐ):** At least one μ differs  


## 2. Group Means and Grand Mean

**Antibiotic A:** [10, 11, 12] →  
$
\bar{X}_A = \frac{10 + 11 + 12}{3} = 11
$

**Antibiotic B:** [7, 8, 9] →  
$
\bar{X}_B = \frac{7 + 8 + 9}{3} = 8
$

**Antibiotic C:** [4, 5, 6] →  
$
\bar{X}_C = \frac{4 + 5 + 6}{3} = 5
$

**Grand Mean:**  
$
\bar{X}_{grand} = \frac{10+11+12+7+8+9+4+5+6}{9} = 8
$


## 3. Sum of Squares (SS)

**Between Groups (SSB):**  
$SSB = \sum n_i (\bar{X}_i - \bar{X}_{grand})^2$ 

$SSB = 3(11-8)^2 + 3(8-8)^2 + 3(5-8)^2 = 54$

**Within Groups / Error (SSE):**  
$
SSE = \sum (x_{ij} - \bar{X}_i)^2
$ 
- Antibiotic A: 1 + 0 + 1 = 2  
- Antibiotic B: 1 + 0 + 1 = 2  
- Antibiotic C: 1 + 0 + 1 = 2  


SSE = 2 + 2 + 2 = 6


**Total Sum of Squares (SST):**  

SST = SSB + SSE = 60




## 4. Degrees of Freedom (df)

| Source       | df       |
|-------------|----------|
| Between     | k − 1 = 2 |
| Within      | N − k = 6 |
| Total       | N − 1 = 8 |



## 5. Mean Squares (MS)

$MSB = \frac{SSB}{df_{between}} = 27$

$MSE = \frac{SSE}{df_{within}} = 1$



## 6. F-Statistic

$F = \frac{MSB}{MSE} = 27$



## 7. P-Value and Conclusion

- **Critical F (α = 0.05, df1=2, df2=6):** 5.14  
- **Decision:** F > Fcritical → 27 > 5.14  
- **Conclusion:** Reject H₀. There is a statistically significant difference in mean plant growth among the fertilizers.