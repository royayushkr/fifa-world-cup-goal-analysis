# FIFA World Cup: Statistical Analysis of Goal Scoring Trends

## 📌 Project Overview
This project investigates historical soccer data to determine if there is a statistically significant difference in the number of goals scored in Women's international matches compared to Men's. Focusing specifically on **FIFA World Cup** matches played after **January 1, 2002**, this analysis employs non-parametric hypothesis testing to validate the intuition that women's matches feature higher aggregate scores.

## 🚀 Key Objectives
* **Data Integration:** Combine and standardize results from separate Men's and Women's international football datasets.
* **Exploratory Data Analysis:** Analyze the distribution of goals scored (normality checks) to select appropriate statistical tests.
* **Hypothesis Testing:** Perform a **Wilcoxon-Mann-Whitney** test to determine statistical significance.

## 🧪 Hypothesis Formulation
To answer the question *"Are more goals scored in women's international soccer matches than men's?"*, the following hypotheses were established:

* **Null Hypothesis ($H_0$):** The mean number of goals scored in women's international soccer matches is the same as men's.
* **Alternative Hypothesis ($H_A$):** The mean number of goals scored in women's international soccer matches is **greater** than men's.

## 🛠️ Technical Stack
* **Language:** Python 3.x
* **Libraries:**
    * **Pandas:** Data ingestion, datetime conversion, and subsetting.
    * **Matplotlib:** Visualizing distributions (Histograms).
    * **SciPy (Stats):** Performing the Mann-Whitney U test.

## 📊 Methodology & Insights

### 1. Data Processing
* The analysis filtered data to include only official **FIFA World Cup** matches (excluding qualifiers) post-2002 to ensure a modern and comparable standard of play.
* A new feature, `goals_scored`, was engineered by summing home and away scores for every match.

### 2. Normality Check
* Histograms were generated for both groups.
* **Observation:** The goal count data was **not normally distributed** (right-skewed). Consequently, a non-parametric test (Wilcoxon-Mann-Whitney) was selected over a standard t-test.

### 3. Statistical Testing
A right-tailed Mann-Whitney U test was conducted with a significance level ($\alpha$) of **0.01**.

## 💻 Code Highlight: Statistical Test
The project utilizes `scipy.stats` to perform the hypothesis test efficiently.

```python
# Performing right-tailed Wilcoxon-Mann-Whitney test
results_scipy = mannwhitneyu(
    x=women_subset['goals_scored'],
    y=men_subset['goals_scored'],
    alternative='greater'
)

# P-value extraction
p_val = results_scipy.pvalue
print(f"P-value: {p_val}")
