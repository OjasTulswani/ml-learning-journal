# Lecture 1: Understanding Statistics for Machine Learning

Statistics is a core foundation of Machine Learning (ML). It helps us **understand data**, **build better models**, and **evaluate their performance**. Before diving deep into ML algorithms, it's important to understand the basics of statistics.

---

## What Is Statistics?

Statistics is the field that deals with:

- **Collecting data**
- **Analyzing data**
- **Interpreting results**
- **Presenting findings**
- **Organizing information**

Many ML techniques—like **regression**, **classification**, and **clustering**—are built on statistical ideas.

Statistics is broadly divided into two types:

1. **Descriptive Statistics**
2. **Inferential Statistics**

Let’s look at each in a beginner-friendly way.

---

# 1. Descriptive Statistics

Descriptive statistics help us **summarize and describe** the important features of a dataset. They turn large amounts of data into simple, understandable summaries.

### Key Concepts

### **a. Measures of Central Tendency**

These tell us where the _center_ of the data lies.

- **Mean**: The average.
- **Median**: The middle value when data is sorted.
- **Mode**: The value that appears most often.

_Example:_  
Suppose we have test scores:  
`70, 80, 80, 90, 100`

- Mean = (70 + 80 + 80 + 90 + 100) / 5 = **84**
- Median = **80** (middle value when sorted)
- Mode = **80** (most frequent)

---

### **b. Measures of Dispersion**

These describe how **spread out** the data is.

- **Range**: Max − Min
- **Variance**: Measures how far numbers spread from the mean
- **Standard Deviation**: The square root of variance (also shows spread)

_Example:_  
Using the same scores:

- Range = 100 − 70 = **30**

A large range or standard deviation means the values are spread widely; a small one means the data is clustered.

---

### **c. Data Visualization**

Graphs make data easier to understand.

- **Histograms** show frequency of values
- **Box plots** show distribution and outliers
- **Scatter plots** show relationships between two variables

Visualization helps spot **patterns**, **trends**, or **unusual points**.

---

### Why Descriptive Statistics Matter

They help you quickly understand the **shape**, **center**, and **spread** of your data before building ML models.

---

# 2. Inferential Statistics

While descriptive statistics summarize the data we have, **inferential statistics help us make conclusions about a bigger population** based on a smaller sample.

### Key Concepts

### **a. Sampling**

Choosing a smaller group from a larger population.
The smaple should be random and representative i.e it covers all type of categories from data

_Example:_  
Instead of surveying **all** customers, a company might survey **200 customers** and use that sample to understand overall satisfaction.

---

### **b. Hypothesis Testing**

Used to test claims about a population.

_Example:_  
A company claims that their new ad campaign increases sales.  
Hypothesis testing can help determine if data supports this claim.

---

### **c. Confidence Intervals**

A range of values likely to contain the true population value.

_Example:_  
A sample mean height might be **170 cm**, with a 95% confidence interval of **168–172 cm**.  
This means we’re 95% confident the actual average height of the population is in that range.

---

### **d. Regression Analysis**

Helps understand relationships between variables and make predictions.

_Example:_  
Predicting a house price based on:

- size
- location
- number of rooms

Regression finds patterns in the data to make these predictions.

---

### Why Inferential Statistics Matter

They let us:

- Make predictions,
- Test ideas,
- Quantify uncertainty,
- Draw conclusions about populations from samples.
