# Customer Segmentation using Clustering Algorithms

## Problem Statement
Businesses often have thousands of customers with varying ages, incomes, and spending behaviors. Treating every customer the same leads to inefficient marketing. This project uses **unsupervised machine learning** to automatically group customers into distinct segments, enabling businesses to design targeted marketing strategies for each group.

## Dataset
**Mall Customer Segmentation Data** (200 records)

| Feature | Description |
|---|---|
| CustomerID | Unique identifier |
| Genre | Gender (Male/Female) |
| Age | Customer age |
| Annual Income (k$) | Annual income in thousands |
| Spending Score (1-100) | Score assigned based on spending behavior |

No target variable — this is an unsupervised learning problem.

## Approach

### 1. Exploratory Data Analysis
- Analyzed distributions of Age, Annual Income, and Spending Score
- Scatter plot of Income vs Spending Score revealed 5 visually distinct customer groups, confirming the dataset is suitable for clustering

### 2. Preprocessing
- Selected features: Age, Annual Income, Spending Score
- Applied **StandardScaler** to normalize features (mean=0, std=1), since distance-based algorithms like K-Means are sensitive to feature scale — without scaling, Income (range 15-137) would dominate over Age (range 18-70)

### 3. Finding Optimal Clusters
- Used the **Elbow Method** (WCSS vs K, for K=1 to 10)
- Elbow observed around K=5, consistent with the 5 groups seen in EDA

### 4. K-Means Clustering
- Applied K-Means with K=5 (`init='k-means++'`) to improve centroid initialization and convergence stability
- **Silhouette Score: 0.408**

### 5. Hierarchical Clustering
- Built a dendrogram using Ward linkage
- Applied Agglomerative Clustering with 5 clusters
- **Silhouette Score: 0.390**

### 6. Algorithm Comparison

| Algorithm | Silhouette Score |
|---|---|
| **K-Means** | **0.408** |
| Hierarchical | 0.390 |

K-Means selected as the final model because it achieved the highest Silhouette Score and its assumptions (compact, roughly spherical, similarly sized clusters) aligned well with the observed data distribution.

## Evaluation Metric Selection

Since customer segmentation is an unsupervised learning problem and no ground-truth labels are available, traditional supervised metrics such as Accuracy, Precision, Recall, and F1-score cannot be used.

Therefore, Silhouette Score was chosen to evaluate cluster quality, as it measures how well-separated and cohesive the clusters are using only the data's geometry.

### 7. PCA Visualization
- Reduced 3 scaled features to 2 principal components (explained variance ≈ 77.5%)
- PCA was used only for visualization purposes and not for clustering itself
- Visualized the 5 K-Means clusters in 2D

### 8. Cluster Profiling & Business Recommendations

| Cluster | Avg Age | Avg Income (k$) | Avg Spending Score | Size | Segment | Recommended Action |
|---|---|---|---|---|---|---|
| 0 | 55.3 | 47.6 | 41.7 | 58 | Mature Moderate-Spending Customers | General campaigns |
| 1 | 32.9 | 86.1 | 81.5 | 40 | High-Value / Premium Customers | VIP offers, loyalty programs |
| 2 | 25.8 | 26.1 | 74.8 | 26 | Budget-Conscious High Spenders | Discounts, installment plans |
| 3 | 26.7 | 54.3 | 40.9 | 45 | Standard / Average Customers | Cost-efficient marketing |
| 4 | 44.4 | 89.8 | 18.5 | 31 | Potential Upsell Customers | Targeted upselling, re-engagement |

## Key Takeaways
- Demonstrated end-to-end unsupervised ML pipeline: EDA → preprocessing → clustering → evaluation → visualization → business interpretation
- Selected the final clustering algorithm based on quantitative evaluation using Silhouette Score rather than visual inspection alone
- Translated technical clusters into actionable, business-oriented customer segments

## Tech Stack
- Python, Pandas, NumPy
- Scikit-learn (KMeans, AgglomerativeClustering, StandardScaler, PCA, silhouette_score)
- Matplotlib, Seaborn, SciPy (dendrogram)

## Future Improvements
- Evaluate DBSCAN and density-based clustering methods on larger customer datasets
- Explore Gaussian Mixture Models (GMM)
- Build an interactive Streamlit dashboard for real-time customer segment exploration
