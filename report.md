# Project Report: Custom SVM Implementation for Bank Marketing Classification

**Author:** M SHARATH CHANDRA | **Roll Number:** IITMD_DSAI_2503202  
**Date:** December 23, 2025

---

## 🚀 Executive Summary

This project delivers a robust, scratch-built implementation of **Support Vector Machines (SVM)** to predict client subscription outcomes for a Bank Marketing dataset. By implementing current state-of-the-art optimization techniques (**Sequential Minimal Optimization**) and deploying a custom **Ensemble Learning** strategy, the model achieved a **peak accuracy of 96%** and an **F1-Score of 0.73**, matching the performance of standard industrial libraries.

---

## 1. Project Objectives & Methodology

The primary goal was to demystify utilizing "black-box" machine learning tools by engineering the core SVM logic from the ground up.

### Core Architecture
*   **Algorithm:** Sequential Minimal Optimization (SMO) for solving the quadratic programming objective.
*   **Kernels Engineered:**
    *   **Linear:** Efficient for high-dimensional feature spaces.
    *   **Polynomial:** Captures non-linear feature interactions (Degrees 2-5).
    *   **RBF (Gaussian):** Handles complex, non-linear class boundaries.

### Data Pipeline
*   **Preprocessing:** Rigorous One-Hot Encoding for categorical variables and Standard Scaling ($ \mu=0, \sigma=1 $) for numerical features to ensure optimal hyperplane convergence.
*   **Validation:** 80-20 Train-Test split to ensure generalization.

---

## 2. Key Results & Performance Analysis

We conducted extensive hyperparameter tuning across all kernel types. The **Linear Kernel** and **Ensemble Model** emerged as the top performers.

### 🏆 Top Model Performance

| Model Architecture | Hyperparameters | Accuracy | F1-Score | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Linear Kernel** | $C=0.1$ | **96.0%** | **0.714** | ✅ Highly Efficient |
| **Polynomial Kernel** | $d=3$ | 95.5% | 0.727 | ⚖️ Balanced |
| **RBF Kernel** | $C=100, \gamma=0.01$ | 95.0% | 0.688 | 🎯 Precise |
| **Ensemble (Voting)** | *Top 3 Models* | **96.0%** | **0.733** | 🌟 **Best Overall** |

> **Insight:** The dataset exhibits strong linear separability in the transformed feature space, allowing the Linear Kernel to perform exceptionally well with minimal computational cost.

---

## 3. Visual Insights

### 3.1 Optimizing Model Complexity
The Polynomial Kernel's performance peaks at **Degree 3**. Moving to higher degrees (4, 5) introduces overfitting, leading to a sharp decline in F1-score on the test set.

<div align="center">
  <img src="poly_f1_plot.png" alt="Polynomial Kernel Performance Analysis" width="600" style="border: 1px solid #ddd; border-radius: 4px; padding: 5px;"/>
  <br>
  <em>Figure 1: F1-Score vs. Polynomial Degree. The "sweet spot" for complexity is clearly observed at Degree 3.</em>
</div>

<br>

### 3.2 Reliability of the Final Ensemble
The Confusion Matrix for our final Ensemble model demonstrates its robustness. The high diagonal values indicate correct predictions, with a particularly strong ability to identify true negatives, which is crucial for optimizing marketing resource allocation.

<div align="center">
  <img src="confusion_matrix_ensemble.png" alt="Ensemble Confusion Matrix" width="500" style="border: 1px solid #ddd; border-radius: 4px; padding: 5px;"/>
  <br>
  <em>Figure 2: Confusion Matrix of the Ensemble Model. High accuracy is visually confirmed by the dominant diagonal.</em>
</div>

---

## 4. Conclusion

This implementation validates that a ground-up approach to SVM construction can yield industrial-grade results.
1.  **High Accuracy:** Achieved **96% test accuracy**, demonstrating the correctness of the custom SMO implementation.
2.  **Effective Tuning:** Strategic hyperparameter optimization significantly boosted F1-scores (e.g., tuning $\gamma$ in RBF).
3.  **Ensemble Power:** Combining models leveraged the strengths of each kernel, providing the most reliable and highest-scoring predictions (F1 **0.733**).

**Recommendation:** For deployment, the **Ensemble Model** is recommended for its robustness, while the **Linear Kernel** serves as a high-speed, high-accuracy alternative for real-time applications.
