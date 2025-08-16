# AllLife Bank Customer Segmentation

## Overview
This project segments AllLife Bank customers based on account limits and channel usage to uncover distinct customer groups for targeted marketing and service strategies. It applies unsupervised learning (clustering) on structured banking data and uses dimensionality reduction for visualization and interpretability.

---

## Goals
- Group customers into meaningful segments based on behavior and account attributes
- Summarize segment profiles to inform marketing and service decisions
- Provide a reproducible workflow for unsupervised customer analysis

---

## Methodology

### 1) Data Preparation
- Loaded customer data from `Credit Card Customer Data.xlsx`
- Removed identifier columns (`Sl_No`, `Customer Key`) from modeling
- Scaled numerical features with `StandardScaler`

### 2) Feature Space and Visualization
- Applied **PCA** to visualize and interpret segment separation in lower dimensions

### 3) Clustering
- Trained **KMeans** (with `n_clusters=3`) as the primary method
- Compared with **Agglomerative Clustering** as a secondary approach
- Used **silhouette score** to assess cluster separation

### 4) Segment Interpretation
- Profiled clusters using summary statistics across:
  - `Avg_Credit_Limit`
  - `Total_Credit_Cards`
  - `Total_visits_bank`
  - `Total_visits_online`
  - `Total_calls_made`

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
- Chosen configuration: **KMeans with 3 clusters** (based on silhouette performance and interpretability)
- Segments are primarily differentiated by credit limit, number of cards, and channel usage patterns (branch visits, online visits, call frequency)
- PCA plots show clear separation consistent with the chosen cluster count
