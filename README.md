# Customer Segmentation using K-Means and Hierarchical Clustering

## Problem Statement

Businesses often have thousands of customers with different demographics, purchasing habits, and spending behaviors. Treating all customers the same can lead to inefficient marketing campaigns and lower customer engagement.

This project uses **unsupervised machine learning** techniques to automatically segment customers into meaningful groups, enabling businesses to design targeted marketing strategies and improve customer retention.

---

## Dataset

**Marketing Campaign Dataset**

* Total Customers: **2240**
* Features: **29**
* Dataset contains customer demographics, purchasing behavior, campaign responses, and spending information.

### Key Features Used

* Age
* Total Spending
* Total Purchases
* Total Children

Additional categorical variables were encoded using One-Hot Encoding during preprocessing.

Since no target variable exists, this is an **unsupervised learning problem**.

---

## Project Workflow

### 1. Data Cleaning & Preprocessing

* Handled missing values
* Removed outliers
* Performed feature engineering
* Applied One-Hot Encoding for categorical variables
* Standardized numerical features using StandardScaler

### 2. Feature Engineering

Created meaningful business-oriented features:

* Total_Spending
* Total_Purchases
* Total_Children
* Age

These features better capture customer behavior than raw attributes alone.

### 3. Dimensionality Reduction

Applied **Principal Component Analysis (PCA)** to reduce dimensionality and visualize customer segments effectively.

PCA was used only for visualization and not for clustering itself.

### 4. Finding Optimal Number of Clusters

Used the **Elbow Method** to determine the optimal number of clusters.

The elbow point suggested:

* Optimal Clusters (K) = **4**

---

## Clustering Algorithms

### K-Means Clustering

Applied K-Means clustering with:

* K = 4
* Random State = 42

### Hierarchical Clustering

Applied Agglomerative (Hierarchical) Clustering for comparison.

---

## Algorithm Evaluation

Since clustering is an unsupervised learning task, traditional metrics such as Accuracy, Precision, Recall, and F1-score cannot be used.

Therefore, **Silhouette Score** was used to evaluate cluster quality.

| Algorithm                    | Silhouette Score |
| ---------------------------- | ---------------- |
| K-Means                      | 0.433            |
| Hierarchical (Agglomerative) | 0.364            |

### Final Model Selection

K-Means achieved a higher Silhouette Score, indicating better cluster separation and cohesion.

Therefore, **K-Means was selected as the final clustering algorithm.**

---

## Key Results

* Processed and analyzed a marketing campaign dataset containing 2240 customers and 29 features.
* Compared K-Means and Hierarchical Clustering algorithms.
* Determined the optimal number of clusters (K=4) using the Elbow Method.
* Achieved a Silhouette Score of 0.433 using K-Means.
* Achieved a Silhouette Score of 0.364 using Hierarchical Clustering.
* Selected K-Means as the final clustering algorithm due to superior cluster separation and cohesion.
* Generated business-oriented customer segments for targeted marketing strategies.

---

## Business Impact

Customer segmentation enables organizations to:

* Identify high-value customers
* Design targeted marketing campaigns
* Improve customer retention
* Optimize promotional spending
* Personalize customer engagement strategies

---

## Tech Stack

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn
* SciPy

### ML Techniques Used

* K-Means Clustering
* Hierarchical Clustering
* PCA
* StandardScaler
* One-Hot Encoding
* Elbow Method
* Silhouette Score

---

## Future Improvements

* Evaluate DBSCAN for density-based clustering
* Explore Gaussian Mixture Models (GMM)
* Add SHAP-style cluster interpretation
* Build an interactive Streamlit dashboard
* Deploy the segmentation pipeline for real-time customer analysis
