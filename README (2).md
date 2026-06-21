# Generative Models vs Traditional AI-Driven Anomaly Detection in Large-Scale System Logs

> **MS Thesis — Department of Computer Science**  
> Asad Khan | GitHub: [@asadkhanofficial2341-beep](https://github.com/asadkhanofficial2341-beep)

---

## Overview

This repository contains the complete experimental pipeline for the MS thesis comparing **Generative Models** (VAE, GAN) against **Traditional AI-driven** (Random Forest, CNN, LSTM Autoencoder, Isolation Forest, One-Class SVM) anomaly detection techniques applied to real-world large-scale system logs.

The study evaluates 7 machine learning models across two benchmark log datasets — **Apache Spark** and **Hadoop OpenStack** — using ROC-AUC, Recall, and F1-Score as primary metrics.

---

## Datasets

| Dataset | Source | Log Type | Size |
|---|---|---|---|
| **Spark** | Apache Spark cluster logs | Distributed computing | Large-scale |
| **Hadoop** | OpenStack Hadoop logs | Cloud infrastructure | Large-scale |

Raw data is stored under `data/raw/spark/` and `data/raw/hadoop_openstack/`.

---

## Models Evaluated

| # | Model | Category |
|---|---|---|
| 1 | Random Forest | Supervised (Traditional) |
| 2 | CNN Classifier | Supervised (Deep Learning) |
| 3 | LSTM Autoencoder | Semi-supervised (Deep Learning) |
| 4 | Isolation Forest | Unsupervised (Traditional) |
| 5 | One-Class SVM | Unsupervised (Traditional) |
| 6 | VAE (Variational Autoencoder) | Generative |
| 7 | GAN (Generative Adversarial Network) | Generative |

---

## Results Summary

### Spark Dataset

| Rank | Model | ROC-AUC | Recall | F1-Score |
|---|---|---|---|---|
| 1 | **CNN Classifier** | **0.9978** | 1.00 | 0.16 |
| 2 | Random Forest | 0.9902 | 0.89 | 0.44 |
| 3 | LSTM Autoencoder | 0.9822 | 0.93 | 0.05 |
| 4 | Isolation Forest | 0.9559 | 0.04 | 0.04 |
| 5 | VAE | 0.7700 | 0.16 | 0.01 |
| 6 | GAN | 0.2479 | 0.12 | 0.01 |
| 7 | One-Class SVM | 0.2388 | 0.01 | 0.00 |

### Hadoop (OpenStack) Dataset

| Rank | Model | ROC-AUC | Recall | F1-Score |
|---|---|---|---|---|
| 1 | **Random Forest** | **1.0000** | 1.00 | 1.00 |
| 2 | CNN Classifier | 0.9617 | 0.84 | 0.91 |
| 3 | LSTM Autoencoder | 0.6519 | 0.29 | 0.45 |
| 4 | GAN | 0.6133 | 0.01 | 0.03 |
| 5 | VAE | 0.5235 | 0.07 | 0.12 |
| 6 | One-Class SVM | 0.2383 | 0.20 | 0.32 |
| 7 | Isolation Forest | 0.2092 | 0.46 | 0.60 |

---

## Key Findings

- **Supervised > Unsupervised > Generative** — consistent across both datasets
- **CNN Classifier** achieved best ROC-AUC on Spark (0.9978)
- **Random Forest** achieved perfect scores on Hadoop (ROC-AUC = 1.0000, F1 = 1.00)
- **Generative models (VAE, GAN)** consistently underperformed on both datasets, confirming that generative approaches are not yet competitive for log anomaly detection at scale

---

## Repository Structure

```
ASAD-thesis-files/
├── notebooks/
│   ├── spark/          # 5 Jupyter notebooks — Spark experiments
│   └── hadoop/         # 5 Jupyter notebooks — Hadoop experiments
├── results/
│   ├── spark/          # 7 result files (metrics, plots, outputs)
│   └── hadoop/         # 11 result files (metrics, plots, outputs)
├── data/
│   └── raw/
│       ├── spark/              # Raw Spark log dataset
│       └── hadoop_openstack/   # Raw Hadoop OpenStack log dataset
└── docs/               # Thesis documentation and references
```

---

## How to Run

All notebooks are designed to run on **Google Colab**.

### Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/asadkhanofficial2341-beep/ASAD-thesis-files.git
   ```

2. Open [Google Colab](https://colab.research.google.com/)

3. Upload or mount the notebook from `notebooks/spark/` or `notebooks/hadoop/`

4. Upload the corresponding raw dataset from `data/raw/` when prompted

5. Run all cells in order — each notebook is self-contained

> **Note:** Notebooks may require GPU runtime for LSTM, VAE, and GAN experiments. In Colab: `Runtime → Change runtime type → T4 GPU`

---

## Requirements

All dependencies are installed within each notebook via `pip`. No local setup required when using Google Colab.

Key libraries used:

- `scikit-learn` — Random Forest, Isolation Forest, One-Class SVM
- `tensorflow` / `keras` — CNN, LSTM Autoencoder, VAE, GAN
- `pandas`, `numpy` — Data processing
- `matplotlib`, `seaborn` — Visualization
- `drain3` — Log parsing (if applicable)

---

## Collaborators

| Name | GitHub |
|---|---|
| Asad Khan | [@asadkhanofficial2341-beep](https://github.com/asadkhanofficial2341-beep) |
| Hashim Abbas | [@HashimAbbasii](https://github.com/HashimAbbasii) |

---

## License

This repository is part of an academic MS thesis. Please cite appropriately if referencing this work.
