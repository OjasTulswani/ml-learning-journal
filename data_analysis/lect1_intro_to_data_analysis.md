# Data Analysis Process

## What is Data Analysis?

Data Analysis is the process of **turning raw data into insights** by:

- Asking the right questions
- Cleaning and transforming data
- Exploring patterns and relationships
- Drawing meaningful conclusions

---

## The Data Analysis Workflow

```
1. Understand the Problem
2. Ask Analytical Questions
3. Data Wrangling (Cleaning & Preparation)
4. Exploratory Data Analysis (EDA)
5. Insights & Conclusions
6. (Optional) Feature Engineering for ML
```

---

## Understanding the Problem

Before touching the data, understand:

### Key Questions

- What is the **goal**?
- Is this:

  - Classification?
  - Regression?
  - Clustering?
  - Descriptive analysis?

- What does **success** look like?

### Example

> “We want to understand what factors affect house prices.”

---

## Asking the Right Questions (Most Important Step)

### Types of Questions

#### Descriptive Questions

- What is the average value?
- How is data distributed?
- How many missing values exist?

#### Diagnostic Questions

- Why did this trend happen?
- Why are some values extreme?

#### Relationship-Based Questions

- Does X affect Y?
- Are two variables correlated?

#### Predictive Questions (ML-oriented)

- Which features are most important?
- Can we predict Y using X?

### Example Questions

- Does income affect spending score?
- Are higher education levels linked to higher salaries?
- Do outliers affect the mean significantly?

---

## Data Wrangling (Data Cleaning & Preparation)

> **80% of real-world data analysis happens here**

### Data Wrangling Includes:

### 3.1 Inspecting the Data

```python
df.head()
df.tail()
df.shape
df.info()
df.describe()
```

Look for:

- Data types
- Missing values
- Strange values
- Incorrect formats

---

### 3.2 Handling Missing Values

#### Identify

```python
df.isnull().sum()
```

#### Strategies

| Scenario         | Method        |
| ---------------- | ------------- |
| Numerical        | Mean / Median |
| Categorical      | Mode          |
| Too many missing | Drop column   |
| Small dataset    | Drop rows     |

```python
df['age'].fillna(df['age'].median(), inplace=True)
```

---

### 3.3 Handling Duplicates

```python
df.duplicated().sum()
df.drop_duplicates(inplace=True)
```

---

### 3.4 Correcting Data Types

```python
df['date'] = pd.to_datetime(df['date'])
df['category'] = df['category'].astype('category')
```

---

### 3.5 Handling Outliers

#### Detect (IQR Method)

```python
Q1 = df['salary'].quantile(0.25)
Q3 = df['salary'].quantile(0.75)
IQR = Q3 - Q1
```

#### Options

- Remove
- Cap (winsorize)
- Keep (if meaningful)

**Never remove outliers blindly**

---

### 3.6 Feature Engineering (Basic)

- Create new columns
- Extract info from existing columns

```python
df['price_per_sqft'] = df['price'] / df['area']
```

---

## Exploratory Data Analysis (EDA)

EDA helps **understand patterns, trends, and relationships**.

---

### 4.1 Univariate Analysis (One Variable)

#### Numerical

- Mean, Median, Std
- Histogram
- Boxplot

```python
sns.histplot(df['age'], kde=True)
sns.boxplot(x=df['salary'])
```

#### Categorical

- Value counts
- Bar plot

```python
df['gender'].value_counts()
sns.countplot(x='gender', data=df)
```

---

### 4.2 Bivariate Analysis (Two Variables)

#### Numerical vs Numerical

- Scatter plot
- Correlation

```python
sns.scatterplot(x='age', y='salary', data=df)
df[['age','salary']].corr()
```

#### Categorical vs Numerical

- Boxplot
- Violin plot

```python
sns.boxplot(x='gender', y='salary', data=df)
```

#### Categorical vs Categorical

- Countplot
- Crosstab

```python
pd.crosstab(df['gender'], df['purchased'])
```

---

### 4.3 Multivariate Analysis

- Pairplot
- Heatmap

```python
sns.pairplot(df)
sns.heatmap(df.corr(), annot=True)
```

---

## Statistical Thinking During EDA

Use statistics to **support observations**.

### Key Concepts in Practice

- Mean vs Median → skewness
- Variance & Std → spread
- Covariance & Correlation → relationships
- PDF/CDF → probability behavior

### Example Insight

> “Since mean > median, the data is right-skewed.”

---

## Drawing Insights & Conclusions

### How to Write Conclusions

- Start with the question
- State the observation
- Support with evidence
- Mention limitations

### Example Conclusion

> “Income and spending score show a moderate positive correlation (0.62), suggesting higher-income customers tend to spend more. However, some high-income customers spend less, indicating other behavioral factors.”

---

## Common Mistakes to Avoid

❌ Jumping to ML without analysis
❌ Removing outliers without reasoning
❌ Over-plotting without insight
❌ Confusing correlation with causation
❌ Ignoring missing data patterns

---

## How This Connects to Machine Learning

| Data Analysis   | ML                   |
| --------------- | -------------------- |
| Understand data | Choose model         |
| Clean data      | Better accuracy      |
| EDA             | Feature selection    |
| Insights        | Model interpretation |
