# CIR Yield Curve Modeling

## Stochastic Interest Rate Modelling and Prediction using the Cox–Ingersoll–Ross (CIR) Model

Finance Club IIT Roorkee Open Project

---

## Project Overview

This project implements, calibrates, and extends the Cox–Ingersoll–Ross (CIR) short-rate model for yield curve reconstruction.

The objective is to determine whether an entire yield curve can be reconstructed using only the 3-Month Treasury yield as input. The project follows the workflow specified in the Finance Club IIT Roorkee Open Project and evaluates performance on an unseen test dataset.

The baseline CIR model is calibrated using Exact Maximum Likelihood Estimation (MLE). Its limitations are then analyzed, and two extensions are developed:

1. Deterministic Shift Extension (CIR-inspired)
2. Regime-Aware CIR Extension

The final regime-aware model achieves strong out-of-sample performance and exceeds the project verification threshold.

---

## Repository Structure

```text
cir-yield-curve-modeling
│
├── CIR_PROJECT_final_iitr.ipynb     # Final submission notebook
│
├── notebooks/
│   └── CIR_Project.ipynb            # Development notebook
│
└── README.md
```

---

## Final Submission Notebook

**Open the following notebook for evaluation:**

`CIR_PROJECT_final_iitr.ipynb`

This notebook contains:

* Data preprocessing and quality checks
* Exploratory data analysis
* Mean-reversion diagnostics
* CIR model implementation
* Exact CIR calibration using Maximum Likelihood Estimation
* Feller condition verification
* Yield curve reconstruction using bond pricing formulas
* Deterministic shift extension
* Regime-aware extension
* Out-of-sample backtesting and evaluation

---

## Methodology

### 1. Data Preparation

Historical zero-coupon yield curves are loaded and cleaned. The 3-Month yield is treated as a proxy for the instantaneous short rate.

### 2. CIR Calibration

The CIR process

dr(t) = κ(θ − r(t))dt + σ√r(t)dW(t)

is calibrated using the exact transition density of the CIR model and Maximum Likelihood Estimation.

### 3. Yield Curve Reconstruction

Using the calibrated parameters and closed-form CIR bond pricing formulas, the entire yield curve is reconstructed from the observed short rate.

### 4. Model Extension

Analysis of reconstruction errors reveals systematic bias in the baseline CIR model. To address this:

* A deterministic maturity-dependent correction is introduced.
* A regime-aware version of the correction is developed using separate shift functions for low-rate and high-rate environments.

### 5. Out-of-Sample Testing

The model is evaluated on unseen test data.

Only the 3-Month yield is supplied as input during prediction, and the remaining maturities are reconstructed and compared with actual yields.

---

## Results

| Model              |    RMSE |     R² |
| ------------------ | ------: | -----: |
| CIR                | 0.00836 | -0.379 |
| CIR-inspired Shift | 0.00310 |  0.810 |
| Regime-Aware CIR   | 0.00242 |  0.884 |

### Key Observation

The baseline CIR model systematically underestimates medium- and long-term yields. Introducing deterministic and regime-dependent corrections substantially improves predictive accuracy.

The final regime-aware model achieves:

**Out-of-Sample R² = 0.884**

which exceeds the project verification threshold of **0.85**.

---

## Requirements

The notebook expects the dataset files provided with the project:

* `train_data.csv`
* `test_data.csv`
* `test_data_3M.csv`

These files should be available in the working directory before running the notebook.

---

## Created By

Akarsh Garg

Finance Club IIT Roorkee Open Project Submission
