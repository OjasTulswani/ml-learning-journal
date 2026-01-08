# Exploratory Data Analysis (EDA)

## Short Definition

**Exploratory Data Analysis (EDA)** is the process of uncovering the inherent characteristics of a dataset using **statistical** and **visualization** techniques.

---

## Core Components of EDA

Exploratory Data Analysis typically consists of several stages that help data scientists understand and explore a dataset. While the exact steps may vary depending on the problem and data, EDA commonly includes:

1. Data Collection
2. Data Cleaning and Preprocessing
3. Descriptive Statistics
4. Univariate Analysis
5. Bivariate Analysis
6. Multivariate Analysis
7. Feature Engineering
8. Visualization

---

## EDA Level 0 — Initial Understanding

**Goal:** Perform basic checks to get a rough idea of what the dataset looks like.

### Typical Checks

* Column names
* Data types
* Null count per column
* Percentage of null values
* Distinct values count
* Percentage of distinct values
* Non-null count
* Top / most frequent values
* Summary statistics:

  * Mean
  * Median
  * Standard deviation
  * Min / Max
  * 25th percentile (Q1)
  * 75th percentile (Q3)
* DataFrame shape (rows × columns)
* Memory usage

This level focuses on **understanding structure and quality**, not transformation.

---

## EDA Level 1 — Data Preparation & Transformation

**Goal:** Use insights from Level 0 to prepare the dataset for deeper analysis.

### Key Steps

1. **Standardize column names**

   * Convert to lowercase
   * Replace spaces with underscores (`_`)

2. **Handle missing values**

   * Fill null / NaN values using domain-appropriate logic

3. **Correct data types**

   * Convert columns to more suitable types
   * Encode categorical variables using:

     * `get_dummies`
     * mapping techniques

4. **Data validation**

   * Ensure consistency, correctness, and logical integrity

5. **Mapping / Binning**

   * Group or bin categorical features where appropriate

---

## Handling Missing Values

Deciding how to fill missing values is one of the **most critical and time-consuming parts** of EDA.

* Missing values should only be filled when:

  * There is sufficient **domain knowledge**
  * The **data distribution** is well understood
* Incorrect imputation can significantly affect model performance

### Common Techniques

* Use **boxplots** to:

  * Identify outliers
  * Understand relationships between variables
* Analyze patterns in missingness rather than blindly filling values

---

## Data Validation

When dealing with unclean or duplicated data:

* If duplicates differ by only one or two columns:

  * Use ranking methods to:

    * Keep the row with the **least null values**
    * Keep the **most recent** record
    * Or **merge records** to preserve information

### Outcome of EDA Level 1

By the end of Level 1, you should have:

* A **clear reference table** documenting:

  * How null values were filled
  * Updated column data types
  * Feature classification:

    * Numerical
    * Categorical
    * Identifier

This documentation simplifies downstream modeling and feature importance analysis.

---

## Data Profiling

**Data profiling** is often the first practical step in EDA.

### Purpose

To collect high-level information about the dataset, including:

* Number of rows and columns
* Data types
* Value ranges
* Missing values
* Outliers
* Duplicates
* Inconsistencies

### Common Tools & Techniques

* Descriptive statistics
* Frequency tables
* Histograms
* Box plots
* Scatter plots
* Correlation matrices

> **Key Insight:**
> Data rarely comes perfectly clean or consistent. Identifying issues early can save significant time later.

**Example:**
In one project, data profiling revealed inconsistent date formats across multiple sources. Fixing this early prevented major downstream issues, highlighting the importance of this step.

---

## Data Cleaning

Data cleaning ensures the dataset is accurate, consistent, and usable.

### Standard Data Cleaning Steps

1. Identify and properly handle missing data
2. Remove duplicate records to ensure data integrity
3. Detect and address outliers that may skew analysis
4. Standardize formats and fix inconsistencies
5. Validate data against predefined rules and constraints
6. Transform variables when required for analysis
7. Resolve structural issues or anomalies
8. Document the entire cleaning process for transparency and reproducibility

---

## EDA Level 2 — Understanding the Transformed Data

### Recap

* **EDA Level 0:** Explored the raw dataset to understand structure and basic characteristics.
* **EDA Level 1:** Cleaned, validated, and transformed the data based on insights from Level 0.

**EDA Level 2** focuses on **understanding the transformed dataset** and evaluating how useful each feature is for analysis or modeling.

At this stage, the dataset should be:

* Clean
* Properly typed
* Free of major inconsistencies
* Ready for statistical analysis and modeling

---

## Key Tools and Techniques Used in EDA Level 2

### 1. Correlation Analysis

**Purpose:**
To measure the strength and direction of relationships between numerical variables.

**Common Methods:**

* Pearson correlation (linear relationships)
* Spearman correlation (monotonic relationships)
* Kendall correlation (rank-based)

**Key Insights:**

* Identify highly correlated features
* Detect multicollinearity
* Understand linear dependencies

**Typical Outputs:**

* Correlation matrices
* Heatmaps

---

### 2. Information Value (IV) / Weight of Evidence (WOE)

**Purpose:**
To evaluate the predictive power of features, especially in **classification problems** (commonly used in credit risk modeling).

**Key Concepts:**

* **WOE:** Measures how well a category or bin separates classes
* **IV:** Aggregates WOE to assess overall feature importance

**IV Interpretation (Rule of Thumb):**

* `< 0.02` → Not predictive
* `0.02 – 0.1` → Weak
* `0.1 – 0.3` → Medium
* `> 0.3` → Strong

**Use Cases:**

* Feature selection
* Binning validation
* Detecting data leakage

---

### 3. Feature Importance from Models

**Purpose:**
To understand which features contribute most to model predictions.

**Common Approaches:**

* Tree-based model feature importance (e.g., Random Forest, XGBoost)
* Coefficients from linear or logistic regression
* Permutation importance
* SHAP values (advanced)

**Key Insights:**

* Rank features by influence
* Identify redundant or noisy features
* Validate domain assumptions

---

### 4. Statistical Tests

**Purpose:**
To formally test hypotheses and validate relationships in the data.

**Common Tests:**

* **Numerical vs Numerical:**

  * Pearson / Spearman correlation tests
* **Categorical vs Categorical:**

  * Chi-square test
* **Numerical vs Categorical:**

  * t-test
  * ANOVA
  * Mann–Whitney U test

**Key Insights:**

* Determine statistical significance
* Validate whether observed patterns are meaningful
* Reduce false assumptions from visual analysis alone

---

### 5. Further Analysis on Imputed Data

**Purpose:**
To ensure that imputation has not introduced bias or distorted distributions.

**Key Checks:**

* Compare original vs imputed distributions
* Validate summary statistics before and after imputation
* Analyze imputed values across target classes
* Check impact on model performance

**Why It Matters:**
Imputed data can unintentionally alter relationships, making this step crucial for reliable modeling.

---

## Output of EDA Level 2

By the end of EDA Level 2, you should have:

* A clear understanding of:

  * Feature relationships
  * Feature predictive power
* A refined feature set ready for modeling
* Documented insights explaining:

  * Why certain features are kept or dropped
  * How transformations impact model performance
