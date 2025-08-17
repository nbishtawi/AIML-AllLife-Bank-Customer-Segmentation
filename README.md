# AllLife Bank Customer Segmentation

## Overview
This project segments AllLife Bank customers based on account limits and channel usage to uncover distinct customer groups for targeted marketing and service strategies. It applies unsupervised learning (clustering) on structured banking data and uses dimensionality reduction for visualization and interpretability.

---

## Goals
- Group customers into meaningful segments based on behavior and account attributes
- Compare clustering approaches to select the most effective method
- Summarize segment profiles to inform marketing and service decisions

---

## Methodology

### 1) Data Preparation
- Loaded customer data from `Credit Card Customer Data.xlsx`
- Removed identifier columns (`Sl_No`, `Customer Key`) from modeling
- Scaled numerical features with `StandardScaler`

### 2) Feature Space and Visualization
- Applied **PCA** to visualize and interpret segment separation in lower dimensions

### 3) Clustering Approaches
- **KMeans Clustering** (`n_clusters=3`)  
  - Silhouette Score: **0.516**  
  - Faster to compute, provides similar grouping to hierarchical  
- **Hierarchical Clustering (Agglomerative)** (`n_clusters=3`)  
  - Silhouette Score: **0.591**  
  - More computationally intensive (especially dendrogram construction), but achieved higher separation quality  
- Both methods converged on 3 clusters as the optimal number

### 4) Model Selection
- Chosen approach: **Hierarchical Clustering**  
- Rationale: higher silhouette score and more clearly separated segments  

---

## Repository Structure
```
AllLife-Bank-Customer-Segmentation/
├── alllife_customer_segmentation.ipynb # Main notebook (rename from AllLife Bank Customer Segmentation Project.ipynb)
├── Credit Card Customer Data.xlsx # Customer dataset
└── README.md # Project documentation
```

---

## Dataset
Rows: 660  
Columns: 7  
Fields:
- Identifiers (excluded from modeling): `Sl_No`, `Customer Key`
- Features: `Avg_Credit_Limit`, `Total_Credit_Cards`, `Total_visits_bank`, `Total_visits_online`, `Total_calls_made`

---

## Results

### Cluster Comparison
- **KMeans** and **Hierarchical** clustering both suggested 3 clusters  
- Cluster counts between the two methods were nearly identical, with only a 1-observation difference for certain clusters  
- Cluster 2 in KMeans matched Cluster 1 in Hierarchical in terms of customer count  

### Final Choice: Hierarchical Clustering
- **Silhouette Score (Hierarchical):** 0.591  
- **Silhouette Score (KMeans):** 0.516  
- Hierarchical chosen for better separation, despite longer computation time  

---

## Business Insights (Hierarchical Clustering)

- **Cluster 0** (387 customers)  
  - Avg Credit Limit: very low to moderate  
  - Total Calls: very low to low  
  - Uses online portal rarely, moderate to high number of in-person visits  
  - Low to moderate number of credit cards  

- **Cluster 1** (50 customers)  
  - Avg Credit Limit: very moderate to very high  
  - Total Calls: very low to low  
  - Uses online portal moderately to often/very high, rarely visits bank in person  
  - Moderate to very high number of credit cards  

- **Cluster 2** (223 customers)  
  - Avg Credit Limit: very low  
  - Total Calls: low to high  
  - Rarely visits bank or uses online portal (both low)  
  - Very low to low number of credit cards  
