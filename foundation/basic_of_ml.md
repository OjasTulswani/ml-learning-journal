# Basics of Machine Learning

Machine Learning (ML) is a subset of Artificial Intelligence that enables systems to learn from data and improve their performance without being explicitly programmed.

---

## Types of Machine Learning

### 1. Supervised Learning

In supervised learning, **both inputs and corresponding outputs (labels) are provided**. The model learns the relationship between input and output data.

**Types:**

* **Regression**
  Used when the output is a continuous value (e.g., house price prediction).
* **Classification**
  Used when the output belongs to a fixed set of categories (e.g., spam vs non-spam email).

---

### 2. Unsupervised Learning

In unsupervised learning, **only input data is provided**, and the model must find patterns or structures in the data on its own.

**Types:**

* **Clustering**
  Groups similar data points together based on patterns and similarities (e.g., customer segmentation).
* **Dimensionality Reduction**
  Converts high-dimensional data into a lower-dimensional space without losing important information (e.g., PCA).
* **Anomaly Detection**
  Identifies unusual patterns or behaviors in data that do not conform to expected behavior (e.g., fraud detection).
* **Association Rule Learning**
  Finds interesting relationships between variables in large datasets using *if–then* rules (e.g., market basket analysis).

---

### 3. Semi-Supervised Learning

Semi-supervised learning uses **both labeled and unlabeled data**. Typically, only a small portion of the data is labeled, while the majority is unlabeled. The model learns patterns from unlabeled data and uses labeled data to guide learning.

**Example:**
Google Photos — when a user labels a few images of a person as “Papa,” the system automatically labels other photos of the same person.

---

### 4. Reinforcement Learning

Reinforcement learning is one of the most **trending learning approaches**. An **agent learns by interacting with an environment** and receives rewards or penalties based on its actions. The goal is to maximize cumulative rewards through trial and error, similar to human learning.

**Examples:**

* Self-driving cars (e.g., Tesla)
* Robotics
* Game-playing AI

---

## Training of a Machine Learning Model

### 1. Batch (Offline) Learning

In batch learning, the model is trained using the **entire dataset at once**. After training and testing, the model is deployed to production.

**Workflow:**

1. Collect data
2. Train the model using the full dataset
3. Test the model
4. Deploy to production
5. Repeat periodically (e.g., daily, weekly, or scheduled retraining)

**Advantages:**

* Simple to implement
* Works well for stable datasets

**Disadvantages:**

* Requires significant computational resources for large datasets
* Not suitable for rapidly changing data
* Retraining requires access to the full dataset
* Delays in updating the model with new information

**Example:**
A recommendation system retrained every 24 hours may fail to capture sudden trends (e.g., breaking news like demonetization). Users may search for trending topics immediately, but the model will only update after the next scheduled training cycle, causing outdated recommendations.

---

## Online Learning

In **online learning**, the model initially learns from a **small batch of data**, builds the model, tests it, and then deploys it to production.
After deployment, the model continues to **make predictions and learn directly in production** using incoming data, usually in **small batches or one data point at a time**.

Because the data is small and arrives sequentially, the model can update itself continuously. Over time, the product learns from more data and its performance improves.

**Examples:**

* Online AI chatbots
* Google Keyboard (Gboard)
* YouTube recommendations

---

### Incremental Learning

Online learning follows an **incremental or sequential learning approach**.
The model updates itself step by step as new data arrives, rather than retraining on the entire dataset.

Since data comes in small chunks, this learning can safely happen **in production**, batch by batch, in a sequential manner.

---

## When to Use Online Learning vs Batch Learning

### Use Online Learning When:

* You need a **cost-effective solution**
* You want **fast model updates**
* **Concept drift** is present (data patterns change over time)
* Data arrives continuously (streams)
* Retraining the full dataset frequently is not feasible

Online learning is more effective than batch/offline learning in terms of:

* Speed
* Resource usage
* Handling changing data

Data is processed in **small chunks sequentially** and updated directly on the server.

---

## How Online Learning Is Implemented

Online learning can be implemented using libraries such as:

* **Scikit-learn** (`partial_fit`)
* **Vowpal Wabbit**
* **River**

These frameworks allow models to update incrementally without retraining from scratch.

---

## Learning Rate

The **learning rate** controls how fast a model adapts to new data.

* A **very high learning rate** may cause the model to forget old knowledge too quickly
* A **very low learning rate** may make learning too slow

Choosing the correct learning rate is **crucial**, because an incorrect value can cause the model to:

* Forget previously learned patterns
* Learn too aggressively
* Misbehave in production systems

---

## Out-of-Core Learning

Out-of-core learning is used when the **dataset is too large to fit into memory**.

**Example:**

* Dataset size: 50 GB
* Available RAM: 8 GB

Since the full dataset cannot be loaded at once, the data is divided into **small batches**, and the model is trained batch by batch.

### How It Works

* Data is streamed in mini-batches
* The model updates incrementally
* Uses methods like `partial_fit`

**Example Use Case:**
In text classification (e.g., Reuters-21578 dataset):

* `HashingVectorizer` maintains a consistent feature space
* Models like `SGDClassifier` or `Perceptron` update parameters incrementally

---

### Relationship Between Online and Out-of-Core Learning

* Out-of-core learning is **not a separate learning paradigm**
* It is a **strategy** that can be applied to both supervised and unsupervised learning
* It is closely related to online learning

Models:

* Adapt to new data as it arrives
* Give more importance to recent data
* Avoid storing large historical datasets in memory

**Ideal for real-time applications**, such as:

* Email spam detection
* Recommendation systems
* User feedback-driven systems

---

## Disadvantages of Online Learning

* **Tricky to implement**
  Requires careful handling of learning rate, data quality, and monitoring
* **Risky**
  Bad or noisy data can immediately affect the model in production
* **Harder to debug**
  Errors propagate quickly if not detected early

---

## Batch Learning vs Online Learning

| Feature                | Batch Learning       | Online Learning        |
| ---------------------- | -------------------- | ---------------------- |
| Data processing        | Full dataset at once | Small chunks / streams |
| Model updates          | Periodic             | Continuous             |
| Cost                   | High for large data  | More cost-effective    |
| Speed of updates       | Slow                 | Fast                   |
| Concept drift handling | Poor                 | Excellent              |
| Production risk        | Low                  | Higher                 |

---

## 1. Instance-Based Learning

Instance-based learning is a type of learning where the model **stores the training data** and makes predictions **only when a new input is received**.

- There is **no explicit model training or generalization phase**.
- Predictions are made by comparing the new input with stored training instances.
- A **distance metric** (commonly **Euclidean distance**) is used to find the nearest data points.
- The output is inferred based on the most similar instances in the dataset.

### Key Characteristics
- Stores the entire training dataset
- No mathematical model is built
- Learning happens at **query time**
- Example algorithms: **k-Nearest Neighbors (KNN)**

---

## 2. Model-Based Learning

Model-based learning focuses on **understanding the underlying pattern or relationship** between input features and output labels.

- The algorithm learns a **mathematical relationship** from the training data.
- It creates a **decision boundary** or **decision function**.
- Once the model is trained, the **training data is no longer required**.
- New inputs are passed through the learned function to get predictions.

### Key Characteristics
- Learns parameters from training data
- Builds a generalized model
- Learning happens during the **training phase**
- Example algorithms: **Linear Regression, Logistic Regression, SVM**

---

## Key Differences Between Instance-Based and Model-Based Learning

| Aspect | Instance-Based Learning | Model-Based Learning |
|------|------------------------|---------------------|
| Data Cleaning | Same preprocessing steps as model-based | Same preprocessing steps as instance-based |
| Training Phase | No explicit training | Model is trained on data |
| Pattern Discovery | Happens at query time | Happens during training |
| Model Storage | No model stored | Trained model is stored |
| Generalization | No generalization before prediction | Generalizes during training |
| Prediction on Unseen Data | Uses training data directly | Uses learned model |
| Data Requirement After Training | Must keep entire dataset | Training data can be discarded |
| Storage Requirement | High (stores full dataset) | Low (stores only model parameters) |
| Speed | Slower predictions | Faster predictions |

---

## Conclude 

- **Instance-Based Learning** memorizes data and defers computation until prediction time.
- **Model-Based Learning** builds a generalized model that can efficiently predict unseen data.
- Choice depends on dataset size, memory constraints, and prediction speed requirements.

---
