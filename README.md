# Bank Customer Churn: Predictive Modeling & Algorithmic Implementation

![R](https://img.shields.io/badge/Language-R-blue)
![Tidyverse](https://img.shields.io/badge/Library-Tidyverse-orange)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-green)
![Status](https://img.shields.io/badge/Status-Completed-success)

> **End-to-end churn analysis featuring a custom implementation of ML algorithms (AdaBoost, Naive Bayes, K-NN) built from scratch without libraries.**

## Project Overview
Customer retention is critical for banking profitability. This project analyzes a dataset of bank customers to identify factors contributing to churn and builds predictive models to flag high-risk accounts.

Beyond standard modeling, this project includes a **Research Component**: I manually implemented core machine learning algorithms (from mathematical first principles) to benchmark their performance against optimized production libraries like `caret` and `xgboost`.

## Key Features & Workflow

### 1. Exploratory Analysis & Clustering (Unsupervised)
* **Dimensionality Reduction:** Applied PCA to reduce noise.
* **Clustering:** Compared **K-Means** vs. **Hierarchical Clustering**.
    * *Insight:* Found distinct customer segments based on `Balance` and `NumOfProducts`.

### 2. Predictive Modeling (Supervised)
* **Model Selection:** Trained Logistic Regression, LDA, Random Forest, and Gradient Boosting.
* **Winner:** **XGBoost** achieved the highest recall for the minority class (churners).
* **Optimization:** Tuned hyperparameters to maximize the identification of leaving customers (Recall) rather than just accuracy.

### 3. Algorithmic Implementation (From Scratch)
I re-created the following algorithms using only base R and matrix algebra to understand their inner workings:
* **Naive Bayes:** Manual probability calculation vs. `naivebayes` package.
* **AdaBoost:** Custom iterative weight updates vs. `adabag`.
* **K-Nearest Neighbors:** Euclidean distance matrix calculation vs. `class::knn`.

## Tech Stack
* **Language:** R (Markdown)
* **Data Manipulation:** Tidyverse, Data.Table
* **Machine Learning:** Caret, XGBoost, GBM, RandomForest, Rpart
* **Visualization:** GGplot2, pROC

## Results: Manual vs. Package

One of the key goals was to validate the manual implementations. The custom Naive Bayes model showed competitive performance with the library version, sacrificing slight specificity for higher sensitivity in detecting churners.

| Métrica | Naive Bayes (Package) | Naive Bayes (Manual Implementation) |
| :--- | :--- | :--- |
| **Accuracy** | 83.76% | 83.36% |
| **Recall (Sensitivity)** | 23.24% | **34.55%** |
| **Kappa** | 0.32 | **0.37** |

*(The manual implementation actually outperformed the package in detecting the target class in this specific instance.)*

## 🚀 Installation & Usage

1.  **Clone the repo:**
    ```bash
    git clone [https://github.com/yourusername/bank-churn-prediction.git](https://github.com/yourusername/bank-churn-prediction.git)
    ```
2.  **Install dependencies:**
    ```r
    install.packages(c("tidyverse", "caret", "xgboost", "gbm", "adabag", "naivebayes"))
    ```
3.  **Run the analysis:**
    Open `notebooks/03_algorithms_from_scratch.Rmd` in RStudio and click "Knit" to see the mathematical implementations in action.

## Engineering Decisions
* **Why XGBoost?** Although simpler models like Logistic Regression are interpretable, they failed to capture the non-linear relationships between credit score and account balance. XGBoost offered the best trade-off between performance and speed.
* **Manual Implementation:** Building AdaBoost from scratch revealed the importance of the weighting mechanism for misclassified samples—a nuance often lost when simply calling `train()`.

## 👤 Author
**Gonzalo Cruz Gómez**

---
*Developed as a capstone project for the subject Machine Learning I.*
