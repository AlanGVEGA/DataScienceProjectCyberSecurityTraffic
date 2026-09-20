# DataScienceProjectCyberSecurityTraffic
# Network Traffic Data Analysis for Cybersecurity — UNSW-NB15

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-purple)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Analysis-blue)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-lightblue)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-yellow)

## Overview

This project analyzes network traffic using the **UNSW-NB15 cybersecurity dataset** as part of the **DataXperience course at Universidad EAN**.

The goal is to apply data preparation, exploratory data analysis, descriptive statistics, and visualization techniques to understand differences between **normal and malicious network traffic**.

The project was developed collaboratively by:

- **Angelica Vanessa Castro**
- **Alan Gabriel Vega**

The cybersecurity domain was selected because it provides a realistic technical environment where statistical and data-analysis techniques can be applied to a relevant engineering problem.

From an **Industrial Engineering** perspective, the project focuses on data-driven decision making, variability analysis, risk evaluation, and pattern identification. Previous experience in **Systems Engineering** also provided complementary context for understanding network and cybersecurity concepts.

---

## Research Question

> **What characteristics of network traffic show descriptive differences between normal and malicious connections in the UNSW-NB15 dataset?**

The current stage of the project is focused on **descriptive analysis**.

The results do **not** imply causality and are not yet evidence of predictive performance.

---

## Dataset

The analysis uses the UNSW-NB15 training dataset.

### Dataset used in this project

| Feature | Value |
|---|---:|
| Records | 175,341 |
| Variables | 45 |
| Normal traffic | 56,000 |
| Attack traffic | 119,341 |
| Normal traffic | 31.94% |
| Attack traffic | 68.06% |

The dataset contains both numerical and categorical variables related to:

- Connection duration
- Packets sent and received
- Bytes transferred
- Traffic rates
- Network load
- TCP timing
- Protocol
- Service
- Connection state
- Attack category

Main variables used in the descriptive analysis include:

`dur`, `spkts`, `dpkts`, `sbytes`, `dbytes`, `rate`, `sload`, `dload`, and `tcprtt`.

Target variables:

- `label`: Normal vs Attack
- `attack_cat`: Traffic / attack category

---

## Project Workflow

The project follows a structured data science workflow:

### 1. Data Understanding

- Dataset dimensions
- Variable types
- Numerical and categorical features
- Target variables
- Cardinality analysis
- Initial distributions

### 2. Data Quality Assessment

The dataset was evaluated for:

- Missing values
- Exact duplicates
- Infinite values
- Inconsistent categorical representations
- Data type problems
- Extreme values

### 3. Data Cleaning

A cleaned version of the dataset was generated while preserving relevant observations.

Final validation:

| Quality Check | Result |
|---|---:|
| Missing values | 0 |
| Duplicate rows | 0 |
| Infinite values | 0 |
| Rows removed | 0 |
| Final dimensions | 175,341 × 45 |

Extreme values were **not automatically removed**, since unusual network behavior can represent valid or security-relevant activity.

---

## Descriptive Statistical Analysis

The analysis includes:

### Measures of Central Tendency

- Mean
- Median
- Mode

Several variables showed large differences between mean and median, indicating strongly right-skewed distributions.

Example:

| Variable | Mean | Median | Mode |
|---|---:|---:|---:|
| `dur` | 1.3594 | 0.0016 | 0 |
| `spkts` | 20.2987 | 2 | 2 |
| `dpkts` | 18.9696 | 2 | 0 |
| `sbytes` | 8,844.8438 | 430 | 114 |
| `dbytes` | 14,928.9186 | 164 | 0 |

---

### Measures of Dispersion

The project also evaluates:

- Range
- Variance
- Standard deviation
- Q1
- Q3
- Interquartile Range (IQR)

These measures help identify the amount of variability present in network behavior.

---

## Outlier Analysis

Potential outliers were identified using the **Interquartile Range method**:

\[
IQR = Q3 - Q1
\]

Lower threshold:

\[
Q1 - 1.5 \times IQR
\]

Upper threshold:

\[
Q3 + 1.5 \times IQR
\]

Some of the highest proportions observed were:

| Variable | Outliers |
|---|---:|
| `dload` | 21.75% |
| `dbytes` | 16.04% |
| `spkts` | 14.07% |
| `sbytes` | 13.04% |
| `dpkts` | 11.88% |
| `rate` | 9.89% |

These observations were retained because an extreme network value may represent legitimate behavior or anomalous activity rather than a measurement error.

---

## Normal vs Attack

The project compares descriptive characteristics between normal and malicious traffic.

Examples using median values:

| Variable | Normal | Attack |
|---|---:|---:|
| `dur` | 0.0386 | 0 |
| `spkts` | 12 | 2 |
| `sbytes` | 1,470 | 200 |

The analysis shows descriptive differences in:

- Connection duration
- Number of packets
- Data volume
- Distribution shape
- Variability

Logarithmic transformations using `log1p()` are used **only for visualization purposes** when distributions are strongly skewed.

They do not remove or modify the observations used in the statistical calculations.

---

## Attack Categories

The `attack_cat` variable provides a more detailed view of network behavior.

Categories present in the training data include:

- Normal
- Generic
- Exploits
- Fuzzers
- DoS
- Reconnaissance
- Analysis
- Backdoor
- Shellcode
- Worms

The analysis shows that the different categories do not follow identical statistical behavior.

Categories with very few observations should therefore be interpreted carefully.

---

## Key Findings

1. Several network variables show **strong right-skewed distributions**.

2. The dataset contains a considerable number of statistically extreme observations.

3. Extreme observations should not automatically be interpreted as data errors in a cybersecurity context.

4. Normal and malicious traffic show descriptive differences in variables related to duration, packets, and transferred bytes.

5. Different attack categories exhibit different statistical patterns.

6. No single variable should be interpreted as sufficient to identify an attack.

---

## Professional Application

From an **Industrial Engineering** perspective, this project demonstrates how data analysis can support:

- Evidence-based decision making
- Risk analysis
- Variability analysis
- Pattern identification
- Process monitoring
- Data quality evaluation

From a cybersecurity perspective, exploratory and statistical analysis can help prepare network data for future:

- Intrusion detection systems
- Traffic classification
- Anomaly detection
- Machine learning models

---

## Next Steps

Future stages may include:

- Feature selection
- Correlation analysis
- Training/testing separation
- Predictive classification models
- Model evaluation
- Confusion matrix
- Precision, Recall and F1-score
- Comparison between attack categories

The test dataset will remain reserved for proper model evaluation.

---

## Technologies

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- GitHub
- Google Drive

---

## Repository Contents

```text
DataScienceProjectCyberSecurityTraffic/
│
├── README.md
└── Train_Test_Dataset_UNSW_NB15.ipynb
