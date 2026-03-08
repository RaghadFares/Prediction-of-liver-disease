# 🫀 Liver Disease Prediction – Data Mining Project

> A data mining study that applies **classification** and **clustering** techniques to predict liver disease using patient medical records — helping identify risk factors and support early diagnosis.

---

## 📌 Motivation

Liver disease is a growing global health concern, affecting people of all ages and nationalities and causing millions of deaths annually. This project was initiated to **understand the causes**, analyze contributing factors, explore prevention methods, and extract meaningful insights from real patient data.

---

## 👥 Team – Group 5

| Name | ID |
|------|----|
| Raghad Fares | 443200793 |
| Sereen Al-hmoud | 443200463 |
| Aeshah Almakhlifi | 443200713 |
| Luluh Al-yahya | 443200609 |

**Course:** IT 326 – Data Mining · **Lab:** Wednesday · **Section:** 74557
**Institution:** King Saud University – College of Computer and Information Sciences

---

## 📂 Dataset

| Property | Details |
|----------|---------|
| **Source** | [Kaggle – Liver Disorders](https://www.kaggle.com/datasets/fatemehmehrparvar/liver-disorders) |
| **Records** | 583 patients |
| **Attributes** | 11 (Age, Gender, TB, DB, Alkphos, Sgpt, Sgot, TP, ALB, A/G Ratio, Selector) |
| **Target** | `Selector` — 1 = Liver Disease · 2 = No Liver Disease |
| **Missing Values** | 4 missing values in A/G Ratio column |

---

## ⚙️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=flat&logoColor=white)

---

## 🔄 Project Pipeline

```
Data Understanding → Preprocessing → Data Mining → Evaluation → Findings
```

---

### 1. 🔍 Data Understanding

Key statistical observations:

- **Age** ranges 4–90 years — liver disease spans all age groups
- **TB, DB, Alkphos, Sgpt, Sgot** — very high variance, extreme values present
- **TP, ALB, A/G Ratio** — low to moderate variance, more stable indicators

Visualizations used: Pie Charts, Scatter Plots, Box Plots, Line Graphs

---

### 2. 🧹 Data Preprocessing

| Step | Method |
|------|--------|
| Missing Values | Replaced with column mean (A/G Ratio) |
| Outlier Handling | IQR capping — 388 rows affected |
| Encoding | Gender: Male = 1, Female = 0 |
| Normalization | Min-Max scaling to unify attribute ranges |
| Discretization | Age → Children (0–17), Adults (18–64), Seniors (65+) |
| Aggregation | Grouped by Gender + Selector to analyze mean differences |
| Class Balancing | Downsampled majority class to achieve 40–60% balance |

---

## 🤖 Data Mining Techniques

### 🌳 Classification – Decision Tree

Predicts whether a patient has liver disease based on 10 medical attributes.

| Split | Criterion | Accuracy | Precision | Sensitivity | Specificity | Error Rate |
|-------|-----------|----------|-----------|-------------|-------------|------------|
| 70/30 | Info Gain | 65.0% | 63% | 48% | 78% | 34% |
| 60/40 | Info Gain | 62.5% | 56% | 47% | 73% | 37.4% |
| 80/20 | Info Gain | 62.1% | 50% | 38% | 76% | 37.8% |
| 70/30 | Gini Index | 64.0% | 61% | 48% | 76% | 35% |
| 60/40 | Gini Index | 63.0% | 57.3% | 51% | 72% | 36% |
| **80/20** | **Gini Index** ✅ | **67.0%** | **57.6%** | **48%** | **78%** | **32%** |

> **Best Model:** 80/20 split with **Gini Index** — highest accuracy (67%) and lowest error rate (32%)

The decision tree relies primarily on: **Total Bilirubin (TB)**, followed by Sgot, Alkphos, ALB, TP, DB, and Sgpt.

---

### 🔵 Clustering – K-Means

Groups patients by similarity without using the class label. Tested K = 2, 3, 6.

| K | Avg. Silhouette Score | WSS |
|---|----------------------|-----|
| **K=2** ✅ | **0.329** | 2537.0 |
| K=3 | 0.232 | 2125.6 |
| K=6 | 0.243 | 1526.8 |

> **Best Clustering:** K=2 — highest silhouette score, most distinct and cohesive clusters

Validation: **Silhouette Method** + **Elbow (WSS) Method**

---

## 🏆 Key Findings

- **Men** are significantly more susceptible to liver disease than women
- **No strong age correlation** — disease can affect individuals of all ages
- Elevated **TB, DB, Alkphos, Sgpt, Sgot** strongly associated with liver disease
- Higher **ALB (Albumin)** indicates liver health — lower levels suggest disease
- A **decreasing A/G Ratio** may signal declining liver function
- **Classification outperforms clustering** here since the dataset includes known labels

---

## 📚 References

- Fatemeh Mehrparvar, [Liver Disorders Dataset](https://www.kaggle.com/datasets/fatemehmehrparvar/liver-disorders), Kaggle
- [Liver disease accounts for two million annual deaths globally](https://pubmed.ncbi.nlm.nih.gov/36990226/), PubMed
- [How Many People Have Liver Disease?](https://liverfoundation.org/about-your-liver/facts-about-liver-disease/how-many-people-have-liver-disease/), American Liver Foundation
- Labs and Lecture Slides, IT Department, King Saud University
