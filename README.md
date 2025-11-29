# Uncovering Behavioral Patterns in Social Anxiety

### Clustering & PCA Analysis on Student Health Data

  

## 📌 Project Overview

Rising social anxiety among students is often detected only after symptoms escalate. This project utilizes unsupervised machine learning techniques—specifically **Principal Component Analysis (PCA)** and **K-Means Clustering**—to uncover hidden behavioral risk profiles within anonymized student data.

The goal is to demonstrate how existing survey data (lifestyle, physiological, and mental health history) can be used to identify at-risk groups without the need for expensive diagnostics, enabling better resource allocation for student services.

## 📂 Dataset

The analysis uses the **[Social Anxiety Dataset](https://www.kaggle.com/datasets/natezhang123/social-anxiety-dataset)** from Kaggle.

  * **Size:** 10,000+ records.
  * **Features:** 19 columns covering demographics, lifestyle (sleep, diet, activity), and physiology (heart rate, breathing rate).
  * **Preprocessing:** Data was standardized using `StandardScaler` to handle varying unit scales.

## ⚙️ Methodology

1.  **Exploratory Data Analysis (EDA):** Analyzed correlations and distributions; identified low pairwise correlation among features ($r < 0.31$).
2.  **Dimensionality Reduction:** Applied **PCA** to reduce noise and redundancy. 8 components were retained, preserving \>80% of the variance.
3.  **Clustering:** Implemented **K-Means++** on the PCA-reduced data.
      * *Optimization:* Evaluated using Silhouette Score and Davies-Bouldin Index.
      * *Selection:* $k=2$ provided the most robust (though structurally weak) separation.
4.  **Validation:** Validated the unsupervised clusters against the "Anxiety Level" target variable (which was excluded from training).

## 📊 Key Findings

The model identified two distinct behavioral profiles. Despite weak structural separation in the vector space, the groups showed clear semantic differences:

| Feature | Cluster 0 (Balanced) | Cluster 1 (At-Risk) |
| :--- | :--- | :--- |
| **Sleep Quality** | Average / Good | Significantly Reduced |
| **Physical Activity** | Active | Low Activity |
| **Caffeine Intake** | Low | Very High |
| **Physiological Stress** | Normal Heart/Breathing Rate | Elevated Rates |
| **Therapy Usage** | Low | Frequent |
| **Validation Score** | **Mean Anxiety: 3.37** | **Mean Anxiety: 7.60** |

**Conclusion:** The algorithms successfully segregated students into a "Balanced" group and a "High-Stress/At-Risk" group. Cluster 1 aligns with clear indicators of social anxiety, validating the potential for data-driven early intervention.