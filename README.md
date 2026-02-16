# Healthcare Access Inequity Analysis
**Discovering Forgotten Populations Through Clustering-Driven HAII Index**


**Team:** Nandini Talukdar, Suk Jin Chung  
**Date:** February 2026  

---

## 📄 Full Report

📊 **[View Complete Analysis Report (PDF)](https://drive.google.com/file/d/110b2HqIycVKnnKbJkrfELUhCpZtGLF89/view?usp=sharing)**
📈 **[View Interactive Tableau Dashboard] (https://public.tableau.com/views/Healthcare_Clustering/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**



## Project Overview

This project introduces a novel **Healthcare Access Inequity Index (HAII)** that uses unsupervised machine learning to identify "forgotten populations" - vulnerable groups systematically overlooked in traditional demographic health analyses.

### Key Innovation
Rather than analyzing pre-defined demographic groups, we let the data reveal which populations experience compounded disadvantages through **HDBSCAN clustering** combined with a custom composite inequity metric.

### Impact
Targeting the top 15 HAII populations would reach **~20% of adults** experiencing the worst healthcare access outcomes, maximizing intervention impact per dollar spent.

---

## 🔍 Key Findings

### Top 3 Most Vulnerable Populations
1. **Native Hawaiian/Pacific Islander** (HAII: 58.1) - 16.4% access barriers + 33.5% disease prevalence
2. **Uninsured** (HAII: 56.9) - 21.5% access barriers + 20.2% disease prevalence  
3. **Bisexual** (HAII: 56.4) - 19.9% access barriers + 24.7% disease prevalence

### Critical Discoveries
- **11 "forgotten populations"** identified as statistical outliers experiencing extreme healthcare access barriers
- **Mixed-race populations** (AI/AN + White, Black + White) face unique compounded disadvantages not captured by single-race categories
- **Bisexual individuals** face 2.3× higher barriers than gay/lesbian populations - often overlooked in LGBTQ+ health programs
- **7 "double burden" populations** have BOTH high access barriers AND high disease prevalence
- **5 populations show rapid deterioration** (>0.5% per year worsening) - early warning signals

---

## 📊 Data Source

**CDC National Health Interview Survey (NHIS) Adult Summary Health Statistics (2019-2024)**

- **74 unique demographic subgroups** across 21 categories (age, race/ethnicity, insurance, income, education, employment, marital status, sexual orientation, disability, geography)
- **54 health topics** including 4 access barrier measures and 50 health conditions
- **6 years** of temporal data (2019-2024) enabling trend and volatility analysis
- **26,208 records** representing population-level estimates with confidence intervals

---

## 🛠️ Methodology

### 1. Feature Engineering (12 features per subgroup)
**Access Barriers (7 features):**
- Average access barrier percentage
- Standard deviation, min, max barriers
- Average confidence interval width
- Year-over-year change (deterioration metric)
- Temporal volatility

**Health Conditions (5 features):**
- Average condition prevalence
- Standard deviation, count of conditions tracked
- Year-over-year change in health outcomes
- Condition volatility

### 2. Unsupervised Clustering: HDBSCAN
- **Algorithm:** Hierarchical Density-Based Spatial Clustering of Applications with Noise
- **Why HDBSCAN?** Discovers cluster count automatically, adapts to varying densities, identifies outliers
- **Result:** 3 clusters identified
  - Cluster 0: General Population (n=56)
  - Cluster 1: Elderly/Medicare (n=7)
  - Cluster -1: **Outliers/"Forgotten Populations" (n=11)** ⭐

### 3. HAII Calculation
```
HAII = 30% × access_gap + 25% × prevalence_gap + 20% × deterioration 
       + 15% × volatility + 10% × data_quality_penalty
```

**Severity Classification:**
- 0-25: Low (Monitor)
- 25-50: Moderate (Targeted interventions)
- 50-75: High (Priority action) ⚠️
- 75-100: Critical (Emergency response) 🚨

### 4. Validation
- **Silhouette Score:** 0.31 (acceptable for real-world data)
- **DBCV:** 0.42 (positive cluster validity)
- **Bootstrap Stability:** 73-100% across 10 subsamples
- **Monte Carlo Uncertainty:** Top 5 populations remain "High" severity even at lower confidence bounds



## 📝 Citation

If you use this work in your research, please cite:

```bibtex
@misc{talukdar2026haii,
  author = {Talukdar, Nandini and Chung, Suk Jin},
  title = {Healthcare Access Inequity Analysis: Discovering Forgotten Populations Through Clustering-Driven HAII Index},
  year = {2026},
  publisher = {DubsTech Datathon},
  url = {https://github.com/YOUR_USERNAME/healthcare-inequity-analysis}
}
```


**Built with ❤️ for health equity**
