# MQTT IoT Intrusion Detection â€” ML on Big Data with PySpark

> **Evaluating Machine Learning Techniques on Big Data Frameworks for MQTT IoT Security**  
> IEEE I3CTCON 2026 â€” DOI: [10.1109/I3CTCON68242.2026.11508116](https://doi.org/10.1109/I3CTCON68242.2026.11508116)  
> IEEE Open Journal of the Communications Society (Journal) â€” DOI: [10.1109/OJCOMS.2025.3610132](https://doi.org/10.1109/OJCOMS.2025.3610132)

---

## Overview

A **Big Data Machine Learning pipeline** for detecting intrusions in MQTT-based IoT networks. Built on **Apache PySpark (MLlib)**, this project processes 1.1 million+ rows of real IoT network traffic, trains multiple ML classifiers, and evaluates their performance across 6 attack categories.

MQTT is the backbone protocol of most IoT deployments â€” lightweight but with minimal built-in security, making it a high-value attack surface. This project demonstrates how scalable ML on real traffic data can build effective **Intrusion Detection Systems (IDS)**.

### Published Research
- **Journal:** "Enhancing MQTT Intrusion Detection in IoT Using Machine Learning and Feature Engineering" â€” *IEEE Open Journal of the Communications Society*, 2025 (k-NN accuracy: **98.90%**)
- **Conference:** "Evaluating Machine Learning Techniques on Big Data Frameworks for MQTT IoT Security" â€” *IEEE I3CTCON 2026*

---

## Dataset â€” MQTTEEB-D

| Class | Samples | Type |
|---|---|---|
| Malformed | 527,876 | Attack |
| DoS | 210,158 | Attack |
| Bruteforce | 137,222 | Attack |
| Slowite | 100,454 | Attack |
| Legitimate | 87,479 | Normal |
| Flood | 51,379 | Attack |
| **Total** | **1,114,568** | |

Download from Kaggle: `kaggle datasets download -d <mqtteeb-d>`

---

## Pipeline

```
Raw MQTTEEB-D CSV (1.1M rows)
    â†“
EDA (PySpark) â€” class distribution, feature statistics, correlation
    â†“
Preprocessing â€” outlier removal, feature encoding, VectorAssembler, StandardScaler
    â†“
Data Augmentation â€” oversampling minority classes
    â†“
Model Training â€” Logistic Regression Â· Decision Tree Â· GBT
    â†“
Evaluation â€” Accuracy, Precision, Recall, F1, MulticlassClassificationEvaluator
```

---

## Models

| Notebook | Model | Framework |
|---|---|---|
| `EDA (1).ipynb` | Exploratory Data Analysis | PySpark |
| `logistic regression.ipynb` | Logistic Regression | PySpark MLlib |
| `decision-tree (1).ipynb` | Decision Tree Classifier | PySpark MLlib |
| `gbt-classifier.ipynb` | Gradient Boosted Trees | PySpark MLlib |

---

## Requirements

```bash
pip install pyspark scikit-learn pandas seaborn matplotlib
```

---

## Key Concepts

- **Why PySpark?** 1.1M rows is too large for in-memory single-machine sklearn pipelines. PySpark distributes computation across partitions.
- **GBT vs Random Forest** â€” GBT trains sequentially (each tree corrects previous errors); Random Forest trains in parallel.
- **Class imbalance** â€” Malformed (527K) vs Flood (51K): handled via augmentation and weighted evaluation metrics.
- **VectorAssembler** â€” PySpark's way to combine feature columns into a single vector column for MLlib.

---

## Authors

Geda Tejesh Chowdary Â· Paramkusam Sriharsha Â· Yelipe Gowtham  
Amrita Vishwa Vidyapeetham, Bengaluru
